---
title: 为 Microsoft Defender AV 设置配置本地覆盖
description: 启用或禁用用户在本地更改 Microsoft Defender AV 中的设置。
keywords: 本地覆盖， 本地策略， 组策略， gpo， 锁定， 合并， 列表
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 02/13/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 045cadf06533197fda09baa7352bf03f14dd5ba2
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "51689898"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>阻止或允许用户在本地修改 Microsoft Defender 防病毒策略设置

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

默认情况下，通过组策略对象部署到网络中终结点的 Microsoft Defender 防病毒设置将阻止用户在本地更改设置。 在某些实例中可以更改此情况。

例如，可能需要允许某些用户组 (例如安全研究人员和威胁) 进一步控制他们使用的终结点上的单个设置。

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>配置 Microsoft Defender 防病毒设置的本地覆盖

这些策略的默认设置是 **Disabled**。

如果设置为"已启用"，则终结点上的用户可以使用[Windows](microsoft-defender-security-center-antivirus.md)安全应用、本地组策略设置和 PowerShell cmdlet 对关联的设置进行更改， (适当的) 。 

下表列出了每个替代策略设置以及关联的功能或设置的配置说明。

配置这些设置：

1. 在组策略管理计算机上，打开组 [策略管理控制台](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))，右键单击要配置的组策略对象，**然后单击编辑。**

2. 在组 **策略管理编辑器中** ，转到计算机 **配置，** 然后单击 **管理模板**。

3. 将树展开到 **Microsoft Defender > Windows** 组件，然后展开下表中指定的位置。 

4. 双击 **下表中指定的** 策略设置，将选项设置为所需的配置。 单击 **"确定**"，然后对任何其他设置重复上述操作。

5. 像往常一样部署组策略对象。

位置 | 设置 | 文章
---|---|---|---
MAPS | 配置向 Microsoft MAPS 报告的本地设置替代 | [启用云保护](enable-cloud-protection-microsoft-defender-antivirus.md)
隔离 | 为从隔离文件夹中删除项目配置本地设置替代 | [配置扫描修正](configure-remediation-microsoft-defender-antivirus.md)
实时保护 | 配置本地设置覆盖以监视您的计算机上的文件和程序活动 | [启用和配置 Microsoft Defender 防病毒始终启用保护和监视](configure-real-time-protection-microsoft-defender-antivirus.md)
实时保护 | 配置本地设置覆盖以监视传入和传出文件活动 | [启用和配置 Microsoft Defender 防病毒始终启用保护和监视](configure-real-time-protection-microsoft-defender-antivirus.md)
实时保护 | 配置用于扫描所有下载的文件和附件的本地设置替代 | [启用和配置 Microsoft Defender 防病毒始终启用保护和监视](configure-real-time-protection-microsoft-defender-antivirus.md)
实时保护 | 配置本地设置替代以启用行为监视 | [启用和配置 Microsoft Defender 防病毒始终启用保护和监视](configure-real-time-protection-microsoft-defender-antivirus.md)
实时保护 | 配置本地设置覆盖以启用实时保护 | [启用和配置 Microsoft Defender 防病毒始终启用保护和监视](configure-real-time-protection-microsoft-defender-antivirus.md)
修正 | 为运行计划的完整扫描以完成修正的时间配置本地设置替代 | [配置扫描修正](configure-remediation-microsoft-defender-antivirus.md)
扫描 | 为 CPU 使用率的最大百分比配置本地设置覆盖 | [配置并运行扫描](run-scan-microsoft-defender-antivirus.md)
扫描 | 为计划扫描日配置本地设置覆盖 | [配置计划扫描](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
扫描 | 为计划的快速扫描时间配置本地设置覆盖 | [配置计划扫描](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
扫描 | 为计划扫描时间配置本地设置覆盖 | [配置计划扫描](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
扫描 | 为要用于计划扫描的扫描类型配置本地设置覆盖 | [配置计划扫描](scheduled-catch-up-scans-microsoft-defender-antivirus.md)

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>配置本地和全局定义的威胁修正和排除列表的合并方式

还可以配置本地定义的列表与全局定义列表的组合或合并方式。 此设置适用于排除列表 [、](configure-exclusions-microsoft-defender-antivirus.md)指定的 [修正列表](configure-remediation-microsoft-defender-antivirus.md)和 [攻击面减少](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)。

默认情况下，在本地组策略和 Windows 安全应用中配置的列表将与网络上部署的适当组策略对象定义的列表合并。 存在冲突时，全局定义的列表优先。

你可以禁用此设置，以确保仅使用全局定义的 (如来自任何已部署的 GPO 列表) 列表。

### <a name="use-group-policy-to-disable-local-list-merging"></a>使用组策略禁用本地列表合并

1. 在组策略管理计算机上，打开组 [策略管理控制台](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))，右键单击要配置的组策略对象，**然后单击编辑。**

2. 在组 **策略管理编辑器中** ，转到计算机 **配置，** 然后单击 **管理模板**。

3. 将树展开到 **Microsoft Defender 防病毒> Windows 组件**。

4. 双击配置 **列表的本地管理员合并行为** ，将选项设置为 **已禁用**。 单击“**确定**”。

> [!NOTE]
> 如果禁用本地列表合并，它将覆盖受控文件夹访问权限设置。 它还会覆盖本地管理员设置的任何受保护的文件夹或允许的应用。 有关受控文件夹访问权限设置详细信息，请参阅在 Windows 安全中 [允许阻止的应用](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security)。

## <a name="related-topics"></a>相关主题

- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)
- [配置最终用户与 Microsoft Defender 防病毒的交互](configure-end-user-interaction-microsoft-defender-antivirus.md)