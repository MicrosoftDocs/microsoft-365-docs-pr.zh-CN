---
title: Microsoft 365 多地理位置计划
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: 了解 Microsoft 365 多地理位置、多地理位置的工作原理，以及什么地理位置可用于数据存储。
ms.openlocfilehash: 52c4bc8a23bdf89afb1a3f3eae3fe6348fed8009
ms.sourcegitcommit: f7fbf45af64c5c0727fd5eaab309d20ad097a483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2021
ms.locfileid: "53362710"
---
# <a name="plan-for-microsoft-365-multi-geo"></a><span data-ttu-id="3c68c-103">Microsoft 365 多地理位置计划</span><span class="sxs-lookup"><span data-stu-id="3c68c-103">Plan for Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="3c68c-104">本指南面向跨国公司 (MNC) 的管理员，他们根据公司的经营情况，做好将 Microsoft 365 租户扩大到其他地理位置的准备，以满足数据驻留需求。</span><span class="sxs-lookup"><span data-stu-id="3c68c-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their Microsoft 365 tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="3c68c-105">在多地理位置配置中，Microsoft 365 租户由一个中心位置以及一个或多个附属位置组成。</span><span class="sxs-lookup"><span data-stu-id="3c68c-105">In a multi-geo configuration, your Microsoft 365 tenant consists of a central location and one or more satellite locations.</span></span> <span data-ttu-id="3c68c-106">这是一个跨多个地理位置的租户。</span><span class="sxs-lookup"><span data-stu-id="3c68c-106">This is a single tenant that spans across multiple geo locations.</span></span> <span data-ttu-id="3c68c-107">租户信息（包括地理位置）是在 Azure Active Directory (Azure AD) 中进行管控。</span><span class="sxs-lookup"><span data-stu-id="3c68c-107">Your tenant information, including geo locations, is mastered in Azure Active Directory (Azure AD).</span></span>

<span data-ttu-id="3c68c-108">下面是一些关键的多地理位置术语，有助于了解此配置的基本概念：</span><span class="sxs-lookup"><span data-stu-id="3c68c-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="3c68c-109">**租户** - 组织在 Microsoft 365 中的表示形式，通常有一个或多个关联域（例如，https://contoso.sharepoint.com)）。</span><span class="sxs-lookup"><span data-stu-id="3c68c-109">**Tenant** – An organization's representation in Microsoft 365 which typically has one or more domains associated with it (for example, https://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="3c68c-110">**地理位置** - Microsoft 365 租户中可用于托管数据的地理位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-110">**Geo locations** – The geographic locations available to host data in a Microsoft 365 tenant.</span></span>

-   <span data-ttu-id="3c68c-111">**附属位置** - Microsoft 365 租户中已配置用于托管数据的其他地理位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-111">**Satellite locations** – The additional geo locations that you have configured to host data in your Microsoft 365 tenant.</span></span> <span data-ttu-id="3c68c-112">多地理位置租户跨多个地理位置（例如，北美和欧洲）。</span><span class="sxs-lookup"><span data-stu-id="3c68c-112">Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="3c68c-113">**首选数据位置 (PDL)** - 存储各个用户的 Exchange 和 OneDrive 数据的地理位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-113">**Preferred Data Location (PDL)** – The geo location where an individual user's Exchange and OneDrive data is stored.</span></span> <span data-ttu-id="3c68c-114">这可以由管理员设置为已为租户配置的任何地理位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-114">This can be set by the administrator to any of the geo locations that have been configured for the tenant.</span></span> <span data-ttu-id="3c68c-115">请注意，如果你更改已有 OneDrive 网站的用户的 PDL，用户的 OneDrive 数据不会自动移到新地理位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-115">Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically.</span></span> <span data-ttu-id="3c68c-116">有关详细信息，请参阅[将 OneDrive 库移到其他地理位置](move-onedrive-between-geo-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="3c68c-116">See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span> <span data-ttu-id="3c68c-117">如果用户有 Exchange 邮箱，邮箱会自动移到新首选数据位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-117">If they have an Exchange mailbox, the mailbox is moved to the new preferred data location automatically.</span></span>

<span data-ttu-id="3c68c-118">启用多地理位置需要四个关键步骤：</span><span class="sxs-lookup"><span data-stu-id="3c68c-118">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="3c68c-119">与你的帐户团队协作，_在 Microsoft 365 服务计划中添加多地理位置功能_。</span><span class="sxs-lookup"><span data-stu-id="3c68c-119">Work with your account team to add the _Multi-Geo Capabilities in Microsoft 365_ service plan.</span></span>

2.  <span data-ttu-id="3c68c-120">选择需要的附属位置并将其添加到租户。</span><span class="sxs-lookup"><span data-stu-id="3c68c-120">Choose your desired satellite location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="3c68c-121">将用户的首选数据位置设置为所需的附属位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-121">Set your users' preferred data location to the desired satellite location.</span></span> <span data-ttu-id="3c68c-122">为用户预配的新 OneDrive 网站或 Exchange 邮箱会预配到用户的 PDL。</span><span class="sxs-lookup"><span data-stu-id="3c68c-122">When a new OneDrive site or Exchange mailbox is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="3c68c-123">根据需要，将用户的现有 OneDrive 网站从中心位置迁移到首选数据位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-123">Migrate your users' existing OneDrive sites from the central location to their preferred data location as needed.</span></span> <span data-ttu-id="3c68c-124">（Exchange 邮箱在你设置用户的 PDL 时自动迁移。）</span><span class="sxs-lookup"><span data-stu-id="3c68c-124">(Exchange mailboxes are migrated automatically when you set a user's PDL.)</span></span>

<span data-ttu-id="3c68c-125">若要详细了解如何执行每一步，请参阅[配置 Microsoft 365 多地理位置](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="3c68c-125">See [Configure Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c68c-126">请注意，Microsoft 365 多地理位置旨在满足数据驻留需求，而不是优化性能。</span><span class="sxs-lookup"><span data-stu-id="3c68c-126">Note that Microsoft 365 Multi-Geo is not designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="3c68c-127">若要了解 Microsoft 365 性能优化，请参阅 [Microsoft 365 的网络计划和性能调整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或与支持群组联系。</span><span class="sxs-lookup"><span data-stu-id="3c68c-127">For information about performance optimization for Microsoft 365, see [Network planning and performance tuning for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="3c68c-128">可以将下列任何地理位置配置为，可托管 OneDrive 和 SharePoint 网站以及 Exchange 邮箱的附属位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-128">You can configure any of the following locations to be satellite locations where you can host OneDrive and SharePoint sites, and Exchange mailboxes.</span></span> <span data-ttu-id="3c68c-129">计划使用多地理位置时，列出要添加到 Microsoft 365 租户的位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-129">As you plan for multi-geo, make a list of the locations that you want to add to your Microsoft 365 tenant.</span></span> <span data-ttu-id="3c68c-130">建议从一个或两个附属位置入手，然后根据需要逐渐扩大到更多地理位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-130">We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

<span data-ttu-id="3c68c-p108">配置多地理位置时，请考虑借此机会在迁移到 Microsoft 365 时合并本地基础结构。例如，如果你在新加坡和马来西亚有本地服务器场，则可以将它们合并到 APC 附属位置，前提是数据驻留要求允许你执行此操作。</span><span class="sxs-lookup"><span data-stu-id="3c68c-p108">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Microsoft 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="3c68c-133">最佳做法</span><span class="sxs-lookup"><span data-stu-id="3c68c-133">Best practices</span></span>

<span data-ttu-id="3c68c-134">建议在 Microsoft 365 中创建测试用户，以进行一些初始测试。</span><span class="sxs-lookup"><span data-stu-id="3c68c-134">We recommend that you create a test user in Microsoft 365 to do some initial testing.</span></span> <span data-ttu-id="3c68c-135">让生产用户上手使用 Microsoft 365 多地理位置前，你将使用此用户执行一些测试和验证步骤。</span><span class="sxs-lookup"><span data-stu-id="3c68c-135">We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into Microsoft 365 Multi-Geo.</span></span>

<span data-ttu-id="3c68c-136">使用测试用户完成测试后，选择一个试点组（可能来自 IT 部门），作为首个在新地理位置使用 OneDrive 和 Exchange 的组。</span><span class="sxs-lookup"><span data-stu-id="3c68c-136">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive and Exchange in a new geo location.</span></span> <span data-ttu-id="3c68c-137">对于此第一个组，选择尚未拥有 OneDrive 的用户。</span><span class="sxs-lookup"><span data-stu-id="3c68c-137">For this first group, select users who do not yet have a OneDrive.</span></span> <span data-ttu-id="3c68c-138">建议此初始组的用户数不超过五人，然后遵循批量推出方法逐渐扩大。</span><span class="sxs-lookup"><span data-stu-id="3c68c-138">We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="3c68c-p111">每个用户都应设置“*首选数据位置*”(PDL)，以便 Microsoft 365 可以确定在哪个地理位置预配 OneDrive。用户的首选数据位置必须与所选附属位置或中心位置相匹配。虽然 PDL 字段不是强制性的，但我们建议为所有用户设置一个 PDL。没有 PDL 的用户的工作负载将在中央位置进行预配。</span><span class="sxs-lookup"><span data-stu-id="3c68c-p111">Each user should have a *preferred data location* (PDL) set so that Microsoft 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.</span></span>

<span data-ttu-id="3c68c-p112">创建一个用户列表，并包含他们的用户主体名称 (UPN) 和相应首选数据位置的位置代码。首先包含你的测试用户和初始试点组。在配置过程中你将需要使用这个列表。</span><span class="sxs-lookup"><span data-stu-id="3c68c-p112">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.</span></span>

<span data-ttu-id="3c68c-146">如果用户是从本地 Active Directory 系统同步到 Azure Active Directory，你必须将首选数据位置设置为 Active Directory 属性，并使用 Azure Active Directory Connect 同步它。</span><span class="sxs-lookup"><span data-stu-id="3c68c-146">If your users are synchronized from an on-premises Active Directory system to Azure Active Directory, you must set the preferred data location as an Active Directory attribute and synchronize it by using Azure Active Directory Connect.</span></span> <span data-ttu-id="3c68c-147">无法使用 Azure AD PowerShell 直接为同步用户配置首选数据位置。</span><span class="sxs-lookup"><span data-stu-id="3c68c-147">You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell.</span></span> <span data-ttu-id="3c68c-148">[Azure Active Directory Connect 同步：配置 Microsoft 365 资源的首选数据位置](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)中介绍了在 Active Directory 中设置并同步 PDL 的步骤。</span><span class="sxs-lookup"><span data-stu-id="3c68c-148">The steps to set up PDL in Active Directory and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Microsoft 365 resources](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="3c68c-p114">多地理位置租户的管理可能与非多地理位置租户不同，因为许多 SharePoint 和 OneDrive 设置和服务都具有多地理位置意识。我们建议你在继续配置之前先查看[管理多地理位置环境](administering-a-multi-geo-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="3c68c-p114">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="3c68c-151">阅读 [多地理位置环境的用户体验，](multi-geo-user-experience.md) 详细了解最终用户在多地理位置环境中的体验。</span><span class="sxs-lookup"><span data-stu-id="3c68c-151">Read [User experience in a multi-geo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="3c68c-152">若要开始配置 Microsoft 365 多地理位置，请参阅[配置 Microsoft 365 多地理位置](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="3c68c-152">To get started configuring Microsoft 365 Multi-Geo, see [Configure Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="3c68c-153">完成配置后，记得根据需要[迁移用户的 OneDrive 库](move-onedrive-between-geo-locations.md)，以便让用户从首选数据位置工作。</span><span class="sxs-lookup"><span data-stu-id="3c68c-153">Once you've completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3c68c-154">相关主题</span><span class="sxs-lookup"><span data-stu-id="3c68c-154">Related topics</span></span>

[<span data-ttu-id="3c68c-155">Microsoft 365 多地理位置电子数据展示配置</span><span class="sxs-lookup"><span data-stu-id="3c68c-155">Microsoft 365 Multi-Geo eDiscovery configuration</span></span>](./multi-geo-ediscovery-configuration.md)