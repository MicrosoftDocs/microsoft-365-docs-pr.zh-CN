---
title: Office 365 服务中的 IPv6 支持
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 摘要：介绍了 Microsoft Office 365 组件和 Office 365 政府产品中的 IPv6 支持。
ms.openlocfilehash: f671e8caf868ebbed628a155b73ce6fe413949a9
ms.sourcegitcommit: c1ee4ed3c5826872b57339e1e1aa33b4d2209711
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "48235602"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="3869c-103">Office 365 服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="3869c-103">IPv6 support in Office 365 services</span></span>

<span data-ttu-id="3869c-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="3869c-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="3869c-105">Office 365 支持 IPv6 和 IPv4;但是，并不是所有的 Office 365 功能都完全启用了 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-105">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6.</span></span> <span data-ttu-id="3869c-106">这意味着，您必须同时使用 IPv4 和 IPv6 连接到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3869c-106">This means that you must use both IPv4 and IPv6 to connect to Office 365.</span></span> <span data-ttu-id="3869c-107">如果要筛选出出到 Office 365 的出站流量，则可以在 [office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)一文中找到 office 365 支持的 IPv6 地址的完整列表。</span><span class="sxs-lookup"><span data-stu-id="3869c-107">If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span> <span data-ttu-id="3869c-108">配置网络并允许适当的 IPv6 地址后，可以从 Microsoft 下载中心下载 [Office 365 IPv6 测试计划](https://go.microsoft.com/fwlink/?LinkId=293447) 。</span><span class="sxs-lookup"><span data-stu-id="3869c-108">After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="3869c-109">Office 365 订阅服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="3869c-109">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="3869c-110">Exchange Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="3869c-110">Exchange Online and IPv6</span></span>

<span data-ttu-id="3869c-111">如果用于连接到 Exchange Online 的程序支持 IPv6，则它将在有线网络和无线网络上默认使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-111">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="3869c-112">如果要控制与 Exchange Online 的通信，请使用 [Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)中的 IP 地址范围。</span><span class="sxs-lookup"><span data-stu-id="3869c-112">If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="3869c-113">SharePoint Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="3869c-113">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="3869c-114">**Office 365 政府 G1/G3/G4/K1** 如果用于连接到 SharePoint Online 的程序支持 IPv6，则默认情况下它将尝试使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-114">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="3869c-115">**公用多租户云** Microsoft 在你的请求中启用 SharePoint Online IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-115">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request.</span></span> <span data-ttu-id="3869c-116">您需要为您的组织的 DNS 基础结构提供 CIDR 表示的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3869c-116">You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure.</span></span> <span data-ttu-id="3869c-117">请记住，其他组织无法共享此 DNS 基础结构，以便对租户启用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-117">Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant.</span></span> <span data-ttu-id="3869c-118">启用 IPv6 之后，如果用于连接到 SharePoint Online 的程序支持 IPv6，则默认情况下它使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-118">After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="3869c-119">如果用于连接到 SharePoint Online 的程序支持 IPv6，则它将在有线网络和无线网络上默认使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-119">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="3869c-120">如果要控制与 SharePoint Online 的通信，请使用 [Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)中的 IP 地址范围。</span><span class="sxs-lookup"><span data-stu-id="3869c-120">If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="3869c-121">**Office 365 政府 G1/G3/G4/K1** 如果用于连接到 SharePoint Online 的程序支持 IPv6，则默认情况下它将尝试使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-121">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="3869c-122">Skype for Business 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="3869c-122">Skype for Business and IPv6</span></span>

<span data-ttu-id="3869c-123">请注意，Ipv4 在 Skype for Business 中不受支持，无法再启用。</span><span class="sxs-lookup"><span data-stu-id="3869c-123">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>

### <a name="microsoft-teams-and-ipv6"></a><span data-ttu-id="3869c-124">Microsoft 团队和 IPV6</span><span class="sxs-lookup"><span data-stu-id="3869c-124">Microsoft Teams and IPV6</span></span>

<span data-ttu-id="3869c-125">Microsoft 团队直接路由仅支持 IPv4。</span><span class="sxs-lookup"><span data-stu-id="3869c-125">Microsoft Teams Direct Routing only supports IPv4.</span></span> <span data-ttu-id="3869c-126">Microsoft 团队服务和客户端支持 IPv4 和 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-126">The Microsoft Teams service and client support both IPv4 and IPv6.</span></span> <span data-ttu-id="3869c-127">如果要控制与 Microsoft 团队的通信，请使用 [Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)中的 IP 地址范围。</span><span class="sxs-lookup"><span data-stu-id="3869c-127">If you want to control communications to Microsoft Teams, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="3869c-128">Exchange Online Protection 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="3869c-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="3869c-129">Exchange Online Protection (EOP) 在传输层安全协议进行传输时支持 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-129">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol.</span></span> <span data-ttu-id="3869c-130">对于 EOP 范围，请使用 [Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="3869c-130">For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="3869c-131">适用于 Office 365 政府产品的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="3869c-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="3869c-132">适用于政府产品的 office 365 IPv6 支持符合管理人员和预算 (OMB) 备忘录，以实现管理部门和机构的首席信息官，以及联邦政府采用 Internet 协议版本 6 (IPv6) 备忘录。</span><span class="sxs-lookup"><span data-stu-id="3869c-132">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum.</span></span> <span data-ttu-id="3869c-133">[Microsoft Office 365 For 政府](https://go.microsoft.com/fwlink/p/?LinkId=325414) 是一项多租户服务，可将美国政府数据存储在隔离的社区云中。</span><span class="sxs-lookup"><span data-stu-id="3869c-133">[Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud.</span></span> <span data-ttu-id="3869c-134">与其他 Office 365 产品一样，它提供了工作效率和协作服务，包括 Exchange Online、Skype for Business、SharePoint Online 和适用于企业的 Microsoft 365 应用。</span><span class="sxs-lookup"><span data-stu-id="3869c-134">Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Microsoft 365 Apps for enterprise.</span></span> 

<span data-ttu-id="3869c-135">Microsoft Office 365 政府版产品仅适用于2013及更高版本。</span><span class="sxs-lookup"><span data-stu-id="3869c-135">The Microsoft Office 365 government offerings apply only for 2013 and later.</span></span> <span data-ttu-id="3869c-136">有关 Office 365 政府版产品的详细信息，请参阅 [宣布 office 365 For 政府： A 美国政府社区云](https://go.microsoft.com/fwlink/p/?LinkId=325414)。</span><span class="sxs-lookup"><span data-stu-id="3869c-136">For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414).</span></span> <span data-ttu-id="3869c-137">Arm 规章中的国际流量 (ITAR) 是一组美国政府管理法规，可控制 [美国 Munitions 列表 (USML) ](https://go.microsoft.com/fwlink/p/?LinkId=325415)中的防御相关文章和服务的导出和导入。</span><span class="sxs-lookup"><span data-stu-id="3869c-137">International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="3869c-138">适用于企业的 microsoft Office 365 为 Microsoft 工作效率解决方案提供专用的托管服务，这些服务支持要求联邦信息安全管理 (FISMA) 认证和商业实体受 ITAR 支持的美国联邦机构的安全、隐私和法规遵从性要求。</span><span class="sxs-lookup"><span data-stu-id="3869c-138">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="3869c-139">使用 IPv6 和 Office 365 时需要考虑的事项</span><span class="sxs-lookup"><span data-stu-id="3869c-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="3869c-140">我们建议您不要禁用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-140">We recommend that you do not disable IPv6.</span></span> <span data-ttu-id="3869c-141">有关详细信息，请参阅本 [指南文章](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)。</span><span class="sxs-lookup"><span data-stu-id="3869c-141">For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users).</span></span> <span data-ttu-id="3869c-142">若要确定网络中使用的 IP 版本，请考虑以下事项：</span><span class="sxs-lookup"><span data-stu-id="3869c-142">To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="3869c-143">如果命令提示符处的 **IPConfig** 命令的显示包含名为 "IPv6 地址" 或 "临时 IPv6 地址" 的行，则您的环境中有 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-143">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="3869c-144">如果所有 IPv6 地址都以 "fe80" 开头，并且对应于名为 "Link Local IPv6 Address" 的行，则您的环境中没有 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="3869c-145">这些注意事项可能适用于您的网络：</span><span class="sxs-lookup"><span data-stu-id="3869c-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="3869c-146">公共订阅服务不支持通过 IPv6 通过信用卡购买。</span><span class="sxs-lookup"><span data-stu-id="3869c-146">The public subscription service does not support purchase by credit card over IPv6.</span></span> <span data-ttu-id="3869c-147">此功能不适用于政府社区云 (GCC) ，因为政府拥有企业协议 (EA) 许可。</span><span class="sxs-lookup"><span data-stu-id="3869c-147">This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="3869c-148">IPv6 不支持 (RMS) 方案的某些权限管理服务。</span><span class="sxs-lookup"><span data-stu-id="3869c-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="3869c-149">IPv6 不支持 BlackBerry® Enterprise Server (BE) ，因为 BlackBerry 不支持 IPv6。</span><span class="sxs-lookup"><span data-stu-id="3869c-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="3869c-150">如果使用 Active Directory 联合身份验证服务 (AD FS) 与 Office 365，则不支持使用 IPv6 将 AD FS 网络终结点公布到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3869c-150">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported.</span></span> <span data-ttu-id="3869c-151">使用 Exchange Online 时，不应在 AD FS DNS 条目中包含 AAAA 记录。</span><span class="sxs-lookup"><span data-stu-id="3869c-151">You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="3869c-152">以下是可以用于返回的简短链接：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="3869c-152">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3869c-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3869c-153">See also</span></span>

<span data-ttu-id="3869c-154">[IPv6 学习路线图](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="3869c-154">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="3869c-155">IPv6 生存指南</span><span class="sxs-lookup"><span data-stu-id="3869c-155">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
