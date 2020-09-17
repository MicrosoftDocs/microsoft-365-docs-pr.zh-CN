---
title: Office 365 的网络和迁移规划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
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
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 本文包含有关网络规划、测试和迁移到 Office 365 的信息的链接。
ms.openlocfilehash: 2b08b05b8863fd9351510878f9438264bb2999f5
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "47948444"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="28711-103">Office 365 的网络和迁移规划</span><span class="sxs-lookup"><span data-stu-id="28711-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="28711-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="28711-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="28711-105">本文包含有关网络规划和测试以及迁移到 Office 365 的信息的链接。</span><span class="sxs-lookup"><span data-stu-id="28711-105">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="28711-106">在首次部署或迁移到 Office 365 之前，您可以使用这些主题中的信息来估计所需的带宽，然后测试并验证是否有足够的带宽来部署或迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="28711-106">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

<span data-ttu-id="28711-107">本文是 [Office 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="28711-107">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>

<span data-ttu-id="28711-108">有关为 Microsoft 365 和其他 Microsoft 云平台和服务优化网络的步骤，请参阅适用于 [企业架构师的 Microsoft 云网络](https://aka.ms/cloudarchnetworking) 海报。</span><span class="sxs-lookup"><span data-stu-id="28711-108">For the steps to optimize your network for Microsoft 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span>
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="28711-109">估计网络带宽要求</span><span class="sxs-lookup"><span data-stu-id="28711-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="28711-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="28711-110"><a name="EstimateBandwidthRequirements"> </a></span></span>

<span data-ttu-id="28711-111">使用 Office 365 可能会提高组织的 internet 电路的利用率。</span><span class="sxs-lookup"><span data-stu-id="28711-111">Using Office 365 may increase the utilization of your organization's internet circuit.</span></span> <span data-ttu-id="28711-112">务必要确定当前可用的带宽量是否足以处理在完全部署 Office 365 时的估计增加，同时留下至少20% 的容量来处理最空闲的天数。</span><span class="sxs-lookup"><span data-stu-id="28711-112">It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="28711-113">若要估计带宽，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="28711-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="28711-114">评估将使用每个 Internet 出口的客户端数量。</span><span class="sxs-lookup"><span data-stu-id="28711-114">Assess the number of clients that will use each Internet egress.</span></span> <span data-ttu-id="28711-115">让我们的多 terabit 网络能够处理尽可能多的连接。</span><span class="sxs-lookup"><span data-stu-id="28711-115">Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="28711-116">确定哪些 Office 365 服务和功能将可供客户端使用。</span><span class="sxs-lookup"><span data-stu-id="28711-116">Determine which Office 365 services and features will be available for clients to use.</span></span> <span data-ttu-id="28711-117">您可能拥有不同的服务或使用情况配置文件的用户组。</span><span class="sxs-lookup"><span data-stu-id="28711-117">You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="28711-118">测量客户端的引导组的网络使用情况。</span><span class="sxs-lookup"><span data-stu-id="28711-118">Measure the network use for a pilot group of clients.</span></span> <span data-ttu-id="28711-119">确保试点客户端代表组织中的人员的不同配置文件以及不同的地理位置。</span><span class="sxs-lookup"><span data-stu-id="28711-119">Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations.</span></span> <span data-ttu-id="28711-120">您可以针对 [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) 和 [Microsoft 团队](https://docs.microsoft.com/microsoftteams/prepare-network) 的旧计算器或我们在自己的网络上执行的 [案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) ，对结果进行交叉检查。</span><span class="sxs-lookup"><span data-stu-id="28711-120">You can cross-check your results against our old calculators for [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) and [Microsoft Teams](https://docs.microsoft.com/microsoftteams/prepare-network) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="28711-121">使用试点组中的度量来推断整个组织的需求，并在对网络进行任何更改之前，重新测试以验证评估。</span><span class="sxs-lookup"><span data-stu-id="28711-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="28711-122">测试现有网络</span><span class="sxs-lookup"><span data-stu-id="28711-122">Test your existing network</span></span>
<span data-ttu-id="28711-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="28711-123"><a name="calculators"> </a></span></span>

 <span data-ttu-id="28711-124">**网络工具。**</span><span class="sxs-lookup"><span data-stu-id="28711-124">**Network tools.**</span></span> <span data-ttu-id="28711-125">测试和验证你的 Internet 带宽，以确定下载、上传和延迟限制。</span><span class="sxs-lookup"><span data-stu-id="28711-125">Test and validate your Internet bandwidth to determine download, upload, and latency constraints.</span></span> <span data-ttu-id="28711-126">这些工具将帮助您确定用于迁移的网络功能以及在完全部署之后的功能。</span><span class="sxs-lookup"><span data-stu-id="28711-126">These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
    
- <span data-ttu-id="28711-127">[Microsoft 远程连接分析器](https://go.microsoft.com/fwlink/p/?LinkId=517243)：测试 Exchange Online 环境中的连接性。</span><span class="sxs-lookup"><span data-stu-id="28711-127">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="28711-128">使用 [适用于 Office 365 的 Microsoft 支持和恢复助理](https://diagnostics.office.com/#/Download?env=SOC) 解决 Outlook 和 Office 365 问题。</span><span class="sxs-lookup"><span data-stu-id="28711-128">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="28711-129">针对 Office 365 的网络规划和提高迁移性能的最佳做法</span><span class="sxs-lookup"><span data-stu-id="28711-129">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="28711-130"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="28711-130"><a name="BestPractices"> </a></span></span>

<span data-ttu-id="28711-131">深入了解这些最佳做法，以了解有关改进 Office 365 体验的详细信息。</span><span class="sxs-lookup"><span data-stu-id="28711-131">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="28711-132">想要立即开始帮助你的用户吗？</span><span class="sxs-lookup"><span data-stu-id="28711-132">Want to get started helping your users right away?</span></span> <span data-ttu-id="28711-133">有关在 [慢速网络上使用 office 365 的最佳实践](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) ，请参阅在网络不合作时使用 office 365 的提示（包括 SharePoint Online、Exchange Online 和 Lync online）。</span><span class="sxs-lookup"><span data-stu-id="28711-133">See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating.</span></span> <span data-ttu-id="28711-134">本文链接到 TechNet 和 Support.office.com 上的内容加载以优化 Office 365 体验，其中包括有关自定义网页的简单方法以及如何设置 Internet Explorer 设置以实现最佳 Office 365 体验的信息。</span><span class="sxs-lookup"><span data-stu-id="28711-134">This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="28711-135">阅读 [office 365 网络连接原则](https://aka.ms/o365networkingprinciples) ，了解用于安全管理 Office 365 流量和获得最佳性能的连接原则。</span><span class="sxs-lookup"><span data-stu-id="28711-135">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="28711-136">本文将帮助你了解有关安全优化 Office 365 网络连接的最新指南。</span><span class="sxs-lookup"><span data-stu-id="28711-136">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="28711-137">通过仔细管理 Windows 更新的日程安排，提高邮件迁移性能。</span><span class="sxs-lookup"><span data-stu-id="28711-137">Improve mail migration performance by carefully managing the schedule for Windows Updates.</span></span> <span data-ttu-id="28711-138">您可以成批更新客户端计算机，并确保在迁移到 Office 365 之前更新所有客户端计算机，以控制网络带宽的使用。</span><span class="sxs-lookup"><span data-stu-id="28711-138">You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth.</span></span> <span data-ttu-id="28711-139">有关详细信息，请参阅为 [Office 365 手动更新和配置桌面，以获取最新更新](https://support.microsoft.com/gp/office-2013-365-update)。</span><span class="sxs-lookup"><span data-stu-id="28711-139">For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="28711-140">Office 365 网络流量在被视为受信任的 Internet 服务时执行得最佳，并允许绕过大部分传统筛选和扫描，以避免某些组织将网络流量置于不受信任的 Internet 服务中。</span><span class="sxs-lookup"><span data-stu-id="28711-140">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services.</span></span> <span data-ttu-id="28711-141">这通常包括删除出站处理（如代理用户身份验证和数据包检查），并确保使用正确的网络地址转换在 Internet 上进行本地传出 (NAT) 和足够的带宽容量来处理增加的网络请求。</span><span class="sxs-lookup"><span data-stu-id="28711-141">This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests.</span></span> <span data-ttu-id="28711-142">有关配置网络以将 Office 365 作为受信任的 Internet 服务在网络上进行处理的其他指导，请参阅 [管理 office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="28711-142">Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="28711-143">确保 [管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。</span><span class="sxs-lookup"><span data-stu-id="28711-143">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span> <span data-ttu-id="28711-144">转到 Office 365 的其他流量会导致出站代理连接的增加以及通过 TLS/SSL 的安全通信的增长。</span><span class="sxs-lookup"><span data-stu-id="28711-144">The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="28711-145">如果出站代理要求用户身份验证，则可能会遇到连接速度慢或功能丢失的情况。</span><span class="sxs-lookup"><span data-stu-id="28711-145">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality.</span></span> <span data-ttu-id="28711-146">绕过 Office 365 域的身份验证要求可以降低此开销。</span><span class="sxs-lookup"><span data-stu-id="28711-146">Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="28711-147">如果有大量共享日历和邮箱，您可能会看到从 Outlook 到 Exchange 的连接数增加。</span><span class="sxs-lookup"><span data-stu-id="28711-147">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange.</span></span> <span data-ttu-id="28711-148">例如，对于使用的每个共享日历，Outlook 客户端可能会打开多达两个附加连接。</span><span class="sxs-lookup"><span data-stu-id="28711-148">For instance, the Outlook client may open up to two additional connections for each shared calendar in use.</span></span> <span data-ttu-id="28711-149">在这种情况下，请确保出站代理可以处理连接，或者绕过代理连接到适用于 Office 365 for Outlook 的连接。</span><span class="sxs-lookup"><span data-stu-id="28711-149">In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="28711-150">确定公共 IP 地址支持的最大设备数以及如何在多个 IP 地址之间实现负载平衡。</span><span class="sxs-lookup"><span data-stu-id="28711-150">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses.</span></span> <span data-ttu-id="28711-151">有关详细信息，请参阅[与 Office 365 的 NAT 支持](nat-support-with-microsoft-365.md)。</span><span class="sxs-lookup"><span data-stu-id="28711-151">For more information, see [NAT support with Office 365](nat-support-with-microsoft-365.md).</span></span>
    
5. <span data-ttu-id="28711-152">如果要检查来自网络上的计算机的出站连接，则绕过对 Office 365 域的此筛选可提高连接性和性能。</span><span class="sxs-lookup"><span data-stu-id="28711-152">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance.</span></span> <span data-ttu-id="28711-153">此外，绕过出站检查通常无需进行单个 Internet 出口，并为 Office 365 发来的网络请求启用本地 Internet 出口。</span><span class="sxs-lookup"><span data-stu-id="28711-153">Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="28711-154">某些客户发现内部网络设置可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="28711-154">Some customers find internal network settings may affect performance.</span></span> <span data-ttu-id="28711-155">如最大传输单位 (MTU) 大小、网络自动协商或自动检测以及到 Internet 的子最佳路由等设置是常见的外观。</span><span class="sxs-lookup"><span data-stu-id="28711-155">Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="28711-156">Office 365 的网络规划参考</span><span class="sxs-lookup"><span data-stu-id="28711-156">Network planning reference for Office 365</span></span>
<span data-ttu-id="28711-157"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="28711-157"><a name="NetReference"> </a></span></span>

<span data-ttu-id="28711-158">这些主题包含详细的 Office 365 网络参考信息。</span><span class="sxs-lookup"><span data-stu-id="28711-158">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="28711-159">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="28711-159">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="28711-160">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="28711-160">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="28711-161">Office 365 的外部域名系统记录</span><span class="sxs-lookup"><span data-stu-id="28711-161">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="28711-162">Office 365 服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="28711-162">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="28711-163">Office 365 网络连接原则</span><span class="sxs-lookup"><span data-stu-id="28711-163">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="28711-164">Office 365 视频网络常见问题 (FAQ) </span><span class="sxs-lookup"><span data-stu-id="28711-164">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="28711-165">有关连接到 Office 365 服务的网络设备的计划</span><span class="sxs-lookup"><span data-stu-id="28711-165">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="28711-166">Office 365 服务的安装指南</span><span class="sxs-lookup"><span data-stu-id="28711-166">Setup guides for Office 365 services</span></span>](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a><span data-ttu-id="28711-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28711-167">See also</span></span>

[<span data-ttu-id="28711-168">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="28711-168">Microsoft 365 Enterprise overview</span></span>](microsoft-365-overview.md)
