---
title: 常见标识和设备访问策略 - Microsoft 365策略|Microsoft Docs
description: 介绍推荐的常见标识和设备访问策略和配置。
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: e7148e666b7d96d6de328089fccc4bb444b9f502
ms.sourcegitcommit: b0d3abbccf4dd37e32d69664d3ebc9ab8dea760d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2021
ms.locfileid: "52594001"
---
# <a name="common-identity-and-device-access-policies"></a>常见标识和设备访问策略

**适用对象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 计划 1 和计划 2](defender-for-office-365.md)
- Azure

本文介绍用于保护对 Microsoft 365 云服务的访问的常见建议策略，包括使用 Azure Active Directory (Azure AD) 应用程序代理发布的本地应用程序。

本指南讨论如何在新设置的环境中部署建议的策略。 在单独的实验室环境中设置这些策略，可以在将推出暂存到生产前和生产环境之前了解和评估建议的策略。 新预配的环境可以是仅云环境或混合环境，以反映评估需求。

## <a name="policy-set"></a>策略集

下图演示了推荐的一组策略。 它显示每个策略所适用的保护层，以及策略是适用于电脑、手机和平板电脑，还是适用于这两类设备。 它还指示配置这些策略的地方。

[![用于配置标识和设备访问的常见策略](../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png)

以下是包含指向各个策略的链接的一页 PDF 摘要：

[![用于讲义的标识和设备保护Microsoft 365图像](../../media/microsoft-365-policies-configurations/MSFT-cloud-architecture-identity-device-protection-handout.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [以 PDF 格式查看](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \|[以 PDF 格式下载](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)

本文的其余部分介绍如何配置这些策略。

> [!NOTE]
> 建议在 Intune 中注册设备 (MFA) 要求使用多重身份验证，以确保设备由目标用户拥有。 必须先在 Intune 中注册设备，然后才能强制执行设备合规性策略。

为了给你一些时间来完成这些任务，我们建议按此表中列出的顺序实现基准策略。 但是，可随时实施针对敏感和高度管控级别的保护的 MFA 策略。

|保护级别|策略|详细信息|许可|
|---|---|---|---|
|**Baseline**|[当登录风险为中或高 *时需要* MFA](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5或Microsoft 365 E3 E5 安全附加设备|
||[阻止不支持新式身份验证的客户端](#block-clients-that-dont-support-multi-factor)|不使用新式身份验证的客户端可以绕过条件访问策略，因此阻止这些策略非常重要。|Microsoft 365 E3 或 E5|
||[高风险用户必须更改密码](#high-risk-users-must-change-password)|如果为用户的帐户检测到高风险活动，则强制用户在登录时更改其密码。|Microsoft 365 E5或Microsoft 365 E3 E5 安全附加设备|
||[将应用程序保护策略 (APP) 数据保护](#apply-app-data-protection-policies)|每个平台的一个 Intune 应用保护 (Windows iOS/iPadOS、Android) 。|Microsoft 365 E3 或 E5|
||[需要批准的应用和应用保护](#require-approved-apps-and-app-protection)|使用 iOS、iPadOS 或 Android 对手机和平板电脑强制执行移动应用保护。|Microsoft 365 E3 或 E5|
||[定义设备合规性策略](#define-device-compliance-policies)|每个平台一个策略。|Microsoft 365 E3 或 E5|
||[需要兼容电脑](#require-compliant-pcs-but-not-compliant-phones-and-tablets)|使用 macOS 或 Windows Intune 管理电脑。|Microsoft 365 E3 或 E5|
|**敏感**|[登录风险低、中或高时需要MFA  ](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5或Microsoft 365 E3 E5 安全附加设备|
||[要求兼容电脑 *和* 移动设备](#require-compliant-pcs-and-mobile-devices)|对 macOS 或 macOS (Windows和) iOS、iPadOS 或 Android (平板电脑强制执行 Intune) 。|Microsoft 365 E3 或 E5|
|**高度管控**|[*始终* 需要 MFA](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 或 E5|
|

## <a name="assigning-policies-to-groups-and-users"></a>向组和用户分配策略

在配置策略之前，请确定要用于每一层保护的 Azure AD 组。 通常，基线保护适用于组织中的每个人。 同时包含基线和敏感保护的用户将应用所有基线策略以及敏感策略。 保护是累积的，并且强制执行最严格的策略。

建议的做法是创建用于条件访问排除的 Azure AD 组。 将此组添加到"分配"部分"用户和组"**设置的"** 排除值"中的所有条件 **访问** 策略。 这样，在解决访问问题时，就提供了为用户提供访问权限的方法。 建议仅作为临时解决方案。 监视该组的更改并确保仅按预期使用排除组。

下面是要求 MFA 的组分配和排除的示例。

![MFA 策略的组分配和排除示例](../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png)

以下是结果：

- 当登录风险为中或高时，所有用户都需要使用 MFA。

- 当登录风险较低、中等或较高时，Executive Staff 组的成员需要使用 MFA。

  在这种情况下，Executive Staff 组的成员与基线和敏感条件访问策略匹配。 两个策略的访问控制组合在一起，在这种情况下等效于敏感条件访问策略。

- 始终需要顶级密码Project X 组的成员才能使用 MFA

  在这种情况下，Top Secret Project X 组的成员同时匹配基线和高度管控的条件访问策略。 两种策略的访问控制组合在一起。 由于高度管控条件访问策略的访问控制更加严格，因此使用了该策略。

对组和用户应用较高级别的保护时要谨慎。 例如，Top Secret Project X 组的成员每次登录时都需要使用 MFA，即使他们未针对 Project X 处理高度管控的内容。

作为这些建议的一部分创建的所有 Azure AD 组都必须创建为Microsoft 365组。 这一点对于在保护文档和文档安全时部署Microsoft Teams SharePoint。

![创建组Microsoft 365示例](../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png)

## <a name="require-mfa-based-on-sign-in-risk"></a>基于登录风险要求 MFA

应在要求用户使用 MFA 之前让用户注册 MFA。 如果你有 Microsoft 365 E5、Microsoft 365 E3 E5 安全加载项、Office 365 EMS E5 或单个 Azure AD 高级版 P2 许可证，你可以将 MFA 注册策略与 Azure AD Identity Protection 一同使用，以要求用户注册 MFA。 先决条件 [工作](identity-access-prerequisites.md) 包括使用 MFA 注册所有用户。

注册用户后，可以使用新的条件访问策略要求 MFA 进行登录。

1. 转到 [Azure 门户](https://portal.azure.com)，然后使用你的凭据登录。
2. 在 Azure 服务列表中，选择 **"Azure Active Directory"。**
3. 在"**管理"** 列表中，选择"**安全性"，** 然后选择"条件 **访问"。**
4. 选择 **"新建** 策略"并键入新策略的名称。

下表介绍了条件访问策略设置，要求基于登录风险进行 MFA。

在" **分配"** 部分：

|设置|属性|值|注意|
|---|---|---|---|
|用户和组|包括|**Select users and groups > Users and groups**： Select specific groups containing targeted user accounts.|从包含试点用户帐户的组开始。|
||排除|**用户和组**：选择条件访问例外组;服务帐户 (应用标识) 。|应根据需要临时修改成员身份。|
|云应用或操作|**云应用>包括**|**选择应用**：选择要应用此策略的应用。 例如，选择"Exchange Online"。||
|条件|||配置特定于您的环境和需求的条件。|
||登录风险||请参阅下表中的指南。|
|

### <a name="sign-in-risk-condition-settings"></a>登录风险条件设置

根据目标保护级别应用风险级别设置。

|保护级别|所需的风险级别值|操作|
|---|---|---|
|基线|高、中|检查两者。|
|敏感|高、中、低|检查全部三者。|
|高度管控||保留所有选项未选中状态，以始终强制执行 MFA。|
|

在" **访问控制"** 部分：

|设置|属性|值|操作|
|---|---|---|---|
|授予|**Grant access**||Select|
|||**需要多重身份验证**|支票|
||**需要所有已选控件**||Select|
|

选择 **"** 选择"保存 **"授予"** 设置。

最后，为"启用 **策略"选择"打开"，** 然后选择"创建 **"。**

还应考虑使用 [What if](/azure/active-directory/active-directory-conditional-access-whatif) 工具测试策略。

## <a name="block-clients-that-dont-support-multi-factor"></a>阻止不支持多重身份验证的客户端

将这些表中的设置用于条件访问策略，以阻止不支持多重身份验证的客户端。

有关[支持](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)多重身份验证的 Microsoft 365 请参阅本文。

在" **分配"** 部分：

|设置|属性|值|注意|
|---|---|---|---|
|用户和组|包括|**Select users and groups > Users and groups**： Select specific groups containing targeted user accounts.|从包含试点用户帐户的组开始。|
||排除|**用户和组**：选择条件访问例外组;服务帐户 (应用标识) 。|应根据需要临时修改成员身份。|
|云应用或操作|**云应用>包括**|**选择应用**：选择与不支持新式验证的客户端相对应的应用。||
|条件|**客户端应用**|为 **"配置"****选择"是"** <p> 清除浏览器和 **移动应用以及****桌面客户端的选中标记**||
|

在" **访问控制"** 部分：

|设置|属性|值|操作|
|---|---|---|---|
|授予|**阻止访问**||Select|
||**需要所有已选控件**||Select|
|

选择 **"** 选择"保存 **"授予"** 设置。

最后，为"启用 **策略"选择"打开"，** 然后选择"创建 **"。**

请考虑使用 [What if](/azure/active-directory/active-directory-conditional-access-whatif) 工具测试策略。

例如Exchange Online，可以使用身份验证策略禁用[基本](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online)身份验证，这将强制所有客户端访问请求使用新式验证。

## <a name="high-risk-users-must-change-password"></a>高风险用户必须更改密码

为了确保强制所有高风险用户遭到入侵的帐户在登录时执行密码更改，必须应用以下策略。

Log in to the [Microsoft Azure portal (https://portal.azure.com)](https://portal.azure.com/) with your administrator credentials, and then navigate to **Azure AD Identity Protection > User Risk Policy**.

在" **分配"** 部分：

|类型|属性|值|操作|
|---|---|---|---|
|Users|包括|**所有用户**|Select|
|用户风险|**High**||Select|
|

在"第二 **个工作分配"** 部分：

|类型|属性|值|操作|
|---|---|---|---|
|Access|**允许访问**||Select|
|||**需要更改密码**|支票|
|

选择 **"完成** "保存 **Access** 设置。

最后，为"**强制策略****"选择"打开"，** 然后选择"保存 **"。**

请考虑使用 [What if](/azure/active-directory/active-directory-conditional-access-whatif) 工具测试策略。

结合配置 [Azure AD](/azure/active-directory/authentication/concept-password-ban-bad)密码保护 使用此策略，可检测和阻止已知的弱密码及其变体以及特定于你的组织的其他弱术语。 使用 Azure AD 密码保护可确保更改后的密码是强密码。

## <a name="apply-app-data-protection-policies"></a>应用 APP 数据保护策略

APP 定义允许哪些应用以及它们可以对组织数据采取的操作。 APP 中可用的选项使组织能够定制保护以满足其特定需求。 对于一些用户，实现完整方案所需的策略设置可能并不明显。 为了帮助组织确定移动客户端终结点强化的优先级，Microsoft 引入了适用于 iOS 和 Android 移动应用管理的 APP 数据保护框架的分类。

APP 数据保护框架分为三个不同的配置级别，每个级别都从上一级别构建：

- **Enterprise级别** 1 (保护) 确保应用使用 PIN 进行保护并加密，并执行选择性擦除操作。 对于 Android 设备，此级别验证 Android 设备证明。 这是在邮箱策略中提供类似数据保护Exchange Online，并且向 APP 介绍 IT 和用户填充的条目级别配置。
- **Enterprise级别** 2 (增强) 引入了应用数据泄露防护机制和最低操作系统要求。 这是适用于访问工作或学校数据的大多数移动用户的配置。
- **Enterprise高级数据保护** (级别 3) 引入了高级数据保护机制、增强的 PIN 配置和 APP 移动威胁防护。 访问高风险数据的用户需要此配置。

若要查看每个配置级别和必须保护的最低应用的特定建议，请查看使用应用保护 [策略的数据保护框架](/mem/intune/apps/app-protection-framework)。

根据标识和设备 [访问配置中](microsoft-365-policies-configurations.md)概述的原则，基线和敏感保护层与级别 2 企业增强数据保护设置紧密映射。 高度管控保护层紧密映射到第 3 级企业高数据保护设置。

|保护级别|应用保护策略|详细信息|
|---|---|---|
|基线|[第 2 级增强数据保护](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|级别 2 中强制执行的策略设置包括建议级别 1 的所有策略设置，并且仅添加或更新以下策略设置，以实施比级别 1 更多的控件和更复杂的配置。|
|敏感|[第 2 级增强数据保护](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|级别 2 中强制执行的策略设置包括建议级别 1 的所有策略设置，并且仅添加或更新以下策略设置，以实施比级别 1 更多的控件和更复杂的配置。|
|高度管控|[第 3 级企业高数据保护](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|级别 3 中强制执行的策略设置包括为级别 1 和级别 2 建议的所有策略设置，并且仅添加或更新以下策略设置，以实施比级别 2 更多的控件和更复杂的配置。|
|

若要使用数据保护框架设置 (iOS 和 Android) 中Microsoft Endpoint Manager每个平台创建新的应用保护策略，你可以：

1. 手动创建策略，具体步骤如下：如何使用 Microsoft Intune 创建和[部署应用保护策略](/mem/intune/apps/app-protection-policies)。
2. 使用 Intune 的[PowerShell](https://github.com/microsoftgraph/powershell-intune-samples)脚本导入示例[Intune 应用保护策略配置框架 JSON](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies)模板。

## <a name="require-approved-apps-and-app-protection"></a>需要批准的应用和应用保护

若要强制执行在 Intune 中应用的应用保护策略，必须创建条件访问策略，以要求批准的客户端应用和应用保护策略中设置的条件。

强制执行 APP 保护策略需要一组策略，如使用条件访问要求云 [应用访问应用保护策略中所述](/azure/active-directory/conditional-access/app-protection-based-conditional-access)。 每个策略都包含在此推荐的标识和访问配置策略集内。

若要创建需要已批准应用和应用保护的条件访问策略，请按照方案[1：Microsoft 365](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies)应用需要具有应用保护策略的已批准应用（允许适用于 iOS 和 Android 的 Outlook，但阻止支持 OAuth 的 Exchange ActiveSync 客户端连接到 Exchange Online）中的"步骤 1：为 Microsoft 365 配置 Azure AD 条件访问策略"。

   > [!NOTE]
   > 此策略可确保移动用户可以使用Office访问所有终结点。

如果要启用对 Exchange Online 的移动访问，请实现阻止[ActiveSync](secure-email-recommended-policies.md#block-activesync-clients)客户端Exchange ActiveSync利用基本身份验证的客户端连接到 Exchange Online。 此策略未在本文顶部的插图中显示。 在用于保护电子邮件的策略 [建议中进行了介绍和说明](secure-email-recommended-policies.md)。

若要创建需要适用于 iOS 和 Android 的 Edge 的条件访问策略，请按照方案 2：浏览器应用需要具有应用保护策略（允许适用于 iOS 和 Android 的 Edge）批准的应用中的"步骤[2：](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-2-browser-apps-require-approved-apps-with-app-protection-policies)为 Microsoft 365 配置 Azure AD 条件访问策略"，但阻止其他移动设备 Web 浏览器连接到 Microsoft 365 终结点。

 这些策略利用授权控件["需要批准的客户端应用](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app)"和"[需要应用保护策略"。](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy)

最后，阻止 iOS 和 Android 设备上其他客户端应用的旧身份验证可确保这些客户端无法绕过条件访问策略。 如果你遵循本文中的指南，则已经配置了阻止不支持新式 [身份验证的客户端](#block-clients-that-dont-support-multi-factor)。

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>定义设备合规性策略

设备合规性策略定义设备必须满足的要求，以被确定为合规。 从管理中心内创建 Intune Microsoft Endpoint Manager策略。

必须为每个电脑、手机或平板电脑平台创建策略：

- Android 设备管理员
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1及更高版本
- Windows 10及更高版本

若要创建设备合规性策略，请Microsoft Endpoint Manager管理员凭据 [](https://endpoint.microsoft.com)登录到管理中心，然后导航到"**设备** 合规性 \> **策略** \> **策略"。** 选择 **"创建策略"。**

若要部署设备合规性策略，必须将其分配给用户组。 创建并保存策略后分配策略。 在管理中心，选择策略， **然后选择分配**。 选择要接收策略的组后，选择"保存"以保存该组分配并部署该策略。

有关在 Intune 中创建合规性策略的分步指南，请参阅[](/mem/intune/protect/create-compliance-policy)Intune 文档中的在 Microsoft Intune 创建合规性策略。

### <a name="recommended-settings-for-windows-10-and-later"></a>建议用于 Windows 10 及更高版本的设置

对于运行策略创建过程的步骤 **2 Windows 10** 合规性设置中配置的运行以下设置的 PC，建议使用以下设置。

有关 **设备运行状况> Windows证明服务评估规则，** 请参阅此表。

|属性|值|操作|
|---|---|---|
|需要BitLocker|需要|Select|
|要求在设备上启用安全启动|需要|Select|
|需要代码完整性|需要|Select|
|

对于 **设备属性**，根据你的 IT 和安全策略为操作系统版本指定适当的值。

对于 **"配置管理器合规性"，** 选择"**需要"。**

有关 **系统安全性**，请参阅此表。

|类型|属性|值|操作|
|---|---|---|---|
|Password|需要密码才能解锁移动设备|需要|Select|
||简单密码|阻止|Select|
||密码类型|设备默认值|Select|
||最短密码长度|6 |类型|
||需要密码之前不活动的最大分钟数|15|类型 <p> Android 版本 4.0 及以上或 KNOX 4.0 及以上版本支持此设置。 对于 iOS 设备，iOS 8.0 及以上版本支持。|
||密码过期 (天数) |41|类型|
||防止重复使用的以前密码的数量|5 |类型|
||设备从空闲状态返回时需要密码 (移动设备和全息) |需要|可用于 Windows 10 及更高版本|
|加密|设备上数据存储的加密|需要|Select|
|设备安全|防火墙|需要|Select|
||防病毒|需要|Select|
||反间谍软件|需要|Select <p> 此设置要求在安全中心注册反间谍软件Windows 安全中心解决方案。|
|Defender|Microsoft Defender 反恶意软件|需要|Select|
||Microsoft Defender 反恶意软件最低版本||类型 <p> 仅受桌面Windows 10支持。 Microsoft 建议版本与最新版本的后面版本不超过 5 个。|
||Microsoft Defender 反恶意软件签名最新|需要|Select|
||实时保护|需要|Select <p> 仅受桌面Windows 10支持|
|

#### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

|类型|属性|值|操作|
|---|---|---|---|
|Microsoft Defender for Endpoint 规则Microsoft Endpoint Manager管理中心|[要求设备处于计算机风险分数或处于计算机风险分数之下](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|中|Select|
|

## <a name="require-compliant-pcs-but-not-compliant-phones-and-tablets"></a>要求兼容电脑 (但不符合标准的手机和平板电脑) 

在将策略添加到要求合规电脑之前，请务必在 Intune 中注册设备以管理。 建议在将设备注册到 Intune 中之前使用多重身份验证，确保设备由预期用户拥有。

需要兼容电脑：

1. 转到 [Azure 门户](https://portal.azure.com)，然后使用你的凭据登录。
2. 在 Azure 服务列表中，选择 **"Azure Active Directory"。**
3. 在"**管理"** 列表中，选择"**安全性"，** 然后选择"条件 **访问"。**
4. 选择 **"新建** 策略"并键入新策略的名称。

5. 在 **"** 分配 **"** 下，选择"用户和组"，并包括您希望策略应用于的用户。 此外，排除条件访问排除组。

6. 在 **分配** 下，选择 **云应用或操作**。

7. 对于 **"包含**"，选择" **选择>选择**"，然后从"云应用"列表中选择 **所需的** 应用。 例如，选择"Exchange Online"。 完成后 **选择选择** 。

8. 若要要求兼容电脑 (但不符合手机和平板电脑) ，在"分配"下，选择"设备平台>**条件"。** 为 **"配置"****选择"是"。** 选择 **"选择设备平台****"，Windows****和 macOS"，** 然后选择"完成 **"。**

9. 在 **"访问控制"下**，选择"**授予"。**

10. 选择 **"授予访问权限**"，然后选中"要求设备 **标记为合规"。** 对于多个控件，选择 **"需要所有选定的控件"。** 完成后，选择"**选择"。**

11. 为 **"启用****策略"选择"打开"，** 然后选择"创建 **"。**

> [!NOTE]
> 在启用此策略之前，请确保你的设备合规。 否则，您可能被锁定，在用户帐户已添加到条件访问排除组之前，将无法更改此策略。

## <a name="require-compliant-pcs-and-mobile-devices"></a>要求兼容电脑 *和* 移动设备

若要要求所有设备的合规性：

1. 转到 [Azure 门户](https://portal.azure.com)，然后使用你的凭据登录。
2. 在 Azure 服务列表中，选择 **"Azure Active Directory"。**
3. 在"**管理"** 列表中，选择"**安全性"，** 然后选择"条件 **访问"。**
4. 选择 **"新建** 策略"并键入新策略的名称。

5. 在 **"** 分配 **"** 下，选择"用户和组"，并包括您希望策略应用于的用户。 此外，排除条件访问排除组。

6. 在 **分配** 下，选择 **云应用或操作**。

7. 对于 **"包含**"，选择" **选择>选择**"，然后从"云应用"列表中选择 **所需的** 应用。 例如，选择"Exchange Online"。 完成后 **选择选择** 。

8. 在 **"访问控制"下**，选择"**授予"。**

9. 选择 **"授予访问权限**"，然后选中"要求设备 **标记为合规"。** 对于多个控件，选择 **"需要所有选定的控件"。** 完成后，选择"**选择"。**

10. 为 **"启用****策略"选择"打开"，** 然后选择"创建 **"。**

> [!NOTE]
> 在启用此策略之前，请确保你的设备合规。 否则，您可能被锁定，在用户帐户已添加到条件访问排除组之前，将无法更改此策略。

## <a name="next-step"></a>后续步骤

[![步骤 3：来宾和外部用户策略](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png)](identity-access-policies-guest-access.md)

[了解针对来宾用户和外部用户的策略建议](identity-access-policies-guest-access.md)