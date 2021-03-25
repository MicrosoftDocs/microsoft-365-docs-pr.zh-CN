---
title: 启用受控文件夹访问权限
keywords: 受控文件夹访问权限， windows 10， windows defender， 勒索软件， 保护， 文件， 文件夹， 启用， 打开， 使用
description: 了解如何通过启用受控文件夹访问权限来保护重要文件
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: levinec
ms.author: ellevin
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: a35c18d805ef3645659f49b8340cbb4cabab2f8d
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165065"
---
# <a name="enable-controlled-folder-access"></a>启用受控文件夹访问权限

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

[受控文件夹访问权限](controlled-folders.md) 可帮助你保护重要数据免受恶意应用和威胁（如勒索软件）的侵害。 受控文件夹访问权限包含在 Windows 10 和 Windows Server 2019 中。

可以使用以下任一方法启用受控文件夹访问权限：

* [Windows 安全应用](#windows-security-app)
* [Microsoft Intune](#intune)
* [移动设备管理 (MDM)](#mobile-device-management-mdm)
* [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
* [组策略](#group-policy)
* [PowerShell](#powershell)

[审核](evaluate-controlled-folder-access.md) 模式允许你测试此功能在 (并查看) 事件，而不会影响设备的正常使用。

禁用本地管理员列表合并的组策略设置将覆盖受控文件夹访问权限设置。 它们还通过受控文件夹访问权限覆盖受保护的文件夹和允许的本地管理员设置的应用。 这些策略包括：

* Microsoft Defender 防病毒 **为列表配置本地管理员合并行为**
* System Center Endpoint Protection **允许用户添加排除项和替代项**

有关禁用本地列表合并的信息，请参阅阻止或 [允许用户在本地修改 Microsoft Defender AV 策略设置](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus#configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged)。

## <a name="windows-security-app"></a>Windows 安全应用

1. 通过选择任务栏中的防护图标打开 Windows 安全应用。 还可以搜索 Defender 的"开始" **菜单**。

2. 选择病毒 **&威胁** 防护磁贴 (或左侧菜单栏上的防护图标) 然后选择勒索 **软件保护**。

3. 将受控文件夹访问权限 **的开关设置为****开**。

> [!NOTE]
> 如果使用组策略、PowerShell 或 MDM CSP 配置受控文件夹访问权限，则状态将在设备重启后在 Windows 安全应用中更改。
> If the feature is set to **Audit mode** with any of those tools， the Windows Security app will show the state as **Off**.
> 如果要保护用户配置文件数据，我们建议用户配置文件应位于默认 Windows 安装驱动器上。

## <a name="intune"></a>Intune

1. 登录到 Azure 门户 [并打开](https://portal.azure.com) Intune。

2. 转到设备 **配置文件**  >  **创建**  >  **配置文件**。

3. 将配置文件命名，选择 **"Windows 10 及更高版本**"和"**终结点保护"。** <br/> ![创建终结点保护配置文件](/microsoft-365/security/defender-endpoint/images/create-endpoint-protection-profile) <br/>

4. 转到配置 **Windows Defender**  >  **攻击防护**  >  **受控文件夹访问权限**  >  **启用**。

5. 键入每个有权访问受保护文件夹的应用程序的路径，以及需要保护的其他任何文件夹的路径。 选择“**添加**”。<br/> ![在 Intune 中启用受控文件夹访问权限](/microsoft-365/security/defender-endpoint/images/enable-cfa-intune)<br/>

   > [!NOTE]
   > 应用程序支持 Wilcard，但文件夹不支持。 子文件夹不受保护。 允许的应用将继续触发事件，直到它们重新启动。

6. 选择 **确定** 以保存每个打开的边栏选项卡和 **创建**。

7. 选择配置文件 **分配**、分配给所有用户 **&所有设备"** 和"**保存"。**

## <a name="mobile-device-management-mdm"></a>移动设备管理 (MDM)

使用 [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) 配置服务提供程序 (CSP) 允许应用对受保护的文件夹进行更改。

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. 在 Microsoft Endpoint Configuration Manager 中，转到 **"资产和** 合规性  >  **Endpoint Protection**  >  **Windows Defender攻击防护"。**

2. 选择 **"主页**  >  **创建攻击防护策略"。**

3. 输入名称和说明，选择受控 **文件夹访问权限**，然后选择下一 **步**。

4. 选择是阻止更改还是审核更改、允许其他应用或添加其他文件夹，然后选择"下一步 **"。**
   > [!NOTE]
   > 应用程序支持 Wilcard，但文件夹不支持。 子文件夹不受保护。 允许的应用将继续触发事件，直到它们重新启动。

5. 查看设置，然后选择" **下一** 步"以创建策略。

6. 创建策略后 **，关闭**。

## <a name="group-policy"></a>组策略

1. 在组策略管理设备上，打开组 [策略管理控制台](https://technet.microsoft.com/library/cc731212.aspx)，右键单击要配置的组策略对象， **然后选择编辑**。

2. 在组 **策略管理编辑器中**，转到计算机 **配置，** 然后选择 **管理模板**。

3. 将树展开到 Windows 组件> Microsoft Defender 防病毒> Windows Defender攻击防护> **受控文件夹访问权限**。

4. 双击配置受控文件夹 **访问权限** 设置，将选项设置为 **已启用**。 在选项部分中，必须指定以下选项之一：
    * **启用** - 不允许恶意和可疑应用对受保护文件夹中的文件进行更改。 通知将在 Windows 事件日志中提供。
    * **禁用 (默认)** - 受控文件夹访问权限功能将不起作用。 所有应用都可以对受保护的文件夹中的文件进行更改。
    * **审核模式** - 如果恶意或可疑应用尝试更改受保护文件夹中的文件，将允许更改。 但是，它将记录在 Windows 事件日志中，你可以在这里评估对组织的影响。
    * **仅阻止磁盘修改** - 不受信任的应用尝试写入磁盘扇区将记录在 Windows 事件日志中。 这些日志位于 Microsoft  > Windows > Operational > Windows Defender > Id 1123 >日志。
    * **仅** 审核磁盘修改 - 仅在 Windows 事件日志中记录写入受保护磁盘扇区的尝试 (应用程序和服务日志  >  **Microsoft**  >  **Windows**  >  **Windows Defender**  >  **操作**  >  **ID 1124**) 。 不会记录修改或删除受保护文件夹中的文件的尝试。

      ![在下拉列表中选中的组策略选项"启用"和"审核模式"的屏幕截图](/microsoft-365/security/defender-endpoint/images/cfa-gp-enable)

> [!IMPORTANT]
> 若要完全启用受控文件夹访问权限，必须将组策略选项设置为 **已启用**，然后选择选项下拉菜单中的阻止。

## <a name="powershell"></a>PowerShell

1. 在 **"开始"菜单中键入 powershell，** 右 **键单击**"Windows PowerShell并选择"以 **管理员角色运行"。**

2. 输入以下 cmdlet：

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

可以通过指定 （而不是 ）在审核模式下 `AuditMode` 启用该功能 `Enabled` 。

用于 `Disabled` 关闭该功能。

## <a name="see-also"></a>另请参阅

* [使用受控文件夹访问权限保护重要文件夹](controlled-folders.md)
* [自定义受控文件夹访问权限](customize-controlled-folders.md)
* [评估 Microsoft Defender for Endpoint](evaluate-atp.md)