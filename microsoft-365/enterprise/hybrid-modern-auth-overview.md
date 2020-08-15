---
title: 混合新式验证概述以及与本地 Skype for Business和 Exchange 服务器一起使用的先决条件
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 04/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: 在本文中，您将了解混合新式身份验证以及与本地 Skype for Business 和 Exchange 服务器配合使用的先决条件。
ms.openlocfilehash: 1dbea7643685d68564b1ba09b17c41aa2e5e42f1
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687613"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="1e9e0-103">混合新式验证概述以及将其与本地 Skype for Business和 Exchange 服务器一起使用的先决条件</span><span class="sxs-lookup"><span data-stu-id="1e9e0-103">Hybrid modern authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="1e9e0-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="1e9e0-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1e9e0-105">_新式验证_是一种标识管理，它提供更安全的用户身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-105">_Modern Authentication_ is a method of identity management that offers more secure user authentication and authorization.</span></span> <span data-ttu-id="1e9e0-106">它适用于本地 Skype for Business 服务器和本地 Exchange 服务器的 Office 365 混合部署以及拆分域 Skype for Business 混合部署。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-106">It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids.</span></span> <span data-ttu-id="1e9e0-107">本文链接到有关先决条件、设置/禁用新式验证的相关文档，以及一些相关客户端（例如</span><span class="sxs-lookup"><span data-stu-id="1e9e0-107">This article links to related docs about prerequisites, setup/disabling modern authentication, and to some of the related client (ex.</span></span> <span data-ttu-id="1e9e0-108">Outlook 和 Skype 客户端）的信息。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-108">Outlook and Skype clients) information.</span></span>
  
- [<span data-ttu-id="1e9e0-109">什么是新式验证？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-109">What is modern authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [<span data-ttu-id="1e9e0-110">使用新式验证时有何变化？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-110">What changes when I use modern authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [<span data-ttu-id="1e9e0-111">检查本地环境的新式验证状态</span><span class="sxs-lookup"><span data-stu-id="1e9e0-111">Check the modern authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [<span data-ttu-id="1e9e0-112">是否满足新式验证先决条件？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-112">Do you meet modern authentication prerequisites?</span></span>](#do-you-meet-modern-authentication-prerequisites)
- [<span data-ttu-id="1e9e0-113">在开始之前，我还需要了解哪些信息？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-113">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a><span data-ttu-id="1e9e0-114">什么是新式验证？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-114">What is modern authentication?</span></span>
<span data-ttu-id="1e9e0-115"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="1e9e0-115"><a name="BKMK_WhatisModAuth"> </a></span></span>

<span data-ttu-id="1e9e0-116">新式验证是客户端（例如，笔记本电脑或手机）和服务器之间的身份验证和授权方法的组合，以及某些依赖于你可能已经熟悉的访问策略的安全措施的总称。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-116">Modern authentication is an umbrella term for a combination of authentication and authorization methods between a client (for example, your laptop or your phone) and a server, as well as some security measures that rely on access policies that you may already be familiar with.</span></span> <span data-ttu-id="1e9e0-117">其中包括：</span><span class="sxs-lookup"><span data-stu-id="1e9e0-117">It includes:</span></span>
  
- <span data-ttu-id="1e9e0-118">**身份验证方法**：多重身份验证 (MFA)；智能卡身份验证；基于客户端证书的身份验证</span><span class="sxs-lookup"><span data-stu-id="1e9e0-118">**Authentication methods**: Multi-factor authentication (MFA); smart card authentication; client certificate-based authentication</span></span>
- <span data-ttu-id="1e9e0-119">**身份验证方法**：Microsoft 的开放授权 (OAuth) 实施</span><span class="sxs-lookup"><span data-stu-id="1e9e0-119">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth)</span></span>
- <span data-ttu-id="1e9e0-120">**条件访问策略**：移动应用程序管理 (MAM) 和 Azure Active Directory (Azure AD) 条件访问</span><span class="sxs-lookup"><span data-stu-id="1e9e0-120">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory (Azure AD) Conditional Access</span></span>

<span data-ttu-id="1e9e0-121">通过新式验证来管理用户身份，可以为管理员提供多种保护资源的工具，并为本地（Exchange 和 Skype for Business）、Exchange 混合以及 Skype for Business 混合/拆分域方案提供更安全的身份管理方法。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-121">Managing user identities with modern authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="1e9e0-122">请注意，由于 Skype for Business 与 Exchange 紧密合作，因此 Skype for Business 客户端用户将看到的登录行为将受 Exchange 的新式验证状态影响。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-122">Be aware that because Skype for Business works closely with Exchange, the login behavior Skype for Business client users will see will be affected by the modern authentication status of Exchange.</span></span> <span data-ttu-id="1e9e0-123">如果你具有 Skype for Business _拆分域_混合体系结构，你在其中同时拥有本地 Skype for Business Online 和本地 Skype for Business，并且用户同时位于两个位置，则此方式也适用。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-123">This will also apply if you have a Skype for Business _split-domain_ hybrid architecture, in which you have both Skype for Business Online and Skype for Business on-premises, with users homed in both locations.</span></span>

<span data-ttu-id="1e9e0-124">有关 Office 365 中的新式验证的详细信息，请参阅 [Office 365 客户端应用支持 — 新式身份验证](microsoft-365-client-support-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-124">For more information about modern authentication in Office 365, see [Office 365 Client App Support - Modern Authentication](microsoft-365-client-support-modern-authentication.md).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="1e9e0-125">自 2017 年 8 月起，包括 Skype for Business Online 和 Exchange Online 在内的所有新 Office 365 租户都将默认启用新式验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-125">As of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have modern authentication enabled by default.</span></span> <span data-ttu-id="1e9e0-126">既有租户的默认 MA 状态不会发生变化，但是所有新租户都会自动支持上面列出的一组扩展身份功能。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-126">Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above.</span></span> <span data-ttu-id="1e9e0-127">若要查看你的 MA 状态，请参阅[检查本地环境的新式验证状态](hybrid-modern-auth-overview.md#BKMK_CheckStatus)部分。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-127">To check your MA status, see the [Check the modern authentication status of your on-premises environment](hybrid-modern-auth-overview.md#BKMK_CheckStatus) section.</span></span>
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="1e9e0-128">使用新式验证时有何变化？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-128">What changes when I use modern authentication?</span></span>
<span data-ttu-id="1e9e0-129"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="1e9e0-129"><a name="BKMK_WhatChanges"> </a></span></span>

<span data-ttu-id="1e9e0-130">在本地 Skype for Business 或 Exchange 服务器上使用新式验证时，仍将对用户进行*身份验证*，但*授权*他们对资源（例如文件或电子邮件）进行更改。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-130">When using modern authentication with on-premises Skype for Business or Exchange server, you're still *authenticating* users on-premises, but the story of *authorizing* their access to resources (like files or emails) changes.</span></span> <span data-ttu-id="1e9e0-131">这就是为什么尽管新式验证与客户端和服务器通信有关，但在配置 MA 期间采取的步骤会导致 evoSTS（Azure AD 使用的安全令牌服务）被设置为 Skype for Business 和本地 Exchange Server 的身份验证服务器。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-131">This is why, though modern authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span>
  
<span data-ttu-id="1e9e0-132">对 evoSTS 的更改使你的本地服务器可以利用 OAuth（令牌发行）对客户端进行授权，还可以让你的本地服务器使用云中常见的安全方法（例如多重身份验证）。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-132">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication).</span></span> <span data-ttu-id="1e9e0-133">另外，evoSTS 还会发行令牌，使用户可以请求访问资源而无需在请求中提供密码。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-133">Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request.</span></span> <span data-ttu-id="1e9e0-134">无论用户位于何处（线上还是本地）、无论哪个位置托管所需资源，一旦配置了新式验证，EvoSTS 都将成为授权用户和客户端的核心。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-134">No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once modern authentication is configured.</span></span>
  
<span data-ttu-id="1e9e0-135">例如，如果 Skype for Business 客户端需要访问 Exchange 服务器以代表用户获取日历信息，则会使用 Active Directory 身份验证库 (ADAL) 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-135">For example, if a Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so.</span></span> <span data-ttu-id="1e9e0-136">ADAL 是一个代码库，旨在使用 OAuth 安全令牌将目录中的安全资源提供给客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-136">ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens.</span></span> <span data-ttu-id="1e9e0-137">ADAL 与 OAuth 一起使用以验证声明并交换令牌（而不是密码），以授予用户对资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-137">ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource.</span></span> <span data-ttu-id="1e9e0-138">过去，此类事务中的授权服务（知道如何验证用户声明并发出所需令牌的服务器）可能是本地安全令牌服务，甚至是 Active Directory 联合身份验证服务。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-138">In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services.</span></span> <span data-ttu-id="1e9e0-139">但是，新式验证通过使用 Azure AD 集中了该授权服务。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-139">However, modern authentication centralizes that authority by using Azure AD.</span></span>
  
<span data-ttu-id="1e9e0-140">这也意味着，即使你的 Exchange 服务器和 Skype for Business 环境可能完全位于本地，授权服务器也将处于联机状态，并且你的本地环境必须具有创建和维护与云中的 Office 365 订阅（以及你的订阅将其用作目录的 Azure AD 实例）的连接的能力。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-140">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure AD instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="1e9e0-141">哪些方面没有发生更改？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-141">What doesn't change?</span></span> <span data-ttu-id="1e9e0-142">无论你是在拆分域混合环境还是在本地使用 Skype for Business 和 Exchange 服务器，所有用户都必须首先在*本地*进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-142">Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate *on-premises*.</span></span> <span data-ttu-id="1e9e0-143">在新式验证的混合实施中，_Lyncdiscovery_ 和 _Autodiscovery_ 都指向本地服务器。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-143">In a hybrid implementation of modern authentication, _Lyncdiscovery_ and _Autodiscovery_ both point to your on-premises server.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="1e9e0-144">如果你需要了解 MA 支持的特定 Skype for Business 拓扑，请在[此处](https://technet.microsoft.com/library/mt803262.aspx)进行文档说明。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-144">If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="1e9e0-145">检查本地环境的新式验证状态</span><span class="sxs-lookup"><span data-stu-id="1e9e0-145">Check the modern authentication status of your on-premises environment</span></span>
<span data-ttu-id="1e9e0-146"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="1e9e0-146"><a name="BKMK_CheckStatus"> </a></span></span>

<span data-ttu-id="1e9e0-147">由于新式验证会更改服务利用 OAuth/S2S 时使用的授权服务器，因此你需要知道是否为本地 Skype for Business 和 Exchange 环境启用或禁用了新式验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-147">Because modern authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if modern authentication is enabled or disabled for your on-premises Skype for Business and Exchange environments.</span></span> <span data-ttu-id="1e9e0-148">可以通过运行以下 PowerShell 命令来检查 Exchange 服务器上的状态：</span><span class="sxs-lookup"><span data-stu-id="1e9e0-148">You can check the status on your Exchange servers by running the following PowerShell command:</span></span>

```powershell
Get-OrganizationConfig | ft OAuth*
```

<span data-ttu-id="1e9e0-149">如果 _OAuth2ClientProfileEnabled_ 属性的值为 **False**，则可以进行新式验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-149">If the value of the _OAuth2ClientProfileEnabled_ property is **False**, then modern authentication is disabled.</span></span>

<span data-ttu-id="1e9e0-150">有关 OrganizationConfig cmdlet 的详细信息，请参阅 [OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig)。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-150">For more information about the Get-OrganizationConfig cmdlet, see [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig).</span></span>

<span data-ttu-id="1e9e0-151">可以通过运行以下 PowerShell 命令来检查 Skype for Business 服务器：</span><span class="sxs-lookup"><span data-stu-id="1e9e0-151">You can check your Skype for Business servers by running the following PowerShell command:</span></span>

```powershell
Get-CSOAuthConfiguration
```

<span data-ttu-id="1e9e0-152">如果命令返回空的 _OAuthServers_ 属性，或者如果 _ClientADALAuthOverride_ 属性的值不是 **Allowed**，则表示新式验证已禁用。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-152">If the command returns an empty _OAuthServers_ property, or if the value of the _ClientADALAuthOverride_ property is not **Allowed**, then modern authentication is disabled.</span></span>

<span data-ttu-id="1e9e0-153">有关 CsOAuthConfiguration cmdlet 的详细信息，请参阅 [CsOAuthConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration)。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-153">For more information about the Get-CsOAuthConfiguration cmdlet, see [Get-CsOAuthConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration).</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="1e9e0-154">是否满足新式验证先决条件？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-154">Do you meet modern authentication prerequisites?</span></span>

<span data-ttu-id="1e9e0-155">在继续之前，请验证并检查列表中的以下项目：</span><span class="sxs-lookup"><span data-stu-id="1e9e0-155">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="1e9e0-156">**特定于 Skype for Business**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-156">**Skype for Business specific**</span></span>
  - <span data-ttu-id="1e9e0-157">所有服务器都必须具有 Skype for Business Server 2015 或更高版本 2017 年 5 月的累积更新 (CU5)</span><span class="sxs-lookup"><span data-stu-id="1e9e0-157">All servers must have May 2017 cumulative update (CU5) for Skype for Business Server 2015 or later</span></span>
    - <span data-ttu-id="1e9e0-158">**例外** — Survivability Branch Appliance (SBA) 可以是当前版本（基于 Lync 2013）</span><span class="sxs-lookup"><span data-stu-id="1e9e0-158">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span>
  - <span data-ttu-id="1e9e0-159">你的 SIP 域被添加为 Office 365 中的联合域</span><span class="sxs-lookup"><span data-stu-id="1e9e0-159">Your SIP domain is added as a Federated domain in Office 365</span></span>
  - <span data-ttu-id="1e9e0-160">所有 SFB 前端必须具有与 Internet、Office 365 身份验证 URL (TCP 443) 以及[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)的“Microsoft 365 通用和 Office”部分第 56 行和第 125 行中列出的已知证书根CRL (TCP 80) 的出站连接。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-160">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 56 and 125 of the 'Microsoft 365 Common and Office' section of [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
- <span data-ttu-id="1e9e0-161">**混合 Office 365 环境中的本地 Skype for Business**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-161">**Skype for Business on-premises in a hybrid Office 365 environment**</span></span>
  - <span data-ttu-id="1e9e0-162">Skype for Business Server 2019 部署（所有服务器都运行 Skype for Business Server 2019）。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-162">A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.</span></span>
  - <span data-ttu-id="1e9e0-163">Skype for Business Server 2015 部署（所有服务器都运行 Skype for Business Server 2015）。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-163">A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.</span></span>
  - <span data-ttu-id="1e9e0-164">最多具有两个不同服务器版本的部署，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e9e0-164">A deployment with a maximum of two different server versions as listed below:</span></span>
    - <span data-ttu-id="1e9e0-165">Skype for Business Server 2015</span><span class="sxs-lookup"><span data-stu-id="1e9e0-165">Skype for Business Server 2015</span></span>
    - <span data-ttu-id="1e9e0-166">Skype for Business Server 2019</span><span class="sxs-lookup"><span data-stu-id="1e9e0-166">Skype for Business Server 2019</span></span>
  - <span data-ttu-id="1e9e0-167">所有 Skype for Business 服务器都必须安装最新的累积更新，请参阅 [Skype for Business服务器更新](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)以查找和管理所有可用更新。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-167">All Skype for Business servers must have the latest cumulative updates installed, see [Skype for Business Server updates](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) to find and manage all available updates.</span></span>
  - <span data-ttu-id="1e9e0-168">混合环境中没有 Lync Server 2010 或 2013。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-168">There is no Lync Server 2010 or 2013 in the hybrid environment.</span></span>

>[!NOTE]
><span data-ttu-id="1e9e0-169">如果你的 Skype for Business 前端服务器使用代理服务器进行 Internet 访问，则必须在 web.config 文件的配置部分中为每个前端输入使用的代理服务器 IP 和端口号。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-169">If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span>
  
- <span data-ttu-id="1e9e0-170">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span><span class="sxs-lookup"><span data-stu-id="1e9e0-170">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
- <span data-ttu-id="1e9e0-171">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span><span class="sxs-lookup"><span data-stu-id="1e9e0-171">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> <span data-ttu-id="1e9e0-172">确保为 [Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)订阅 RSS 源，以随时获取最新的必需 URL 列表。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-172">Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) to stay current with the latest listings of required URLs.</span></span>
  
- <span data-ttu-id="1e9e0-173">**特定于 Exchange 服务器**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-173">**Exchange Server specific**</span></span>
  - <span data-ttu-id="1e9e0-174">你正在使用 Exchange Server 2013 CU19 及更高版本、Exchange Server 2016 CU8 及更高版本或 Exchange Server 2019 CU1 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-174">You're using either Exchange server 2013 CU19 and up, Exchange server 2016 CU8 and up, or Exchange Server 2019 CU1 and up.</span></span>
  - <span data-ttu-id="1e9e0-175">环境中没有 Exchange server 2010。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-175">There is no Exchange server 2010 in the environment.</span></span>
  - <span data-ttu-id="1e9e0-176">未配置 SSL 卸载。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-176">SSL Offloading is not configured.</span></span> <span data-ttu-id="1e9e0-177">支持 SSL 终止和重新加密。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-177">SSL termination and re-encryption is supported.</span></span>
  - <span data-ttu-id="1e9e0-178">如果你的环境利用代理服务器基础结构来允许服务器连接到 Internet，请确保所有 Exchange 服务器都具有 [InternetWebProxy ](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) 属性中定义的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-178">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
  
- <span data-ttu-id="1e9e0-179">**混合 Office 365 环境中的本地 Exchange Server**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-179">**Exchange Server on-premises in a hybrid Office 365 environment**</span></span>

  - <span data-ttu-id="1e9e0-180">如果你使用的是 Exchange Server 2013，则必须有至少一台服务器安装了邮箱和客户端访问服务器角色。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-180">If you are using Exchange Server 2013, at least one server must have the Mailbox and Client Access server roles installed.</span></span> <span data-ttu-id="1e9e0-181">虽然可以在单独的服务器上安装邮箱和客户端访问角色，但我们强烈建议你在同一服务器上安装这两个角色，这样可以提供额外的可靠性和更好的性能。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-181">While it is possible to install the Mailbox and Client Access roles on separate servers, we strongly recommend that you install both roles on the same server to provide additional reliability and improved performance.</span></span>
  - <span data-ttu-id="1e9e0-182">如果你使用的是 Exchange Server 2016 或更高版本，则必须有至少一台服务器安装了邮箱服务器角色。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-182">If you are using Exchange server 2016 or later version, at least one server must have the Mailbox server role installed.</span></span>
  - <span data-ttu-id="1e9e0-183">混合环境中没有 Exchange server 2007 或 2010。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-183">There is no Exchange server 2007 or 2010 in the Hybrid environment.</span></span>
  - <span data-ttu-id="1e9e0-184">所有 Exchange 服务器都必须安装最新的累积更新，请参阅 [将 Exchange 升级到最新累积更新](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)以查找和管理所有可用更新。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-184">All Exchange servers must have the latest cumulative updates installed, see [Upgrade Exchange to the latest Cumulative Updates](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) to find and manage all available updates.</span></span>

- <span data-ttu-id="1e9e0-185">**Exchange 客户端和协议要求**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-185">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="1e9e0-186">以下客户端支持新式身份验证：</span><span class="sxs-lookup"><span data-stu-id="1e9e0-186">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="1e9e0-187">**客户端**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-187">**Clients**</span></span>|<span data-ttu-id="1e9e0-188">**主协议**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-188">**Primary Protocol**</span></span>|<span data-ttu-id="1e9e0-189">**备注**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-189">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="1e9e0-190">Outlook 2013 和 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="1e9e0-190">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="1e9e0-191">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="1e9e0-191">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="1e9e0-192">必须在 Exchange 中启用 MAPI over HTTP，以对这些客户端使用新式验证（对于新安装的 Exchange 2013 Service Pack 1 和更高版本，通常已启用或为“True”）；有关详细信息，请参阅[如何将新式验证用于 Office 2013 和 Office 2016 客户端应用](modern-auth-for-office-2013-and-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-192">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>  <br/> <span data-ttu-id="1e9e0-193">确保运行的是最低要求的 Outlook 内部版本；请参阅[使用 Windows Installer (MSI) 的 Outlook 版本的最新更新](https://docs.microsoft.com/officeupdates/outlook-updates-msi)。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-193">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="1e9e0-194">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="1e9e0-194">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="1e9e0-195">Exchange Web 服务</span><span class="sxs-lookup"><span data-stu-id="1e9e0-195">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="1e9e0-196">Outlook for iOS 和 Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="1e9e0-196">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="1e9e0-197">有关详细信息，请参阅[将混合新式验证用于 Outlook for iOS 和 Outlook for Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-197">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="1e9e0-198">Exchange ActiveSync 客户端（例如，iOS11 邮件）</span><span class="sxs-lookup"><span data-stu-id="1e9e0-198">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="1e9e0-199">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="1e9e0-199">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="1e9e0-200">对于支持新式验证的 Exchange ActiveSync 客户端，必须重新创建配置文件才能从基本身份验证切换到新式验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-200">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="1e9e0-201">**一般先决条件**</span><span class="sxs-lookup"><span data-stu-id="1e9e0-201">**General prerequisites**</span></span>
  - <span data-ttu-id="1e9e0-202">如果使用 AD FS，则应使用 Windows 2012 R2 AD FS 3.0 及更高版本进行联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-202">If you use AD FS, you should have Windows 2012 R2 AD FS 3.0 and above for federation.</span></span>
  - <span data-ttu-id="1e9e0-203">身份配置是 Azure AD Connect 支持的任何类型，例如密码哈希同步、传递身份验证和 Office 365 支持的本地 STS。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-203">Your identity configurations are any of the types supported by Azure AD Connect, such as password hash sync, pass-through authentication, and on-premises STS supported by Office 365.</span></span>
  - <span data-ttu-id="1e9e0-204">已配置 Azure AD Connect 并可正常进行用户复制和同步。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-204">You have Azure AD Connect configured and functioning for user replication and sync.</span></span>
  - <span data-ttu-id="1e9e0-205">已验证已使用 Exchange 经典混合拓扑模式在本地和 Office 365 环境之间配置了混合部署。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-205">You have verified that hybrid is configured using Exchange Classic Hybrid Topology mode between your on-premises and Office 365 environment.</span></span> <span data-ttu-id="1e9e0-206">Exchange混合部署的官方支持声明指明必须拥有当前 CU 或当前 CU-1。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-206">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    > [!NOTE]
    > <span data-ttu-id="1e9e0-207">[混合代理](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)不支持混合新式验证。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-207">Hybrid modern authentication is not supported with the [Hybrid Agent](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).</span></span>

  - <span data-ttu-id="1e9e0-208">确保本地测试用户以及 Office 365 中的混合测试用户都可以登录到 Skype for Business 桌面客户端（如果要对 Skype 使用新式验证）和 Microsoft Outlook（如果要对 Exchange 使用新式验证）。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-208">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use modern authentication with Skype) and Microsoft Outlook (if you want to use modern authentication with Exchange).</span></span>

## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="1e9e0-209">在开始之前，我还需要了解哪些信息？</span><span class="sxs-lookup"><span data-stu-id="1e9e0-209">What else do I need to know before I begin?</span></span>
<span data-ttu-id="1e9e0-210"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="1e9e0-210"><a name="BKMK_Whatelse"> </a></span></span>

- <span data-ttu-id="1e9e0-211">本地服务器的所有方案都涉及在本地设置新式验证（实际上，对于 Skype for Business，存在一系列受支持的拓扑），以便负责身份验证和授权的服务器位于 Microsoft 云中（Azure AD 的安全令牌服务，称为“evoSTS”），并更新与你的本地 Skype for Business 或 Exchange 安装所使用的 URL 或命名空间有关的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-211">All the scenarios for on-premises servers involve setting up modern authentication on-premises (in fact, for Skype for Business there is a list of supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (Azure AD's security token service, called 'evoSTS'), and updating Azure AD about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange.</span></span> <span data-ttu-id="1e9e0-212">因此，本地服务器具有 Microsoft 云依赖性。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-212">Therefore, on-premises servers take on a Microsoft Cloud dependency.</span></span> <span data-ttu-id="1e9e0-213">可以考虑采取此操作来配置“混合身份验证”。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-213">Taking this action could be considered configuring 'hybrid auth'.</span></span>
- <span data-ttu-id="1e9e0-214">本文链接到可帮助你选择支持的新式验证拓扑（仅对 Skype for Business 必需）的其他文章以及概述了设置步骤，或者针对本地 Exchange 和本地 Skype for business 禁用新式验证的步骤的操作说明文章。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-214">This article links out to others that will help you choose supported modern authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable modern authentication, for Exchange on-premises and Skype for Business on-premises.</span></span> <span data-ttu-id="1e9e0-215">如果需要一个在服务器环境中使用新式验证的基地，请在浏览器中收藏此页面。</span><span class="sxs-lookup"><span data-stu-id="1e9e0-215">Favorite this page in your browser if you're going to need a home-base for using modern authentication in your server environment.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1e9e0-216">相关主题</span><span class="sxs-lookup"><span data-stu-id="1e9e0-216">Related Topics</span></span>
<span data-ttu-id="1e9e0-217"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="1e9e0-217"><a name="BKMK_URLListforMA"> </a></span></span>

- [<span data-ttu-id="1e9e0-218">如何配置本地 Exchange Server 以使用新式验证</span><span class="sxs-lookup"><span data-stu-id="1e9e0-218">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
- [<span data-ttu-id="1e9e0-219">新式验证支持的 Skype for Business 拓扑</span><span class="sxs-lookup"><span data-stu-id="1e9e0-219">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/library/mt803262.aspx)
- [<span data-ttu-id="1e9e0-220">如何配置本地 Skype for Business 以使用新式验证</span><span class="sxs-lookup"><span data-stu-id="1e9e0-220">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [<span data-ttu-id="1e9e0-221">从 Skype for Business 和 Exchange 删除或禁用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="1e9e0-221">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
