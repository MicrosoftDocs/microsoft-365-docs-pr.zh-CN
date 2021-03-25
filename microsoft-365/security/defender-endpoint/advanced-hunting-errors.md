---
title: 处理 Microsoft Defender ATP 高级搜寻中的错误
description: 了解使用高级搜寻时显示的错误
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， mdatp， microsoft defender atp， wdatp， m365， 搜索， 查询， 遥测， 架构， kusto， 超时， 资源， 错误， 未知错误
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 64c8a13ba9e8110d761245315969b9e1882b3448
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056261"
---
# <a name="handle-advanced-hunting-errors"></a>处理高级搜寻错误

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhunting-abovefoldlink)

高级搜寻显示用于通知语法错误和查询达到预定义限制 [的错误](advanced-hunting-limits.md)。 有关如何解决或避免错误的提示，请参阅下表。 

| 错误类型 | 原因 | 解决方案 | 错误消息示例 |
|--|--|--|--|
| 语法错误 | 查询包含无法识别的名称，包括对不存在的运算符、列、函数或表的引用。 | 确保对 [Kusto 运算符和函数的引用](https://docs.microsoft.com/azure/data-explorer/kusto/query/) 正确无误。 检查 [架构，](advanced-hunting-schema-reference.md) 了解正确的高级搜寻列、函数和表。 将变量字符串括在引号中，以便识别它们。 编写查询时，请使用来自查询的自动完成IntelliSense。 | `A recognition error occurred.` |
| 语义错误 | 虽然查询使用有效的运算符、列、函数或表名称，但在其结构和结果逻辑中都有错误。 在某些情况下，高级搜寻可标识导致错误的特定运算符。 | 检查查询结构中的错误。 有关指南 [，请参阅 Kusto](https://docs.microsoft.com/azure/data-explorer/kusto/query/) 文档。 编写查询时，请使用来自查询的自动完成IntelliSense。 |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| 超时 | 查询只能在超时前的 [有限时段内运行](advanced-hunting-limits.md)。运行复杂查询时，此错误可能更频繁地发生。 | [优化查询](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| CPU 限制 | 同一租户中的查询已超出基于租户大小分配的 [CPU](advanced-hunting-limits.md) 资源。 | 该服务每 15 分钟、每天检查一次 CPU 资源使用率，在使用率超过分配的限制的 10% 后显示警告。 如果使用率达到 100%，该服务将阻止查询，直到下一个每日或 15 分钟周期之后。 [优化查询以避免达到 CPU 限制](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| 超过结果大小限制  | 查询的结果集大小已超出最大限制。 如果数据大小结果集，导致在 10，000 条记录的限制下截断不能减小到可接受的大小，则可能会发生此错误。 具有多个包含可调整内容列的结果更有可能受到此错误的影响。 | [优化查询](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| 资源消耗过多 | 查询占用了大量资源，并且已停止完成。 在某些情况下，高级搜寻可标识未优化的特定运算符。 | [优化查询](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| 未知错误 | 由于未知原因，查询失败。 | 再次尝试运行查询。 如果查询继续返回未知错误，请通过门户联系 Microsoft。 | `An unexpected error occurred during query execution. Please try again in a few minutes.`

## <a name="related-topics"></a>相关主题
- [高级搜寻最佳做法](advanced-hunting-best-practices.md)
- [服务限制](advanced-hunting-limits.md)
- [了解架构](advanced-hunting-schema-reference.md)
- [Kusto 查询语言概述](https://docs.microsoft.com/azure/data-explorer/kusto/query/)