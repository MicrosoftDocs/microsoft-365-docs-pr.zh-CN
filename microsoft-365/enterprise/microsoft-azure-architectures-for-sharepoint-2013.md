---
title: SharePoint 2013 的 Microsoft Azure 体系结构
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
- seo-marvel-apr2020
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 了解哪些类型的 SharePoint 2013 解决方案可以托管在 Microsoft Azure 虚拟机中，以及如何将 Azure 设置为托管一个。
ms.openlocfilehash: eed74e2dcbe383f0f63e7f6ea2fc70fe7b51b1b3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50924172"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="33f26-103">SharePoint 2013 的 Microsoft Azure 体系结构</span><span class="sxs-lookup"><span data-stu-id="33f26-103">Microsoft Azure Architectures for SharePoint 2013</span></span>

<span data-ttu-id="33f26-104">Azure 是用于托管 SharePoint Server 2013 解决方案的绝佳环境。</span><span class="sxs-lookup"><span data-stu-id="33f26-104">Azure is a good environment for hosting a SharePoint Server 2013 solution.</span></span> <span data-ttu-id="33f26-105">在大多数情况下，我们建议使用 Microsoft 365，但托管在 Azure 中的 SharePoint Server 场可能是特定解决方案的良好选择。</span><span class="sxs-lookup"><span data-stu-id="33f26-105">In most cases, we recommend Microsoft 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions.</span></span> <span data-ttu-id="33f26-106">本文介绍如何构建 SharePoint 解决方案，使它们适合 Azure 平台。</span><span class="sxs-lookup"><span data-stu-id="33f26-106">This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform.</span></span> <span data-ttu-id="33f26-107">我们将以下面两个特定解决方案为例进行说明：</span><span class="sxs-lookup"><span data-stu-id="33f26-107">The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="33f26-108">Microsoft Azure 中的 SharePoint Server 2013 灾难恢复</span><span class="sxs-lookup"><span data-stu-id="33f26-108">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="33f26-109">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="33f26-109">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="33f26-110">用于 Azure 基础结构服务的建议 SharePoint 解决方案</span><span class="sxs-lookup"><span data-stu-id="33f26-110">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="33f26-p102">Azure 基础结构服务是用于托管 SharePoint 解决方案的极具吸引力的选项。某些解决方案比其他解决方案更适合此平台。下表显示了建议的解决方案。</span><span class="sxs-lookup"><span data-stu-id="33f26-p102">Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="33f26-114">**解决方案**</span><span class="sxs-lookup"><span data-stu-id="33f26-114">**Solution**</span></span>|<span data-ttu-id="33f26-115">**为何建议将此解决方案用于 Azure**</span><span class="sxs-lookup"><span data-stu-id="33f26-115">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33f26-116">开发和测试环境</span><span class="sxs-lookup"><span data-stu-id="33f26-116">Development and test environments</span></span>  <br/> |<span data-ttu-id="33f26-117">创建和管理这些环境非常容易。</span><span class="sxs-lookup"><span data-stu-id="33f26-117">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="33f26-118">将内部部署 SharePoint 服务器场灾难恢复到 Azure</span><span class="sxs-lookup"><span data-stu-id="33f26-118">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="33f26-119">**承载的辅助数据中心** 使用 Azure，而不是在其他地区投资建设辅助数据中心。</span><span class="sxs-lookup"><span data-stu-id="33f26-119">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="33f26-p103">**低成本灾难恢复环境** 维护和支付比内部部署灾难恢复环境更少的资源。资源数量取决于您选择的灾难恢复环境：冷备用、温备用或热备用。</span><span class="sxs-lookup"><span data-stu-id="33f26-p103">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. </span></span><br/> <span data-ttu-id="33f26-p104">**更有弹性的平台** 如果发生灾难，轻松扩展恢复 SharePoint 服务器场以满足负载要求。当您不再需要这些资源时，进行缩放。</span><span class="sxs-lookup"><span data-stu-id="33f26-p104">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. </span></span><br/> <span data-ttu-id="33f26-124">请参阅[Microsoft Azure 中的 SharePoint Server 2013 灾难恢复](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="33f26-124">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="33f26-125">使用 Microsoft 365 中不可用的功能和规模的面向 Internet 的网站</span><span class="sxs-lookup"><span data-stu-id="33f26-125">Internet-facing sites that use features and scale not available in Microsoft 365</span></span>  <br/> |<span data-ttu-id="33f26-126">**集中精力** 构建一个很棒的网站，而不是构建基础结构。</span><span class="sxs-lookup"><span data-stu-id="33f26-126">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="33f26-p105">**利用 Azure 中的弹性** 根据需要通过添加新服务器调整服务器场大小，仅支付您需要的资源。不支持动态计算机分配（自动缩放）。</span><span class="sxs-lookup"><span data-stu-id="33f26-p105">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). </span></span><br/> <span data-ttu-id="33f26-129">**使用 Azure Active Directory (AD)** 利用客户帐户的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="33f26-129">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="33f26-130">**添加 Microsoft 365 中不可用的 SharePoint 功能** 添加深度报告和 Web 分析。</span><span class="sxs-lookup"><span data-stu-id="33f26-130">**Add SharePoint functionality not available in Microsoft 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="33f26-131">请参阅[Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)。</span><span class="sxs-lookup"><span data-stu-id="33f26-131">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="33f26-132">支持 Microsoft 365 或本地环境的应用场</span><span class="sxs-lookup"><span data-stu-id="33f26-132">App farms to support Microsoft 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="33f26-133">在 Azure 中构建、测试和承载应用程序，以支持内部部署和云环境。</span><span class="sxs-lookup"><span data-stu-id="33f26-133">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="33f26-134">在 Azure 中承载此角色，而无需为内部部署环境购买新硬件。</span><span class="sxs-lookup"><span data-stu-id="33f26-134">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="33f26-135">对于 Intranet 以及协作解决方案和工作负载，请考虑下列选项：</span><span class="sxs-lookup"><span data-stu-id="33f26-135">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="33f26-136">确定 Microsoft 365 是否满足你的业务需求，或者是否属于解决方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="33f26-136">Determine if Microsoft 365 meets your business requirements or can be part of the solution.</span></span> <span data-ttu-id="33f26-137">Microsoft 365 提供始终保持最新的丰富功能集。</span><span class="sxs-lookup"><span data-stu-id="33f26-137">Microsoft 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="33f26-138">如果 Microsoft 365 不满足您的所有业务要求，请考虑 Microsoft 咨询服务和 MCS (SharePoint 2013) 。</span><span class="sxs-lookup"><span data-stu-id="33f26-138">If Microsoft 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS).</span></span> <span data-ttu-id="33f26-139">相比自定义体系结构而言，标准体系结构的支持更快速、便宜和简单。</span><span class="sxs-lookup"><span data-stu-id="33f26-139">A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="33f26-140">如果标准实现不满足您的业务需求，请考虑使用自定义的内部部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="33f26-140">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="33f26-p108">如果使用云平台对于满足您的业务需求非常重要，请考虑托管在 Azure 中的 SharePoint 2013 的标准或自定义实现。相比其他非纯 Microsoft 公共云平台而言，在 Azure 中支持 SharePoint 解决方案要容易得多。</span><span class="sxs-lookup"><span data-stu-id="33f26-p108">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="33f26-143">设计 Azure 环境之前</span><span class="sxs-lookup"><span data-stu-id="33f26-143">Before you design the Azure environment</span></span>

<span data-ttu-id="33f26-p109">本文以 SharePoint 拓扑为例，您可以将这些设计理念用于任何 SharePoint 服务器场拓扑。在设计 Azure 环境之前，请使用以下拓扑、体系结构、容量和性能指导设计 SharePoint 服务器场：</span><span class="sxs-lookup"><span data-stu-id="33f26-p109">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="33f26-146">面向 SharePoint 2013 IT 专业人员的体系结构设计</span><span class="sxs-lookup"><span data-stu-id="33f26-146">Architecture design for SharePoint 2013 IT pros</span></span>](/SharePoint/technical-reference/technical-diagrams)
    
- [<span data-ttu-id="33f26-147">Plan for performance and capacity management in SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="33f26-147">Plan for performance and capacity management in SharePoint Server 2013</span></span>](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="33f26-148">确定 Active Directory 域类型</span><span class="sxs-lookup"><span data-stu-id="33f26-148">Determine the Active Directory domain type</span></span>

<span data-ttu-id="33f26-p110">每个 SharePoint 服务器场依赖于 Active Directory 来提供用于服务器场设置的管理帐户。目前，Azure 中提供 SharePoint 解决方案的两个选项。将在下表中介绍详细信息。</span><span class="sxs-lookup"><span data-stu-id="33f26-p110">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.</span></span>
  
|<span data-ttu-id="33f26-152">**选项**</span><span class="sxs-lookup"><span data-stu-id="33f26-152">**Option**</span></span>|<span data-ttu-id="33f26-153">**说明**</span><span class="sxs-lookup"><span data-stu-id="33f26-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33f26-154">专用域</span><span class="sxs-lookup"><span data-stu-id="33f26-154">Dedicated domain</span></span>  <br/> |<span data-ttu-id="33f26-p111">您可以在 Azure 中部署一个隔离的专用 Active Directory 域以支持您的 SharePoint 服务器场。这是面向公众的 Internet 站点的最佳选择。</span><span class="sxs-lookup"><span data-stu-id="33f26-p111">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="33f26-157">通过跨界连接扩展本地域</span><span class="sxs-lookup"><span data-stu-id="33f26-157">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="33f26-p112">当您通过跨界连接扩展本地域时，用户通过您的 Intranet 访问 SharePoint 服务器场，就像它托管在本地一样。您可以利用您的本地 Active Directory 和 DNS 实现。</span><span class="sxs-lookup"><span data-stu-id="33f26-p112">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="33f26-160">在 Azure 中构建灾难恢复环境以便从本地服务器场进行故障转移时，将需要跨界连接。</span><span class="sxs-lookup"><span data-stu-id="33f26-160">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="33f26-p113">本文介绍通过跨界连接扩展本地域的设计理念。如果您的解决方案使用专用域，则不需要跨界连接。</span><span class="sxs-lookup"><span data-stu-id="33f26-p113">This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="33f26-163">设计虚拟网络</span><span class="sxs-lookup"><span data-stu-id="33f26-163">Design the virtual network</span></span>

<span data-ttu-id="33f26-p114">首先，您在 Azure 中需要有一个虚拟网络，其中包括您将用于放置虚拟机的子网。虚拟网络需要专用 IP 地址空间，其中的某些部分将分配给子网。</span><span class="sxs-lookup"><span data-stu-id="33f26-p114">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="33f26-166">如果要通过（灾难恢复环境所必需的）跨域连接将本地网络扩展到 Azure，则必须选择一个未在组织网络中的任何位置使用的专用地址空间，其中可以包括您的本地环境和其他 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="33f26-166">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="33f26-167">**图 1：本地环境和 Azure 中的虚拟网络。**</span><span class="sxs-lookup"><span data-stu-id="33f26-167">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![SharePoint 解决方案的 Microsoft Azure 虚拟网络设计。Azure 网关的一个子网。虚拟机的一个子网。](../media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="33f26-171">在此图中：</span><span class="sxs-lookup"><span data-stu-id="33f26-171">In this diagram:</span></span>
  
- <span data-ttu-id="33f26-p116">Azure 中的虚拟网络与本地环境并列。两个环境尚未通过跨界连接（可以是站点到站点 VPN 连接，也可以是 ExpressRoute）进行连接。</span><span class="sxs-lookup"><span data-stu-id="33f26-p116">A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="33f26-p117">在这种情况下，虚拟网络仅包括子网，不包括任何其他体系结构元素。一个子网将托管 Azure 网关，其他的子网将托管 SharePoint 场层，还有另外一个子网将托管 Active Directory 和 DNS。</span><span class="sxs-lookup"><span data-stu-id="33f26-p117">At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="33f26-176">添加跨界连接</span><span class="sxs-lookup"><span data-stu-id="33f26-176">Add cross-premises connectivity</span></span>

<span data-ttu-id="33f26-p118">下一个部署步骤将创建跨界连接（如果适用于您的解决方案）。对于跨界连接，Azure 网关驻留在单独的网关子网中，您必须创建和分配地址空间。</span><span class="sxs-lookup"><span data-stu-id="33f26-p118">The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="33f26-179">在计划跨界连接时，您将定义并创建 Azure 网关和到本地网关设备的连接。</span><span class="sxs-lookup"><span data-stu-id="33f26-179">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="33f26-180">**图 2：使用 Azure 网关和本地网关设备提供本地环境和 Azure 之间的站点到站点连接**</span><span class="sxs-lookup"><span data-stu-id="33f26-180">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![通过跨界连接（可以是站点到站点 VPN 连接，也可以是 ExpressRoute）连接到 Azure 虚拟网络的本地环境。](../media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="33f26-182">在此图中：</span><span class="sxs-lookup"><span data-stu-id="33f26-182">In this diagram:</span></span>
  
- <span data-ttu-id="33f26-183">添加到上图中时，本地环境将通过跨界连接（可以是站点到站点 VPN 连接，也可以是 ExpressRoute）来连接到 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="33f26-183">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="33f26-184">Azure 网关位于网关子网上。</span><span class="sxs-lookup"><span data-stu-id="33f26-184">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="33f26-185">本地环境包括网关设备，如路由器或 VPN 服务器。</span><span class="sxs-lookup"><span data-stu-id="33f26-185">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="33f26-186">有关规划和创建跨界虚拟网络的其他信息，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="33f26-186">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="33f26-187">将 Active Directory 域服务 (AD DS) 和 DNS</span><span class="sxs-lookup"><span data-stu-id="33f26-187">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="33f26-188">在 Azure 中进行灾难恢复时，您在混合方案中部署 Windows Server AD 和 DNS，其中 Windows Server AD 部署在本地和 Azure 虚拟机上。</span><span class="sxs-lookup"><span data-stu-id="33f26-188">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="33f26-189">**图 3：混合 Active Directory 域配置**</span><span class="sxs-lookup"><span data-stu-id="33f26-189">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![部署到 Azure 虚拟网络和 SharePoint 场子网的 STwo 虚拟机是域控制器和 DNS 服务器的副本](../media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="33f26-p119">此图在上一张图的基础之上构建，它将两个虚拟机添加到 Windows Server AD 和 DNS 子网。这些虚拟机是域控制器和 DNS 服务器的副本。它们是本地 Windows Server AD 环境的扩展。</span><span class="sxs-lookup"><span data-stu-id="33f26-p119">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="33f26-p120">下表为 Azure 中的这些虚拟机提供了配置建议。使用这些建议作为设计您自己的环境的起点，即使是对 Azure 环境不与本地环境通信的专用域也是如此。</span><span class="sxs-lookup"><span data-stu-id="33f26-p120">The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="33f26-196">**项**</span><span class="sxs-lookup"><span data-stu-id="33f26-196">**Item**</span></span>|<span data-ttu-id="33f26-197">**配置**</span><span class="sxs-lookup"><span data-stu-id="33f26-197">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33f26-198">Azure 中的虚拟机大小</span><span class="sxs-lookup"><span data-stu-id="33f26-198">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="33f26-199">标准层中的 A1 或 A2 大小</span><span class="sxs-lookup"><span data-stu-id="33f26-199">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="33f26-200">操作系统</span><span class="sxs-lookup"><span data-stu-id="33f26-200">Operating system</span></span>  <br/> |<span data-ttu-id="33f26-201">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="33f26-201">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="33f26-202">Active Directory 角色</span><span class="sxs-lookup"><span data-stu-id="33f26-202">Active Directory role</span></span>  <br/> |<span data-ttu-id="33f26-p121">指定为全局目录服务器的 AD DS 域控制器。此配置减少了通过跨界连接的输出流量。</span><span class="sxs-lookup"><span data-stu-id="33f26-p121">AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="33f26-205">在高更改率（这并不常见）多域环境中，将内部部署域控制器配置为不与 Azure 中的全局目录服务器同步，以减少复制流量。</span><span class="sxs-lookup"><span data-stu-id="33f26-205">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="33f26-206">DNS 角色</span><span class="sxs-lookup"><span data-stu-id="33f26-206">DNS role</span></span>  <br/> |<span data-ttu-id="33f26-207">在域控制器上安装和配置 DNS 服务器服务。</span><span class="sxs-lookup"><span data-stu-id="33f26-207">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="33f26-208">数据磁盘</span><span class="sxs-lookup"><span data-stu-id="33f26-208">Data disks</span></span>  <br/> |<span data-ttu-id="33f26-p122">将 Active Directory 数据库、日志和 SYSVOL 放在其他 Azure 数据磁盘上。不要将它们放在操作系统磁盘或 Azure 提供的临时磁盘上。</span><span class="sxs-lookup"><span data-stu-id="33f26-p122">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="33f26-211">IP 地址</span><span class="sxs-lookup"><span data-stu-id="33f26-211">IP addresses</span></span>  <br/> |<span data-ttu-id="33f26-212">使用静态 IP 地址，并在域控制器配置完毕后，将虚拟机网络配置为将这些地址分配到虚拟网络中的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="33f26-212">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="33f26-p123">在 Azure 中部署 Active Directory 之前，阅读[在 Azure 虚拟机上部署 Windows Server Active Directory 的指南](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)。这些指南将帮助您确定您的解决方案是否需要不同的体系结构或不同的配置设置。</span><span class="sxs-lookup"><span data-stu-id="33f26-p123">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="33f26-215">添加 SharePoint 服务器场</span><span class="sxs-lookup"><span data-stu-id="33f26-215">Add the SharePoint farm</span></span>

<span data-ttu-id="33f26-216">将 SharePoint 服务器场虚拟机置于适当的子网的层级中。</span><span class="sxs-lookup"><span data-stu-id="33f26-216">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="33f26-217">**图 4：SharePoint 虚拟机的位置**</span><span class="sxs-lookup"><span data-stu-id="33f26-217">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![添加到 SharePoint 场子网内的 Azure 虚拟网络中的数据库服务器和 SharePoint 服务器角色](../media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="33f26-219">此图构建在上一张图的基础之上，它将 SharePoint 服务器场服务器角色添加到了相应的层级中。</span><span class="sxs-lookup"><span data-stu-id="33f26-219">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="33f26-220">运行 SQL Server 的两个数据库虚拟机创建数据库层。</span><span class="sxs-lookup"><span data-stu-id="33f26-220">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="33f26-221">运行以下每个层级的 SharePoint Server 2013 的两个虚拟机：前端服务器、分布式缓存服务器和后端服务器。</span><span class="sxs-lookup"><span data-stu-id="33f26-221">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="33f26-222">设计和优化可用性集和错误域的服务器角色</span><span class="sxs-lookup"><span data-stu-id="33f26-222">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="33f26-p124">错误域是角色实例在其中运行的硬件分组。同一错误域中的虚拟机可同时由 Azure 基础结构更新。否则它们可能同时发生故障，因为它们共享同一个机架。为避免同一错误域上具有两个虚拟机的风险，可以将您的虚拟机配置为可用性集，这可确保每个虚拟机位于不同的错误域中。如果三个虚拟机均配置为可用性集，Azure 保证位于同一错误域中的虚拟机不超过两个。</span><span class="sxs-lookup"><span data-stu-id="33f26-p124">A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="33f26-p125">为 SharePoint 服务器场设计 Azure 体系结构时，将相同的服务器角色配置为可用性集的一部分。这样可以确保您的虚拟机的分布在多个错误域。</span><span class="sxs-lookup"><span data-stu-id="33f26-p125">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="33f26-230">**图 5：使用 Azure 可用性集为 SharePoint 服务器层级提供高可用性**</span><span class="sxs-lookup"><span data-stu-id="33f26-230">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![SharePoint 2013 解决方案的 Azure 基础结构中的可用性集配置。](../media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="33f26-p126">此图调用 Azure 基础结构内可用性集的配置。下面每一个角色使用一个单独的可用性集：</span><span class="sxs-lookup"><span data-stu-id="33f26-p126">This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="33f26-234">Active Directory 和 DNS</span><span class="sxs-lookup"><span data-stu-id="33f26-234">Active Directory and DNS</span></span>
    
- <span data-ttu-id="33f26-235">数据库</span><span class="sxs-lookup"><span data-stu-id="33f26-235">Database</span></span>
    
- <span data-ttu-id="33f26-236">后端</span><span class="sxs-lookup"><span data-stu-id="33f26-236">Back end</span></span>
    
- <span data-ttu-id="33f26-237">分布式缓存</span><span class="sxs-lookup"><span data-stu-id="33f26-237">Distribute cache</span></span>
    
- <span data-ttu-id="33f26-238">前端</span><span class="sxs-lookup"><span data-stu-id="33f26-238">Front end</span></span>
    
<span data-ttu-id="33f26-p127">SharePoint 服务器场可能需要在 Azure 平台中进行优化。要确保所有组件的高可用性，请确保服务器角色的配置均相同。</span><span class="sxs-lookup"><span data-stu-id="33f26-p127">The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="33f26-p128">下面是一个示例，其中显示了满足特定容量和性能目标的标准 Internet 网站体系结构。此示例显示了以下体系结构模型的特点：[SharePoint Server 2013 的 Internet 网站搜索体系结构](https://go.microsoft.com/fwlink/p/?LinkId=261519)。</span><span class="sxs-lookup"><span data-stu-id="33f26-p128">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="33f26-243">**图 6：三层服务器场的容量和性能目标规划示例**</span><span class="sxs-lookup"><span data-stu-id="33f26-243">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![具有能满足特定容量和性能目标的组件分配的标准 SharePoint 2013 Internet 网站体系结构](../media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="33f26-245">在此图中：</span><span class="sxs-lookup"><span data-stu-id="33f26-245">In this diagram:</span></span>
  
- <span data-ttu-id="33f26-246">显示了三层服务器场：Web 服务器、应用程序服务器和数据库服务器。</span><span class="sxs-lookup"><span data-stu-id="33f26-246">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="33f26-247">三个 Web 服务器配置相同，均具有多个组件。</span><span class="sxs-lookup"><span data-stu-id="33f26-247">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="33f26-248">两个数据库服务器的配置相同。</span><span class="sxs-lookup"><span data-stu-id="33f26-248">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="33f26-p129">三个应用程序服务器的配置不相同。这些服务器角色需要对 Azure 中的可用性集进行优化。</span><span class="sxs-lookup"><span data-stu-id="33f26-p129">The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="33f26-251">让我们进一步了解一下应用程序服务器层。</span><span class="sxs-lookup"><span data-stu-id="33f26-251">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="33f26-252">**图 7：优化之前的应用程序服务器层**</span><span class="sxs-lookup"><span data-stu-id="33f26-252">**Figure 7: Application server tier before fine tuning**</span></span>

![调整 Microsoft Azure 可用性集之前的示例 SharePoint Server 2013 应用程序服务器层](../media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="33f26-254">在此图中：</span><span class="sxs-lookup"><span data-stu-id="33f26-254">In this diagram:</span></span>
  
- <span data-ttu-id="33f26-255">三个服务器都包含在应用程序层中。</span><span class="sxs-lookup"><span data-stu-id="33f26-255">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="33f26-256">第一个服务器包含四个组件。</span><span class="sxs-lookup"><span data-stu-id="33f26-256">The first server includes four components.</span></span>
    
- <span data-ttu-id="33f26-257">第二个服务器包括三个组件。</span><span class="sxs-lookup"><span data-stu-id="33f26-257">The second server includes three components.</span></span>
    
- <span data-ttu-id="33f26-258">第三个服务器包含两个组件。</span><span class="sxs-lookup"><span data-stu-id="33f26-258">The third server includes two components.</span></span>
    
<span data-ttu-id="33f26-p130">您可按服务器场的性能和容量目标确定组件数量。要调整 Azure 的此体系结构，我们将在所有三个服务器之间复制这四个组件。这将增加除性能和容量所需组件以外的组件数量。权衡点是当将这三个虚拟机分配至某个可用性集时，此设计确保了 Azure 平台中所有四个组件的高可用性。</span><span class="sxs-lookup"><span data-stu-id="33f26-p130">You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="33f26-263">**图 8：优化之后的应用程序服务器层**</span><span class="sxs-lookup"><span data-stu-id="33f26-263">**Figure 8: Application server tier after fine tuning**</span></span>

![调整 Microsoft Azure 可用性集之后的示例 SharePoint Server 2013 应用程序服务器层](../media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="33f26-265">此图显示了使用相同的四个组件进行相同配置的所有三个应用程序服务器。</span><span class="sxs-lookup"><span data-stu-id="33f26-265">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="33f26-266">将可用性集添加到 SharePoint 场层后，即完成实现过程。</span><span class="sxs-lookup"><span data-stu-id="33f26-266">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="33f26-267">**图 9：Azure 基础结构服务中已完成的 SharePoint 服务器场**</span><span class="sxs-lookup"><span data-stu-id="33f26-267">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Azure 基础结构服务中的示例 SharePoint 2013 场，带有虚拟网络、跨界连接、子网、虚拟机和可用性集。](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="33f26-269">此图显示在 Azure 基础结构服务中实现的 SharePoint 服务器场，以及为每个层级中的服务器提供故障域的可用性集。</span><span class="sxs-lookup"><span data-stu-id="33f26-269">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="33f26-270">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33f26-270">See Also</span></span>

[<span data-ttu-id="33f26-271">Microsoft 365 解决方案和体系结构中心</span><span class="sxs-lookup"><span data-stu-id="33f26-271">Microsoft 365 solution and architecture center</span></span>](../solutions/index.yml)
  
[<span data-ttu-id="33f26-272">Microsoft Azure 中使用 SharePoint Server 2013 的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="33f26-272">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="33f26-273">Microsoft Azure 中的 SharePoint Server 2013 灾难恢复</span><span class="sxs-lookup"><span data-stu-id="33f26-273">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)