---
title: 在 SharePoint Online 新式网页上优化页面权重
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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: 了解如何使用页面诊断工具在 SharePoint Online 新式网站页面中优化页面权重。
ms.openlocfilehash: 64fb3c90db78a23c7f1c3fcfe604c8ef58703be0
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687637"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="2e9fe-103">在 SharePoint Online 新式网页上优化页面权重</span><span class="sxs-lookup"><span data-stu-id="2e9fe-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="2e9fe-104">SharePoint Online 新式网页包括呈现导航/命令栏下内容区域中的图像、文本和对象等页面内容所需的序列化代码，还包括形成页面框架的其他 HTML 代码。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="2e9fe-105">页面权重是此 HTML 代码的一种度量，且应限制来确保最佳页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="2e9fe-106">本文将帮助你了解如何减少新式页面中的页面权重。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="2e9fe-107">要详细了解 SharePoint Online 新式门户中的性能，请参阅[新式 SharePoint 体验中的性能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="2e9fe-108">使用适用于 SharePoint 的页面诊断工具分析页面权重</span><span class="sxs-lookup"><span data-stu-id="2e9fe-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="2e9fe-109">适用于 SharePoint 的页面诊断工具是一款面向新 Microsoft Edge (https://www.microsoft.com/edge)) 和 Chrome 浏览器的浏览器扩展，可用于分析 SharePoint Online 新式门户和经典发布网站页面。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-109">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="2e9fe-110">该工具对已分配的每个页面提供一个报告，其中显示根据一组定义的性能条件得出的页面性能情况。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="2e9fe-111">要安装和了解适用于 SharePoint 的页面诊断工具，请参阅[使用适用于 SharePoint Online 的页面诊断工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="2e9fe-112">页面诊断工具仅适用于 SharePoint Online，无法用于 SharePoint 系统页面。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-112">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="2e9fe-113">通过适用于 SharePoint 的页面诊断工具分析 SharePoint 网页时，可在“_诊断测试_”窗格的“\*\*页面权重小于 500KB \*\*”结果中查看页面相关信息。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-113">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="2e9fe-114">如果页面权重低于基线值，则结果将显示为绿色；如果页面权重大于基线值，则结果显示为红色。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-114">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="2e9fe-115">可能的结果包括：</span><span class="sxs-lookup"><span data-stu-id="2e9fe-115">Possible results include:</span></span>

- <span data-ttu-id="2e9fe-116">**需要注意**（红色）：页面权重大于 500KB</span><span class="sxs-lookup"><span data-stu-id="2e9fe-116">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="2e9fe-117">**无需操作**（绿色）：页面权重小于 500KB</span><span class="sxs-lookup"><span data-stu-id="2e9fe-117">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="2e9fe-118">如果“**需要注意**”部分中显示“**页面权重小于 500KB**”结果，则可单击结果了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-118">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![SharePoint 结果请求](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="2e9fe-120">修正页面权重问题</span><span class="sxs-lookup"><span data-stu-id="2e9fe-120">Remediate page weight issues</span></span>

<span data-ttu-id="2e9fe-121">如果页面权重大于 500KB，可通过减少 Web 部件数量并将页面内容限制到适当程度，缩短整体页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-121">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="2e9fe-122">有关减少页面权重的一般指南包括：</span><span class="sxs-lookup"><span data-stu-id="2e9fe-122">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="2e9fe-123">将页面内容限制到适当的量，并使用多个页面显示相关内容。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-123">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="2e9fe-124">尽可能少地使用具有大量属性包的 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-124">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="2e9fe-125">尽可能地使用非交互式汇总视图。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-125">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="2e9fe-126">通过适当设置图像大小、使用压缩后的图像格式并确保其下载自 CDN，优化图像大小。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-126">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="2e9fe-127">可在以下文章中找到有关限制权重的其他指南：</span><span class="sxs-lookup"><span data-stu-id="2e9fe-127">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="2e9fe-128">优化 SharePoint 中的页面性能</span><span class="sxs-lookup"><span data-stu-id="2e9fe-128">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="2e9fe-129">在修改页面来修正性能问题之前，请在分析结果中记下页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-129">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="2e9fe-130">修改后再次运行工具，查看新结果是否在基线标准范围内，同时检查新的页面加载时间，查看是否有提升。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-130">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![页面加载时间结果](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="2e9fe-132">页面加载时间可能由于网络加载、具体时间和其他暂时条件等各种因素而有所不同。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-132">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="2e9fe-133">应在更改前后多次测试页面加载时间，以帮助求出结果平均值。</span><span class="sxs-lookup"><span data-stu-id="2e9fe-133">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="2e9fe-134">相关主题</span><span class="sxs-lookup"><span data-stu-id="2e9fe-134">Related topics</span></span>

[<span data-ttu-id="2e9fe-135">优化 SharePoint Online 性能</span><span class="sxs-lookup"><span data-stu-id="2e9fe-135">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="2e9fe-136">优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="2e9fe-136">Tune Office 365 performance</span></span>](tune-microsoft-365-performance.md)

[<span data-ttu-id="2e9fe-137">新式 SharePoint 体验中的性能</span><span class="sxs-lookup"><span data-stu-id="2e9fe-137">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="2e9fe-138">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="2e9fe-138">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="2e9fe-139">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2e9fe-139">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-microsoft-365-cdn-with-spo.md)
