---
title: 配置 Microsoft Defender 防病毒检测的修正
description: 配置 Microsoft Defender 防病毒在检测到威胁时应执行哪些操作，以及隔离文件应在隔离文件夹中保留多久
keywords: 修正， 修复， 删除， 威胁， 隔离， 扫描， 还原
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 03/16/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 7f41e9c5b38e93ce84fbd971e02ebc2d77432c3f
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "51689909"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>配置 Microsoft Defender 防病毒检测的修正

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

当 Microsoft Defender 防病毒运行扫描时，它会尝试修正或删除检测到的威胁。 你可以配置 Microsoft Defender 防病毒应对特定威胁、是否应在修正前创建还原点以及何时应删除威胁。

本文介绍如何使用组策略配置这些设置，但您也可以使用 Microsoft Endpoint Configuration [Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings)和 Microsoft [Intune。](/intune/device-restrictions-configure) 

您还可以使用[ `Set-MpPreference` PowerShell cmdlet](/powershell/module/defender/set-mppreference)或[ `MSFT_MpPreference` WMI 类](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)配置这些设置。

## <a name="configure-remediation-options"></a>配置修正选项

1. 在组策略管理计算机上，打开组 [策略管理控制台](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))，右键单击要配置的组策略对象，**然后单击编辑。**

2. 在组 **策略管理编辑器中** ，转到计算机 **配置，** 然后选择 **管理模板**。

3. 将树展开到 **Windows 组件** Microsoft Defender  >  **防病毒**。 

4. 使用下表选择一个位置，然后根据需要编辑策略。 

5. 选择“**确定**”。

|位置 | 设置 | 说明 | 如果未 (默认设置)  |
|:---|:---|:---|:---|
|扫描 | 创建系统还原点 | 在尝试清理或扫描之前，将每天创建一个系统还原点 | 已禁用|
|扫描 | 打开从扫描历史记录文件夹中删除项目 | 指定项目应在扫描历史记录中保留的天数 | 30 天 |
|根 | 关闭常规修正 | 你可以指定 Microsoft Defender 防病毒是否自动修正威胁，或者它是否应该询问终结点用户应该怎么办。 | 禁用 (自动修正威胁)  |
|隔离 | 配置从隔离文件夹删除项目 | 指定在删除项目之前应在隔离中保留的天数 | 90 天 |
|威胁 | 指定检测到威胁警报时不应采取默认操作的威胁警报级别 | Microsoft Defender 防病毒检测到的每一个威胁都分配有 (、中等、高或严重级别) 。 可以使用此设置定义在隔离、删除或忽略每个威胁级别 (、删除或忽略威胁)  | 不适用 |
|威胁 | 指定检测到时不应采取默认操作的威胁 | 指定应该如何 (威胁 ID 来) 特定威胁。 你可以指定是应隔离、删除还是忽略特定威胁 | 不适用 |

> [!IMPORTANT]
> Microsoft Defender 防病毒根据许多因素检测并修正文件。 有时，完成修正需要重新启动。 即使检测稍后被确定为误报，也必须完成重新启动以确保所有其他修正步骤已完成。
>
> 如果你确定 Microsoft Defender 防病毒根据误报隔离了文件，可以在设备重启后从隔离区还原该文件。 请参阅 [在 Microsoft Defender 防病毒中还原隔离的文件](restore-quarantined-files-microsoft-defender-antivirus.md)。
> 
> 若要在将来避免此问题，可以从扫描中排除文件。 请参阅 [配置并验证 Microsoft Defender 防病毒扫描的排除项](configure-exclusions-microsoft-defender-antivirus.md)。

另请参阅 [配置修正所需的计划完整 Microsoft Defender 防病毒扫描，](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) 了解与修正相关的更多设置。

## <a name="see-also"></a>另请参阅

- [配置 Microsoft Defender 防病毒扫描选项](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [配置计划的 Microsoft Defender 防病毒扫描](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [配置并运行按需 Microsoft Defender 防病毒扫描](run-scan-microsoft-defender-antivirus.md)
- [配置终结点上显示的通知](configure-notifications-microsoft-defender-antivirus.md)
- [配置最终用户 Microsoft Defender 防病毒交互](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [自定义、启动和查看 Microsoft Defender 防病毒扫描和修正的结果](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)