---
title: 高级搜寻的查询最佳做法
description: 了解如何在使用高级搜寻时构建快速、高效且无错误的威胁搜寻查询
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， mdatp， microsoft defender atp， wdatp 搜索， 查询， 遥测， 自定义检测， 架构， kusto， 避免超时， 命令行， 进程 ID
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6259ac1c5804b244c825a1bb54401640fdefaf34
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51055491"
---
# <a name="advanced-hunting-query-best-practices"></a>高级搜寻查询最佳做法

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-bestpractices-abovefoldlink)

## <a name="optimize-query-performance"></a>优化查询性能

应用这些建议可更快地获取结果，并避免在运行复杂查询时出现超时。

- 尝试新查询时，请始终使用 `limit` 来避免出现过大的结果集。 还可以使用 `count` 初步评估结果集的大小。
- 首先使用时间筛选器。 理想情况下，将查询限制为七天。
- 将预期会删除大多数数据的筛选器放在查询的开头，紧跟在时间筛选器后面。
- 查找完整标记时，请使用 `has` 运算符覆盖 `contains`。
- 查找特定的列，而不是在所有列上运行全文搜索。
- 联接表时，先指定行数较少的表。
- 仅 `project` 已联接表的所需列。

>[!TIP]
>有关提高查询性能的更多指导，请参阅 [Kusto 查询最佳做法](https://docs.microsoft.com/azure/kusto/query/best-practices)。

## <a name="query-tips-and-pitfalls"></a>查询提示和易犯错误

### <a name="queries-with-process-ids"></a>通过进程 ID 查询

进程 ID (PID) 在 Windows 中回收，并重新用于新进程。 它们本身不能用作特定进程的唯一标识符。 若要获取特定设备上进程的唯一标识符，请使用进程 ID 和进程创建时间。 当围绕进程加入或汇总数据时，请包含设备标识符 (或) 、进程 ID (或) 以及进程创建时间 (或 `DeviceId` `DeviceName` `ProcessId` `InitiatingProcessId` `ProcessCreationTime` `InitiatingProcessCreationTime`) 。

以下示例查询将查找通过端口 445 (SMB) 访问 10 个以上 IP 地址（可能扫描文件共享）的进程。

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

该查询按 `InitiatingProcessId` 和 `InitiatingProcessCreationTime` 进行汇总，以便查看单个进程，而不会混用具有同一进程 ID 的多个进程。

### <a name="queries-with-command-lines"></a>通过命令行查询

命令行可能会有所不同。 在适用的情况下，筛选文件名称，并执行模糊匹配。

有很多方法可以构造命令行来完成任务。 例如，攻击者可以使用环境变量或引号引用带/不带路径、不带文件扩展名的映像文件。 此外，攻击者还可以更改参数的顺序或添加多个引号和空格。

若要使用命令行创建更持久的查询，请采用以下做法：

- 通过匹配文件名字段来识别已知进程（例如 *net.exe* 或 *psexec.exe*），而不是在命令行字段上进行筛选。
- 查询命令行参数时，请勿按特定顺序查找多个不相关参数的完全匹配。 而是使用正则表达式或使用多个单独的 Contains 运算符。
- 使用不区分大小写的匹配项。 例如，使用 `=~` 、 `in~` 和 `contains` ，而不是 、 `==` `in` 和 `contains_cs`
- 为了减轻 DOS 命令行混淆技术的影响，请考虑删除引号，将逗号替换为空格，并用单个空格替换多个连续的空格。 请注意，还有一些更复杂的 DOS 混淆技术需要适用其他方法，但这些方法可以帮助解决最常见的问题。

下面的示例演示了构造查询的各种方式，该查询将查找 *net.exe* 文件以停止 Windows Defender 防火墙服务：

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on filename, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc" 

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc" 
```

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-bestpractices-belowfoldlink)

## <a name="related-topics"></a>相关主题

- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [了解架构](advanced-hunting-schema-reference.md)
- [处理查询结果](advanced-hunting-query-results.md)
- [自定义检测概述](overview-custom-detections.md)