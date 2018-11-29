---
title: Microsoft 365 Enterprise 服务概述 | Microsoft Docs
description: 本内容概述了 Microsoft 365 Enterprise 和可供企业采纳的建议。
author: jeffgilb
manager: femila
ms.prod: microsoft-365-business
ms.topic: article
ms.date: 08/23/2017
ms.author: jeffgilb
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: 7772421a32abd863f4301a4bc3d8264d8fe44242
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "26865960"
---
# <a name="microsoft-365-enterprise-services-and-concepts"></a>Microsoft 365 Enterprise 服务与概念

Microsoft 365 企业版专为大型组织而设计，集成了 Office 365 企业版、Windows 10 企业版和企业移动性 + 安全性 (EMS)，让所有人都能够尽情挥洒创意，并安全地开展协作。 Microsoft 365 企业版包括 Windows 10 企业版，以及 Office 365 专业增强版包含的 Office 应用程序。

Windows 10 和 Office 365 专业增强版都在 3 月和 9 月通过半年频道发布了适用于企业的新功能。 通过半年频道发布的功能的支持期为 18 个月。 Microsoft Intune 和 System Center Configuration Manager 都提供可用于部署和更新 Windows 10 和 Office 365 专业增强版的功能。

下面列出了 Windows 10、Office 365 专业增强版、Microsoft Intune 和 System Center Configuration Manager 的最新版本：

|     |**半年频道（定向）**|**半年频道**|
|:-----|:-----|:-----|
|**Windows 10**|Windows 10 Fall Creators Update（即将推出）|版本 1703|
|**Office 365 专业增强版**|版本 1803|版本 1708|
|**Intune**|不适用|版本 1708|
|**System Center Configuration Manager**|Technical Preview 版本 1708|版本 1706<sup>*</sup>|

<sup>*</sup>System Center Configuration Manager 最新分支的更新 1706 作为控制台内更新提供，用于运行版本 1606、1610 或 1702 的之前安装的网站。

> [!NOTE]
> Microsoft Azure 服务也会定期更新，但没有按版本号划分的参考资料。 若要查看 Azure 服务的最新更新和即将发布的更新，请参阅[云平台路线图](https://www.microsoft.com/cloud-platform/roadmap)。

若要详细了解这些版本提供的功能，请参阅以下文章：
- [Windows 10 中的新增功能](https://docs.microsoft.com/windows/whats-new/)
- [Windows 10 发布信息](https://technet.microsoft.com/windows/release-info)
- [Windows 10 更新历史记录](https://support.microsoft.com/help/4018124/windows-10-update-history)
- [Office 365 客户端更新频道版本](https://technet.microsoft.com/office/mt465751)
- [Microsoft Intune 新增功能](https://docs.microsoft.com/intune/whats-new)
- [System Center Configuration Manager 中的新增功能](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-incremental-versions)
- [System Center Configuration Manager Technical Preview 1708 中的功能](https://docs.microsoft.com/sccm/core/get-started/capabilities-in-technical-preview-1708)

## <a name="services-overview"></a>服务概述

本部分概述了 Microsoft 365 Enterprise 随附的 EMS 和 Office 365 服务，并介绍了一些必须掌握的核心概念，以便读者可以了解如何充分利用此解决方案来满足组织需求。 借助这些服务提供的功能，Microsoft 云企业管理员不仅可以保护公司员工的标识和设备，还可以控制对公司数据本身的访问（无论是在传输中，还是在静态状态下）。

|服务|描述|
|-------|-----------|
|[Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)|Azure AD 提供一整套标识管理功能，包括多重身份验证、设备注册、自助式密码管理、自助式组管理、基于角色的访问控制、应用程序使用情况监视、各种审核以及安全监视和警报。|
|[Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection)|借助此服务，可以检测影响组织标识的潜在漏洞，并通过条件访问策略配置对低、中、高登录风险和用户风险的自动响应。|
|[Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)|借助此服务，组织可以将永久有权执行特权操作的用户数降至最低；Azure AD Privileged Identity Management 引入了符合条件的管理员这一概念。符合条件的管理员应为偶尔（而不是每天）需要特权的用户。 在用户需要访问权限之前，此角色处于非活动状态。完成激活过程后，此管理员角色将在预先确定的一段时间内处于活动状态。|
|[Azure 信息保护](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection)| Azure 信息保护是基于云的解决方案，属于 EMS E5 产品/服务，可有助于组织分类、标示和保护文档和电子邮件。 这可以由定义规则和条件的管理员自动进行、由用户手动进行或是组合进行（在这种情况下会向用户提供建议）。 可使用 Azure 信息保护标签对文档和电子邮件应用分类。 执行此操作时，分类在任何时候都是可识别的，无论数据的存储位置在哪或者与谁共享数据。<br><br>Azure 信息保护策略设置受 [Azure Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms) 保护。 与标签的应用方式类似，使用 Rights Management 应用的保护会一直为文档和电子邮件提供保护，与位置无关（无论是在组织内外、网络内外、文件服务器内外，还是在应用程序内外）。|
|[Microsoft Intune](https://docs.microsoft.com/intune/understand-explore/introduction-to-microsoft-intune)|Intune 是一种基于云的企业移动管理 (EMM) 服务，可帮助员工提高工作效率，同时保护企业数据。 Intune 与 Azure AD 紧密集成以提供标识和访问控制，Intune 可用于管理设备和应用程序。 [Intune 设备管理](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)功能用于配置和保护用户设备，包括 Windows 电脑。<br><br>Intune 设备管理功能支持[自带设备办公 (BYOD)](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-byod) 注册，以便用户能够注册个人手机、平板电脑或电脑；此外，还支持[企业自有设备 (COD)](https://docs.microsoft.com/enterprise-mobility-security/solutions/issue-corp-devices) 注册，从而支持自动注册、共享设备或预授权的注册需求配置等管理方案。 为提高安全性，甚至可以要求必须通过 MFA 才能注册设备。 注册管理功能后，Intune 可以配置设备功能和设置，以实现对公司资源的安全访问。|

## <a name="important-concepts-to-understand"></a>需要了解的重要概念
下表介绍了应熟悉的核心概念和 EMS 功能。

|核心概念|描述|
|------------|-----------|
|[Azure 多重身份验证 (MFA)](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)|作为 Microsoft 的双重验证解决方案，Azure MFA 有助于保护对数据和应用程序的访问，同时可以满足用户对简单登录过程的需求。 此解决方案通过一系列验证方法（包括电话呼叫、短信或移动应用验证）提供了安全系数高的身份验证。|
|[Azure AD 条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)|借助 Azure AD 的这一功能，可以根据特定条件强制控制对环境中云应用的访问。 通过施加控制，可以对访问附加要求，也可以阻止访问。 条件访问的实现依据为策略。|
|[Exchange Online 数据丢失防护 (DLP)](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)|作为 Exchange Online 计划 2 和 Office 365 订阅的高级功能，Exchange Online 数据丢失防护 (DLP) 策略可有助于组织跨 Office 365 标识、监视和自动保护敏感信息。<br><br>通过 Exchange Online DLP 策略，可以跨多个位置（如 Exchange Online、SharePoint Online 和 OneDrive for Business）标识敏感信息。 例如，这些策略有助于标识包含敏感信息的文档，或防止与组织外部人员意外共享敏感信息。|
|[Exchange 邮件流/传输规则](https://support.office.com/article/Define-mail-flow-rules-to-encrypt-or-decrypt-email-messages-9B7DAF19-D5F2-415B-BC43-A0F5F4A585E8)|Exchange 邮件流规则（亦称为“传输规则”）在通过组织传递的邮件中查找特定条件，并采取相应措施。 邮件流规则与许多电子邮件客户端中的收件箱规则一样。 邮件流规则与在客户端应用程序（如 Outlook）中设置的规则的主要区别在于，邮件流规则针对的是传递中的邮件，而不是已传递的邮件。 邮件流规则还包含一组更丰富的条件、异常和操作，以便用户可以灵活实现多种类型的邮件传递策略。|
|[Intune 移动设备管理](https://docs.microsoft.com/intune/understand-explore/introduction-to-microsoft-intune)|Intune 使用移动操作系统中的可用协议或 API 提供移动设备管理 (MDM)。 具体包括如下任务：为设备注册管理功能以便 IT 有访问企业服务的设备清单、配置设备以确保它们符合公司安全和运行状况标准、提供用于访问企业服务的证书和 Wi-Fi/VPN 配置文件、报告和衡量设备是否符合公司标准、从受管理设备中删除企业数据。|
|[Intune 应用保护策略](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)|无论是否为设备注册管理功能，Intune 应用保护策略都可用于保护公司在移动应用中的数据。 事实上，用户的移动设备甚至可以由其他非 Microsoft MDM 解决方案进行管理，同时[通过 Intune 保护 Office 365 信息](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-company-data-without-managing-devices)。 在确保员工仍可高效工作的同时，还可以防止有意和无意数据丢失。 通过实现应用级策略，既可以限制对公司资源的访问，也可以让数据在 IT 部门的控制范围之内。|
|[Azure AD 令牌生存期](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes)|可以指定 Azure Active Directory (Azure AD) 颁发的令牌的生存期。 可以为组织中的所有应用程序、多租户（多组织）应用程序或组织中的特定服务主体设置令牌生存期。|
|Microsoft 标识中转站|Microsoft 为每个移动平台提供应用，以允许跨不同供应商的应用桥接凭据，并提供需要从一个安全位置验证凭据的特殊增强功能。 我们称之为“中转站”。 在 iOS 和 Android 上，这些中转站是通过 Microsoft Authenticator 和 Intune 公司门户应用提供。 在 Windows 10 中，此功能由操作系统中内置的帐户选择器提供，在技术上称为“Web 身份验证中转站”。|

## <a name="security-best-practices-and-recommendations"></a>安全最佳做法和建议
并不存在适用于所有客户环境的最佳建议，[推荐的安全策略和配置](microsoft-365-policies-configurations.md)一文介绍了应了解的重要安全最佳实践概念。 本文还介绍了一些通用的 Microsoft 建议，这些建议针对如何在 Microsoft 云中应用策略和配置，以确保员工在安全的环境中高效工作。

### <a name="baseline-recommended-security-policies-and-configurations"></a>推荐的基线安全策略和配置
[通用身份识别与设备访问策略建议](identity-access-policies.md)介绍了一些通用的策略，这些策略可帮助你保护 Microsoft 365 Enterprise。 此外，还介绍了我们为了向用户提供最佳 SSO 体验而推荐的默认平台客户端配置，以及条件访问的技术先决条件。

### <a name="exchange-online-access-policies"></a>Exchange Online 访问策略
Microsoft 在[可帮助保护电子邮件的策略建议](secure-email-recommended-policies.md)中提供了建议，可帮助你保护支持新式验证和条件访问的组织电子邮件和电子邮件客户端。 这些建议是[通用身份识别与设备访问策略建议](identity-access-policies.md)的补充。

### <a name="sharepoint-online-access-policies"></a>SharePoint Online 访问策略
除[通用身份识别与设备访问策略建议](identity-access-policies.md)和[可帮助保护电子邮件的策略建议](secure-email-recommended-policies.md)外，[保护 SharePoint Online 文件访问](sharepoint-file-access-policies.md)中也提供了建议。 本文介绍了必须创建哪些新策略，以及应如何修订现有策略，以保护 Exchange Online 电子邮件和 SharePoint Online 文件访问。

## <a name="deploy-windows-10-and-office-365-proplus"></a>部署 Windows 10 和 Office 365 专业增强版
了解如何部署 Windows 10 和 Office 365 专业增强版，以及如何集成到 Microsoft Azure Active Directory (Azure AD) 或本地 Active Directory 域服务 (AD DS) 中。 使用 Intune、System Center Configuration Manager 和组策略，将 Windows 10、Office 365 专业增强版和其他业务线应用程序部署到新设备，或将现有设备升级到 Windows 10，以便管理设备。

有关详细信息，请参阅以下文章：
- [Windows 10 部署注意事项](https://docs.microsoft.com/windows/deployment/planning/windows-10-deployment-considerations)
- [Office 365 专业增强版的部署指南](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [在企业中部署 Office 365 专业增强版的最佳做法指南](https://docs.microsoft.com/DeployOffice/best-practices/best-practices)
- [使用 Intune 将 Office 365 专业增强版应用程序分配到 Windows 10 设备](https://docs.microsoft.com/intune/apps-add-office365)

若要获取部署 Microsoft 365 方面的帮助，请[联系 FastTrack](https://fasttrack.microsoft.com/microsoft365)。

## <a name="manage-updates-to-windows-10-and-office-365-proplus"></a>管理 Windows 10 和 Office 365 专业增强版的更新
单击以下链接，可以了解如何最大限度地控制 Windows 10 和 Office 365 专业增强版的质量和功能更新。 了解如何有效控制带宽使用，并应用最新功能和安全更新程序，不断更新 Windows 和 Office。

有关详细信息，请参阅以下文章：
- [Windows 即服务概述](https://docs.microsoft.com/windows/deployment/update/waas-overview)
- [Office 365 专业增强版的更新频道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)
- [使用 Intune 管理软件更新](https://docs.microsoft.com/intune/windows-update-for-business-configure)
- [使用 System Center Configuration Manager 部署 Windows 10 更新](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-configuration-manager)<sup>*</sup>
- [使用 Configuration Manager 管理 Office 365 专业增强版](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates)

<sup>*</sup>Microsoft 建议当前使用 Configuration Manager 管理 Windows 更新的组织，继续对 Windows 10 客户端计算机这样做。

## <a name="next-steps"></a>后续步骤
[Microsoft 365 Enterprise 产品页](https://www.microsoft.com/microsoft-365/enterprise)<br/>
[云平台路线图](https://www.microsoft.com/cloud-platform/roadmap)
