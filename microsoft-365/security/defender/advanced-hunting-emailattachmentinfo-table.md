---
title: 高级搜寻架构中的 EmailAttachmentInfo 表
description: 在高级搜寻架构的 EmailAttachmentInfo 表中，了解电子邮件附件信息
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， Microsoft 365 Defender， microsoft 365， m365， 搜索， 查询， 遥测， 架构参考， kusto， 表格， 列， 数据类型， 说明， EmailAttachmentInfo， 网络消息 ID， 发件人， 收件人， 附件 ID， 附件名称， 恶意软件裁定
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
mms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 961474fa62981364919ae3bf482a886eb9a5e821
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935493"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 365 Defender



高级 `EmailAttachmentInfo` 搜寻[架构中的](advanced-hunting-overview.md)表包含有关由 Microsoft Defender for Office 365 处理的电子邮件附件的信息。 使用此参考来构建从此表返回信息的查询。

有关高级搜寻架构中其他表的信息，请[参阅高级搜寻参考](advanced-hunting-schema-tables.md)。

| 列名称 | 数据类型 | 说明 |
|-------------|-----------|-------------|
| `Timestamp` | datetime | 记录事件的日期和时间 |
| `NetworkMessageId` | string | 由用户生成的电子邮件的唯一Microsoft 365 |
| `SenderFromAddress` | string | 发件人标题中的发件人电子邮件地址（电子邮件收件人在其电子邮件客户端上可以看到） |
| `SenderDisplayName` | string | 通讯簿中显示的发件人姓名，通常是给定或名字、中间名首字母和姓氏或姓氏的组合 |
| `SenderObjectId` | string | Azure AD 中发件人帐户的唯一标识符 |
| `RecipientEmailAddress` | string | 收件人的电子邮件地址，或通讯组列表扩展后收件人的电子邮件地址 |
| `RecipientObjectId` | string | Azure AD 中电子邮件收件人的唯一标识符 |
| `FileName` | string | 录制操作所应用到的文件的名称 |
| `FileType` | string | 文件扩展名类型 |
| `SHA256` | string | 录制操作所应用到的文件的 SHA-256。 通常不会填充此字段 — 可用时使用 SHA1 列。 |
| `ThreatTypes` | string | 关于电子邮件是否包含恶意软件、网络钓鱼或其他威胁的电子邮件筛选堆栈裁定 |
| `ThreatNames` | string | 找到的恶意软件或其他威胁的检测名称 |
| `DetectionMethods` | string | 用于检测电子邮件中的恶意软件、网络钓鱼或其他威胁的方法 |
| `ReportId` | long | 基于重复计数器的事件标识符。 若要标识唯一事件，此列必须与 DeviceName 和 Timestamp 列一起使用。 |

## <a name="related-topics"></a>相关主题
- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [使用共享查询](advanced-hunting-shared-queries.md)
- [跨设备、电子邮件、应用和标识进行查寻](advanced-hunting-query-emails-devices.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)
