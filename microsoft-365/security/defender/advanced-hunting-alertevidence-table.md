---
title: 高级搜寻架构中的 AlertEvidence 表
description: 了解与高级搜寻架构的 AlertEvidence 表中的警报关联的信息
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， Microsoft 365 Defender， microsoft 365， m365， 搜索， 查询， 遥测， 架构参考， kusto， 表格， 列， 数据类型， 说明， AlertInfo， 警报， 实体， 证据， 文件， IP 地址， 设备， 计算机， 用户， 帐户
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
ms.openlocfilehash: 5ecab217a6181096e4689d78fa2bdddc0a767d0d
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51932579"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 365 Defender

高级搜寻架构中的表包含与 `AlertEvidence` 来自 Microsoft Defender for Endpoint、Microsoft Defender for Office 365、Microsoft Cloud App Security 和 Microsoft Defender for Identity 的警报相关联的各种实体（文件、IP 地址、URL、用户或设备）[](advanced-hunting-overview.md)的信息。 使用此参考来构建从此表返回信息的查询。

有关高级搜寻架构中其他表的信息，请[参阅高级搜寻参考](advanced-hunting-schema-tables.md)。

| 列名称 | 数据类型 | 说明 |
|-------------|-----------|-------------|
| `Timestamp` | datetime | 记录事件的日期和时间 |
| `AlertId` | string | 警报的唯一标识符 |
| `ServiceSource` | string | 提供警报信息的产品或服务 |
| `EntityType` | string | 对象类型，例如文件、进程、设备或用户 |
| `EvidenceRole` | string | 如何在警报中涉及实体，以指示它是否受到影响或只是相关 |
| `EvidenceDirection` | string | 指示实体是网络连接的来源还是目标 |
| `FileName` | string | 录制操作所应用到的文件的名称 |
| `FolderPath` | string | 包含已记录操作所应用到的文件的文件夹 |
| `SHA1` | string | 录制操作所应用到的文件的 SHA-1 |
| `SHA256` | string | 录制操作所应用到的文件的 SHA-256。 通常不填充此字段 -使用 SHA1 列（如果可用）。 |
| `FileSize` | int | 文件大小（以字节为单位） |
| `ThreatFamily` | string | 可疑或恶意文件或进程的分类依据的恶意软件系列 |
| `RemoteIP` | string | 连接到的 IP 地址 |
| `RemoteUrl` | string | 连接到的 URL 或完全限定域名 (FQDN) |
| `AccountName` | string | 帐户的用户名 |
| `AccountDomain` | string | 帐户的域 |
| `AccountSid` | string | 帐户 (SID) 安全标识符 |
| `AccountObjectId` | string | Azure Active Directory |
| `AccountUpn` | string | 帐户 (UPN) 用户主体名称 |
| `DeviceId` | string | 服务中设备的唯一标识符 |
| `DeviceName` | string | 计算机的完全限定域名 (FQDN) |
| `LocalIP` | string | 分配给通信期间使用的本地设备的 IP 地址 |
| `NetworkMessageId` | string | 由 Office 365 生成的电子邮件的唯一标识符 |
| `EmailSubject` | string | 电子邮件主题 |
| `ApplicationId` | string | 应用程序的唯一标识符 |
| `Application` | string | 执行录制的操作的应用程序 |
| `ProcessCommandLine` | string | 用于创建新过程的命令行 |
| `AdditionalFields` | string | 有关 JSON 数组格式的事件的其他信息 |
| `RegistryKey` |string | 已记录操作所应用到的注册表项 |
| `RegistryValueName` |string | 已记录操作所应用到的注册表值的名称 |
| `RegistryValueData` |string | 已记录操作应用于的注册表值的数据 |

## <a name="related-topics"></a>相关主题
- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [使用共享查询](advanced-hunting-shared-queries.md)
- [跨设备、电子邮件、应用和标识进行查寻](advanced-hunting-query-emails-devices.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)
