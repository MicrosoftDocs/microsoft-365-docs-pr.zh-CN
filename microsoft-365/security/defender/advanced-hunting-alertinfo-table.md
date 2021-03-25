---
title: 高级搜寻架构中的 AlertInfo 表
description: 了解高级搜寻架构的 AlertInfo 表中的警报生成事件
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， Microsoft 威胁防护， microsoft 365， mtp， m365， 搜索， 查询， 遥测， 架构参考， kusto， 表格， 列， 数据类型， 说明， AlertInfo， 警报， 严重性， 类别， MITRE， ATT&CK， Microsoft Defender ATP， MDATP， Office 365 ATP， Microsoft Cloud App Security， MCAS， 和 Azure ATP
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
ms.openlocfilehash: bc81c9c8406a6e70df6ec38e3896ef9977a120e2
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51055294"
---
# <a name="alertinfo"></a>AlertInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 365 Defender



高级 `AlertInfo` 搜寻架构 [中的](advanced-hunting-overview.md) 表包含有关来自 Microsoft Defender for Endpoint、Microsoft Defender for Office 365、Microsoft Cloud App Security 和 Microsoft Defender for Identity 的警报的信息。 使用此参考来构建从此表返回信息的查询。

有关高级搜寻架构中其他表的信息，请[参阅高级搜寻参考](advanced-hunting-schema-tables.md)。

| 列名称 | 数据类型 | 说明 |
|-------------|-----------|-------------|
| `Timestamp` | datetime | 记录事件的日期和时间 |
| `AlertId` | string | 警报的唯一标识符 |
| `Title` | string | 警报的标题 |
| `Category` | string | 由警报标识的威胁指示器或违反活动的类型 |
| `Severity` | string | 指示警报所标识的威胁指示器或违反活动的潜在影响（高、中或低） |
| `ServiceSource` | string | 提供警报信息的产品或服务 |
| `DetectionSource` | string | 标识值得注意的组件或活动的检测技术或传感器 |
| `AttackTechniques` | string | MITRE ATT&触发警报的活动相关的 CK 技术 |

## <a name="related-topics"></a>相关主题
- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [使用共享查询](advanced-hunting-shared-queries.md)
- [跨设备、电子邮件、应用和标识进行查寻](advanced-hunting-query-emails-devices.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)