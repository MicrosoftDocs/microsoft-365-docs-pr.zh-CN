---
title: 将本地网络连接到 Microsoft Azure 虚拟网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 摘要：了解如何使用站点间 VPN 连接为 Office 服务器工作负载配置跨界 Azure 虚拟网络。
ms.openlocfilehash: 00fd1c2246e9e9ac3eb55ca5ece9d84ecf49a1d3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50907704"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a><span data-ttu-id="1de80-103">将本地网络连接到 Microsoft Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="1de80-103">Connect an on-premises network to a Microsoft Azure virtual network</span></span>

<span data-ttu-id="1de80-p101">Azure 跨界虚拟网络连接到本地网络，从而可扩展网络以包含在 Azure 基础结构服务中托管的子网和虚拟机。上述连接可让本地网络中的计算机直接访问 Azure 中的虚拟机，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="1de80-p101">A cross-premises Azure virtual network is connected to your on-premises network, extending your network to include subnets and virtual machines hosted in Azure infrastructure services. This connection lets computers on your on-premises network to directly access virtual machines in Azure and vice versa.</span></span> 

<span data-ttu-id="1de80-106">例如，在 Azure 虚拟机上运行的目录同步服务器需要查询本地域控制器以查询帐户更改，以及将这些更改与 Microsoft 365 订阅同步。</span><span class="sxs-lookup"><span data-stu-id="1de80-106">For example, a directory synchronization server running on an Azure virtual machine needs to query your on-premises domain controllers for changes to accounts and synchronize those changes with your Microsoft 365 subscription.</span></span> <span data-ttu-id="1de80-107">本文演示如何使用准备好托管 Azure 虚拟机的站点间虚拟专用网络 (VPN) 连接设置跨界 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="1de80-107">This article shows you how to set up a cross-premises Azure virtual network using a site-to-site virtual private network (VPN) connection that is ready to host Azure virtual machines.</span></span>

## <a name="configure-a-cross-premises-azure-virtual-network"></a><span data-ttu-id="1de80-108">配置跨界 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="1de80-108">Configure a cross-premises Azure virtual network</span></span>

<span data-ttu-id="1de80-p103">Azure 中的虚拟机无需与本地环境隔离。若要将 Azure 虚拟机连接到本地网络资源，必须配置 Azure 跨界虚拟网络。下图显示了使用 Azure 中的虚拟机部署跨部署 Azure 虚拟网络所需的组件。</span><span class="sxs-lookup"><span data-stu-id="1de80-p103">Your virtual machines in Azure don't have to be isolated from your on-premises environment. To connect Azure virtual machines to your on-premises network resources, you must configure a cross-premises Azure virtual network. The following diagram shows the required components to deploy a cross-premises Azure virtual network with a virtual machine in Azure.</span></span>
  
![通过站点间 VPN 连接来连接到 Microsoft Azure 的本地网络连接](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
<span data-ttu-id="1de80-p104">在该关系图中，有两个通过站点间 VPN 连接进行连接的网络：本地网络和 Azure 虚拟网络。站点间 VPN 连接为：</span><span class="sxs-lookup"><span data-stu-id="1de80-p104">In the diagram, there are two networks connected by a site-to-site VPN connection: the on-premises network and the Azure virtual network. The site-to-site VPN connection is:</span></span>

- <span data-ttu-id="1de80-115">在可寻址和位于在公共 Internet 上的两个终结点之间。</span><span class="sxs-lookup"><span data-stu-id="1de80-115">Between two endpoints that are addressable and located on the public Internet.</span></span>
- <span data-ttu-id="1de80-116">两端分别为本地网络中的 VPN 设备和 Azure 虚拟网络中的 Azure VPN 网关。</span><span class="sxs-lookup"><span data-stu-id="1de80-116">Terminated by a VPN device on the on-premises network and an Azure VPN gateway on the Azure virtual network.</span></span>

<span data-ttu-id="1de80-p105">Azure 虚拟网络托管虚拟机。Azure 虚拟网络上从虚拟机发出的网络流量将转发到 VPN 网关，然后再跨站点间 VPN 连接将流量转发到本地网络上的 VPN 设备。本地网络的路由基础结构接着会将流量转发到其目标。</span><span class="sxs-lookup"><span data-stu-id="1de80-p105">The Azure virtual network hosts virtual machines. Network traffic originating from virtual machines on the Azure virtual network gets forwarded to the VPN gateway, which then forwards the traffic across the site-to-site VPN connection to the VPN device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination.</span></span>

>[!Note]
><span data-ttu-id="1de80-p106">此外，你还可以使用 [ExpressRoute](https://azure.microsoft.com/services/expressroute/)，即组织和 Microsoft 网络之间的直接连接。ExpressRoute 上的流量不会在公共 Internet 上传输。本文对 ExpressRoute 的用法将不做介绍。</span><span class="sxs-lookup"><span data-stu-id="1de80-p106">You can also use [ExpressRoute](https://azure.microsoft.com/services/expressroute/), which is a direct connection between your organization and Microsoft's network. Traffic over ExpressRoute does not travel over the public Internet. This article does not describe the use of ExpressRoute.</span></span>
>
  
<span data-ttu-id="1de80-123">要设置 Azure 虚拟网络和本地网络之间的 VPN 连接，请按照以下步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="1de80-123">To set up the VPN connection between your Azure virtual network and your on-premises network, follow these steps:</span></span> 
  
1. <span data-ttu-id="1de80-124">本地：为指向本地 VPN 设备的 Azure 虚拟网络的地址空间定义并创建本地网络路由。</span><span class="sxs-lookup"><span data-stu-id="1de80-124">**On-premises:** Define and create an on-premises network route for the address space of the Azure virtual network that points to your on-premises VPN device.</span></span>
    
2. <span data-ttu-id="1de80-125">Microsoft Azure：使用站点间 VPN 连接创建一个 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="1de80-125">**Microsoft Azure:** Create an Azure virtual network with a site-to-site VPN connection.</span></span> 
    
3. <span data-ttu-id="1de80-126">本地：将本地硬件或软件 VPN 设备配置为终止使用遵循 Internet 协议安全性 (IPsec) 的 VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="1de80-126">**On premises:** Configure your on-premises hardware or software VPN device to terminate the VPN connection, which uses Internet Protocol security (IPsec).</span></span>
    
<span data-ttu-id="1de80-127">建立站点到站点 VPN 连接后，将 Azure 虚拟机添加到虚拟网络子网。</span><span class="sxs-lookup"><span data-stu-id="1de80-127">After you establish the site-to-site VPN connection, you add Azure virtual machines to the subnets of the virtual network.</span></span>
  
## <a name="plan-your-azure-virtual-network"></a><span data-ttu-id="1de80-128">规划你的 Azure 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="1de80-128">Plan your Azure virtual network</span></span>
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a><span data-ttu-id="1de80-129">先决条件</span><span class="sxs-lookup"><span data-stu-id="1de80-129">Prerequisites</span></span>
<a name="Prerequisites"></a>

- <span data-ttu-id="1de80-p107">Azure 订阅。有关 Azure 订阅的信息，请转到[如何购买 Azure 页面](https://azure.microsoft.com/pricing/purchase-options/)。</span><span class="sxs-lookup"><span data-stu-id="1de80-p107">An Azure subscription. For information about Azure subscriptions, go to the [How To Buy Azure page](https://azure.microsoft.com/pricing/purchase-options/).</span></span>
    
- <span data-ttu-id="1de80-132">可用的专用 IPv4 地址空间，将分配给虚拟网络及其子网，具有足够的空间容纳现在和将来所需的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="1de80-132">An available private IPv4 address space to assign to the virtual network and its subnets, with sufficient room for growth to accommodate the number of virtual machines needed now and in the future.</span></span>
    
- <span data-ttu-id="1de80-p108">本地网络中的可用 VPN 设备，用于终止支持 IPsec 要求的站点间 VPN 连接。有关详细信息，请参阅[有关用于站点间虚拟网络连接的 VPN 设备](/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="1de80-p108">An available VPN device in your on-premises network to terminate the site-to-site VPN connection that supports the requirements for IPsec. For more information, see [About VPN devices for site-to-site virtual network connections](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
    
- <span data-ttu-id="1de80-135">对路由基础结构的变更，以便路由到 Azure 虚拟网络地址空间的流量转发到承载站点间 VPN 连接的 VPN 设备。</span><span class="sxs-lookup"><span data-stu-id="1de80-135">Changes to your routing infrastructure so that traffic routed to the address space of the Azure virtual network gets forwarded to the VPN device that hosts the site-to-site VPN connection.</span></span>
    
- <span data-ttu-id="1de80-136">Web 代理，向连接到本地网络的计算机和 Azure 虚拟网络授予 Internet 访问权限。</span><span class="sxs-lookup"><span data-stu-id="1de80-136">A web proxy that gives computers that are connected to the on-premises network and the Azure virtual network access to the Internet.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="1de80-137">解决方案体系结构设计假设</span><span class="sxs-lookup"><span data-stu-id="1de80-137">Solution architecture design assumptions</span></span>

<span data-ttu-id="1de80-138">下面的列表显示已为该解决方案体系结构做出的设计选择。</span><span class="sxs-lookup"><span data-stu-id="1de80-138">The following list represents the design choices that have been made for this solution architecture.</span></span> 
  
- <span data-ttu-id="1de80-p109">此解决方案使用具有站点间 VPN 连接的单个 Azure 虚拟网络。Azure 虚拟网络承载可能包含多个虚拟机的单个子网。</span><span class="sxs-lookup"><span data-stu-id="1de80-p109">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that can contain multiple virtual machines.</span></span> 
    
- <span data-ttu-id="1de80-p110">可以使用 Windows Server 2016 或 Windows Server 2012 中的路由和远程访问服务 (RRAS) 在本地网络和 Azure 虚拟网络之间建立 IPsec 站点间 VPN 连接。还可以使用其他选项，例如 Cisco 或 Juniper Networks VPN 设备。</span><span class="sxs-lookup"><span data-stu-id="1de80-p110">You can use the Routing and Remote Access Service (RRAS) in Windows Server 2016 or Windows Server 2012 to establish an IPsec site-to-site VPN connection between the on-premises network and the Azure virtual network. You can also use other options, such as Cisco or Juniper Networks VPN devices.</span></span>
    
- <span data-ttu-id="1de80-p111">本地网络可能还具有 Active Directory 域服务 (AD DS)、域名系统 (DNS) 和代理服务器等网络资源。根据你的要求，它可能在将部分网络资源放到 Azure 虚拟网络中时非常有帮助。</span><span class="sxs-lookup"><span data-stu-id="1de80-p111">The on-premises network might still have network services like Active Directory Domain Services (AD DS), Domain Name System (DNS), and proxy servers. Depending on your requirements, it might be beneficial to place some of these network resources in the Azure virtual network.</span></span>
    
<span data-ttu-id="1de80-p112">对于具有一个或多个子网的现有 Azure 虚拟网络，确定是否还有剩余的地址空间以便附加子网托管您所需的虚拟机，具体取决于您的要求。如果您没有供附加子网使用的剩余地址空间，请创建具有站点间 VPN 连接的其他虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="1de80-p112">For an existing Azure virtual network with one or more subnets, determine whether there is remaining address space for an additional subnet to host your needed virtual machines, based on your requirements. If you don't have remaining address space for an additional subnet, create an additional virtual network that has its own site-to-site VPN connection.</span></span>
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a><span data-ttu-id="1de80-147">规划 Azure 虚拟网络的路由基础结构变更</span><span class="sxs-lookup"><span data-stu-id="1de80-147">Plan the routing infrastructure changes for the Azure virtual network</span></span>

<span data-ttu-id="1de80-148">您必须将本地路由基础结构配置为将目标为 Azure 虚拟网络的地址空间的流量转发到承载站点间 VPN 连接的本地 VPN 设备。</span><span class="sxs-lookup"><span data-stu-id="1de80-148">You must configure your on-premises routing infrastructure to forward traffic destined for the address space of the Azure virtual network to the on-premises VPN device that is hosting the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="1de80-149">更新路由基础结构的具体方法取决于您管理路由信息的方式，可能的选项如下：</span><span class="sxs-lookup"><span data-stu-id="1de80-149">The exact method of updating your routing infrastructure depends on how you manage routing information, which can be:</span></span>
  
- <span data-ttu-id="1de80-150">基于手动配置路由表更新。</span><span class="sxs-lookup"><span data-stu-id="1de80-150">Routing table updates based on manual configuration.</span></span>
    
- <span data-ttu-id="1de80-151">基于路由协议路由表更新，例如路由信息协议 (RIP) 或开放式最短路径优先 (OSPF) 协议。</span><span class="sxs-lookup"><span data-stu-id="1de80-151">Routing table updates based on routing protocols, such as Routing Information Protocol (RIP) or Open Shortest Path First (OSPF).</span></span>
    
<span data-ttu-id="1de80-152">咨询路由专家，确保目标为 Azure 虚拟网络的流量将转发到本地 VPN 设备。</span><span class="sxs-lookup"><span data-stu-id="1de80-152">Consult with your routing specialist to make sure that traffic destined for the Azure virtual network is forwarded to the on-premises VPN device.</span></span>
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a><span data-ttu-id="1de80-153">规划发送到本地 VPN 设备以及从本地 VPN 设备发出的流量的防火墙规则</span><span class="sxs-lookup"><span data-stu-id="1de80-153">Plan for firewall rules for traffic to and from the on-premises VPN device</span></span>

<span data-ttu-id="1de80-154">如果您的 VPN 位于一个外围网络，且该外围网络和 Internet 之间存在防火墙，您可能需要对防火墙进行配置，以便以下规则允许站点间 VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="1de80-154">If your VPN device is on a perimeter network that has a firewall between the perimeter network and the Internet, you might have to configure the firewall for the following rules to allow the site-to-site VPN connection.</span></span>
  
- <span data-ttu-id="1de80-155">到 VPN 设备的流量（从 Internet 传入）：</span><span class="sxs-lookup"><span data-stu-id="1de80-155">Traffic to the VPN device (incoming from the Internet):</span></span>
    
  - <span data-ttu-id="1de80-156">VPN 设备的目标 IP 地址和 IP 协议 50</span><span class="sxs-lookup"><span data-stu-id="1de80-156">Destination IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="1de80-157">VPN 设备的目标 IP 地址和 UDP 目标端口 500</span><span class="sxs-lookup"><span data-stu-id="1de80-157">Destination IP address of the VPN device and UDP destination port 500</span></span>
    
  - <span data-ttu-id="1de80-158">VPN 设备的目标 IP 地址和 UDP 目标端口 4500</span><span class="sxs-lookup"><span data-stu-id="1de80-158">Destination IP address of the VPN device and UDP destination port 4500</span></span>
    
- <span data-ttu-id="1de80-159">来自 VPN 设备的流量（传出到 Internet）：</span><span class="sxs-lookup"><span data-stu-id="1de80-159">Traffic from the VPN device (outgoing to the Internet):</span></span>
    
  - <span data-ttu-id="1de80-160">VPN 设备的源 IP 地址和 IP 协议 50</span><span class="sxs-lookup"><span data-stu-id="1de80-160">Source IP address of the VPN device and IP protocol 50</span></span>
    
  - <span data-ttu-id="1de80-161">VPN 设备的源 IP 地址和 UDP 源端口 500</span><span class="sxs-lookup"><span data-stu-id="1de80-161">Source IP address of the VPN device and UDP source port 500</span></span>
    
  - <span data-ttu-id="1de80-162">VPN 设备的源 IP 地址和 UDP 源端口 4500</span><span class="sxs-lookup"><span data-stu-id="1de80-162">Source IP address of the VPN device and UDP source port 4500</span></span>
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a><span data-ttu-id="1de80-163">规划 Azure 虚拟网络的专用 IP 地址空间</span><span class="sxs-lookup"><span data-stu-id="1de80-163">Plan for the private IP address space of the Azure virtual network</span></span>

<span data-ttu-id="1de80-164">Azure 虚拟网络的专用 IP 地址空间必须能够容纳 Azure 用于承载虚拟网络的地址，且具有至少一个有足够地址供 Azure 虚拟机使用的子网。</span><span class="sxs-lookup"><span data-stu-id="1de80-164">The private IP address space of the Azure virtual network must be able to accommodate addresses used by Azure to host the virtual network and with at least one subnet that has enough addresses for your Azure virtual machines.</span></span>
  
<span data-ttu-id="1de80-165">要确定子网需要的地址数量，请计算您现在需要的虚拟机数量，估计未来增长的数量，然后使用下表确定子网大小。</span><span class="sxs-lookup"><span data-stu-id="1de80-165">To determine the number of addresses needed for the subnet, count the number of virtual machines that you need now, estimate for future growth, and then use the following table to determine the size of the subnet.</span></span>
  
|<span data-ttu-id="1de80-166">**所需的虚拟机数量**</span><span class="sxs-lookup"><span data-stu-id="1de80-166">**Number of virtual machines needed**</span></span>|<span data-ttu-id="1de80-167">**所需的主机位数**</span><span class="sxs-lookup"><span data-stu-id="1de80-167">**Number of host bits needed**</span></span>|<span data-ttu-id="1de80-168">**子网大小**</span><span class="sxs-lookup"><span data-stu-id="1de80-168">**Size of the subnet**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1de80-169">1-3</span><span class="sxs-lookup"><span data-stu-id="1de80-169">1-3</span></span>  <br/> |<span data-ttu-id="1de80-170">3</span><span class="sxs-lookup"><span data-stu-id="1de80-170">3</span></span>  <br/> |<span data-ttu-id="1de80-171">/29</span><span class="sxs-lookup"><span data-stu-id="1de80-171">/29</span></span>  <br/> |
|<span data-ttu-id="1de80-172">4-11</span><span class="sxs-lookup"><span data-stu-id="1de80-172">4-11</span></span>  <br/> |<span data-ttu-id="1de80-173">4 </span><span class="sxs-lookup"><span data-stu-id="1de80-173">4</span></span>  <br/> |<span data-ttu-id="1de80-174">/28</span><span class="sxs-lookup"><span data-stu-id="1de80-174">/28</span></span>  <br/> |
|<span data-ttu-id="1de80-175">12-27</span><span class="sxs-lookup"><span data-stu-id="1de80-175">12-27</span></span>  <br/> |<span data-ttu-id="1de80-176">5 </span><span class="sxs-lookup"><span data-stu-id="1de80-176">5</span></span>  <br/> |<span data-ttu-id="1de80-177">/27</span><span class="sxs-lookup"><span data-stu-id="1de80-177">/27</span></span>  <br/> |
|<span data-ttu-id="1de80-178">28-59</span><span class="sxs-lookup"><span data-stu-id="1de80-178">28-59</span></span>  <br/> |<span data-ttu-id="1de80-179">6 </span><span class="sxs-lookup"><span data-stu-id="1de80-179">6</span></span>  <br/> |<span data-ttu-id="1de80-180">/26</span><span class="sxs-lookup"><span data-stu-id="1de80-180">/26</span></span>  <br/> |
|<span data-ttu-id="1de80-181">60-123</span><span class="sxs-lookup"><span data-stu-id="1de80-181">60-123</span></span>  <br/> |<span data-ttu-id="1de80-182">7 </span><span class="sxs-lookup"><span data-stu-id="1de80-182">7</span></span>  <br/> |<span data-ttu-id="1de80-183">/25</span><span class="sxs-lookup"><span data-stu-id="1de80-183">/25</span></span>  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a><span data-ttu-id="1de80-184">用于配置 Azure 虚拟网络的规划工作表</span><span class="sxs-lookup"><span data-stu-id="1de80-184">Planning worksheet for configuring your Azure virtual network</span></span>
<span data-ttu-id="1de80-185"><a name="worksheet"> </a></span><span class="sxs-lookup"><span data-stu-id="1de80-185"><a name="worksheet"> </a></span></span>

<span data-ttu-id="1de80-186">在创建托管虚拟机的 Azure 虚拟网络之前，您必须在下表中确定所需的设置。</span><span class="sxs-lookup"><span data-stu-id="1de80-186">Before you create an Azure virtual network to host virtual machines, you must determine the settings needed in the following tables.</span></span>
  
<span data-ttu-id="1de80-187">有关虚拟网络的设置，请填写表 V。</span><span class="sxs-lookup"><span data-stu-id="1de80-187">For the settings of the virtual network, fill in Table V.</span></span>
  
 <span data-ttu-id="1de80-188">**表 V：跨部署虚拟网络配置**</span><span class="sxs-lookup"><span data-stu-id="1de80-188">**Table V: Cross-premises virtual network configuration**</span></span>
  
|<span data-ttu-id="1de80-189">**项**</span><span class="sxs-lookup"><span data-stu-id="1de80-189">**Item**</span></span>|<span data-ttu-id="1de80-190">**Configuration 元素**</span><span class="sxs-lookup"><span data-stu-id="1de80-190">**Configuration element**</span></span>|<span data-ttu-id="1de80-191">**说明**</span><span class="sxs-lookup"><span data-stu-id="1de80-191">**Description**</span></span>|<span data-ttu-id="1de80-192">**值**</span><span class="sxs-lookup"><span data-stu-id="1de80-192">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1de80-193">1.</span><span class="sxs-lookup"><span data-stu-id="1de80-193">1.</span></span>  <br/> |<span data-ttu-id="1de80-194">虚拟网络名称</span><span class="sxs-lookup"><span data-stu-id="1de80-194">Virtual network name</span></span>  <br/> |<span data-ttu-id="1de80-195">要分配给 Azure 虚拟网络的名称（例如，DirSyncNet）。</span><span class="sxs-lookup"><span data-stu-id="1de80-195">A name to assign to the Azure virtual network (example DirSyncNet).</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png) |
|<span data-ttu-id="1de80-197">2.</span><span class="sxs-lookup"><span data-stu-id="1de80-197">2.</span></span>  <br/> |<span data-ttu-id="1de80-198">虚拟网络位置</span><span class="sxs-lookup"><span data-stu-id="1de80-198">Virtual network location</span></span>  <br/> |<span data-ttu-id="1de80-199">将包含虚拟网络的 Azure 数据中心（如美国西部）。</span><span class="sxs-lookup"><span data-stu-id="1de80-199">The Azure datacenter that will contain the virtual network (such as West US).</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="1de80-201">3.</span><span class="sxs-lookup"><span data-stu-id="1de80-201">3.</span></span>  <br/> |<span data-ttu-id="1de80-202">VPN 设备 IP 地址</span><span class="sxs-lookup"><span data-stu-id="1de80-202">VPN device IP address</span></span>  <br/> |<span data-ttu-id="1de80-p113">Internet 上 VPN 设备接口的公用 IPv4 地址。与 IT 部门协作，以确定该地址。</span><span class="sxs-lookup"><span data-stu-id="1de80-p113">The public IPv4 address of your VPN device's interface on the Internet. Work with your IT department to determine this address.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="1de80-206">4.</span><span class="sxs-lookup"><span data-stu-id="1de80-206">4.</span></span>  <br/> |<span data-ttu-id="1de80-207">虚拟网络地址空间</span><span class="sxs-lookup"><span data-stu-id="1de80-207">Virtual network address space</span></span>  <br/> |<span data-ttu-id="1de80-p114">虚拟网络地址空间（在一组专用地址前缀中定义）。与 IT 部门协作，以确定该地址空间。地址空间应为无类别域际路由选择 (CIDR) 格式，也称为网络前缀格式。例如，10.24.64.0/20。</span><span class="sxs-lookup"><span data-stu-id="1de80-p114">The address space (defined in a single private address prefix) for the virtual network. Work with your IT department to determine this address space. The address space should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png) <br/> |
|<span data-ttu-id="1de80-213">5.</span><span class="sxs-lookup"><span data-stu-id="1de80-213">5.</span></span>  <br/> |<span data-ttu-id="1de80-214">IPsec 共享的密钥</span><span class="sxs-lookup"><span data-stu-id="1de80-214">IPsec shared key</span></span>  <br/> |<span data-ttu-id="1de80-p115">一组 32 位字符的随机字母数字字符串，用于对站点间 VPN 连接的两端进行身份验证。与 IT 或安全部门协作来确定此密钥值，然后将其存储在安全的位置。或者，请参阅[创建 IPsec 预共享密钥的随机字符串](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1de80-p115">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value and then store it in a secure location. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![线条](../media/Common-Images/TableLine.png) <br/> |
   
<span data-ttu-id="1de80-219">此解决方案的子网请填写表 S。</span><span class="sxs-lookup"><span data-stu-id="1de80-219">Fill in Table S for the subnets of this solution.</span></span>
  
- <span data-ttu-id="1de80-p116">对于第一个子网，请为 Azure 网关子网确定 28 位的地址空间（带有 /28 前缀长度）。有关如何确定此地址空间的信息，请参阅 [Calculating the gateway subnet address space for Azure virtual networks](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks)（计算 Azure 虚拟网络的网关子网地址空间）。</span><span class="sxs-lookup"><span data-stu-id="1de80-p116">For the first subnet, determine a 28-bit address space (with a /28 prefix length) for the Azure gateway subnet. See [Calculating the gateway subnet address space for Azure virtual networks](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) for information about how to determine this address space.</span></span>
    
- <span data-ttu-id="1de80-222">对于第二个子网，请指定友好名称（基于虚拟网络地址空间的单一 IP 地址空间）和描述性目的。</span><span class="sxs-lookup"><span data-stu-id="1de80-222">For the second subnet, specify a friendly name, a single IP address space based on the virtual network address space, and a descriptive purpose.</span></span>
    
<span data-ttu-id="1de80-p117">与 IT 部门协作以确定这些虚拟网络地址空间中的地址空间。这两个地址空间应为 CIDR 格式。</span><span class="sxs-lookup"><span data-stu-id="1de80-p117">Work with your IT department to determine these address spaces from the virtual network address space. Both address spaces should be in CIDR format.</span></span>
  
 <span data-ttu-id="1de80-225">**表 S：虚拟网络中的子网**</span><span class="sxs-lookup"><span data-stu-id="1de80-225">**Table S: Subnets in the virtual network**</span></span>
  
|<span data-ttu-id="1de80-226">**项**</span><span class="sxs-lookup"><span data-stu-id="1de80-226">**Item**</span></span>|<span data-ttu-id="1de80-227">**子网名称**</span><span class="sxs-lookup"><span data-stu-id="1de80-227">**Subnet name**</span></span>|<span data-ttu-id="1de80-228">**子网地址空间**</span><span class="sxs-lookup"><span data-stu-id="1de80-228">**Subnet address space**</span></span>|<span data-ttu-id="1de80-229">**用途**</span><span class="sxs-lookup"><span data-stu-id="1de80-229">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1de80-230">1.</span><span class="sxs-lookup"><span data-stu-id="1de80-230">1.</span></span>  <br/> |<span data-ttu-id="1de80-231">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="1de80-231">GatewaySubnet</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="1de80-233">Azure 网关使用的子网。</span><span class="sxs-lookup"><span data-stu-id="1de80-233">The subnet used by the Azure gateway.</span></span>  <br/> |
|<span data-ttu-id="1de80-234">2.</span><span class="sxs-lookup"><span data-stu-id="1de80-234">2.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
   
<span data-ttu-id="1de80-p118">对于您想要让虚拟网络中的虚拟机使用的本地 DNS 服务器，请填写表 D。为 DNS 服务器提供友好名称和单一 IP 地址。此友好名称不需要与 DNS 服务器的主机名或计算机名相匹配。请注意已列出两个空白条目，但您可以添加更多。与 IT 部门协作，以确定该列表。</span><span class="sxs-lookup"><span data-stu-id="1de80-p118">For the on-premises DNS servers that you want the virtual machines in the virtual network to use, fill in Table D. Give each DNS server a friendly name and a single IP address. This friendly name does not need to match the host name or computer name of the DNS server. Note that two blank entries are listed, but you can add more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="1de80-242">**表 D：本地 DNS 服务器**</span><span class="sxs-lookup"><span data-stu-id="1de80-242">**Table D: On-premises DNS servers**</span></span>
  
|<span data-ttu-id="1de80-243">**项**</span><span class="sxs-lookup"><span data-stu-id="1de80-243">**Item**</span></span>|<span data-ttu-id="1de80-244">**DNS 服务器的友好名称**</span><span class="sxs-lookup"><span data-stu-id="1de80-244">**DNS server friendly name**</span></span>|<span data-ttu-id="1de80-245">**DNS 服务器的 IP 地址**</span><span class="sxs-lookup"><span data-stu-id="1de80-245">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="1de80-246">1.</span><span class="sxs-lookup"><span data-stu-id="1de80-246">1.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="1de80-249">2.</span><span class="sxs-lookup"><span data-stu-id="1de80-249">2.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
   
<span data-ttu-id="1de80-p119">要通过站点间 VPN 连接将数据包从 Azure 虚拟网络传输到组织网络，则必须使用本地网络配置虚拟网络。此本地网络包含组织的本地网络上的所有位置的地址空间列表（使用 CIDR 格式），虚拟网络中的虚拟机必须能够访问这些本地网络。这可能是本地网络上的所有位置或部分位置。用于定义本地网络的地址空间列表必须是唯一的，并且不得与用于此虚拟网络或其他跨界虚拟网络的地址空间重叠。</span><span class="sxs-lookup"><span data-stu-id="1de80-p119">To route packets from the Azure virtual network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network. This local network has a list of the address spaces (in CIDR format) for all of the locations on your organization's on-premises network that the virtual machines in the virtual network must reach. This can be all of the locations on the on-premises network or a subset. The list of address spaces that define your local network must be unique and must not overlap with the address spaces used for this virtual network or your other cross-premises virtual networks.</span></span>
  
<span data-ttu-id="1de80-p120">对于本地网络地址空间集，请填写表 L。请注意已列出三个空白条目，但通常需要更多。与 IT 部门协作，以确定该列表。</span><span class="sxs-lookup"><span data-stu-id="1de80-p120">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list.</span></span>
  
 <span data-ttu-id="1de80-258">**表 L：本地网络的地址前缀**</span><span class="sxs-lookup"><span data-stu-id="1de80-258">**Table L: Address prefixes for the local network**</span></span>
  
|<span data-ttu-id="1de80-259">**项**</span><span class="sxs-lookup"><span data-stu-id="1de80-259">**Item**</span></span>|<span data-ttu-id="1de80-260">**本地网络地址空间**</span><span class="sxs-lookup"><span data-stu-id="1de80-260">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1de80-261">1.</span><span class="sxs-lookup"><span data-stu-id="1de80-261">1.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="1de80-263">2.</span><span class="sxs-lookup"><span data-stu-id="1de80-263">2.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="1de80-265">3.</span><span class="sxs-lookup"><span data-stu-id="1de80-265">3.</span></span>  <br/> |![线条](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a><span data-ttu-id="1de80-267">部署路线图</span><span class="sxs-lookup"><span data-stu-id="1de80-267">Deployment roadmap</span></span>
<span data-ttu-id="1de80-268"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="1de80-268"><a name="DeploymentRoadmap"> </a></span></span>

<span data-ttu-id="1de80-269">在 Azure 中创建跨界虚拟网络并添加虚拟机包含三个阶段：</span><span class="sxs-lookup"><span data-stu-id="1de80-269">Creating the cross-premises virtual network and adding virtual machines in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="1de80-270">阶段 1：准备本地网络。</span><span class="sxs-lookup"><span data-stu-id="1de80-270">Phase 1: Prepare your on-premises network.</span></span>
    
- <span data-ttu-id="1de80-271">阶段 2：在 Azure 中创建跨界虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="1de80-271">Phase 2: Create the cross-premises virtual network in Azure.</span></span>
    
- <span data-ttu-id="1de80-272">阶段 3（可选）：添加虚拟机。</span><span class="sxs-lookup"><span data-stu-id="1de80-272">Phase 3 (Optional): Add virtual machines.</span></span>
    
### <a name="phase-1-prepare-your-on-premises-network"></a><span data-ttu-id="1de80-273">阶段 1：准备您的本地网络:</span><span class="sxs-lookup"><span data-stu-id="1de80-273">Phase 1: Prepare your on-premises network</span></span>
<a name="Phase1"></a>

<span data-ttu-id="1de80-p121">必须配置本地网络，其中路由指向目标为虚拟网络地址空间的流量并将流量提供给本地网络边缘中的路由器。请咨询你的网络管理员，以确定如何将路由添加到本地网络的路由结构。</span><span class="sxs-lookup"><span data-stu-id="1de80-p121">You must configure your on-premises network with a route that points to and ultimately delivers traffic destined for the address space of the virtual network to the router on the edge of the on-premises network. Consult with your network administrator to determine how to add the route to the routing infrastructure of your on-premises network.</span></span>
  
<span data-ttu-id="1de80-276">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1de80-276">Here is your resulting configuration.</span></span>
  
![本地网络上必须有指向 VPN 设备的虚拟网络地址空间的路由。](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="1de80-278">阶段 2：在 Azure 中创建跨部署虚拟网络</span><span class="sxs-lookup"><span data-stu-id="1de80-278">Phase 2: Create the cross-premises virtual network in Azure</span></span>
<a name="Phase2"></a>

<span data-ttu-id="1de80-p122">首先，请打开 Azure PowerShell 提示符。如果没有安装 Azure PowerShell，请参阅 [Azure PowerShell 使用入门](/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="1de80-p122">First, open an Azure PowerShell prompt. If you have not installed Azure PowerShell, see [Get started with Azure PowerShell](/powershell/azure/get-started-azureps).</span></span>

 
<span data-ttu-id="1de80-281">下一步，使用此命令登录 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="1de80-281">Next, login to your Azure account with this command.</span></span>
  
```powershell
Connect-AzAccount
```

<span data-ttu-id="1de80-282">使用以下命令获得订阅名称。</span><span class="sxs-lookup"><span data-stu-id="1de80-282">Get your subscription name using the following command.</span></span>
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

<span data-ttu-id="1de80-p123">通过这些命令设置 Azure 订阅。使用正确的订阅名称替换引号内的所有内容（包括 < 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="1de80-p123">Set your Azure subscription with these commands. Replace everything within the quotes, including the < and > characters, with the correct subscription name.</span></span>
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="1de80-p124">接下来，为虚拟网络创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出您现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="1de80-p124">Next, create a new resource group for your virtual network. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="1de80-287">使用这些命令创建新的资源组。</span><span class="sxs-lookup"><span data-stu-id="1de80-287">Create your new resource group with these commands.</span></span>
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="1de80-288">接下来，请创建 Azure 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="1de80-288">Next, you create the Azure virtual network.</span></span>
  
```powershell
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="1de80-289">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1de80-289">Here is your resulting configuration.</span></span>
  
![虚拟网络尚未连接到本地网络。](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
<span data-ttu-id="1de80-291">下一步，请使用这些命令来创建站点间 VPN 连接的网关。</span><span class="sxs-lookup"><span data-stu-id="1de80-291">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```powershell
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

<span data-ttu-id="1de80-292">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1de80-292">Here is your resulting configuration.</span></span>
  
![虚拟网络现有一个网关。](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
<span data-ttu-id="1de80-p125">接下来，请将本地 VPN 设备配置为连接到 Azure VPN 网关。有关详细信息，请参阅[有关用于站点间 Azure 虚拟网络连接的 VPN 设备](/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="1de80-p125">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [About VPN Devices for site-to-site Azure Virtual Network connections](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="1de80-296">若要配置 VPN 设备，您需要以下各项:</span><span class="sxs-lookup"><span data-stu-id="1de80-296">To configure your VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="1de80-297">用于虚拟网络的 Azure VPN 网关的公用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="1de80-297">The public IPv4 address of the Azure VPN gateway for your virtual network.</span></span> <span data-ttu-id="1de80-298">使用 **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** 命令显示此地址。</span><span class="sxs-lookup"><span data-stu-id="1de80-298">Use the **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** command to display this address.</span></span>
    
- <span data-ttu-id="1de80-299">站点间 VPN 连接的 IPsec 预共享密钥（表 V - 项 5 - 值列）</span><span class="sxs-lookup"><span data-stu-id="1de80-299">The IPsec pre-shared key for the site-to-site VPN connection (Table V- Item 5 - Value column).</span></span>
    
<span data-ttu-id="1de80-300">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1de80-300">Here is your resulting configuration.</span></span>
  
![虚拟网络现已连接到本地网络。](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a><span data-ttu-id="1de80-302">阶段 3（可选）：添加虚拟机</span><span class="sxs-lookup"><span data-stu-id="1de80-302">Phase 3 (Optional): Add virtual machines</span></span>

<span data-ttu-id="1de80-p127">在 Azure 中创建所需的虚拟机。有关详细信息，请参阅[在 Azure 门户中创建 Windows 虚拟机](https://go.microsoft.com/fwlink/p/?LinkId=393098)。</span><span class="sxs-lookup"><span data-stu-id="1de80-p127">Create the virtual machines you need in Azure. For more information, see [Create a Windows virtual machine with the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span></span>
  
<span data-ttu-id="1de80-305">使用以下设置：</span><span class="sxs-lookup"><span data-stu-id="1de80-305">Use the following settings:</span></span>
  
- <span data-ttu-id="1de80-p128">在“基本信息”选项卡中，选择与虚拟网络相同的订阅和资源组。稍后将需要使用这些信息登录到虚拟机。在“实例详细信息”部分中，选择适当的虚拟机大小。在安全位置记录管理员帐户用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="1de80-p128">On the **Basics** tab, select the same subscription and resource group as your virtual network. You will need these later to sign in to the virtual machine. In the **Instance details** section, choose the appropriate virtual machine size. Record the administrator account user name and password in a secure location.</span></span> 
    
- <span data-ttu-id="1de80-p129">在“网络”选项卡中，选择虚拟网络的名称和托管虚拟机（非网关子网）的子网。将所有其他设置保留为其默认值。</span><span class="sxs-lookup"><span data-stu-id="1de80-p129">On the **Networking** tab, select the name of your virtual network and the subnet for hosting virtual machines (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="1de80-p130">请检查内部 DNS 验证虚拟机是否正确使用 DNS，确保已为新虚拟机添加地址 (A) 记录。要访问 Internet，必须将 Azure 虚拟机配置为使用本地网络的代理服务器。有关要在服务器上执行的其他配置步骤，请与网络管理员联系。</span><span class="sxs-lookup"><span data-stu-id="1de80-p130">Verify that your virtual machine is using DNS correctly by checking your internal DNS to ensure that Address (A) records were added for you new virtual machine. To access the Internet, your Azure virtual machines must be configured to use your on-premises network's proxy server. Contact your network administrator for additional configuration steps to perform on the server.</span></span>
  
<span data-ttu-id="1de80-315">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1de80-315">Here is your resulting configuration.</span></span>
  
![虚拟网络现在托管可从本地网络访问的虚拟机。](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a><span data-ttu-id="1de80-317">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1de80-317">Next step</span></span>
  
[<span data-ttu-id="1de80-318">在 Microsoft Azure 中部署 Microsoft 365 目录同步</span><span class="sxs-lookup"><span data-stu-id="1de80-318">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)