---
title: 评估攻击面减少规则
description: 了解攻击面减少如何使用自定义演示工具阻止和阻止攻击。
keywords: 攻击面减少， hips， 主机入侵防护系统， 保护规则， 反攻击， 攻击， 感染防护， 评估， 测试， 演示
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: levinec
ms.author: ellevin
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 13b1ac5f71f2bc24ad6f52af6722e12fab935270
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056341"
---
# <a name="evaluate-attack-surface-reduction-rules"></a>评估攻击面减少规则

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)

攻击面减少规则有助于防止恶意软件通常用来危害设备或网络的操作。 为运行以下任一版本的 Windows 的设备设置攻击面减少规则：

- Windows 10 专业 [版版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 或更高版本
- Windows 10 企业版 [版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 或更高版本
- Windows Server [版本 1803 (半年 ](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803) 频道) 或更高版本
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

了解如何通过启用审核模式直接在你的组织中测试功能来评估攻击面减少规则。

> [!TIP]
> 还可以访问 Microsoft Defender for Endpoint 演示方案[](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground)网站，demo.wd.microsoft.com 确认功能是否正常工作并查看其工作方式。

## <a name="use-audit-mode-to-measure-impact"></a>使用审核模式衡量影响

在审核模式下启用攻击面减少规则，以查看在功能完全启用时可能阻止的应用记录。 测试此功能在组织中如何工作，以确保它不会影响你的业务线应用。 您还可以了解规则在正常使用期间将多久发生一次。

若要在审核模式下启用攻击面减少规则，请使用以下 PowerShell cmdlet：

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

其中 `<rule ID>` 是 [攻击面减少规则的 GUID 值](attack-surface-reduction.md#attack-surface-reduction-rules)。

若要在审核模式下启用所有添加的攻击面减少规则，请使用以下 PowerShell cmdlet：

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> 如果你想要完全审核攻击面减少规则在组织中如何工作，你将需要使用管理工具将此设置部署到你的网络 (设备) 。

您还可以使用组策略、Intune 或移动设备管理 (MDM) 配置服务提供程序 () 配置和部署设置。 在主要的攻击 [面减少规则文章中了解更多信息](attack-surface-reduction.md) 。

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>在 Windows 事件查看器中查看攻击面减少事件

若要查看已阻止的应用，请打开事件查看器，并筛选 Microsoft-Windows-Windows Defender/操作日志中的事件 ID 1121。 下表列出了所有网络保护事件。

事件 ID | 说明
-|-
 5007 | 更改设置时的事件
 1121 | 攻击面减少规则在阻止模式下触发时的事件
 1122 | 在审核模式下触发攻击面减少规则时的事件

## <a name="customize-attack-surface-reduction-rules"></a>自定义攻击面减少规则

在评估过程中，你可能希望单独配置每个规则，或者将某些文件和进程排除在功能评估外。

有关 [使用管理工具（](customize-attack-surface-reduction.md) 包括组策略和 MDM CSP 策略）配置功能的信息，请参阅自定义攻击面减少规则。

## <a name="see-also"></a>另请参阅

* [使用攻击面减少规则减少攻击面](attack-surface-reduction.md)
* [使用审核模式评估Windows Defender](audit-windows-defender.md)
* [攻击面减少常见问题解答](attack-surface-reduction.md)