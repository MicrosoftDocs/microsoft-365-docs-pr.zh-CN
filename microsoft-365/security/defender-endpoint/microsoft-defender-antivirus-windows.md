---
title: Microsoft Defender 防病毒
description: 了解如何管理、配置和使用 Microsoft Defender 防病毒、内置反恶意软件和防病毒保护。
keywords: Microsoft Defender 防病毒、Windows Defender、反恶意软件、SCEP、System Center 端点保护、System Center Configuration Manager、病毒、恶意软件、威胁、检测、保护、安全
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Priority
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.openlocfilehash: ceaf694d8b81e6b06ffe74efc4ad3d4d73471752
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322515"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Windows 10 中的 Microsoft Defender 防病毒

**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

Microsoft Defender 防病毒是 Microsoft Defender for Endpoint 中下一代保护的主要组件。 此保护结合了机器学习、大数据分析、深度威胁抵御研究和 Microsoft 云基础结构来保护组织中的设备（或终结点）。 Microsoft Defender 防病毒内置于 Windows 中，与 Microsoft Defender for Endpoint 一起在设备上和云中提供保护。 

## <a name="compatibility-with-other-antivirus-products"></a>与其他防病毒软件产品的兼容性

如果正在设备上使用非 Microsoft 防病毒/反恶意软件产品，可能可以在使用非 Microsoft 防病毒软件解决方案的同时以被动模式运行 Microsoft Defender 防病毒。 具体取决于所使用的操作系统，以及设备是否已加入 Defender for Endpoint。 要了解详细信息，请参阅 [Microsoft Defender 防病毒](microsoft-defender-antivirus-compatibility.md)。

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>比较主动模式、被动模式和已禁用模式

下表介绍了 Microsoft Defender 防病毒处于主动模式、被动模式或已禁用模式下应发生的情况。

| 模式  | 发生的情况  |
|---------|---------|
| 主动模式 | 在主动模式下，Microsoft Defender 防病毒用作设备上的主防病毒应用。 将扫描文件，修正威胁，并将检测到的威胁列在组织的安全报告中和 Windows 安全中心应用中。 |
| 被动模式 | 在被动模式下，不将 Microsoft Defender 防病毒用作设备上的主防病毒应用。 将扫描文件，并报告检测到的威胁，但 Microsoft Defender 防病毒不会修正威胁。   |
| 已禁用或卸载  | 在已禁用或卸载时，不使用 Microsoft Defender 防病毒。 不会扫描文件，并且不会修正威胁。 通常，我们不建议禁用或卸载 Microsoft Defender 防病毒。  |

要了解详细信息，请参阅 [Microsoft Defender 防病毒](microsoft-defender-antivirus-compatibility.md)。

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>检查设备上的 Microsoft Defender 防病毒状态

要检查设备上的 Microsoft Defender 防病毒状态，可以使用几种方法之一，例如 Windows 安全中心应用或 Windows PowerShell。

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>使用 Windows 安全中心应用检查 Microsoft Defender 防病毒状态

1. 在 Windows 设备上，选择“开始”菜单，然后开始键入 `Security`。 然后在结果中打开 Windows 安全中心应用。

2. 选择“**病毒和威胁防护**”。

3. 在“**病毒和威胁防护设置**”下选择“**管理设置**”。

设置页面上将显示防病毒/反恶意软件解决方案的名称。

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>使用 PowerShell 检查 Microsoft Defender 防病毒状态

1. 选择“开始”菜单，然后开始键入 `PowerShell`。 然后在结果中打开 Windows PowerShell。

2. 类型 `Get-MpComputerStatus`。

3. 在结果列表中，查看 **AMRunningMode** 行。

   - **正常** 表示 Microsoft Defender 防病毒在主动模式下运行。
   - **被动模式** 表示 Microsoft Defender 防病毒正在运行，但不是设备上的主要防病毒/反恶意软件产品。
   - **EDR 阻止模式** 表示 Microsoft Defender 防病毒正在运行，并且已启用 Microsoft Defender for Endpoint 中名为“阻止模式下的 EDR”的功能。 （请参阅 [阻止模式下的终结点检测和响应 (EDR)](edr-in-block-mode.md)。）
   - **SxS 被动模式** 表示 Microsoft Defender 防病毒与其他防病毒/反恶意软件产品一起运行，但处于被动模式下，并且设备未加入 Microsoft Defender for Endpoint。 在这种情况下，Microsoft Defender 防病毒使用有限的定期扫描。 要了解详细信息，请参阅 [在 Microsoft Defender 防病毒中使用有限的定期扫描](limited-periodic-scanning-microsoft-defender-antivirus.md)。

要了解 Get-MpComputerStatus PowerShell cmdlet 的详细信息，请参阅参考文章 [get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus)。

## <a name="get-your-antivirusantimalware-platform-updates"></a>获取防病毒/反恶意软件平台更新

请务必确保 Microsoft Defender 防病毒或任何防病毒/反恶意软件解决方案保持最新。 Microsoft 定期发布更新，以帮助确保你的设备具有最新技术来防范新的恶意软件和攻击技术。 要了解详细信息，请参阅 [管理 Microsoft Defender 防病毒更新和应用基线](manage-updates-baselines-microsoft-defender-antivirus.md)。 

## <a name="see-also"></a>另请参阅

- [Windows Server 上的 Microsoft Defender 防病毒软件](microsoft-defender-antivirus-on-windows-server.md)
- [Microsoft Defender 防病毒管理和配置](configuration-management-reference-microsoft-defender-antivirus.md)
- [评估 Microsoft Defender 防病毒保护](evaluate-microsoft-defender-antivirus.md)
