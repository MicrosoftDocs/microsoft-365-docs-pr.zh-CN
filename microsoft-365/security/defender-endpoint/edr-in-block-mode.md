---
title: 阻止模式下的终结点检测和响应
description: 了解阻止模式下的终结点检测和响应
keywords: Microsoft Defender ATP，阻止模式下的 EDR，被动模式阻止
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.custom:
- next-gen
- edr
ms.date: 01/26/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: b31e7aeb9178cb6021434319e55ddef927d7c263
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165869"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>在阻止模式下， (EDR) 终结点检测和响应

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>什么是阻止模式下的 EDR？

[在阻止模式下](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) (EDR) 终结点检测和响应功能可提供对恶意项目的保护，即使 Microsoft Defender 防病毒在被动模式下运行。 打开后，阻止模式下的 EDR 将阻止在设备上检测到的恶意项目或行为。 阻止模式下的 EDR 在后台工作，可修正在泄露后检测到的恶意项目。 

阻止模式下的 EDR 也与威胁和漏洞& [集成](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)。 如果尚未启用 EDR，组织[](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-security-recommendation)的安全团队会获得一条安全建议，以在阻止模式下打开它。 

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="建议在阻止模式下打开 EDR":::

> [!NOTE]
> 若要获取最佳保护，请确保为终结点基线 **[部署 Microsoft Defender。](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)**

## <a name="what-happens-when-something-is-detected"></a>检测到某些内容时会发生什么情况？

当在阻止模式下打开 EDR 并检测到恶意项目时，适用于终结点的 Microsoft Defender 将阻止并修正这些项目。 你将在操作中心看到检测状态为"已阻止"或 **"** 已阻止"为已完成 [操作](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/respond-machine-alerts#check-activity-details-in-action-center)。

下图显示了在阻止模式下通过 EDR 检测并阻止的不需要软件的实例：

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="阻止模式下的 EDR 检测到某些内容":::


## <a name="enable-edr-in-block-mode"></a>在阻止模式下启用 EDR

> [!IMPORTANT]
> 在阻止 [模式下打开](#requirements-for-edr-in-block-mode) EDR 之前，请确保满足要求。

1. 转到 Microsoft Defender 安全中心 [https://securitycenter.windows.com](https://securitycenter.windows.com) () 并登录。 

2. 选择 **"设置**  >  **""高级功能"。**

3. 在阻止 **模式下打开 EDR。**

> [!NOTE]
> 阻止模式下的 EDR 只能在 Microsoft Defender 安全中心中打开。 不能使用注册表项、Intune 或组策略在阻止模式下启用或禁用 EDR。

## <a name="requirements-for-edr-in-block-mode"></a>阻止模式下的 EDR 要求

|要求  |详细信息  |
|---------|---------|
|权限 |在 Azure Active Directory 中分配的全局管理员或 [安全管理员角色](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal)。 请参阅 [基本权限](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/basic-permissions)。 |
|操作系统     |以下版本之一： <br/>- Windows 10 (所有版本)  <br/>- Windows Server 版本 1803 或更高版本 <br/>- Windows Server 2019         |
|Windows E5 注册     |Windows E5 包含在以下订阅中： <br/>- Microsoft 365 E5 <br/>- Microsoft 365 E3 以及 Identity &威胁防护产品 <br/><br/>请参阅[每个](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview?view=o365-worldwide&preserve-view=true#components)[计划的组件和功能](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)。       |
|Microsoft Defender 防病毒  |必须在主动模式或被动模式下安装并运行 Microsoft Defender 防病毒。  (可以将 Microsoft Defender 防病毒与非 Microsoft 防病毒解决方案一同使用。) 确认 Microsoft Defender 防病毒 [处于主动或被动模式](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode)。 |
|云保护 |确保配置了 Microsoft Defender 防病毒，以启用 [云保护](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus)。 |
|Microsoft Defender 防病毒反恶意软件客户端 |确保你的客户端是最新的。 使用 PowerShell 以管理员角色运行 [Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus?view=win10-ps&preserve-view=true) cmdlet。 在 **AMProductVersion** 行中，应该会看到 **4.18.2001.10** 或更上方。 |
|Microsoft Defender 防病毒引擎 |确保你的引擎是最新的。 使用 PowerShell 以管理员角色运行 [Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus?view=win10-ps&preserve-view=true) cmdlet。 在 **AMEngineVersion** 行中，应该会看到 **1.1.16700.2** 或更上方。 |

> [!IMPORTANT]
> 若要获取最佳保护值，请确保防病毒解决方案配置为接收定期更新和基本功能，并且已配置排除 [项](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus)。 阻止模式下的 EDR 遵守为 Microsoft Defender 防病毒定义的排除项。

## <a name="frequently-asked-questions"></a>常见问题解答 

### <a name="do-i-need-to-turn-edr-in-block-mode-on-even-when-i-have-microsoft-defender-antivirus-running-on-devices"></a>我是否需要在阻止模式下打开 EDR，即使我在设备上运行 Microsoft Defender 防病毒？

我们建议在阻止模式下保持 EDR 处于打开状态，无论 Microsoft Defender 防病毒是在被动模式下运行还是处于活动模式。 块模式下的 EDR 通过 Microsoft Defender for Endpoint 提供另一层防御。 它允许 Defender for Endpoint 根据攻破后的行为 EDR 检测采取操作。 

### <a name="will-edr-in-block-mode-have-any-impact-on-a-users-antivirus-protection"></a>阻止模式下的 EDR 是否将影响用户的防病毒保护？ 

阻止模式下的 EDR 不会影响在用户设备上运行的第三方防病毒保护。 如果主防病毒解决方案遗漏了某些内容，或者存在泄露后检测，则阻止模式下的 EDR 可以正常工作。 阻止模式下的 EDR 的工作方式与被动模式下 [的 Microsoft Defender 防病毒](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state)的工作方式类似，但它也会阻止和修正检测到的恶意项目或行为。 

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>为什么需要使 Microsoft Defender 防病毒保持最新状态？ 

由于 Microsoft Defender 防病毒会检测并修正恶意项目，因此保持其最新状态非常重要。 为了在块模式中实现 EDR 有效，它使用最新的设备学习模型、行为检测和启发。 [Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection)功能堆栈以集成方式工作。 若要获得最佳保护价值，应使 Microsoft Defender 防病毒保持最新。  

### <a name="why-do-we-need-cloud-protection-on"></a>为什么需要云保护？ 

需要云保护才能在设备上启用该功能。 云保护 [允许 Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection) 基于安全智能的广度和深度以及行为和设备学习模型提供最新且最丰富的保护。

### <a name="how-do-i-set-microsoft-defender-antivirus-to-passive-mode"></a>如何将 Microsoft Defender 防病毒设置为被动模式？

请参阅 [启用 Microsoft Defender 防病毒并确认它处于被动模式](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/switch-to-microsoft-defender-setup#enable-microsoft-defender-antivirus-and-confirm-its-in-passive-mode)。

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>如何确认 Microsoft Defender 防病毒处于主动或被动模式？

若要确认 Microsoft Defender 防病毒是在主动模式还是被动模式下运行，可以在运行 Windows 的设备上使用命令提示符或 PowerShell。

#### <a name="use-powershell"></a>使用 PowerShell

1. 选择"开始"菜单，开始键入 `PowerShell` ，然后Windows PowerShell结果中的"开始"菜单。

2. 类型 `Get-MpComputerStatus`。

3. 在结果列表中，在 **AMRunningMode** 行中查找下列值之一：   
   - `Normal`
   - `Passive Mode`  
   - `SxS Passive Mode`

若要了解更多信息，请参阅 [Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus)。

#### <a name="use-command-prompt"></a>使用命令提示符

1. 选择"开始"菜单，开始键入 `Command Prompt` ，然后在结果中打开 Windows 命令提示符。

2. 类型 `sc query windefend`。

3. 在结果列表中的 **"状态** "行中，确认服务正在运行。

## <a name="see-also"></a>另请参阅

- [技术社区博客：在阻止模式下引入 EDR：停止其跟踪中的攻击](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)
- [行为阻止和抑制](behavioral-blocking-containment.md)
- [更好地结合：Microsoft Defender 防病毒和 Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/why-use-microsoft-antivirus)
