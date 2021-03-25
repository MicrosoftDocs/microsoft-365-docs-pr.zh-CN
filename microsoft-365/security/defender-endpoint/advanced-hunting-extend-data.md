---
title: 使用正确的设置扩展高级搜寻范围
description: 检查 Windows 设备上审核设置和其他设置，以帮助确保你在高级搜寻中获得最全面的数据
keywords: 高级搜寻， 事件， 透视， 实体， 审核设置， 用户帐户管理， 安全组管理， 威胁搜寻， 网络威胁搜寻， 搜索， 查询， 遥测， mdatp， Microsoft Defender ATP， Microsoft Defender for Endpoint， Windows Defender， Windows Defender ATP， Windows Defender 高级威胁防护
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
ms.date: 10/10/2020
ms.technology: mde
ms.openlocfilehash: 60e8710415e328d06fac4c02e428094e5e4bcc92
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056258"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>使用正确的设置扩展高级搜寻范围

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[高级](advanced-hunting-overview.md) 搜寻依赖于来自整个组织的数据。 若要尽可能获取最全面的数据，请确保在相应的数据源中具有正确的设置。

## <a name="advanced-security-auditing-on-windows-devices"></a>Windows 设备上的高级安全审核

打开这些高级审核设置，以确保获取有关设备上活动的数据，包括本地帐户管理、本地安全组管理和服务创建。

Data | 说明 | 架构表 | 如何配置
-|-|-|-
帐户管理 | 捕获为指示本地帐户创建、删除和其他与帐户相关的活动 `ActionType` 的各种值的事件 | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - 部署高级安全审核策略 [：审核用户帐户管理](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [了解高级安全审核策略](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)
安全组管理 | 捕获为指示本地安全组创建和其他本地组管理活动 `ActionType` 的各种值的事件 | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - 部署高级安全审核策略： [审核安全组管理](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [了解高级安全审核策略](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)
服务安装 | 使用 值 捕获的事件 `ActionType` `ServiceInstalled` ，指示已创建服务 | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - 部署高级安全审核策略： [审核安全系统扩展](https://docs.microsoft.com/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [了解高级安全审核策略](https://docs.microsoft.com/windows/security/threat-protection/auditing/advanced-security-auditing)

## <a name="related-topics"></a>相关主题

- [高级搜寻概述](advanced-hunting-overview.md)
- [了解查询语言](advanced-hunting-query-language.md)
- [了解架构](advanced-hunting-schema-reference.md)
- [处理查询结果](advanced-hunting-query-results.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)
- [自定义检测概述](overview-custom-detections.md)