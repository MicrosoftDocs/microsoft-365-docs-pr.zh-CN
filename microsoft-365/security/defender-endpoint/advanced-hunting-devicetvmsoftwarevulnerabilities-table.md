---
title: 高级搜寻架构中的 DeviceTvmSoftwareVulnerabilities 表
description: 了解设备上发现的软件漏洞，以及解决高级搜寻架构的 DeviceTvmSoftwareVulnerabilities 表中每个漏洞的可用安全更新列表。
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， mdatp， microsoft defender atp， wdatp 搜索， 查询， 遥测， 架构参考， kusto， 表， 列， 数据类型， 说明， 威胁 & 漏洞管理， TVM， 设备管理， 软件， 清单， 漏洞， CVE ID， OS DeviceTvmSoftwareInventoryVulnerabilities
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6b38297cd0fa2e931619ff9c0557d2ae868c7aa4
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056392"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

高级 `DeviceTvmSoftwareVulnerabilities` 搜寻架构中的表包含已安装 [软件&](next-gen-threat-and-vuln-mgt.md) 漏洞的威胁和漏洞管理列表。 此表还包括操作系统信息、CVE ID 和漏洞严重性信息。 例如，您可以使用此表来搜寻涉及其软件中具有严重漏洞的设备的事件。 使用此参考来构建从该表返回信息的查询。

>[!NOTE]
>和 `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` 表已替换 `DeviceTvmSoftwareInventoryVulnerabilities` 表。 前两个表一起包含可用于帮助通知漏洞管理活动的更多列。

有关高级搜寻架构中其他表的信息，请参阅[高级搜寻参考](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)。

| 列名称 | 数据类型 | 说明 |
|-------------|-----------|-------------|
| `DeviceId` | string | 服务中设备的唯一标识符 |
| `DeviceName` | string | 设备的完全限定 (FQDN) FQDN |
| `OSPlatform` | string | 在设备上运行的操作系统的平台。 这表示特定操作系统，包括同一系列中的变体，如 Windows 10 和 Windows 7。 |
| `OSVersion` | string | 在设备上运行的操作系统的版本 |
| `OSArchitecture` | string | 在设备上运行的操作系统的体系结构 |
| `SoftwareVendor` | string | 软件供应商的名称 |
| `SoftwareName` | string | 软件产品的名称 |
| `SoftwareVersion` | string | 软件产品版本号 |
| `CveId` | string | 通用漏洞披露 (CVE) 系统下分配给安全漏洞的唯一标识符 |
| `VulnerabilitySeverityLevel` | string | 基于 CVSS 分数和受威胁环境影响的动态因素为安全漏洞分配的严重性级别 |
| `RecommendedSecurityUpdate` | string | 软件供应商提供的用于解决漏洞的安全更新的名称或说明 |
| `RecommendedSecurityUpdateId` | string | 相应指南或知识库的适用安全更新或标识符的标识符 (KB) 文章 |



## <a name="related-topics"></a>相关主题

- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [了解架构](advanced-hunting-schema-reference.md)
- [威胁和漏洞管理概述](next-gen-threat-and-vuln-mgt.md)