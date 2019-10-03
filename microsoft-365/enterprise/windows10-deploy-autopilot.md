---
title: 使用 Windows Autopilot 为新设备部署 Windows 10 企业版
description: 提供有关使用 Windows Autopilot 配置和部署 Windows 10 企业版的指南。
keywords: Microsoft 365，Microsoft 365 Enterprise，Microsoft 365 文档，Windows 10 企业版，部署，Windows Autopilot
author: greg-lindsay
localization_priority: Normal
ms.collection: M365-modern-desktop
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/30/2018
ms.author: greglin
ms.openlocfilehash: 2ce02826ae2b0661d3b893c1074e692ce93cf9f3
ms.sourcegitcommit: 8bcd76e5c8749a5670fbc3356957a089454c03d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "37370279"
---
# <a name="step-3-deploy-windows-10-enterprise-for-new-devices-with-windows-autopilot"></a>步骤3：使用 Windows Autopilot 为新设备部署 Windows 10 企业版

*本文适用于 Microsoft 365 企业版的 E3 和 E5 版本*

![阶段 3：Windows 10 企业版](./media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)

如果你有新的 Windows 10 电脑，则可以使用 Windows Autopilot 为你的组织自定义现成体验（OOBE），并部署具有已配置的应用程序和设置的新系统。 没有要部署的映像，没有要注入的驱动程序，没有要管理的基础结构。 用户可以独立完成部署过程，无需咨询其 IT 管理员。

您可以设置和预配置新的 Windows 10 设备，让它们准备好使用 Windows Autopilot 进行高效使用。 若要了解有关 Windows Autopilot 的详细信息（包括福利和 Windows Autopilot 方案），请参阅[Windows Autopilot 概述](https://docs.microsoft.com/windows/deployment/windows-Autopilot/windows-10-Autopilot)。 准备就绪后，请按照以下部件开始设置新设备。

## <a name="part-1-start-windows-autopilot-deployment"></a>第1部分：启动 Windows Autopilot 部署
请参阅[Windows Autopilot 概述](https://docs.microsoft.com/windows/deployment/windows-Autopilot/windows-10-Autopilot)to：

1. 了解并完成 Windows Autopilot 部署的先决条件。 先决条件包括：
    - **设备注册和 OOBE 自定义**

        若要注册设备，您需要获取其硬件 ID 并进行注册。 我们正在与各种硬件供应商合作，让他们为你提供所需的信息，或代表你上传。 您还可以选择使用生成包含设备的硬件 ID 的 .csv 文件的 PowerShell 脚本来捕获此信息。

        注册设备后，可以配置 OOBE 自定义选项，包括跳过隐私设置和 EULA。

    - **针对 OOBE 的公司品牌塑造**

        这使您可以在设备 OOBE 期间添加品牌显示。

    - **Microsoft Intune 中的 MDM 自动注册**
        
        在将设备连接到 Azure AD 时，自动注册允许用户在 Intune 中为设备管理注册其 Windows 10 设备。 若要注册，用户需要将其工作帐户添加到其个人拥有的设备，或将公司拥有的设备加入 Azure AD。 在后台，还会为该设备注册使用 Intune 进行管理。

    - **Windows Autopilot 所使用的云服务的网络连接**

        Windows Autopilot 部署程序使用大量云服务将设备恢复到生产状态，并且必须可从注册为 Windows Autopilot 设备的设备访问这些服务。 

    - **设备必须已预安装 Windows 10 版本 1703 或更高版本**

2. 了解并为您的组织选择 Windows Autopilot 部署计划。 您可以从以下部署程序中进行选择：
    - **适用于企业的 Microsoft Store**
    - **Microsoft Intune**
    - **合作伙伴中心**

## <a name="part-2-set-up-a-windows-10-device-for-microsoft-365"></a>第2部分：为 Microsoft 365 设置 Windows 10 设备
在为 Microsoft 365 用户设置 Windows 设备之前，请确保所有 Windows 设备运行的是 Windows 10、版本1703（创意者更新）或更高版本。

在组织中的所有 Windows 设备都已升级到 Windows 10 创意者更新或已在运行 Windows 10 创意者更新之后，您可以将这些设备加入到组织的 Azure Active Directory 中。

### <a name="set-up-a-brand-new-or-newly-upgraded-windows-10-device"></a>设置全新的或新升级的 Windows 10 设备
按照以下步骤操作，在运行 Windows 10 创意者更新（或更高版本）的全新设备上或在升级到 Windows 10 创意者更新（或更高版本）但尚未通过全新安装程序更新的设备上使用 Windows 10 OOBE 设置设备。

1. 如果没有配置无线网络，请确保通过有线或以太网连接将设备连接到 internet。
2. 请浏览 Windows 设备设置体验。 在新的或重置设备上，安装程序体验将以 "开始" 的 "地区" 开头 **。此权限正确吗？** 闪屏.
3. 完成 Windows 10 设备设置，直到显示" **设置方式**"页面。 在此处，为组织选择 "**设置**"。
4. 使用 Microsoft 365 用户的帐户和密码登录。 根据用户密码设置的不同，可能会提示您更新密码。 
5. 完成 Windows 10 设备设置。

完成后，设备将连接到您的组织的 Azure AD。

### <a name="set-up-a-device-that-has-already-completed-out-of-box-setup"></a>设置已完成的设备的开箱即用安装程序
如果你的设备具有 Windows 10 创意者更新（或更高版本），并且已通过 "开箱即用" 安装程序，请执行以下步骤。

1. 在运行 Windows 10 版本1703（创意者更新）的用户的 Windows 电脑上，选择**Windows**徽标，然后选择 "**设置**" 图标。
2. 2.在" **设置**"中，转到" **帐户**"。
3. 在 "**你的信息**" 页上，选择 "**访问工作或学校** > **连接**"。
4. 在 "**设置工作或学校帐户**" 对话框中的 "**替代操作**" 下，选择 "将**此设备加入 Azure Active Directory**"。
5. 在 "**让你登录**" 页面上，输入你的工作或学校帐户，然后选择 "**下一步**"。
6. 在 "**输入密码**" 页面上，输入您的密码，然后选择 "**登录**"。
7. 在 "**确保这是你的组织**" 页上，验证信息是否正确，然后选择 "**加入**"。
8. 在 "**全是" 设置！** 页面上，选择 "**完成**"。

完成后，用户将连接到您的组织的 Azure AD。

### <a name="verify-the-device-is-connected-to-azure-ad"></a>验证设备是否连接到 Azure AD
按照以下步骤操作，以使用 Azure AD 验证设备的同步状态，然后开始在设备上使用 Microsoft 365 帐户。 

1. 打开 "**设置**"。
2. 在 "**访问工作或学校**" 页面上，选择 "**已连接到<organization name> ** " 区域以显示按钮**信息**并**断开连接**。
3. 选择 "**信息**" 以获取你的同步状态。
4. 在 "**同步状态**" 页上，选择 "**同步**" 以获取电脑上的最新移动设备管理策略。
5. 若要开始使用 Microsoft 365 帐户，请转到 Windows "**开始**" 按钮，右键单击您当前的帐户图片，然后选择 "**切换**帐户"。
6. 使用组织电子邮件和密码进行登录。

如果在企业环境中使用 Windows 10 时遇到问题，可以参阅[主要 Microsoft 支持解决方案，了解最常见的问题](https://docs.microsoft.com/windows/client-management/windows-10-support-solutions)。 这些资源包括知识库文章、更新和库文章。

作为临时检查点，请查看对应于此步骤的[退出条件](windows10-exit-criteria.md#crit-windows10-step3)。

## <a name="next-step"></a>后续步骤

|||
|:-------|:-----|
|![第 4 步](./media/stepnumbers/Step4.png)| [监视设备运行状况和合规性](windows10-enable-windows-analytics.md) |



<!--
## Phase 1: Consideration phase
This guide makes several assumptions regarding essential, business-critical considerations before upgrading an OS in an enterprise environment.

**Requirements**

Make sure you have the following requirements deployed and licensed.

| Product | License |
|:---|:---|
| Microsoft Intune | E3, E5, or Intune standalone |
| Azure AD Premium | E3 or E5 |
| Office 365 ProPlus | Business Premium, E3, E5, or Office 365 ProPlus standalone |

Before upgrading an OS in an enterprise environment, take the following technical aspects into account:
* [Infrastructure](#step-1-infrastructure)
* [Apps](#step-2-apps)
* [Governance and business processes](#step-3-governance-and-business-processes)

This guide is meant only to provide Microsoft's best recommendations around these assumptions by providing links to existing documentation.

### Step 1: Infrastructure
Consider your organization's collection of hardware, software, policies, networks, and other related technologies as part of the deployment process. 

For Windows Autopilot, these are the infrastructure you need to take into account:

#### Group Policy
With Windows Autopilot, a device automatically joins their organization’s Azure AD group once a user signs into their organization from the device. The Group Policy policies (along with other customized settings and apps) are automatically pushed to the new device. It’s critical to understand that these policies must be properly configured within an organization before setting up Windows Autopilot profiles.

Windows 10 introduces many new features and removes and changes many others in Windows 7 and 8.1, including new Group Policy settings which need to be tested and implemented as part of a Windows 10 migration. The following resources provide examples on assessing current group policies for Windows, including Group Policy Objects in the Active Directory structure:

* [Manage Windows 10 with administrative templates](https://go.microsoft.com/fwlink/?linkid=860226) - Get step-by-step info on how to manage Windows 10 with administrative templates
* [Group Policy settings that apply to Windows 10](https://docs.microsoft.com/windows/client-management/group-policies-for-enterprise-and-education-editions) - Find out which Group Policy settings apply only to Windows 10 Enterprise


#### Data management
Be sure to back up user data if necessary. Because of the out-of-box experience (OOBE), user data isn't saved on a net-new computer. We recommend configuring a backup scenario as needed. For example, export all user data to a OneDrive for Business account, BitLocker To Go-encrypted USB flash drive, or network file server. For more info, see:
* [How to back up or transfer your data on a Windows-based computer](https://go.microsoft.com/fwlink/?linkid=860230) - Get step-by-step info on how to manually back up your personal files and settings.
* [Redirect known folders to OneDrive for Business](https://go.microsoft.com/fwlink/?linkid=846620) - Learn how to set a policy at the domain level to make sure users all sync to the same folder when they install the OneDrive sync client and how you can set additional policies to redirect the Documents folder to that sync location.

### Step 2: Apps

#### Security
Security clients (like antivirus, anti-malware, and anti-spam) are typically found on all PCs within an organization. Because these programs hook into the deeper levels of the OS, you may need to perform a compatibility assessment before starting any Windows 10 migrations. You may need to upgrade, reconfigure, or even replace Some software. Not performing this assessment can lead to:
* Native app compatibility checks failing and preventing an in-place upgrade from starting.
* Broken functionality in the security software.
* Instability after upgrading to Windows 10 (like crashing and reduced performance)

We recommend using Windows Defender Antivirus and Windows Advanced Threat Protection (ATP). For more info, see [Enable Windows 10 Enterprise security features](windows10-enable-security-features.md)

**Antivirus**

Assess current antivirus software. Windows 10 comes with Windows Defender Antivirus to protect devices from malware, viruses, and security threats. We recommend Windows Defender Antivirus. To enable Windows Defender Antivirus, see [Windows Defender Antivirus](windows10-enable-security-features.md#windows-defender-antivirus) and [Protect devices with Windows Defender Antivirus](https://go.microsoft.com/fwlink/?linkid=860254).

To learn about antivirus solutions from other providers, see [Consumer antivirus software providers for Windows](https://go.microsoft.com/fwlink/?linkid=67345).

#### App readiness
Each Windows 10 release provides improved app compatibility. However, some apps may not be compatible. Depending on the app, you may need to only do a simple upgrade or configuration update before upgrading to Windows 10. In other circumstances, you may need to remove an app entirely.

Be sure to assess business critical apps and understand the impact of upgrading to the next OS. Prioritize the workloads that impact the least number of people during deployment. 

See the following Upgrade Readiness resources to help with app inventory, driver compatibility issues, and usage information:
* [Manage Windows Upgrades with Upgrade Readiness](https://go.microsoft.com/fwlink/?linkid=860255) - Learn about the tools to help you plan and manage the upgrade process end to end, which allow you to adopt new Windows releases more quickly.
* [Configure Windows diagnostics data](https://go.microsoft.com/fwlink/?linkid=859970) - Find out about the importance of Windows diagnostic data and how Microsoft protects that data.

> [!NOTE]
> Upgrade Readiness may not be able to assess compatibility for custom and line-of-business (LOB) apps in an organization.

#### Language packs

For a Microsoft 365 powered device, you'll also need to download Office 365 ProPlus language packs that applies to the client. These come in 32-bit (x86) or 64-bit (x64). A specific language must be installed as the default. You can install other languages later. For more info, see these resources:
* [Choose between 64-bit or 32-bit version of Office](https://go.microsoft.com/fwlink/?linkid=862361) - Helps you decide which version of Office is right for you.
* [Language accessory pack for Office](https://go.microsoft.com/fwlink/?linkid=860280) - Follow the steps to install the language accessory pack for Office.
* [Add an additional language pack](https://go.microsoft.com/fwlink/?linkid=860281) - Get step-by-step info on adding a language or setting language preferences in Office.

### Step 3: Governance and business processes

#### Windows as a service
Windows 10 introduced the concept of Windows as a service. This greatly changes the frequency and style of updates to Windows. Instead of new versions being released every 3-5 years, a more incremental model is used where two smaller updates (Feature Updates) are released yearly. For more info, see:
* [Windows as a service on the Windows IT Pro Center](https://www.microsoft.com/itpro/windows-10/windows-as-a-service)
* [Overview of Windows as a service](https://go.microsoft.com/fwlink/?linkid=860288)
* [Update Windows 10 in the enterprise](https://go.microsoft.com/fwlink/?linkid=860285)

#### Pilot users and deployment rings
Be sure to have a pilot group of users selected from different parts of the business. If you have Microsoft 365 powered devices, Windows 10 and Office 365 ProPlus users should be in these deployment rings. You need to create deployment groups to help minimize the effect on network bandwidth.

**Windows 10 deployment rings**

There are three servicing channels for OS deployment rings:
* Windows Insider Program - Provides organizations with the opportunity to test and provide feedback on features that are shipped in the next feature update.
* Semi-Annual Channel - Provides new functionality with twice-per-year feature update releases. Organizations can choose when to deploy updates from the Semi-Annual Channel.
* Long-Term Servicing Channel (LTSC) - Used for specialized devices and receives new feature releases about every three years.

For more info, see:
* [Windows Insider Program, Semi-Annual Channel, and Long-Term Servicing Channel](https://go.microsoft.com/fwlink/?linkid=860293)
* [Build deployment rings for Windows 10 updates](https://go.microsoft.com/fwlink/?linkid=860294)
* [Manage software updates using Intune in Azure Portal](https://docs.microsoft.com/intune/windows-update-for-business-configure)

**Office 365 ProPlus**

For Microsoft 365 powered devices, you must also be able to support the six-month update channel for both IT and business users. One way to do so is to have three groups:
* Current Channel
* Deferred Channel
* First-release for Deferred Channel

Each group has different configuration files, as users from the Current Channel are used as a pilot to test earlier updates. For more info, see:
* [Update process for Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860299)
* [Manage updates to Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860300)
* [Configure update settings for Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860301)
* [Update channels for Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860302)
* [Version and build numbers of update channel releases](https://go.microsoft.com/fwlink/?linkid=860304)

For more info, see [Phase 4: Office 365 ProPlus infrastructure for Microsoft 365 Enterprise](office365proplus-infrastructure.md).

## Phase 2: Testing phase
Once you've completed the scenarios and requirements in [Step 1: Consideration phase](#step-1-consideration-phase), you can move to this stage. 

To use Windows Autopilot, make sure you are ready to perform these tasks:
* [Networking](#step-1-networking)
* [Identity](#step-2-identity)
* [Client readiness](#step-3-client-readiness)
* [Diagnostics data](#step-4-diagnostics-data)

### Step 1: Networking
Ports to the client need to be opened for Office 365 ProPlus (for a Microsoft 365 powered device) and Configuration Manager. For more details about setting up your Microsoft 365 Enterprise networking infrastructure, see [Phase 1: Networking](networking-infrastructure.md).

When setting up your networking infrastructure as part of Windows deployment, make sure you complete these steps:
1. Read the best practices for [network planning and improving migration performance for Office 365](http://go.microsoft.com/fwlink/?LinkId=733655).
2. [Plan for network devices that connect to Office 365 services](http://go.microsoft.com/fwlink/?LinkId=733652).
3. [Review network impact of directory synchronization](http://go.microsoft.com/fwlink/?LinkId=733652).
4. Calculate the number of clients to use per IP address and understand [Network Address Translation (NAT) support with Office 365](http://go.microsoft.com/fwlink/?LinkId=733653) and how it impacts the number of users and client devices you can serve with a single IP address.
5. If your organization restricts computers on your network from connecting to the Internet, you'll need to understand the [endpoints (fully qualified domain names (FQDNs), ports, URLs, IPv4, and IPv6 address ranges)](http://go.microsoft.com/fwlink/?LinkID=280129) that you should include in your outbound allow lists to ensure your computers can successfully use Office 365 services.
6. [Create domain name system records for Office 365 at any Domain Name System hosting provider](http://go.microsoft.com/fwlink/?LinkId=733656).
7. [Reduce mail exchange (MX) DNS record time to live (TTL) value](http://go.microsoft.com/fwlink/?LinkId=733656).

### Step 2: Identity
Intelligent security for Microsoft 365 Enterprise, in which the right users have access to the right resources with an appropriate level of access, begins with identity management. For more details about setting up your Microsoft 365 Enterprise identity infrastructure, see [Phase 2: Identity](identity-infrastructure.md).

When setting up your identity infrastructure as part of Windows deployment, make sure you complete these tasks:
1. [Add a domain and users to Office 365](http://go.microsoft.com/fwlink/?LinkID=526338).
2. [Install and run the Office 365 IdFix tool](http://go.microsoft.com/fwlink/?LinkId=733662), which scans your on-premises Active Directory environment and identifies problems that might impact directory synchronization and slow your migration to Office 365.
3. Configure Active Directory for directory synchronization with Office 365 and [integrate on-premises directories with Azure AD](http://go.microsoft.com/fwlink/?LinkId=733661).
4. [Prepare to provision users through directory synchronization to Office 365](http://go.microsoft.com/fwlink/?LinkId=733659).
5. Know the [prerequisites for Azure AD Connect](http://go.microsoft.com/fwlink/?LinkId=733663), then install and run the Azure AD Connect tool to synchronize your on-premises Active Directory to the Azure AD service used by Office 365.
6. Determine custom installation of Azure AD Connect (full version of SQL Server for directory synchronization, if required).
7. [Integrate your on-premises identities with Azure AD](http://go.microsoft.com/fwlink/?LinkID=733485).
8. [Sync a list of required attributes with AD Connect](https://go.microsoft.com/fwlink/?linkid=860363) to get all the features in Office 365 and Windows 10.
9. Activate Windows 10 Enterprise licenses, which are checked based on Azure AD credentials.

    This provides a systematic way to assign licenses to end users and groups in your organization. For more info, see [Windows 10 Subscription Activation](https://go.microsoft.com/fwlink/?linkid=860365) and [Deploy Windows 10 licenses](https://go.microsoft.com/fwlink/?linkid=860367).

### Step 3: Client readiness

#### System requirements
To prepare for Windows 10 deployment through Windows Autopilot, make sure you meet these system requirements:
* Windows 10, version 1703 or later
* Intune licenses other mobile device management (MDM) services to manage devices
* Storage and bandwith requires minimal customization
* Diagnostic data (set at Basic level or above) - For more info, see [2.4 Diagnostic data](#24-diagnostic-data).
* Windows 10 Enterprise E3 or E5
* Devices must be registered to your organization - For more info, see [Plan for network devices that connect to Office 365 services](http://go.microsoft.com/fwlink/?LinkId=733652).
* Devices must be pre-installed with Windows 10, version 1703 or later
* Devices must have access to the Internet
* Azure AD Premium P1 or P2 is installed and configured and [automatic enrollment must be configured](https://go.microsoft.com/fwlink/?linkid=860700)

### Step 4: Diagnostic data
Microsoft uses diagnostic data to help keep Windows devices secure by identifying malware trends and other threats and to help us improve the quality of Windows and Microsoft services. You must ensure that the diagnostics service is enabled at a minimum level of Basic on all endpoints in you organization. **By default, this service is enabled and set to the Enhanced level.** However, it’s good practice to check and ensure that they are receiving sensor data. Setting levels through policies overrides device-level settings. For more info, see:

You can configure your operating system diagnostic data settings using the management tools you’re already using, such as Group Policy, MDM, or Windows Provisioning. You can also manually change your settings using Registry Editor. Setting your diagnostic data levels through a management policy overrides any device level settings.

Use the appropriate value in the table below when you configure the management policy.

| Level | Data gathered | Value |
|:--- |:--- |:--- |
| Security | Security data only. | 0 |
| Basic | Security data, and basic system and quality data. | 1 |
| Enhanced | Security data, basic system and quality data, and enhanced insights and advanced reliability data. | 2 |
| Full | Security data, basic system and quality data, enhanced insights and advanced reliability data, and full diagnostics data. | 3 |

You can enable diagnostics data through these methods:
* Microsoft Intune - If you plan to use Intune to manage your devices, you can create a configuration policy to enable diagnostic data by configuring the <a href="https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry" target="blank">SystemAllowTelemetry</a> system policy. For more info on setting up configuration policies, see [Manage settings and features on your devices with Microsoft Intune policies](https://aka.ms/intuneconfigpolicies).
* Registry Editor - You can use the Registry Editor to manually enable diagnostic data on each device in your organization, or write a script to edit the registry. If a management policy already exists, such as Group Policy or MDM, it will override this registry setting.
* Group Policy - If you do not plan to enroll devices in Intune, you can use a Group Policy object to set your organization’s diagnostic data level.
* Command prompt - You can set Windows 10 diagnostics data and service to automatically start with the command prompt. This method is best if you are testing the service on only a few devices. Enabling the service to start automatically with this command will not configure the diagnostic data level. If you have not configured a diagnostic data level using management tools, the service will operate with the default Enhanced level.

See [Configure Windowsdiagnostic data in your organization](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization) to learn more about Windows diagnostic data and how you can enable it based on the method that you choose.

## Phase 3: Deployment phase
When ready, complete these:

1. Enable auto-enrollment using Azure AD Premium.

    To allow this functionality, see [Enable Windows 10 automatic enrollment](https://go.microsoft.com/fwlink/?linkid=860990).

2. Register device ID.

    To register devices, you need to acquire their hardware IDs. Currently, we are working with hardware vendors to enable them to provide hardware IDs or upload them on their customer’s behalf.

    Currently, Surface supports Autopilot. Autopilot support from other hardware manufacturers are upcoming. 

    To capture the hardware ID information manually, use the Get-WindowsAutopilotInfo PowerShell script. The script generates a CSV file with the device's hardware ID. Install the PowerShellGet module, download the PowerShell script, run it, save the CSV file, and then upload it to the Microsoft Store for Business.

    For more info, see:
    * [Overview of registering devices to your organization](https://go.microsoft.com/fwlink/?linkid=860991)
    * [Install and upgrade PowerShellGet module](https://go.microsoft.com/fwlink/?linkid=861001)
    * [Use PowerShell to get the device hardware ID](https://go.microsoft.com/fwlink/?linkid=861007)

    By uploading this information to the [Microsoft Store for Business](https://go.microsoft.com/fwlink/?linkid=691471) or Partner Center admin portal, you'll be able to assign devices to your organization. These portals also provide additional options and customizations to configure your devices.

3. Deploy Office 365 ProPlus 2016 apps to Windows 10 devices using Intune.

    For a Microsoft 365 powered device, you'll need to deploy the Office 365 ProPlus 2016 suite to Windows 10 user groups. To do this:
    1. Configure the app suite by choosing specific Office 365 ProPlus apps.
    2. Configure app information, such as suite name, description, and category.
    3. Configure app settings, including versioning (32-bit versus 64-bit), the update channel, and languages.
    4. Save these configurations.

    The app suite should show up in the app panel. If you see an error message, see [Assign Office 365 ProPlus apps to devices that run Windows 10](https://go.microsoft.com/fwlink/?linkid=857153) to help troubleshoot the issue.

4. Deploy Windows Autopilot.

    You can manage devices for your organization and apply an Autopilot deployment profile to your devices. When people in your organization run the OOBE for the device, the profile configures Windows based on the Autopilot deployment profile you applied to the device. As part of the overall process, you need to perform these tasks:
    1. Add devices
    2. Group devices (optional)
    3. Create Autopilot deployment profile
    4. Apply Autopilot deployment profile

    For step-by-step guidance see [Manage Windows device deployment with Windows Autopilot](https://go.microsoft.com/fwlink/?linkid=852442).

    For end users, they can set up a device that's been configured through Autopilot by:
    1. Turning on the new Windows 10 device.
    2. Selecting the language.
    3. Connecting to a network.
    4. Entering their Azure AD email and password.

    Azure AD Join and MDM then automatically enroll the device. MDM also applies organization-configured policies, settings, and apps.

5. Manage Windows device deployment with Windows Autopilot deployment.

    You can manage new devices in the [Microsoft Store for Business](https://go.microsoft.com/fwlink/?linkid=691471). New devices must meet these requirements:
    * Have Windows 10, version 1703 or later installed
    * Have not been through Windows OOBE

    For more info, see [Manage Autopilot deployment profiles using Microsoft Store for Business](https://go.microsoft.com/fwlink/?linkid=852441).

-->


