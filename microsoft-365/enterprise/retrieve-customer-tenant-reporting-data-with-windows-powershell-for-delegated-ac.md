---
title: 通过 DAP 合作伙伴的 Windows PowerShell检索客户租户报告数据
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 摘要：使用适用于 Microsoft Exchange Online 的远程 Windows PowerShell 从各个客户租户中检索报表。
ms.openlocfilehash: 8ea5f9834bfcc0d517fc1e0938c3547d88d1d8a8
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927212"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="316d3-103">通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据</span><span class="sxs-lookup"><span data-stu-id="316d3-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="316d3-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="316d3-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="316d3-105">使用远程Windows PowerShell Microsoft Exchange Online从单个客户租户检索报告。</span><span class="sxs-lookup"><span data-stu-id="316d3-105">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="316d3-106">联合和云解决方案提供商 (云解决方案提供商) 合作伙伴可以直接通过 Exchange Online PowerShell 的远程 Windows PowerShell访问客户租户报告的数据。</span><span class="sxs-lookup"><span data-stu-id="316d3-106">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remote Windows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="316d3-107">这样，合作伙伴可以收集并保存报告数据，然后对其执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="316d3-107">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="316d3-108">打开远程连接后，检索有关客户租赁的报告数据与在客户租赁中运行任何 cmdlet 的效果是一样的。</span><span class="sxs-lookup"><span data-stu-id="316d3-108">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="316d3-109">本文使用 Exchange Online Windows PowerShell远程租户连接到单个客户租赁并检索报告。</span><span class="sxs-lookup"><span data-stu-id="316d3-109">In this article, you use remote Windows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="316d3-110">默认情况下，Windows PowerShell 不支持聚合多个客户租赁中的报告数据。</span><span class="sxs-lookup"><span data-stu-id="316d3-110">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="316d3-111">通过此过程检索的报告仅适用于您连接到的  _DelegatedOrg_。</span><span class="sxs-lookup"><span data-stu-id="316d3-111">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="316d3-112">准备工作</span><span class="sxs-lookup"><span data-stu-id="316d3-112">Before you begin</span></span>

- <span data-ttu-id="316d3-p103">您需要使用远程 Windows PowerShell 连接到您的 Exchange Online 租户。有关说明，请参阅[通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户](/powershell/exchange/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="316d3-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](/powershell/exchange/connect-to-exchange-online-powershell)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="316d3-115">运行 Get-StaleMailboxReport 示例</span><span class="sxs-lookup"><span data-stu-id="316d3-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="316d3-116">打开到 Exchange Online 的远程会话后，运行此命令可检索日期范围 03/25/2015 到 03/31/2015 的 **Get-StaleMailboxReport** 。</span><span class="sxs-lookup"><span data-stu-id="316d3-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="316d3-p104">有许多其他报告 cmdlet 可用于 Exchange Online、Lync Online 和 SharePoint Online，还有其他报告 cmdlet 可用于您可以使用的邮件跟踪。若要了解有关可用的报告 cmdlet 和 Office 365 报告 Web 服务的详细信息，请参阅下一节中的主题。</span><span class="sxs-lookup"><span data-stu-id="316d3-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="316d3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="316d3-119">See also</span></span>

#### 

<span data-ttu-id="316d3-120">[Office 365 报告 Web 服务](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))</span><span class="sxs-lookup"><span data-stu-id="316d3-120">[Office 365 Reporting web service](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))</span></span>
  
[<span data-ttu-id="316d3-121">Exchange Online 中的报告 cmdlet</span><span class="sxs-lookup"><span data-stu-id="316d3-121">Reporting cmdlets in Exchange Online</span></span>](/powershell/module/exchange/get-csclientdevicedetailreport)
  
[<span data-ttu-id="316d3-122">适于合作伙伴的帮助</span><span class="sxs-lookup"><span data-stu-id="316d3-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)