---
title: 将 Windows 服务器载入 Microsoft Defender for Endpoint 服务
description: 载入 Windows 服务器，以便它们可以将传感器数据发送到 Microsoft Defender for Endpoint 传感器。
keywords: 载入服务器， 服务器， 2012r2， 2016， 2019， 服务器载入， 设备管理， 配置 Windows ATP 服务器， 载入 Microsoft Defender 终结点服务器， 载入 Microsoft Defender for Endpoint Server
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bd92b44892b49a007316acb97296a44514db0578
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51054818"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>将 Windows 服务器载入 Microsoft Defender for Endpoint 服务

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- Windows Server 2008 R2 SP1
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server (SAC) 版本 1803 及更高版本
- Windows Server 2019 及更高版本
- Windows Server 2019 核心版本

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configserver-abovefoldlink)


Defender for Endpoint 扩展了支持，还包括 Windows Server 操作系统。 此支持通过 Microsoft Defender 安全中心控制台无缝提供高级攻击检测和调查功能。

有关许可和基础结构需要满足的实际指导，请参阅使用 Defender for Endpoint [保护 Windows 服务器](https://techcommunity.microsoft.com/t5/What-s-New/Protecting-Windows-Server-with-Windows-Defender-ATP/m-p/267114#M128)。

有关如何下载和使用 Windows 服务器的 Windows 安全基线的指南，请参阅 [Windows 安全基线](https://docs.microsoft.com/windows/device-security/windows-security-baselines)。

<br>

## <a name="windows-server-2008-r2-sp1-windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2008 R2 SP1、Windows Server 2012 R2 和 Windows Server 2016

可以使用以下任一选项将 Windows Server 2008 R2 SP1、Windows Server 2012 R2 和 Windows Server 2016 载入 Defender for Endpoint：

- **选项 1：**[通过安装和配置 Microsoft](#option-1-onboard-by-installing-and-configuring-microsoft-monitoring-agent-mma) Monitoring Agent (MMA) 
- **选项 2：**[通过 Azure 安全中心载入](#option-2-onboard-windows-servers-through-azure-security-center)
- **选项 3：**[通过 Microsoft Endpoint Manager 版本 2002 及更高版本载入](#option-3-onboard-windows-servers-through-microsoft-endpoint-manager-version-2002-and-later)


使用提供的任一选项完成载入步骤后，你需要配置和更新 [System Center Endpoint Protection 客户端](#configure-and-update-system-center-endpoint-protection-clients)。


> [!NOTE]
> 每个节点都需要 Defender for Endpoint 独立服务器许可证，才能通过 Microsoft 监视代理 (选项 1) 或 Microsoft Endpoint Manager (选项 3) 载入 Windows 服务器。 或者，每个节点都需要 Azure Defender for Servers 许可证，才能通过 Azure 安全中心 (选项 2) 载入 Windows 服务器，请参阅 Azure 安全中心中提供的支持 [功能](https://docs.microsoft.com/azure/security-center/security-center-services)。


### <a name="option-1-onboard-by-installing-and-configuring-microsoft-monitoring-agent-mma"></a>选项 1：通过安装和配置 Microsoft Monitoring Agent (MMA) 
你需要为 Windows 服务器安装和配置 MMA，以将传感器数据报告给 Defender for Endpoint。 有关详细信息，请参阅使用 [Azure Log Analytics 代理收集日志数据](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent)。

如果你已在使用 System Center Operations Manager (SCOM) 或 Azure Monitor (以前称为 Operations Management Suite (OMS) ) ，请附加 Microsoft Monitoring Agent (MMA) 以通过多托管支持向 Defender for Endpoint 工作区报告。

通常，您需要执行以下步骤：
1. 满足开始之前部分 **中列出的载入** 要求。
2. 从 Microsoft Defender 安全中心打开服务器监视。
3. 安装和配置服务器的 MMA，以将传感器数据报告给 Defender for Endpoint。
4. 配置和更新 System Center Endpoint Protection 客户端。


> [!TIP]
> 载入设备后，你可以选择运行检测测试，以验证它是否正确载入到服务。 有关详细信息，请参阅对新载入的 Defender 终结点终结点运行检测 [测试](run-detection-test.md)。


#### <a name="before-you-begin"></a>准备工作 
执行以下步骤以满足载入要求：

 - 对于 Windows Server 2008 R2 SP1 或 Windows Server 2012 R2，请确保安装以下修补程序：
    - [客户体验和诊断遥测更新](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

 - 此外，对于 Windows Server 2008 R2 SP1，请确保满足以下要求：
    - 安装 [2 月每月更新汇总](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
    - 安装 [.NET framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (或更高版本) [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

 - 对于 Windows Server 2008 R2 SP1 和 Windows Server 2012 R2：配置和更新 [System Center Endpoint Protection 客户端](#configure-and-update-system-center-endpoint-protection-clients)。

    > [!NOTE]
    > 只有当组织使用 System Center Endpoint Protection (SCEP) 并且要载入 Windows Server 2008 R2 SP1 和 Windows Server 2012 R2 时，才需要此步骤。


<span id="server-mma"/>

### <a name="install-and-configure-microsoft-monitoring-agent-mma-to-report-sensor-data-to-microsoft-defender-for-endpoint"></a>安装和配置 Microsoft 监视代理 (MMA) 向 Microsoft Defender for Endpoint 报告传感器数据

1. 下载代理设置文件 [：Windows 64 位代理](https://go.microsoft.com/fwlink/?LinkId=828603)。

2. 使用在上一过程中获取的 Workspace ID 和 Workspace 密钥，选择以下任一安装方法在 Windows 服务器上安装代理：
    - [使用安装程序 手动安装代理](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)。 <br>
    在"**代理设置选项"** 页上，选择"将代理 **连接到 Azure Log Analytics (OMS) "。**
    - [使用命令行 安装代理](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line)。
    - [使用脚本 配置代理](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation)。

> [!NOTE]
> 如果你是美国政府客户，[](gov.md)在"Azure 云"下，如果使用安装向导，或者使用命令行或脚本，则需要选择"Azure 美国政府"，将"OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE"参数设置为 1。


<span id="server-proxy"/>

### <a name="configure-windows-server-proxy-and-internet-connectivity-settings-if-needed"></a>根据需要配置 Windows 服务器代理和 Internet 连接设置
如果你的服务器需要使用代理与 Defender for Endpoint 通信，请使用以下方法之一将 MMA 配置为使用代理服务器：


- [配置 MMA 以使用代理服务器](https://docs.microsoft.com/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [配置 Windows 以将代理服务器用于所有连接](configure-proxy-internet.md)

如果代理或防火墙已在使用中，请确保服务器可以直接访问所有 Microsoft Defender for Endpoint 服务 URL，且无需 SSL 拦截。 有关详细信息，请参阅启用对 [Defender for Endpoint 服务 URL 的访问](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)。 使用 SSL 拦截将阻止系统与 Defender for Endpoint 服务通信。 

完成后，你应该在一小时内在门户中看到已载入的 Windows 服务器。

### <a name="option-2-onboard-windows-servers-through-azure-security-center"></a>选项 2：通过 Azure 安全中心载入 Windows 服务器
1. 在 Microsoft Defender 安全中心导航窗格中，**选择设置**  >  **设备管理**  >  **载入**。

2. 选择 **Windows Server 2008 R2 SP1、2012 R2 和 2016** 作为操作系统。

3. 单击 **Azure 安全中心中的载入服务器**。

4. 按照 Microsoft Defender for Endpoint with Azure 安全中心 [中的载入说明进行操作](https://docs.microsoft.com/azure/security-center/security-center-wdatp)。

完成载入步骤后，你需要配置和更新 System Center [Endpoint Protection 客户端](#configure-and-update-system-center-endpoint-protection-clients)。

> [!NOTE]
> - 若要通过 Azure Defender for Servers (以前是 Azure 安全中心标准版) 载入，服务器必须在 Microsoft 监视代理 (MMA) 设置中配置适当的工作区和密钥。
> - 配置后，相应的云管理包将部署在计算机中，并且传感器 (MsSenseS.exe) 将部署和启动。 
> - 如果服务器配置为使用 OMS 网关服务器作为代理，则也要求这样做。

### <a name="option-3-onboard-windows-servers-through-microsoft-endpoint-manager-version-2002-and-later"></a>选项 3：通过 Microsoft Endpoint Manager 版本 2002 及更高版本载入 Windows 服务器
可以使用 Microsoft Endpoint Manager Windows Server 2012版本 2002 和更高版本载入 R2 和 Windows Server 2016。 有关详细信息，请参阅[Microsoft Endpoint Manager current branch 中的 Microsoft Defender for Endpoint。](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)

完成载入步骤后，你需要配置和更新 System Center [Endpoint Protection 客户端](#configure-and-update-system-center-endpoint-protection-clients)。

<br>

## <a name="windows-server-sac-version-1803-windows-server-2019-and-windows-server-2019-core-edition"></a>Windows Server (SAC) 版本 1803、Windows Server 2019 和 Windows Server 2019 Core 版本
可以使用以下部署方法载入 Windows Server (SAC) 版本 1803、Windows Server 2019 或 Windows Server 2019 Core 版本：

- [本地脚本](configure-endpoints-script.md) 
- [组策略](configure-endpoints-gp.md)
- [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [System Center Configuration Manager 2012 / 2012 R2 1511 / 1602](configure-endpoints-sccm.md#onboard-devices-using-system-center-configuration-manager)
- [用于非永久性设备的 VDI 载入脚本](configure-endpoints-vdi.md)

> [!NOTE]
> - 通过 Microsoft Endpoint Manager 的 Windows Server 2019 载入程序包当前附带了一个脚本。 若要详细了解如何在 Configuration Manager 中部署脚本，请参阅 Configuration [Manager 中的程序包和程序](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs)。
> - 本地脚本适用于概念证明，但不应用于生产部署。 对于生产部署，我们建议使用组策略或 Microsoft Endpoint Configuration Manager。

对 Windows Server 的支持可更深入地了解服务器活动、内核和内存攻击检测的范围，并启用响应操作。

1. 使用适用于 Windows 10 设备的相同工具和方法在 Windows 服务器上配置适用于终结点载入设置的 Defender。 有关详细信息，请参阅载入 [Windows 10 设备](configure-endpoints.md)。

2. 如果你运行的是第三方反恶意软件解决方案，则需要应用以下 Microsoft Defender AV 被动模式设置。 验证是否正确配置了它：

    1. 设置以下注册表项：
       - 路径： `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
       - 名称：ForceDefenderPassiveMode
       - 类型：REG_DWORD
       - Value: 1

    1. 运行以下 PowerShell 命令以验证被动模式是否配置：

       ```PowerShell
       Get-WinEvent -FilterHashtable @{ProviderName="Microsoft-Windows-Sense" ;ID=84}
       ```

    1. 确认找到包含被动模式事件的最近事件：

       ![被动模式验证结果的图像](images/atp-verify-passive-mode.png)

3. 运行以下命令检查是否安装了 Microsoft Defender AV：

   ```sc.exe query Windefend```

    如果结果是"指定服务作为已安装服务不存在"，则需要安装 Microsoft Defender AV。 有关详细信息，请参阅 [Windows 10 中的 Microsoft Defender 防病毒](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)。
    
    有关如何使用组策略在 Windows 服务器上配置和管理 Microsoft Defender 防病毒的信息，请参阅使用组策略设置配置 [和管理 Microsoft Defender 防病毒](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)。

<br>

## <a name="integration-with-azure-security-center"></a>与 Azure 安全中心集成
Defender for Endpoint 可以与 Azure 安全中心集成，以提供全面的 Windows 服务器保护解决方案。 通过此集成，Azure 安全中心可以使用 Defender for Endpoint 功能为 Windows 服务器提供改进的威胁检测。

此集成中包含以下功能：
- 自动载入 - 在载入到 Azure 安全中心的 Windows 服务器上自动启用 Defender for Endpoint 传感器。 有关 Azure 安全中心载入详细信息，请参阅载入 Azure 安全中心 [标准增强的安全性](https://docs.microsoft.com/azure/security-center/security-center-onboarding)。

    > [!NOTE]
    > 自动载入仅适用于 Windows Server 2008 R2 SP1、Windows Server 2012 R2 和 Windows Server 2016。

- Azure 安全中心监视的 Windows 服务器还将在 Defender for Endpoint 中可用 - Azure 安全中心无缝连接到 Defender for Endpoint 租户，跨客户端和服务器提供单个视图。  此外，适用于终结点的 Defender 警报将在 Azure 安全中心控制台中提供。
- 服务器调查 - Azure 安全中心客户可以访问 Microsoft Defender 安全中心执行详细调查，以发现潜在泄露的范围。

> [!IMPORTANT]
> - 当你使用 Azure 安全中心监视服务器时，会自动在美国为美国 (，在欧盟为欧洲和英国用户创建 Defender for Endpoint) 。<br>
Defender for Endpoint 收集的数据存储在预配期间标识的租户地理位置中。
> - 如果在使用 Azure 安全中心之前使用 Defender for Endpoint，则数据将存储在创建租户时指定的位置，即使以后与 Azure 安全中心集成。
> - 配置后，你无法更改数据存储的位置。 如果需要将数据移动到其他位置，需要联系 Microsoft 支持部门来重置租户。 <br>
已针对 Office 365 GCC 客户禁用利用此集成的服务器终结点监视。

<br>

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>配置和更新 System Center Endpoint Protection 客户端

Defender for Endpoint 与 System Center Endpoint Protection 集成。 集成提供了恶意软件检测的可见性，并禁止潜在恶意文件或可疑恶意软件，从而停止攻击在组织中传播。

若要启用此集成，需要执行以下步骤：
- 安装 [Endpoint Protection 客户端的 2017 年 1 月反恶意软件平台更新](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)。

- [将 SCEP 客户端云保护服务成员身份配置为](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus)**高级** 设置。

<br>

## <a name="offboard-windows-servers"></a>载出 Windows 服务器
可以使用适用于 Windows 10 客户端设备的相同方法从 Windows Server (SAC) 、Windows Server 2019 和 Windows Server 2019 Core 版本上离开。

对于其他 Windows 服务器版本，你有两个选项从服务中离开 Windows 服务器：
- 卸载 MMA 代理
- 删除 Defender for Endpoint 工作区配置

> [!NOTE]
> "载出"会导致 Windows 服务器停止向门户发送传感器数据，但 Windows 服务器的数据（包括对已保留的任何警报的引用）最多保留 6 个月。

### <a name="uninstall-windows-servers-by-uninstalling-the-mma-agent"></a>通过卸载 MMA 代理卸载 Windows 服务器
若要卸载 Windows 服务器，你可以从 Windows 服务器卸载 MMA 代理或将其从报告分离到 Defender for Endpoint 工作区。 在离开代理后，Windows 服务器将不再将传感器数据发送到 Defender for Endpoint。
有关详细信息，请参阅禁用 [代理](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent)。

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>删除 Defender for Endpoint 工作区配置
若要从 Windows 服务器中注销，可以使用下列方法之一：

- 从 MMA 代理中删除 Defender for Endpoint 工作区配置
- 运行 PowerShell 命令以删除配置

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>从 MMA 代理中删除 Defender for Endpoint 工作区配置

1. 在 **"Microsoft 监视代理属性"** 中，选择 **"Azure Log Analytics (OMS) "** 选项卡。

2. 选择"适用于终结点的 Defender"工作区，然后单击"删除 **"。**

    ![Microsoft 监视代理属性的图像](images/atp-mma.png)

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>运行 PowerShell 命令以删除配置

1. 获取工作区 ID：

   1. 在导航窗格中，选择"**设置**  >  **""载入"。**

   1. 选择 **Windows Server 2008 R2 SP1、2012 R2 和 2016** 作为操作系统并获取工作区 ID：

      ![Windows 服务器载入的图像](images/atp-server-offboarding-workspaceid.png)

2. 打开提升的 PowerShell 并运行以下命令。 使用你获取的工作区 ID 并替换 `WorkspaceID` ：

    ```powershell
    $ErrorActionPreference = "SilentlyContinue"
    # Load agent scripting object
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```

<br>

## <a name="related-topics"></a>相关主题
- [载入 Windows 10 设备](configure-endpoints.md)
- [载入非 Windows 设备](configure-endpoints-non-windows.md)
- [配置代理和 Internet 连接设置](configure-proxy-internet.md)
- [在新载入的适用于终结点的 Defender 设备上运行检测测试](run-detection-test.md)
- [Microsoft Defender 终结点载入问题疑难解答](troubleshoot-onboarding.md)