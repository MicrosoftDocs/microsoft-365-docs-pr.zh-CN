---
title: 建议的安全文档策略 - Microsoft 365策略|Microsoft Docs
description: 介绍 Microsoft 建议中有关如何保护 SharePoint 文件访问的策略。
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
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 1771f71e444233ffce60a4a56273d3062fe8b70d
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "51203167"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>用于保护网站和SharePoint的策略建议

**适用对象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 计划 1 和计划 2](defender-for-office-365.md)
- SharePoint Online 


本文介绍如何实施推荐的标识和设备访问策略来保护SharePoint OneDrive for Business。 本指南基于通用[标识和设备访问策略。](identity-access-policies.md)

这些建议基于三种不同的安全和保护层，用于 SharePoint 文件，这些文件可以基于你的需求粒度应用：**基线**、敏感和 **高度管控**。  你可以了解有关这些安全层以及推荐的客户端操作系统（概述中这些建议 [所引用）的更多信息](microsoft-365-policies-configurations.md)。

除了实现本指南之外，请确保为SharePoint网站配置适当的保护，包括为敏感和高度管控内容设置适当的权限。

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>更新常见策略以包括SharePoint OneDrive for Business

若要保护SharePoint和设备OneDrive，下图说明了从通用标识和设备访问策略更新的策略。

[![用于保护对服务及其依赖Teams的访问的策略更新摘要](../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)

如果在创建SharePoint策略时包括了策略，则只需创建新策略。 对于条件访问策略，SharePoint包括OneDrive。

新策略通过对指定的网站应用特定访问要求，为敏感和高度管控SharePoint设备保护。

下表列出了需要查看和更新的策略，或创建新的SharePoint。 常见策略链接到常见标识和设备访问策略文章中的关联 [配置说明](identity-access-policies.md) 。

|保护级别|策略|详细信息|
|---|---|---|
|**Baseline**|[当登录风险为中或高 *时需要* MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|将SharePoint包括在云应用的分配中。|
||[阻止不支持新式身份验证的客户端](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|将SharePoint包括在云应用的分配中。|
||[应用 APP 数据保护策略](identity-access-policies.md#apply-app-data-protection-policies)|请确保所有推荐的应用都包含在应用列表中。 请务必为 iOS、Android、 (的每个平台更新Windows) 。|
||[需要兼容电脑](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|将SharePoint包括在云应用列表中。|
||[在应用中使用应用强制SharePoint](#use-app-enforced-restrictions-in-sharepoint)|添加新策略。 这将Azure Active Directory (Azure AD) 使用 SharePoint 中指定的设置。 此策略适用于所有用户，但仅影响对访问策略中包含的SharePoint的访问。|
|**敏感**|[登录风险低、中或高 *时需要* MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|将SharePoint包括在云应用的分配中。|
||[要求兼容电脑 *和* 移动设备](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|将SharePoint包括在云应用列表中。|
||[SharePoint访问控制策略](#sharepoint-access-control-policies)：允许仅浏览器访问SharePoint非托管设备的特定网站。|这将阻止编辑和下载文件。 使用 PowerShell 指定网站。|
|**高度管控**|[*始终* 需要 MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|将SharePoint包括在云应用的分配中。|
||[SharePoint访问控制策略](#use-app-enforced-restrictions-in-sharepoint)：阻止从非SharePoint访问特定网站。|使用 PowerShell 指定网站。|
|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>在应用程序中使用应用强制SharePoint

如果在 SharePoint 中实现访问控制，则必须在 Azure AD 中创建此条件访问策略，以告诉 Azure AD 强制执行在 SharePoint 中配置的策略。 此策略适用于所有用户，但仅影响在使用 PowerShell 创建访问控件时对使用 PowerShell 指定的SharePoint。

若要配置此策略，请参阅控制从非托管设备SharePoint或OneDrive访问特定网站集或帐户["。](/sharepoint/control-access-from-unmanaged-devices)

## <a name="sharepoint-access-control-policies"></a>SharePoint访问控制策略

Microsoft 建议通过设备访问控制SharePoint敏感和高度管控内容保护网站中的内容。 为此，可创建一个策略，指定保护级别以及要应用保护的网站。

- 敏感网站：允许仅浏览器访问。 这将阻止用户编辑和下载文件。
- 高度管控网站：阻止从非托管设备访问。

请参阅控制非托管设备SharePoint OneDrive中的"阻止或限制SharePoint访问特定网站集或帐户["。](/sharepoint/control-access-from-unmanaged-devices)

## <a name="how-these-policies-work-together"></a>这些策略如何协同工作

网站权限通常SharePoint访问网站的业务需求，了解这一点很重要。 这些权限由网站所有者管理，并且可以是高度动态的。 使用SharePoint访问策略可确保保护这些站点，无论用户被分配到与基线、敏感或高度管控保护相关联的 Azure AD 组。

下图提供了一个示例，SharePoint访问策略如何保护用户对网站的访问。

[![设备访问SharePoint如何保护网站的示例](../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)

[查看此图像的较大版本](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)

为一位用户分配了基线条件访问策略，但可以SharePoint敏感或高度管控保护的网站访问这些网站。

- 如果为访问敏感或高度管控网站而为使用电脑的成员，则只要其电脑合规，就授予他的访问权。
- 如果作为使用非托管电话（允许基线用户使用）的敏感网站，则他将收到对敏感网站的仅浏览器访问权限，因为为此网站配置了设备访问策略。
- 如果作为使用非托管电话的会员的一员，则由于为该网站配置了访问策略，因此将阻止他访问。 他只能使用自己托管且合规的电脑访问此网站。

## <a name="next-step"></a>后续步骤

![步骤 4：云Microsoft 365策略](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

为：配置条件访问策略：

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)