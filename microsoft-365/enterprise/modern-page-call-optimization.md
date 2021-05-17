---
title: 在 SharePoint Online 新式发布网页和经典发布网页中优化页面调用
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 了解如何通过限制到 SharePoint Online 服务终结点的调用数量来优化 SharePoint Online 中的新式和经典发布网页。
ms.openlocfilehash: cab0f6a020bd1148a0e852b5a393a6ad907f9771
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50921614"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="40c1a-103">在 SharePoint Online 新式发布网页和经典发布网页中优化页面调用</span><span class="sxs-lookup"><span data-stu-id="40c1a-103">Optimize page calls in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="40c1a-104">SharePoint Online 新式和经典发布网页都包含从 SharePoint 功能和 CDN 加载数据（或对其进行调用）的链接。</span><span class="sxs-lookup"><span data-stu-id="40c1a-104">Both SharePoint Online modern and classic publishing sites contain links that load data from (or make calls to) SharePoint features and CDNs.</span></span> <span data-ttu-id="40c1a-105">页面调用次数越多，页面加载所耗时间越长。</span><span class="sxs-lookup"><span data-stu-id="40c1a-105">The more calls made by a page, the longer the page takes to load.</span></span> <span data-ttu-id="40c1a-106">这称为 **最终用户感知延迟** (**EUPL**)。</span><span class="sxs-lookup"><span data-stu-id="40c1a-106">This is known as **end user perceived latency** or **EUPL**.</span></span>

<span data-ttu-id="40c1a-107">本文将帮助你了解如何确定从新式和经典发布网页调用外部终结点的次数及所造成的影响，以及如何限制其对最终用户感知延迟的影响。</span><span class="sxs-lookup"><span data-stu-id="40c1a-107">This article will help you understand how to determine the number and impact of calls to external endpoints from your modern and classic publishing site pages and how to limit their effect on end user perceived latency.</span></span>

>[!NOTE]
><span data-ttu-id="40c1a-108">要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](/sharepoint/modern-experience-performance)。</span><span class="sxs-lookup"><span data-stu-id="40c1a-108">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a><span data-ttu-id="40c1a-109">使用适用于 SharePoint 的页面诊断工具分析页面调用</span><span class="sxs-lookup"><span data-stu-id="40c1a-109">Use the Page Diagnostics for SharePoint tool to analyze page calls</span></span>

<span data-ttu-id="40c1a-110">适用于 SharePoint 的页面诊断工具是一款面向新 Microsoft Edge（https://www.microsoft.com/edge) 和 Chrome 浏览器）的浏览器扩展，可用于分析 SharePoint Online 新式门户和经典发布网站页面。</span><span class="sxs-lookup"><span data-stu-id="40c1a-110">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="40c1a-111">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="40c1a-111">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="40c1a-112">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="40c1a-112">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="40c1a-113">页面诊断工具仅适用于 SharePoint Online，无法在 SharePoint 系统页面上使用。</span><span class="sxs-lookup"><span data-stu-id="40c1a-113">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="40c1a-114">通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网页时，可在“_诊断测试_”窗格的“**对 SharePoint 的请求**”结果中查看外部调用相关信息。</span><span class="sxs-lookup"><span data-stu-id="40c1a-114">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about external calls in the **Requests to SharePoint** result in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="40c1a-115">如果网页包含的调用低于基线数量，则该行显示为绿色；如果页面超过基线数量，则显示为红色。</span><span class="sxs-lookup"><span data-stu-id="40c1a-115">The line will appear in green if the site page contains fewer than the baseline number of calls, and red if the page exceeds the baseline number.</span></span> <span data-ttu-id="40c1a-116">新式页面和经典页面的基线数量不相同，因为经典网页使用 HTTP1.1，而新式页面使用 HTTP2.0：</span><span class="sxs-lookup"><span data-stu-id="40c1a-116">The baseline number is different for modern and classic pages because classic site pages use HTTP1.1 and modern pages use HTTP2.0:</span></span>

- <span data-ttu-id="40c1a-117">新式网页包含的调用不得超过 **25** 次。</span><span class="sxs-lookup"><span data-stu-id="40c1a-117">Modern site pages should contain no more than **25** calls</span></span>
- <span data-ttu-id="40c1a-118">经典发布页面包含的调用不得超过 **6** 次。</span><span class="sxs-lookup"><span data-stu-id="40c1a-118">Classic publishing pages should contain no more than **6** calls</span></span>

<span data-ttu-id="40c1a-119">可能的结果包括：</span><span class="sxs-lookup"><span data-stu-id="40c1a-119">Possible results include:</span></span>

- <span data-ttu-id="40c1a-120">**需要注意**（红色）：页面超过调用的基线数量</span><span class="sxs-lookup"><span data-stu-id="40c1a-120">**Attention required** (red): The page exceeds the baseline number of calls</span></span>
- <span data-ttu-id="40c1a-121">**需要注意**（绿色）：页面包含的调用低于基线数量</span><span class="sxs-lookup"><span data-stu-id="40c1a-121">**No action required** (green): The page contains fewer than the baseline number of calls</span></span>

<span data-ttu-id="40c1a-122">如果“**需要注意**”部分中显示“**对 SharePoint 的请求**”，可单击结果了解详细信息，例如页面上调用总数和 URL 列表。</span><span class="sxs-lookup"><span data-stu-id="40c1a-122">If the **Requests to SharePoint** result appears in the **Attention required** section, you can click the result for details, including the total number of calls on the page and a list of the URLs.</span></span>

![对 SharePoint 的请求结果](../media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a><span data-ttu-id="40c1a-124">修正与页面上调用过多相关的性能问题</span><span class="sxs-lookup"><span data-stu-id="40c1a-124">Remediate performance issues related to too many calls on a page</span></span>

<span data-ttu-id="40c1a-125">如果页面包含太多调用，可在“**对 Sharepoint 的请求**”结果中使用 URL 列表，以确定是否有任何重复的调用、应批处理的调用或返回应缓存的数据的调用。</span><span class="sxs-lookup"><span data-stu-id="40c1a-125">If a page contains too many calls, you can use the list of URLs in the **Requests to Sharepoint** results to determine whether there are any repeated calls, calls that should be batched, or calls that return data that should be cached.</span></span>

<span data-ttu-id="40c1a-126">“**批处理 REST 调用**”可帮助减少性能开销。</span><span class="sxs-lookup"><span data-stu-id="40c1a-126">**Batching REST calls** can help to reduce performance overhead.</span></span> <span data-ttu-id="40c1a-127">要详细了解 API 调用批处理，请参阅[使用 REST API 进行批处理请求](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis)。</span><span class="sxs-lookup"><span data-stu-id="40c1a-127">For more information about API call batching, see [Make batch requests with the REST APIs](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).</span></span>

<span data-ttu-id="40c1a-128">通过 **使用缓存** 来存储 API 调用的结果，让客户端能够使用缓存的数据而不是对每个后续页面加载进行额外的调用，从而提升热请求的性能。</span><span class="sxs-lookup"><span data-stu-id="40c1a-128">**Using a cache** to store the results of an API call can improve the performance of a warm request by allowing the client to use the cached data instead of making an additional call for each subsequent page load.</span></span> <span data-ttu-id="40c1a-129">可通过多种方法，根据业务要求处理此解决方案。</span><span class="sxs-lookup"><span data-stu-id="40c1a-129">There are multiple ways to approach this solution depending on the business requirement.</span></span> <span data-ttu-id="40c1a-130">通常情况下，如果数据对所有用户都一样，很好的选择是使用 [_Azure Redis_ 缓存](https://azure.microsoft.com/services/cache/)等中间层缓存服务来显著减少对网站的 API 流量，因为用户会从缓存服务中请求数据，而不是直接从 SPO 中请求。</span><span class="sxs-lookup"><span data-stu-id="40c1a-130">Typically if the data will be the same for all users, using a middle-tier caching service like [_Azure Redis_ cache](https://azure.microsoft.com/services/cache/) is a great option to significantly reduce API traffic against a site, as the users would request the data from the caching service instead of directly from SPO.</span></span> <span data-ttu-id="40c1a-131">唯一需要的 SPO 调用就是刷新中间层的缓存。</span><span class="sxs-lookup"><span data-stu-id="40c1a-131">The only SPO calls needed would be to refresh the middle-tier's cache.</span></span> <span data-ttu-id="40c1a-132">如果每个用户的数据不同，则最好是实现客户端缓存，例如 LocalStorage 或甚至是 Cookie。</span><span class="sxs-lookup"><span data-stu-id="40c1a-132">If the data will fluctuate on an individual user basis, it may be best to implement a client side cache, like LocalStorage or even a Cookie.</span></span> <span data-ttu-id="40c1a-133">这样，同一用户无需在缓存持续时间内发出后续请求，从而减少调用量，但与专用缓存服务相比效率更低。</span><span class="sxs-lookup"><span data-stu-id="40c1a-133">This will still reduce call volumes by eliminating subsequent requests made by the same user for the cache duration, but will be less efficient than a dedicated caching service.</span></span> <span data-ttu-id="40c1a-134">借助 PnP，几乎无需额外的开发即可使用 LocalStorage。</span><span class="sxs-lookup"><span data-stu-id="40c1a-134">PnP allows you to use LocalStorage with little additional development required.</span></span>

<span data-ttu-id="40c1a-135">在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="40c1a-135">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="40c1a-136">修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。</span><span class="sxs-lookup"><span data-stu-id="40c1a-136">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![页面加载时间结果](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="40c1a-138">页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。</span><span class="sxs-lookup"><span data-stu-id="40c1a-138">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="40c1a-139">应在更改前后多次测试页面加载时间，以帮助求出结果平均值。</span><span class="sxs-lookup"><span data-stu-id="40c1a-139">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="40c1a-140">相关主题</span><span class="sxs-lookup"><span data-stu-id="40c1a-140">Related topics</span></span>

[<span data-ttu-id="40c1a-141">优化 SharePoint Online 性能</span><span class="sxs-lookup"><span data-stu-id="40c1a-141">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="40c1a-142">优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="40c1a-142">Tune Office 365 performance</span></span>](tune-microsoft-365-performance.md)

[<span data-ttu-id="40c1a-143">新式 SharePoint 体验中的性能</span><span class="sxs-lookup"><span data-stu-id="40c1a-143">Performance in the modern SharePoint experience</span></span>](/sharepoint/modern-experience-performance)

[<span data-ttu-id="40c1a-144">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="40c1a-144">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="40c1a-145">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="40c1a-145">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-microsoft-365-cdn-with-spo.md)