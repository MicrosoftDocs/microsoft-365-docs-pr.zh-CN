---
title: 高级搜寻架构中的 DeviceInfo 表
description: 了解高级搜寻架构的 DeviceInfo 表中的操作系统、计算机名称和其他计算机信息
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， Microsoft 威胁防护， microsoft 365， mtp， m365， 搜索， 查询， 遥测， 架构参考， kusto， 表格， 列， 数据类型， 说明， machineinfo， DeviceInfo， 设备， 计算机， 操作系统， 平台， 用户
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 46efb531331cf76472c67c769c96804d11fb9e4b
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51055274"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 365 Defender



高级 `DeviceInfo` 搜寻 [架构中的](advanced-hunting-overview.md) 表包含有关组织中设备的信息，包括操作系统版本、活动用户和计算机名称。 使用此参考来构建从此表返回信息的查询。

有关高级搜寻架构中其他表的信息，请[参阅高级搜寻参考](advanced-hunting-schema-tables.md)。

| 列名称 | 数据类型 | 说明 |
|-------------|-----------|-------------|
| `Timestamp` | datetime | 记录事件的日期和时间 |
| `DeviceId` | string | 服务中的计算机的唯一标识符 |
| `DeviceName` | string | 计算机的完全限定域名 (FQDN) |
| `ClientVersion` | string | 计算机上运行的终结点代理或传感器的版本 |
| `PublicIP` | string | 已载入计算机用于连接到 Microsoft Defender for Endpoint 服务的公共 IP 地址。 这可能是计算机本身、NAT 设备或代理的 IP 地址 |
| `OSArchitecture` | string | 计算机上运行的操作系统的体系结构 |
| `OSPlatform` | string | 计算机上运行的操作系统平台。 这表示特定操作系统，包括同一系列中的变体，如 Windows 10 和 Windows 7 |
| `OSBuild` | string | 计算机上运行的操作系统的生成版本 |
| `IsAzureADJoined` | boolean | 指示计算机是否已加入 Azure Active Directory 的布尔值指示器 |
| `AadObjectId` | string | Azure AD 中设备的唯一标识符 |
| `LoggedOnUsers` | string | 事件时以 JSON 数组格式登录的所有用户的列表 |
| `RegistryDeviceTag` | string | 通过注册表添加的机器标记 |
| `ReportId` | long | 基于重复计数器的事件标识符。 若要标识唯一事件，此列必须与 DeviceName 和 Timestamp 列一起使用 |
|`AdditionalFields` | string | 有关 JSON 数组格式的事件的其他信息 |
| `OSVersion` | string | 计算机上运行的操作系统版本 |
| `MachineGroup` | string | 计算机的机器组。 基于角色的访问控制使用该组来确定对计算机的访问权限 |

`DeviceInfo`该表提供基于检测信号的设备信息，检测信号是定期报告或来自设备的信号。 每隔十五分钟，设备发送包含经常更改的属性（如 ）的部分检测信号 `LoggedOnUsers` 。 每天发送一次包含设备属性的完整检测信号。

可以使用以下示例查询获取设备的最新状态：

```kusto
// Get latest information on user/device
DeviceInfo
| where DeviceName == "example" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId 
```

## <a name="related-topics"></a>相关主题
- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [使用共享查询](advanced-hunting-shared-queries.md)
- [跨设备、电子邮件、应用和标识进行查寻](advanced-hunting-query-emails-devices.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)