---
title: Microsoft 365 中的管理访问控制
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom: seo-marvel-apr2020
description: 本文提供了 Microsoft 365 中的管理访问控制和数据分类的概述。
ms.openlocfilehash: b5063f89e89b6cffffda53a5df3088a80f89c242
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687639"
---
# <a name="administrative-access-controls-in-microsoft-365"></a><span data-ttu-id="d80c1-103">Microsoft 365 中的管理访问控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-103">Administrative access controls in Microsoft 365</span></span> 

<span data-ttu-id="d80c1-104">Microsoft 已在系统和控件中进行了大量投资，以自动化 microsoft 365 的大多数操作，同时有意限制 Microsoft 对客户内容的访问。</span><span class="sxs-lookup"><span data-stu-id="d80c1-104">Microsoft has invested heavily in systems and controls that automate most Microsoft 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="d80c1-105">人类控制服务，软件运行服务。</span><span class="sxs-lookup"><span data-stu-id="d80c1-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="d80c1-106">这使 Microsoft 能够在规模扩展时管理 Microsoft 365，并管理对客户内容的内部威胁的风险。</span><span class="sxs-lookup"><span data-stu-id="d80c1-106">This enables Microsoft to manage Microsoft 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="d80c1-107">默认情况下，Microsoft 工程师拥有零的管理权限，并在 Microsoft 365 中提供对客户内容的零访问权限。</span><span class="sxs-lookup"><span data-stu-id="d80c1-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Microsoft 365.</span></span> <span data-ttu-id="d80c1-108">Microsoft 工程师可在有限的时间段中对客户的内容进行有限的审核和安全访问。</span><span class="sxs-lookup"><span data-stu-id="d80c1-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="d80c1-109">只有在服务操作必要时才进行访问，并且仅当由 Microsoft 高级管理的成员批准时才能访问。</span><span class="sxs-lookup"><span data-stu-id="d80c1-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="d80c1-110">对于客户密码箱许可的客户，客户提供对其在 Microsoft 365 上托管的内容的访问审批。</span><span class="sxs-lookup"><span data-stu-id="d80c1-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Microsoft 365.</span></span>

<span data-ttu-id="d80c1-111">Microsoft 使用多种形式的云传递提供了在线服务：</span><span class="sxs-lookup"><span data-stu-id="d80c1-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="d80c1-112">**公共云：** 包括在北美、南美洲、欧洲、亚洲、澳大利亚等托管的 Microsoft 365、Azure 和其他服务的多租户版本。</span><span class="sxs-lookup"><span data-stu-id="d80c1-112">**Public clouds:** Includes multi-tenant versions of Microsoft 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="d80c1-113">**国家/地区云：** 包括 (美国以外的所有 sovereign 和第三方运营云，除了之前) 之外的所有和第三方运行的云（如中国 () 运营的中国 365 Microsoft 365）和德语中的 Microsoft (由 Microsoft 运营，但在一种模型中，在德语数据受信者、德国电信中，控制并监控 Microsoft 对包含客户数据) 的客户数据</span><span class="sxs-lookup"><span data-stu-id="d80c1-113">**National clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Microsoft 365 in China (operated by 21Vianet), and Microsoft 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to customer data and systems that contain customer data).</span></span>
- <span data-ttu-id="d80c1-114">**政府群：** 包含适用于美国政府客户的 Microsoft 365 和 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="d80c1-114">**Government clouds:** Includes Microsoft 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="d80c1-115">出于本文的目的，Microsoft 365 服务包括：</span><span class="sxs-lookup"><span data-stu-id="d80c1-115">For purposes of this article, Microsoft 365 services include:</span></span>

- [<span data-ttu-id="d80c1-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d80c1-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="d80c1-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="d80c1-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="d80c1-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d80c1-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="d80c1-119">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="d80c1-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="d80c1-120">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="d80c1-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="d80c1-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d80c1-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="d80c1-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="d80c1-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="microsoft-365-access-controls"></a><span data-ttu-id="d80c1-123">Microsoft 365 访问控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-123">Microsoft 365 access controls</span></span>

<span data-ttu-id="d80c1-124">出于访问控制目的，Microsoft 将 Microsoft 365 数据分类为客户数据或其他类型的数据。</span><span class="sxs-lookup"><span data-stu-id="d80c1-124">For access control purposes, Microsoft categorizes Microsoft 365 data as customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="d80c1-125">客户数据</span><span class="sxs-lookup"><span data-stu-id="d80c1-125">Customer data</span></span>

<span data-ttu-id="d80c1-126">客户数据是在使用 Microsoft 365 服务时代表客户提供或代表客户提供的所有数据。</span><span class="sxs-lookup"><span data-stu-id="d80c1-126">Customer data is all data provided by or on behalf of a customer when using Microsoft 365 services.</span></span> <span data-ttu-id="d80c1-127">这是由 Microsoft 365 用户直接创建或上载的客户内容，包括：</span><span class="sxs-lookup"><span data-stu-id="d80c1-127">This is customer content directly created or uploaded by Microsoft 365 users, including:</span></span>

- <span data-ttu-id="d80c1-128">电子邮件</span><span class="sxs-lookup"><span data-stu-id="d80c1-128">Emails</span></span>
- <span data-ttu-id="d80c1-129">SharePoint Online 内容</span><span class="sxs-lookup"><span data-stu-id="d80c1-129">SharePoint Online content</span></span>
- <span data-ttu-id="d80c1-130">即时消息</span><span class="sxs-lookup"><span data-stu-id="d80c1-130">Instant messages</span></span>
- <span data-ttu-id="d80c1-131">日历项目</span><span class="sxs-lookup"><span data-stu-id="d80c1-131">Calendar items</span></span>
- <span data-ttu-id="d80c1-132">文档</span><span class="sxs-lookup"><span data-stu-id="d80c1-132">Documents</span></span>
- <span data-ttu-id="d80c1-133">联系人</span><span class="sxs-lookup"><span data-stu-id="d80c1-133">Contacts</span></span>
- <span data-ttu-id="d80c1-134">最终用户可识别的信息 (EUII) 用户特有或 linkable 给个人用户但不包含客户内容的数据 (数据) </span><span class="sxs-lookup"><span data-stu-id="d80c1-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content)</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="d80c1-135">其他类型的数据</span><span class="sxs-lookup"><span data-stu-id="d80c1-135">Other types of data</span></span>

<span data-ttu-id="d80c1-136">其他类型的数据包括：</span><span class="sxs-lookup"><span data-stu-id="d80c1-136">Other types of data include:</span></span>

- <span data-ttu-id="d80c1-137">**帐户数据：** 包括管理员在注册或购买服务) 时提供的管理数据 (信息，以及付款数据 (有关付款仪器的信息，如信用卡详细信息) 。</span><span class="sxs-lookup"><span data-stu-id="d80c1-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="d80c1-138">**组织的可识别信息：** 包含用于标识租户、使用情况数据，而不是 linkable 给个人用户或包含在客户内容中的数据。</span><span class="sxs-lookup"><span data-stu-id="d80c1-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="d80c1-139">**系统元数据：** 包括包含配置设置、系统状态、Microsoft IP 地址和订阅和租户的技术信息的服务日志。</span><span class="sxs-lookup"><span data-stu-id="d80c1-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="d80c1-140">Microsoft 已建立了访问控制机制，以确保没有人撤销对客户数据或访问控制数据的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d80c1-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="d80c1-141">访问控制数据管理对环境中其他类型的数据或函数的访问，包括对客户内容或 EUII、Microsoft 密码、安全证书和其他与身份验证相关的数据的访问。</span><span class="sxs-lookup"><span data-stu-id="d80c1-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="d80c1-142">访问控制机制还可防止对 Microsoft 365 生产环境进行未批准的物理、逻辑或远程访问。</span><span class="sxs-lookup"><span data-stu-id="d80c1-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Microsoft 365 production environment.</span></span>

<span data-ttu-id="d80c1-143">Microsoft 为 microsoft 365 提供了三种访问控制类别：</span><span class="sxs-lookup"><span data-stu-id="d80c1-143">There are three categories of access controls used by Microsoft for operating Microsoft 365:</span></span>

- <span data-ttu-id="d80c1-144">隔离控件</span><span class="sxs-lookup"><span data-stu-id="d80c1-144">Isolation controls</span></span>
- <span data-ttu-id="d80c1-145">人员控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-145">Personnel controls</span></span>
- <span data-ttu-id="d80c1-146">技术控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-146">Technology controls</span></span>

<span data-ttu-id="d80c1-147">结合后，这些控制措施有助于防止和检测 Microsoft 365 中的恶意操作。</span><span class="sxs-lookup"><span data-stu-id="d80c1-147">When combined, these controls help prevent and detect malicious actions in Microsoft 365.</span></span> <span data-ttu-id="d80c1-148">除了 Microsoft 使用的隔离、人员和技术控件之外，还有第四个类别的控件：由客户实施的控件。</span><span class="sxs-lookup"><span data-stu-id="d80c1-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="d80c1-149">Microsoft 365 允许您以与在本地环境中管理数据的方式管理数据。</span><span class="sxs-lookup"><span data-stu-id="d80c1-149">Microsoft 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="d80c1-150">将组织注册为 Microsoft 365 的人员将自动成为全局管理员。</span><span class="sxs-lookup"><span data-stu-id="d80c1-150">The person who signs up an organization for Microsoft 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="d80c1-151">全局管理员可以访问管理门户中的所有功能，并且可以：</span><span class="sxs-lookup"><span data-stu-id="d80c1-151">The global admin has access to all features in management portals and can:</span></span>

- <span data-ttu-id="d80c1-152">创建或编辑用户</span><span class="sxs-lookup"><span data-stu-id="d80c1-152">Create or edit users</span></span>
- <span data-ttu-id="d80c1-153">向其他人分配管理员角色</span><span class="sxs-lookup"><span data-stu-id="d80c1-153">Assign admin roles to others</span></span>
- <span data-ttu-id="d80c1-154">重置用户密码</span><span class="sxs-lookup"><span data-stu-id="d80c1-154">Reset user passwords</span></span>
- <span data-ttu-id="d80c1-155">管理用户许可证</span><span class="sxs-lookup"><span data-stu-id="d80c1-155">Manage user licenses</span></span>
- <span data-ttu-id="d80c1-156">管理域</span><span class="sxs-lookup"><span data-stu-id="d80c1-156">Manage domains</span></span>
- <span data-ttu-id="d80c1-157">批准客户密码箱请求</span><span class="sxs-lookup"><span data-stu-id="d80c1-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="d80c1-158">建议每个组织至少配置两个管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="d80c1-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="d80c1-159">对于大型企业组织，我们建议专门的管理员帐户来提供不同的功能。</span><span class="sxs-lookup"><span data-stu-id="d80c1-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="d80c1-160">有关分配管理员角色和权限的信息，请参阅 [分配管理员角色](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles) 和 [关于管理员角色](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="d80c1-160">For information about assigning admin roles and permissions, see [Assign admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles) and [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).</span></span>

## <a name="related-links"></a><span data-ttu-id="d80c1-161">相关链接</span><span class="sxs-lookup"><span data-stu-id="d80c1-161">Related Links</span></span>

- [<span data-ttu-id="d80c1-162">隔离控件</span><span class="sxs-lookup"><span data-stu-id="d80c1-162">Isolation Controls</span></span>](microsoft-365-isolation-controls.md)
- [<span data-ttu-id="d80c1-163">人员控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-163">Personnel Controls</span></span>](microsoft-365-personnel-controls.md)
- [<span data-ttu-id="d80c1-164">技术控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-164">Technology Controls</span></span>](microsoft-365-technology-controls.md)
- [<span data-ttu-id="d80c1-165">监视和审核访问控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-165">Monitoring and Auditing Access Controls</span></span>](microsoft-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="d80c1-166">Yammer Enterprise 访问控制</span><span class="sxs-lookup"><span data-stu-id="d80c1-166">Yammer Enterprise Access Controls</span></span>](microsoft-365-yammer-enterprise-access-controls.md)
