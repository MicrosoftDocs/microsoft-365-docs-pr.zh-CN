---
title: 适用于 Office 365 的 Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: 了解如何使用 Azure ExpressRoute 和 Office 365，并规划网络实现项目（如果要使用它进行部署）。
ms.openlocfilehash: 3691161767aba784039cbf317a51429c9ee6444c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687576"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="24d1a-103">适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="24d1a-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="24d1a-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="24d1a-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="24d1a-105">了解如何将 Azure ExpressRoute 与 Office 365 结合使用，以及如何规划在部署 Azure ExpressRoute 以用于 Office 365 时所需的网络实施项目。</span><span class="sxs-lookup"><span data-stu-id="24d1a-105">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365.</span></span> <span data-ttu-id="24d1a-106">在 Azure 中运行的基础结构和平台服务通常可解决网络体系结构和性能注意事项的好处。</span><span class="sxs-lookup"><span data-stu-id="24d1a-106">Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations.</span></span> <span data-ttu-id="24d1a-107">在这些情况下，我们建议为 Azure 提供 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="24d1a-107">We recommend ExpressRoute for Azure in these cases.</span></span> <span data-ttu-id="24d1a-108">作为服务产品（如 Office 365 和 Dynamics 365）构建为通过 Internet 安全可靠地访问。</span><span class="sxs-lookup"><span data-stu-id="24d1a-108">Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet.</span></span> <span data-ttu-id="24d1a-109">您可以阅读有关 Internet 性能和安全性的信息，以及在 [评估 office 365 网络连接](assessing-network-connectivity.md)的文章中，您可能会考虑 office 365 的 Azure ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="24d1a-109">You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Assessing Office 365 network connectivity](assessing-network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="24d1a-110">需要 Microsoft 授权才能使用适用于 Office 365 的 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="24d1a-110">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="24d1a-111">当客户的法规要求要求直接连接时，Microsoft 会检查每个客户请求并授权 ExpressRoute for Office 365 的使用情况。</span><span class="sxs-lookup"><span data-stu-id="24d1a-111">Microsoft reviews every customer request and authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="24d1a-112">如果您有这样的要求，请提供指向您所解释的法规的文本摘录和 web 链接，这意味着在从 [Office 365 请求的 ExpressRoute For Office 请求](https://aka.ms/O365ERReview) 中需要直接连接才能开始 Microsoft 评审。</span><span class="sxs-lookup"><span data-stu-id="24d1a-112">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="24d1a-113">尝试为 Office 365 创建路由筛选器的未授权订阅将收到一 [条错误消息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="24d1a-113">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>

<span data-ttu-id="24d1a-114">现在，您可以为选定的 Office 365 网络流量添加到 Office 365 的直接网络连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-114">You can now add a direct network connection to Office 365 for selected Office 365 network traffic.</span></span> <span data-ttu-id="24d1a-115">Azure ExpressRoute 提供了一个直接连接，可预测的性能，并附带了适用于 Microsoft 网络组件的99.95% 的正常运行时间 SLA。</span><span class="sxs-lookup"><span data-stu-id="24d1a-115">Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components.</span></span> <span data-ttu-id="24d1a-116">对于不受 Azure ExpressRoute 支持的服务，您仍需要 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-116">You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="24d1a-117">规划适用于 Office 365 的 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="24d1a-117">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="24d1a-118">除了 internet 连接之外，还可以选择通过直接连接（可预测性和 Microsoft 网络组件的99.95% 正常运行时间 SLA）将 Office 365 网络流量的子集路由。</span><span class="sxs-lookup"><span data-stu-id="24d1a-118">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components.</span></span> <span data-ttu-id="24d1a-119">Azure ExpressRoute 为你提供与 Office 365 和其他 Microsoft 云服务的专用网络连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-119">Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="24d1a-120">无论您是否具有现有 MPLS WAN，可以通过三种方式之一将 ExpressRoute 添加到网络体系结构中;通过受支持的云交换共同位置提供程序、以太网点到点连接提供程序或通过 MPLS 连接提供程序。</span><span class="sxs-lookup"><span data-stu-id="24d1a-120">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider.</span></span> <span data-ttu-id="24d1a-121">查看 [您的区域中提供了哪些提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。</span><span class="sxs-lookup"><span data-stu-id="24d1a-121">See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="24d1a-122">直接 ExpressRoute 连接将启用与在 [其中包含 Office 365 服务](azure-expressroute.md#BKMK_WhatDoIGet) 的应用程序的连接（如下所示）。</span><span class="sxs-lookup"><span data-stu-id="24d1a-122">The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below.</span></span> <span data-ttu-id="24d1a-123">所有其他应用程序和服务的网络流量将继续穿越 internet。</span><span class="sxs-lookup"><span data-stu-id="24d1a-123">Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="24d1a-124">请考虑以下高级网络图表，该图显示了通过 internet 连接到 Microsoft 数据中心的典型 Office 365 客户，可访问所有 Microsoft 应用程序，如 Office 365、Windows Update 和 TechNet。</span><span class="sxs-lookup"><span data-stu-id="24d1a-124">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet.</span></span> <span data-ttu-id="24d1a-125">客户使用类似的网络路径，无论是从本地网络还是独立的 internet 连接进行连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-125">Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 网络连接](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="24d1a-127">现在，查看已更新的图表，该图表描述了使用 internet 和 ExpressRoute 连接到 Office 365 的 Office 365 客户。</span><span class="sxs-lookup"><span data-stu-id="24d1a-127">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365.</span></span> <span data-ttu-id="24d1a-128">请注意，某些连接（如公用 DNS 和内容传递网络节点）仍需要公共 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-128">Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection.</span></span> <span data-ttu-id="24d1a-129">此外，还请注意，不位于其 ExpressRoute 连接建筑物中的客户用户通过 Internet 进行连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-129">Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![使用 ExpressRoute 的 Office 365 连接](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="24d1a-131">是否仍需要详细信息？</span><span class="sxs-lookup"><span data-stu-id="24d1a-131">Still want more information?</span></span> <span data-ttu-id="24d1a-132">了解如何 [使用 Azure expressroute For office 365 管理网络流量](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) ，并了解如何为 [Office 365 配置 azure expressroute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。</span><span class="sxs-lookup"><span data-stu-id="24d1a-132">Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).</span></span> <span data-ttu-id="24d1a-133">我们还在频道9上记录了10部分 [Azure ExpressRoute For Office 365 培训](https://channel9.msdn.com/series/aer) 系列，以帮助更全面地解释这些概念。</span><span class="sxs-lookup"><span data-stu-id="24d1a-133">We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="24d1a-134">包含什么 Office 365 服务？</span><span class="sxs-lookup"><span data-stu-id="24d1a-134">What Office 365 services are included?</span></span>
<span data-ttu-id="24d1a-135"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="24d1a-135"><a name="BKMK_WhatDoIGet"> </a></span></span>

<span data-ttu-id="24d1a-136">下表列出了通过 ExpressRoute 支持的 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="24d1a-136">The following table lists the Office 365 services that are supported over ExpressRoute.</span></span> <span data-ttu-id="24d1a-137">请查看 " [Office 365 终结点](https://aka.ms/o365endpoints) " 一文，了解对这些应用程序的哪些网络请求需要 internet 连接。</span><span class="sxs-lookup"><span data-stu-id="24d1a-137">Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="24d1a-138">**包含的应用程序**</span><span class="sxs-lookup"><span data-stu-id="24d1a-138">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="24d1a-139">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-139">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-140">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-140">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-141">Delve<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-141">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="24d1a-142">Skype for Business Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-142">Skype for Business Online<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-143">Microsoft 团队 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-143">Microsoft Teams <sup>1</sup></span></span> <br/> |
|<span data-ttu-id="24d1a-144">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-144">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-145">OneDrive for Business<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-145">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-146">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-146">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="24d1a-147">门户和共享<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-147">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-148">Azure Active Directory (Azure AD) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-148">Azure Active Directory (Azure AD) <sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-149">Azure AD Connect<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-149">Azure AD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="24d1a-150">Office<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="24d1a-150">Office<sup>1</sup></span></span> <br/> |

<span data-ttu-id="24d1a-151"><sup>1</sup> 这些应用程序中的每一个都具有不受 ExpressRoute 支持的 internet 连接要求，请参阅 [Office 365 终结点一文](https://aka.ms/o365endpoints) 以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="24d1a-151"><sup>1</sup> Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="24d1a-152">不包含在适用于 Office 365 的 ExpressRoute 中的服务是 Microsoft 365 应用程序，用于企业客户端下载、内部部署标识提供程序登录和 Office 365 (在中国的 21 Vianet) 服务。</span><span class="sxs-lookup"><span data-stu-id="24d1a-152">The services that aren't included with ExpressRoute for Office 365 are Microsoft 365 Apps for enterprise client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="24d1a-153">实现适用于 Office 365 的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="24d1a-153">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="24d1a-154">实施 ExpressRoute 需要参与网络和应用程序所有者，并需要仔细规划，以确定新的 [网络路由体系结构](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、实现安全的带宽要求、高可用性等。</span><span class="sxs-lookup"><span data-stu-id="24d1a-154">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on.</span></span> <span data-ttu-id="24d1a-155">若要实现 ExpressRoute，需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="24d1a-155">To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="24d1a-156">全面了解 Office 365 连接规划中的需要 ExpressRoute 满足。</span><span class="sxs-lookup"><span data-stu-id="24d1a-156">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning.</span></span> <span data-ttu-id="24d1a-157">了解哪些应用程序将使用 internet 或 ExpressRoute，并在使用 internet 和 ExpressRoute for Office 365 流量的上下文中全面规划网络容量、安全性和高可用性需求。</span><span class="sxs-lookup"><span data-stu-id="24d1a-157">Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="24d1a-158">确定 internet 和 ExpressRoute 流量<sup>1</sup>的出口和对等位置。</span><span class="sxs-lookup"><span data-stu-id="24d1a-158">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="24d1a-159">确定 internet 和 ExpressRoute 连接上所需的容量。</span><span class="sxs-lookup"><span data-stu-id="24d1a-159">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="24d1a-160">制定了实施安全性和其他标准外围控制<sup>1</sup>的计划。</span><span class="sxs-lookup"><span data-stu-id="24d1a-160">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="24d1a-161">具有有效的 Microsoft Azure 帐户以订阅 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="24d1a-161">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="24d1a-162">选择连接模型和 [已批准的提供程序](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。</span><span class="sxs-lookup"><span data-stu-id="24d1a-162">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="24d1a-163">请注意，客户可以选择多个连接模型或合作伙伴，而合作伙伴不需要与现有网络提供程序相同。</span><span class="sxs-lookup"><span data-stu-id="24d1a-163">Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="24d1a-164">先验证部署，然后再将流量定向到 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="24d1a-164">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="24d1a-165">（可选） [实施 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) 和评估区域扩展。</span><span class="sxs-lookup"><span data-stu-id="24d1a-165">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="24d1a-166"><sup>1</sup> 重要的性能注意事项。</span><span class="sxs-lookup"><span data-stu-id="24d1a-166"><sup>1</sup> Important performance considerations.</span></span> <span data-ttu-id="24d1a-167">此处的决策可能会大大影响对诸如 Skype for business 等应用程序至关重要的延迟。</span><span class="sxs-lookup"><span data-stu-id="24d1a-167">Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="24d1a-168">有关其他参考，除了[ExpressRoute 文档](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)之外，还应使用我们的[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)。</span><span class="sxs-lookup"><span data-stu-id="24d1a-168">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="24d1a-169">若要购买适用于 Office 365 的 ExpressRoute，您需要与一个或多个 [已批准的提供商](https://azure.microsoft.com/documentation/articles/expressroute-locations/) 合作，以使用 ExpressRoute Premium 订阅设置所需的数量和大小电路。</span><span class="sxs-lookup"><span data-stu-id="24d1a-169">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription.</span></span> <span data-ttu-id="24d1a-170">没有其他许可证可从 Office 365 购买。</span><span class="sxs-lookup"><span data-stu-id="24d1a-170">There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="24d1a-171">以下是可以用于返回的简短链接：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="24d1a-171">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="24d1a-172">准备好注册适用于 [Office 365 的 ExpressRoute](https://aka.ms/ert)吗？</span><span class="sxs-lookup"><span data-stu-id="24d1a-172">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

## <a name="related-topics"></a><span data-ttu-id="24d1a-173">相关主题</span><span class="sxs-lookup"><span data-stu-id="24d1a-173">Related Topics</span></span>

[<span data-ttu-id="24d1a-174">评估 Office 365 网络连接</span><span class="sxs-lookup"><span data-stu-id="24d1a-174">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="24d1a-175">管理 ExpressRoute for Office 365 连接</span><span class="sxs-lookup"><span data-stu-id="24d1a-175">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="24d1a-176">使用 ExpressRoute for Office 365 路由</span><span class="sxs-lookup"><span data-stu-id="24d1a-176">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="24d1a-177">ExpressRoute for Office 365 网络计划</span><span class="sxs-lookup"><span data-stu-id="24d1a-177">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="24d1a-178">实现 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="24d1a-178">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="24d1a-179">在 ExpressRoute for Office 365 方案中使用 BGP 社区</span><span class="sxs-lookup"><span data-stu-id="24d1a-179">Using BGP communities in ExpressRoute for Office 365 scenarios</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="24d1a-180">Skype for Business Online 中的媒体质量和网络连接性能</span><span class="sxs-lookup"><span data-stu-id="24d1a-180">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="24d1a-181">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="24d1a-181">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="24d1a-182">Office 365 性能疑难解答计划</span><span class="sxs-lookup"><span data-stu-id="24d1a-182">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="24d1a-183">Office 365 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="24d1a-183">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="24d1a-184">Office 365 网络和性能优化</span><span class="sxs-lookup"><span data-stu-id="24d1a-184">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

## <a name="see-also"></a><span data-ttu-id="24d1a-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24d1a-185">See also</span></span>

[<span data-ttu-id="24d1a-186">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="24d1a-186">Microsoft 365 Enterprise overview</span></span>](microsoft-365-overview.md)
