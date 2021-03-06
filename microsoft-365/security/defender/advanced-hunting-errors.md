---
title: 处理 Defender 高级搜寻Microsoft 365错误
description: 了解使用高级搜寻时显示的错误
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， Microsoft 365 Defender， microsoft 365， m365， 搜索， 查询， 遥测， 架构， kusto， 超时， 资源， 错误， 未知错误， 限制， 配额， 参数， 分配
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 32d50103c6476a89f24568edeea75a206e37e227
ms.sourcegitcommit: 7cc2be0244fcc30049351e35c25369cacaaf4ca9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2021
ms.locfileid: "51952676"
---
# <a name="handle-advanced-hunting-errors"></a>处理高级搜寻错误

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint


高级搜寻显示错误，以通知语法错误以及查询命中预定义 [配额和使用参数时](advanced-hunting-limits.md)。 有关如何解决或避免错误的提示，请参阅下表。

| 错误类型 | 原因 | 解决方案 | 错误消息示例 |
|--|--|--|--|
| 语法错误 | 查询包含无法识别的名称，包括对不存在的运算符、列、函数或表的引用。 | 确保对 [Kusto 运算符和函数的引用](/azure/data-explorer/kusto/query/) 正确无误。 检查 [架构，](advanced-hunting-schema-tables.md) 了解正确的高级搜寻列、函数和表。 将变量字符串括在引号中，以便识别它们。 编写查询时，请使用来自查询的自动完成IntelliSense。 | `A recognition error occurred.` |
| 语义错误 | 虽然查询使用有效的运算符、列、函数或表名称，但在其结构和结果逻辑中都有错误。 在某些情况下，高级搜寻可标识导致错误的特定运算符。 | 检查查询结构中的错误。 有关指南 [，请参阅 Kusto](/azure/data-explorer/kusto/query/) 文档。 编写查询时，请使用来自查询的自动完成IntelliSense。 |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| 超时 | 查询只能在超时前的 [有限时段内运行](advanced-hunting-limits.md)。运行复杂查询时，此错误可能更频繁地发生。 | [优化查询](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| CPU 限制 | 同一租户中的查询已超出基于租户大小分配的 [CPU](advanced-hunting-limits.md) 资源。 | 该服务每 15 分钟、每天检查一次 CPU 资源使用率，在使用率超过分配的配额的 10% 后显示警告。 如果使用率达到 100%，该服务将阻止查询，直到下一个每日或 15 分钟周期之后。 [优化查询以避免达到 CPU 配额](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| 超过结果大小限制  | 查询的结果集的大小已超出最大大小。 如果数据大小结果集，导致在 10，000 条记录的限制下截断不能减小到可接受的大小，则可能会发生此错误。 具有多个包含可调整内容列的结果更有可能受到此错误的影响。 | [优化查询](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| 资源消耗过多 | 查询占用了大量资源，并且已停止完成。 在某些情况下，高级搜寻可标识未优化的特定运算符。 | [优化查询](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| 未知错误 | 由于未知原因，查询失败。 | 再次尝试运行查询。 如果查询继续返回未知错误，请通过门户联系 Microsoft。 | `An unexpected error occurred during query execution. Please try again in a few minutes.`



## <a name="related-topics"></a>相关主题
- [高级搜寻最佳做法](advanced-hunting-best-practices.md)
- [配额和使用参数](advanced-hunting-limits.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [Kusto 查询语言概述](/azure/data-explorer/kusto/query/)