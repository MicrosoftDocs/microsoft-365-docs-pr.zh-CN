---
title: 有关连接到 Office 365 服务的网络设备的计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 摘要：介绍用于连接到 Office 365 的网络容量、WAN 加速器和负载平衡设备的注意事项。
ms.openlocfilehash: e1209c13eb24d11a2cc9692957bc4ee5f6310f41
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927496"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="28430-103">有关连接到 Office 365 服务的网络设备的计划</span><span class="sxs-lookup"><span data-stu-id="28430-103">Plan for network devices that connect to Office 365 services</span></span>

<span data-ttu-id="28430-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="28430-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>
  
<span data-ttu-id="28430-105">某些网络硬件可能限制支持的并发会话数。</span><span class="sxs-lookup"><span data-stu-id="28430-105">Some network hardware may have limitations on the number of concurrent sessions that are supported.</span></span> <span data-ttu-id="28430-106">对于拥有 2，000 多个用户的组织，我们建议他们监视其网络设备，以确保他们能够处理额外的 Office 365 服务流量。</span><span class="sxs-lookup"><span data-stu-id="28430-106">For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic.</span></span> <span data-ttu-id="28430-107">SNMP (简单网络管理) 可帮助您实现此目标。</span><span class="sxs-lookup"><span data-stu-id="28430-107">Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

<span data-ttu-id="28430-108">本文是 Office [365 的网络规划和性能调整的一部分](./network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="28430-108">This article is part of [Network planning and performance tuning for Office 365](./network-planning-and-performance.md).</span></span>

<span data-ttu-id="28430-109">本地传出 Internet 代理设置还会影响客户端应用程序的 Office 365 服务连接。</span><span class="sxs-lookup"><span data-stu-id="28430-109">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications.</span></span> <span data-ttu-id="28430-110">还必须配置网络代理设备，以允许连接 Microsoft 云服务 URL 和应用程序。</span><span class="sxs-lookup"><span data-stu-id="28430-110">You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications.</span></span> <span data-ttu-id="28430-111">每个组织各不相同。</span><span class="sxs-lookup"><span data-stu-id="28430-111">Every organization is different.</span></span> <span data-ttu-id="28430-112">若要了解 Microsoft 如何管理此过程以及我们预配的带宽量， [请阅读案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="28430-112">To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="28430-113">以下 Skype for Business 帮助文章包含有关 Skype for Business 设置详细信息：</span><span class="sxs-lookup"><span data-stu-id="28430-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="28430-114">解决管理员的 Skype for Business Online 登录错误</span><span class="sxs-lookup"><span data-stu-id="28430-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="28430-115">无法连接到 Skype for Business，或某些功能不起作用，因为本地防火墙会阻止连接</span><span class="sxs-lookup"><span data-stu-id="28430-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="28430-116">虽然其中许多设置是特定于 Skype for Business 的，但有关网络配置的一般指南对于所有 Office 365 服务很有用。</span><span class="sxs-lookup"><span data-stu-id="28430-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="28430-117">确定网络容量</span><span class="sxs-lookup"><span data-stu-id="28430-117">Determining Network Capacity</span></span>

<span data-ttu-id="28430-118">连接上存在的每个网络设备都有其容量限制。</span><span class="sxs-lookup"><span data-stu-id="28430-118">Every network device that exists on a connection has its capacity limit.</span></span> <span data-ttu-id="28430-119">这些设备包括相互连接的客户端和服务器网络适配器、路由器、交换机和集线器。</span><span class="sxs-lookup"><span data-stu-id="28430-119">These devices include the client and server network adapters, routers, switches, and hubs that interconnect them.</span></span> <span data-ttu-id="28430-120">足够的网络容量意味着它们都不是饱和的。</span><span class="sxs-lookup"><span data-stu-id="28430-120">Adequate network capacity means that none of them are saturated.</span></span> <span data-ttu-id="28430-121">监视网络活动对于帮助确保所有网络设备的实际负载都小于其最大容量至关重要。</span><span class="sxs-lookup"><span data-stu-id="28430-121">Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity.</span></span> <span data-ttu-id="28430-122">网络容量影响代理设备性能。</span><span class="sxs-lookup"><span data-stu-id="28430-122">Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="28430-123">在大多数情况下，Internet 连接带宽会设置流量限制。</span><span class="sxs-lookup"><span data-stu-id="28430-123">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic.</span></span> <span data-ttu-id="28430-124">高峰流量时段性能较弱可能是由于过度使用 Internet 链接所致。</span><span class="sxs-lookup"><span data-stu-id="28430-124">Weak performance during peak traffic hours is probably caused by excessive use of the Internet link.</span></span> <span data-ttu-id="28430-125">这种情况还适用于分支机构方案，其中分支机构代理服务器计算机通过慢速广域网 (WAN) 链接连接到分支机构总部的代理设备。</span><span class="sxs-lookup"><span data-stu-id="28430-125">This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="28430-126">若要测试网络容量，请监视代理网络接口上的网络活动。</span><span class="sxs-lookup"><span data-stu-id="28430-126">To test network capacity, monitor the network activity on the proxy network interface.</span></span> <span data-ttu-id="28430-127">如果超过任何网络接口最大带宽的 75%，请考虑增加不足的网络基础结构的带宽。</span><span class="sxs-lookup"><span data-stu-id="28430-127">If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate.</span></span> <span data-ttu-id="28430-128">或者，请考虑使用高级功能，如 HTTP 压缩。</span><span class="sxs-lookup"><span data-stu-id="28430-128">Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="28430-129">WAN 加速器</span><span class="sxs-lookup"><span data-stu-id="28430-129">WAN Accelerators</span></span>

<span data-ttu-id="28430-130">如果你的组织使用广域网 (WAN) 加速代理设备，你在访问 Office 365 服务时可能会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="28430-130">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services.</span></span> <span data-ttu-id="28430-131">你可能需要优化你的网络设备，以确保用户在访问 Office 365 时拥有一致的体验。</span><span class="sxs-lookup"><span data-stu-id="28430-131">You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365.</span></span> <span data-ttu-id="28430-132">例如，Office 365 服务对一些 Office 365 内容和 TCP 标头进行加密。</span><span class="sxs-lookup"><span data-stu-id="28430-132">For example, Office 365 services encrypt some Office 365 content and the TCP header.</span></span> <span data-ttu-id="28430-133">你的设备可能无法处理此类流量。</span><span class="sxs-lookup"><span data-stu-id="28430-133">Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="28430-134">阅读有关将 WAN 优化 [控制器或流量/检查设备与 Office 365](https://support.microsoft.com/kb/2690045)一同使用的支持声明。</span><span class="sxs-lookup"><span data-stu-id="28430-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="28430-135">硬件和软件负载平衡设备</span><span class="sxs-lookup"><span data-stu-id="28430-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="28430-136">组织需要使用硬件负载平衡器 (HLB) 或网络负载平衡 (NLB) 解决方案将请求分发到 Active Directory 联合身份验证服务 (AD FS) 服务器和/或 Exchange 混合服务器。</span><span class="sxs-lookup"><span data-stu-id="28430-136">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers.</span></span> <span data-ttu-id="28430-137">负载平衡设备控制到内部部署服务器的网络流量。</span><span class="sxs-lookup"><span data-stu-id="28430-137">Load-balancing devices control the network traffic to the on-premises servers.</span></span> <span data-ttu-id="28430-138">这些服务器对于确保单一登录和 Exchange 混合部署的可用性至关重要。</span><span class="sxs-lookup"><span data-stu-id="28430-138">These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="28430-139">我们提供内置于 Windows Server 中的基于软件的 NLB 解决方案。</span><span class="sxs-lookup"><span data-stu-id="28430-139">We provide a software-based NLB solution built into Windows Server.</span></span> <span data-ttu-id="28430-140">Office 365 支持此解决方案以实现负载平衡。</span><span class="sxs-lookup"><span data-stu-id="28430-140">Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="28430-141">防火墙和代理</span><span class="sxs-lookup"><span data-stu-id="28430-141">Firewalls and proxies</span></span>

<span data-ttu-id="28430-142">有关配置防火墙和代理以连接到 Office 365 的更多详细信息，请参阅管理 [Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)终结点、评估 [Office 365](assessing-network-connectivity.md)网络连接和 [Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) 终结点常见问题解答，了解有关设备和电路选择的详细信息。</span><span class="sxs-lookup"><span data-stu-id="28430-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Assessing Office 365 network connectivity](assessing-network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="28430-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28430-143">See also</span></span>

[<span data-ttu-id="28430-144">Office 365 服务的设置指南</span><span class="sxs-lookup"><span data-stu-id="28430-144">Setup guides for Office 365 services</span></span>](setup-guides-for-microsoft-365.md)

[<span data-ttu-id="28430-145">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="28430-145">Microsoft 365 Enterprise overview</span></span>](microsoft-365-overview.md)