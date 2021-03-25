---
title: 高级搜寻架构参考
description: 了解高级搜寻架构中的表，以了解可以运行威胁搜寻查询的数据。
keywords: 高级搜寻， 威胁搜寻， 网络威胁搜寻， mdatp， microsoft defender atp， wdatp 搜索， 查询， 遥测， 架构参考， kusto， 表， 数据
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
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: 7516744b72bc86bbf8f776adde690d75f057efd5
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51055671"
---
# <a name="understand-the-advanced-hunting-schema"></a>了解高级搜寻架构

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

高级 [搜寻](advanced-hunting-overview.md) 架构由多个表组成，这些表提供事件信息或有关设备和其他实体的信息。 若要高效构建跨多个表的查询，需要了解高级搜寻架构中的表和列。

## <a name="get-schema-information-in-the-security-center"></a>在安全中心获取架构信息
构造查询时，请使用内置架构参考快速获取有关架构中每个表的以下信息：

- **表** 说明 表中包含的数据类型以及该数据的来源。
- **列**- 表中的所有列。
- **操作** 类型 - 列中可能 `ActionType` 的值，表示表支持的事件类型。 这仅针对包含事件信息的表提供。
- **示例** 查询 - 具有表利用方式的示例查询。

### <a name="access-the-schema-reference"></a>访问架构引用
若要快速访问架构引用，请选择架构表示中表名称旁边的"查看引用"操作。 还可以选择" **架构引用** "来搜索表。

![显示如何访问门户内架构参考的图像](images/ah-reference.png)

## <a name="learn-the-schema-tables"></a>了解架构表

以下引用列出了高级搜寻架构中的所有表。 每个表名称链接到描述该表的列名称的页面。

表和列名称还会在 Microsoft Defender 安全中心内以高级搜寻屏幕上的架构表示形式列出。

| 表名 | 说明 |
|------------|-------------|
| **[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)** | Microsoft Defender 安全中心警报 |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | 设备信息，包括操作系统信息 |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | 设备的网络属性，包括适配器、IP 和 MAC 地址，以及连接的网络和域 |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | 过程创建和相关事件 |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | 网络连接和相关事件 |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | 文件创建、修改和其他文件系统事件 |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | 创建和修改注册表项 |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | 登录和其他身份验证事件 |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | DLL 加载事件 |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | 多个事件类型，包括由安全控件（如 Microsoft Defender 防病毒和 Exploit Protection）触发的事件 |
| **[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)** | 从终结点上的证书验证事件获取的已签名文件的证书信息 |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | 设备上安装的软件清单，包括其版本信息和停止支持状态 |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | 在设备上发现的软件漏洞以及可解决每个漏洞的可用安全更新列表 |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | 公开披露的漏洞的知识库，包括攻击代码是否已公开 |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | 威胁和漏洞管理评估事件，指示设备上的各种安全配置的状态 |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | 威胁和漏洞管理用于评估设备的各种安全配置的知识库；包括各种标准和基准的映射 |


## <a name="related-topics"></a>相关主题
- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [处理查询结果](advanced-hunting-query-results.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)
- [自定义检测概述](overview-custom-detections.md)
- [高级搜寻数据架构更改](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)