---
title: 使用篡改保护保护安全设置
ms.reviewer: pahuijbr, hayhov, oogunrinde
manager: dansimp
description: 使用防篡改保护防止恶意应用更改重要安全设置。
keywords: 恶意软件， defender， 防病毒， 防篡改保护
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.technology: mde
ms.date: 06/23/2021
ms.openlocfilehash: 2e0724900de30629292cdcdc055d3ad3a1867b20
ms.sourcegitcommit: ccbdf2638fc6646bfb89450169953f4c3ce4b9b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "53105412"
---
# <a name="protect-security-settings-with-tamper-protection"></a>使用篡改保护保护安全设置

**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

防篡改保护适用于运行以下版本之一的设备Windows：

- Windows 10
- Windows Server 2019
- Windows服务器版本 1803 或更高版本
- Windows Server 2016

## <a name="overview"></a>概览

在某些类型的网络攻击期间，不良参与者会尝试在你的计算机上禁用安全功能，如防病毒保护。 不良操作者希望禁用安全功能，以便更轻松地访问数据、安装恶意软件，或者以其他方式利用你的数据、标识和设备。 防篡改保护有助于防止这些类型的事件发生。

借助防篡改保护，恶意应用可防止其采取如下操作：

- 禁用病毒和威胁防护
- 禁用实时保护
- 关闭行为监视
- 禁用防病毒 (如 IOfficeAntivirus (IOAV) ) 
- 禁用云保护
- 删除安全智能更新

### <a name="how-it-works"></a>运作方式

篡改保护实质上Microsoft Defender 防病毒其安全的默认值，并阻止通过应用和方法更改安全设置，例如：

- 在注册表编辑器中配置Windows设备
- 通过 PowerShell cmdlet 更改设置
- 通过组策略编辑或删除安全设置

篡改保护不会阻止您查看安全设置。 而且，防篡改保护不会影响第三方防病毒应用向 Windows 安全中心 注册。 如果您的组织正在使用 Windows 10 企业版 E5，则单个用户不能更改篡改保护设置;在这种情况下，防篡改保护由安全团队进行管理。

### <a name="what-do-you-want-to-do"></a>要执行什么操作？

| 要执行此任务... | 请参阅本部分... |
|:---|:---|
| 管理租户中的篡改保护 <p>使用Microsoft Defender 安全中心打开或关闭防篡改保护 | [使用管理程序管理组织的防篡改Microsoft Defender 安全中心](#manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center) |
| 在组织中微调防篡改保护设置 <p>使用 Intune (Microsoft Endpoint Manager) 打开或关闭防篡改保护。 您可以使用此方法为部分或所有用户配置篡改保护。 | [使用 Intune 管理组织的篡改保护](#manage-tamper-protection-for-your-organization-using-intune) |
| 使用 Configuration Manager (组织) 或关闭防篡改保护 | [使用 Configuration Manager 版本 2006 的租户附加管理组织的防篡改保护](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006) |
| 打开或关闭 (设备) 防篡改保护 | [在单个设备上管理篡改保护](#manage-tamper-protection-on-an-individual-device) |
| 查看有关设备上篡改尝试的详细信息 | [查看有关篡改尝试的信息](#view-information-about-tampering-attempts) |
| 查看安全建议 | [查看安全建议](#review-your-security-recommendations) |
| 查看常见问题解答和常见问题 (列表)  | [浏览常见问题解答](#view-information-about-tampering-attempts) |

根据用于启用篡改保护的方法或管理工具，可能依赖于云提供的保护。 

下表提供了有关方法、工具和依赖项的详细信息。

| 如何启用防篡改保护  | 依赖云提供的保护 (MAPS)     |
|:----|:----|
| Microsoft Intune  | 否 |
| Microsoft Endpoint Configuration Manager + 租户附加  |     否  |
| [https://securitycenter.windows.com](https://securitycenter.windows.com)Microsoft Defender 安全中心 ()     |     是 |
| Microsoft 365 Defender门户 [https://security.microsoft.com](https://security.microsoft.com) ()   |     是  |

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center"></a>使用管理程序管理组织的防篡改Microsoft Defender 安全中心

可以使用 Microsoft Defender 安全中心 () 为租户打开或 [https://securitycenter.windows.com](https://securitycenter.windows.com) 关闭防篡改保护。 以下是需要记住的几点：

- 目前，新部署中用于管理Microsoft Defender 安全中心保护的选项默认处于打开状态。 对于现有部署，可选择性地使用防篡改保护，并计划在近期选择默认方法。  (要选择加入，请选择"Microsoft Defender 安全中心"设置"  >  **高级** 功能  >  **篡改** 保护")  

- 使用 Microsoft Defender 安全中心管理篡改保护时，不需要使用 Intune 或租户附加方法。

- 在 Microsoft Defender 安全中心 中管理防篡改保护时，该设置将应用于租户范围，从而影响运行 Windows 10、Windows Server 2016 或 Windows Server 2019 的所有设备。 若要微调防篡改 (例如在某些设备上对防篡改保护，但其他设备) ，请使用[Intune](#manage-tamper-protection-for-your-organization-using-intune)或具有租户附加的[Configuration Manager。](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)

- 如果你有混合环境，则 Intune 中配置的防篡改保护设置优先于在 Microsoft Defender 安全中心 中配置的设置。 

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-defender-security-center"></a>管理设备中的防篡改Microsoft Defender 安全中心

- 您必须具有适当的 [权限](/microsoft-365/security/defender-endpoint/assign-portal-access)，例如全局管理员、安全管理员或安全操作。

- 你的Windows设备必须运行以下版本之一Windows：

   - Windows 10
   - [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
   - Windows服务器版本[1803](/windows/release-health/status-windows-10-1803)或更高版本
   - [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
   - 有关版本详细信息，请参阅Windows 10[发布信息](/windows/release-health/release-information)。

- 你的设备必须[载入到适用于终结点的 Microsoft Defender。](/microsoft-365/security/defender-endpoint/onboarding)

- 你的设备必须使用反恶意软件平台版本 4.18.2010.7 (或) 及 (或) 以上的反恶意软件引擎版本 1.1.17600.5。  ([管理Microsoft Defender 防病毒更新和应用](manage-updates-baselines-microsoft-defender-antivirus.md)比较基准 .) 

- [云提供的保护](enable-cloud-protection-microsoft-defender-antivirus.md) 必须打开。

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-defender-security-center"></a>打开或关闭 (中的) 篡改Microsoft Defender 安全中心 

![打开防篡改保护Microsoft Defender 安全中心](images/mde-turn-tamperprotect-on.png)

1. 转到 [https://securitycenter.windows.com](https://securitycenter.windows.com) "Microsoft Defender 安全中心 () 并登录。

2. 选择 **"设置"。**

3. 转到"**常规**  >  **高级功能"，** 然后打开防篡改保护。

## <a name="manage-tamper-protection-for-your-organization-using-intune"></a>使用 Intune 管理组织的篡改保护

如果你是组织安全团队的一员，并且订阅包含[Intune，](/intune/fundamentals/what-is-intune)可以在 (上或) 上为组织在 Microsoft Endpoint Manager 管理中心中 [https://endpoint.microsoft.com](https://endpoint.microsoft.com) () 。 当你想要微调防篡改保护设置时，请使用 Intune。 例如，如果你希望在某些设备上（而不是所有设备）启用篡改保护，请使用 Intune。

### <a name="requirements-for-managing-tamper-protection-in-intune"></a>在 Intune 中管理防篡改保护的要求

- 您必须具有适当的 [权限](/microsoft-365/security/defender-endpoint/assign-portal-access)，例如全局管理员、安全管理员或安全操作。

- 你的组织使用 [Intune 管理设备](/intune/fundamentals/what-is-device-management)。  ([Intune 许可证](/intune/fundamentals/licenses)是必需的;Intune 包含在 Microsoft 365 E5.) 

- 你的Windows设备必须运行Windows 10 OS [1709、1803、1809](/windows/release-health/status-windows-10-1803)或更高版本。 [](/windows/release-health/status-windows-10-1709) [](/windows/release-health/status-windows-10-1809-and-windows-server-2019)  (有关版本详细信息，请参阅 Windows 10 [release information](/windows/release-health/release-information).) 

- 必须使用安全Windows更新到版本 1.287.60.0 或 (或) 。 [](https://www.microsoft.com/wdsi/definitions)

- 你的设备必须使用反恶意软件平台版本 4.18.1906.3 (或) 及) 或以上的反恶意软件引擎版本 1.1.15500.X (。  ([管理Microsoft Defender 防病毒更新和应用](manage-updates-baselines-microsoft-defender-antivirus.md)比较基准 .) 

### <a name="turn-tamper-protection-on-or-off-in-intune"></a>在 Intune 中打开 (或) 篡改保护

![使用 Intune 打开防篡改保护](images/turnontamperprotect-MEM.png)

1. 转到管理[Microsoft Endpoint Manager](https://endpoint.microsoft.com)中心，然后使用你的工作或学校帐户登录。

2. 选择 **"设备**  >  **配置文件"。**

3. 创建包含以下设置的配置文件：

    - **平台：Windows 10及更高版本**
    - **配置文件类型：终结点保护**
    - **类别：Microsoft Defender 安全中心**
    - **防篡改保护：已启用**

4. 将配置文件分配给一个或多个组。

### <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>是使用Windows Server 2016 1709、1803 Windows 1809 版本？

如果你使用的是 Windows Server 2016，Windows 10版本 1709、1803 或[1809，](/windows/release-health/status-windows-10-1809-and-windows-server-2019)则将不会在 Windows 安全中心 应用中看到篡改保护。 相反，您可以使用 PowerShell 确定是否已启用防篡改保护。 
   
在Windows Server 2016上，设置在启用防篡改保护时，应用不会准确反映实时保护的状态。
   
#### <a name="use-powershell-to-determine-whether-tamper-protection-andor-real-time-protection-are-turned-on"></a>使用 PowerShell 确定是否启用篡改保护和/或实时保护

1. 打开Windows PowerShell应用。

2. 使用 [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell cmdlet。

3. 在结果列表中，查找 或 `IsTamperProtected` `RealTimeProtectionEnabled` 。  (值为 *true* 表示已启用防篡改) 

## <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>使用 Configuration Manager 版本 2006 管理组织的篡改保护

如果你使用的是 Configuration [Manager 版本 2006，](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006)可以使用称为租户附加 的方法管理 Windows 10、Windows Server 2016 和 Windows Server 2019 上的防篡改 *保护设置*。 租户附加使你能够将仅本地 Configuration Manager 设备同步到 Microsoft Endpoint Manager 管理中心，然后将终结点安全配置策略&设备。

:::image type="content" source="images/win-security- exp-policy-endpt-security.png" alt-text="Windows 安全中心体验Endpoint Manager":::

> [!NOTE]
> 该过程可用于将篡改保护扩展到运行 Windows 10 server 2019 Windows设备。 请务必查看此过程中提到的资源的先决条件和其他信息。

1. 设置租户附加。 若要了解更多信息，请参阅Microsoft Endpoint Manager[附加：设备同步和设备操作](/mem/configmgr/tenant-attach/device-sync-actions)。

2. In the [Microsoft Endpoint Manager admin center，](https://go.microsoft.com/fwlink/?linkid=2109431)go to **Endpoint security**  >  **Antivirus**， and then choose **+ Create Policy**. 

   - 在"**平台"** 列表中，选择"Windows 10 **Windows Server (ConfigMgr) "。**  
   - 在"**配置文件"** 列表中 **，Windows 安全中心预览 (体验) 。** <br/>

3. 将策略部署到设备集合。

### <a name="need-help-with-this-method"></a>需要有关此方法的帮助？ 

参阅以下资源：

- [设置中Windows 安全中心体验配置文件Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Tech Community博客：宣布对 Configuration Manager 租户附加客户端进行篡改保护](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>在单个设备上管理篡改保护

> [!NOTE]
> 篡改保护会阻止尝试Microsoft Defender 防病毒注册表修改设置。
>
> 若要帮助确保防篡改不会干扰修改这些设置的第三方安全产品或企业安装脚本，请转到 **Windows 安全中心，** 将安全智能更新到版本 1.287.60.0 或更高版本。   (安全 [智能更新](https://www.microsoft.com/wdsi/definitions).) 
>
> 进行此更新后，防篡改保护将继续保护注册表设置，并且日志会尝试修改它们而不会返回错误。

如果你是家庭用户，或者不受安全团队管理的设置的干扰，可以使用 Windows 安全中心 应用管理篡改保护。 必须在设备上具有相应的管理员权限才能更改安全设置，例如防篡改保护。

下面是在应用应用中Windows 安全中心内容：

![防篡改保护在Windows 10 家庭版](images/tamperprotectionturnedon.png)

1. 选择 **"开始**"，然后开始键入 *"安全"。* 在搜索结果中，选择 **"Windows 安全中心"。**

2. 选择 **病毒&威胁防护**  >  **病毒&威胁防护设置。**

3. 将 **"防篡改保护****"设置为"开**"或"**关"。**

## <a name="view-information-about-tampering-attempts"></a>查看有关篡改尝试的信息

篡改尝试通常指示更大的网络攻击。 不良参与者尝试更改安全设置，作为保留和保持未检测的一种方式。 如果你是组织安全团队的成员，可以查看有关此类尝试的信息，然后采取适当的措施缓解威胁。

当检测到篡改尝试时，在系统[](/microsoft-365/security/defender-endpoint/portal-overview)Microsoft Defender 安全中心 () 。 [https://securitycenter.windows.com](https://securitycenter.windows.com)

![Microsoft Defender 安全中心](images/tamperattemptalert.png)

使用 Microsoft Defender [](/microsoft-365/security/defender-endpoint/advanced-hunting-overview) [for](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) Endpoint 中的终结点检测和响应以及高级搜寻功能，安全运营团队可以调查和处理此类尝试。

## <a name="review-your-security-recommendations"></a>查看安全建议

防篡改保护与 [威胁&漏洞管理功能](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) 集成在一起。 [安全建议](/microsoft-365/security/defender-endpoint/tvm-security-recommendation) 包括确保打开防篡改保护。 例如，可以搜索防 *篡改*。 在结果中，可以选择" **打开防** 篡改保护"了解更多信息并打开它。

![打开防篡改保护](images/tamperprotectsecurityrecos.png)

若要了解有关威胁和漏洞&，请参阅威胁&[漏洞管理Microsoft Defender 安全中心。](/microsoft-365/security/defender-endpoint/tvm-dashboard-insights#threat--vulnerability-management-in-microsoft-defender-security-center)

## <a name="frequently-asked-questions"></a>常见问题解答

### <a name="to-which-windows-os-versions-is-configuring-tamper-protection-is-applicable"></a>操作系统Windows篡改保护适用于哪些版本？

Windows 10OS 1709、1803、1809 或更高版本以及[Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint)。 [](/windows/release-health/status-windows-10-1709) [](/windows/release-health/status-windows-10-1803) [](/windows/release-health/status-windows-10-1809-and-windows-server-2019)

如果使用的是具有租户附加的 Configuration Manager 版本 2006，则防篡改保护可以扩展到 Windows Server 2019。 请参阅 [租户附加：从 ](/mem/configmgr/tenant-attach/deploy-antivirus-policy)管理中心创建和部署终结点安全防病毒策略 (预览) 。

### <a name="will-tamper-protection-have-any-impact-on-third-party-antivirus-registration"></a>篡改保护是否将影响第三方防病毒注册？

否。 第三方防病毒产品将继续在应用程序Windows 安全中心注册。

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>如果设备Microsoft Defender 防病毒处于活动状态，会发生什么情况？

已载入 Microsoft Defender for Endpoint 的设备将Microsoft Defender 防病毒被动模式运行。 防篡改保护将继续保护服务及其功能。 

### <a name="how-can-i-turn-tamper-protection-onoff"></a>如何打开/关闭防篡改保护？

如果你是家庭用户，请参阅 [在单个设备上管理篡改保护](#manage-tamper-protection-on-an-individual-device)。

如果你是使用 [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint)的组织，你应该能够在 Intune 中管理篡改保护，类似于管理其他终结点保护功能的方式。 请参阅本文的以下部分： 

- [使用 Intune 管理篡改保护](#manage-tamper-protection-for-your-organization-using-intune)
- [使用 Configuration Manager 版本 2006 管理篡改保护](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [使用管理程序管理防Microsoft Defender 安全中心](#manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center) 

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-through-my-group-policy"></a>在 Intune 中配置防篡改保护如何影响我Microsoft Defender 防病毒管理策略？

常规组策略不适用于篡改保护，当防篡改保护打开时，Microsoft Defender 防病毒更改将被忽略。 

### <a name="for-microsoft-defender-for-endpoint-is-configuring-tamper-protection-in-intune-targeted-to-the-entire-organization-only"></a>对于 Microsoft Defender for Endpoint，在 Intune 中是否仅针对整个组织配置防篡改保护？

在 Intune 或 Microsoft Endpoint Manager中配置防篡改保护可以面向整个组织以及特定设备和用户组。

### <a name="can-i-configure-tamper-protection-in-microsoft-endpoint-configuration-manager"></a>能否在 Microsoft Endpoint Configuration Manager 中配置防篡改保护？

如果你使用的是租户附加，可以使用租户Microsoft Endpoint Configuration Manager。 参阅以下资源：
- [使用 Configuration Manager 版本 2006 管理组织的篡改保护](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Tech Community博客：宣布对 Configuration Manager 租户附加客户端进行篡改保护](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>我已注册Windows E3。 能否在 Intune 中配置篡改保护？

目前，在 Intune 中配置防篡改保护仅适用于拥有 [Microsoft Defender for Endpoint 的客户](/microsoft-365/security/defender-endpoint)。

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>如果在设备上启用了防篡改保护，如果我尝试更改 Intune、Microsoft Endpoint Configuration Manager 和 Windows Management Instrumentation 中的 Microsoft Defender，会发生什么情况？

你无法更改受篡改保护的功能;将忽略此类更改请求。

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>我是企业客户。 本地管理员能否更改其设备的篡改保护？

否。 本地管理员无法更改或修改篡改保护设置。

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>如果我的设备已载入 Microsoft Defender for Endpoint，然后进入板载状态，会发生什么情况？

如果设备从 Microsoft Defender for Endpoint 脱离，防篡改保护将打开，这是非托管设备的默认状态。 

### <a name="will-there-be-an-alert-about-tamper-protection-status-changing-in-the-microsoft-defender-security-center"></a>是否将在更新过程中收到有关篡改保护状态更改的Microsoft Defender 安全中心？

是。 警报显示在警报 [https://securitycenter.microsoft.com](https://securitycenter.microsoft.com) **下**。

安全运营团队还可使用搜寻查询，如以下示例：

`DeviceAlertEvents | where Title == "Tamper Protection bypass"`

[查看有关篡改尝试的信息](#view-information-about-tampering-attempts)。

## <a name="see-also"></a>另请参阅

[使用Windows保护Endpoint Protection保护Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[获取适用于终结点的 Microsoft Defender 的概述](/microsoft-365/security/defender-endpoint)

[更好地结合：Microsoft Defender 防病毒软件和 Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md)
