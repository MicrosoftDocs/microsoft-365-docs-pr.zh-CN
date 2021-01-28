---
title: 邮件流仪表板中的未接受域报告
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: 管理员可以了解如何使用安全 & 合规中心的邮件流仪表板中的"非接受域"报告监视来自内部部署组织的邮件，其中发件人的域未在 Microsoft 365 中配置。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 401d566158ca3f730af94fab60c471484e244a16
ms.sourcegitcommit: 537e513a4a232a01e44ecbc76d86a8bcaf142482
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/27/2021
ms.locfileid: "50029842"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a><span data-ttu-id="c04f0-103">安全与合规中心中的&报告</span><span class="sxs-lookup"><span data-stu-id="c04f0-103">Non-accepted domain report in the Security & Compliance Center</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="c04f0-104">安全与合规中心的邮件流仪表板中的[](mail-flow-insights-v2.md)"非接受域"报告显示有关来自内部部署电子邮件组织的邮件的信息，其中发件人的域未配置为 Microsoft 365 组织中接受的域。 [&](https://protection.office.com)</span><span class="sxs-lookup"><span data-stu-id="c04f0-104">The **Non-accepted domain** report in the [Mail flow dashboard](mail-flow-insights-v2.md) in the [Security & Compliance Center](https://protection.office.com) displays information about messages from your on-premises email organization where the sender's domain isn't configured as an accepted domain in your Microsoft 365 organization.</span></span>

<span data-ttu-id="c04f0-105">如果我们有数据可以证明这些邮件的意图是恶意的，Microsoft 365 可能会限制这些邮件。</span><span class="sxs-lookup"><span data-stu-id="c04f0-105">Microsoft 365 might throttle these messages if we have data to prove that the intent of these messages is malicious.</span></span> <span data-ttu-id="c04f0-106">因此，了解发生的情况并解决该问题非常重要。</span><span class="sxs-lookup"><span data-stu-id="c04f0-106">Therefore, it's important for you to understand what's happening and to fix the issue.</span></span>

![安全与合规中心的邮件流仪表板中的"非接受&小组件](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a><span data-ttu-id="c04f0-108">非接受域报告的报告视图</span><span class="sxs-lookup"><span data-stu-id="c04f0-108">Report view for the Non-accepted domain report</span></span>

<span data-ttu-id="c04f0-109">单击"非接受 **域"小部件上的** 图表将进入 **非接受域** 报告。</span><span class="sxs-lookup"><span data-stu-id="c04f0-109">Clicking the chart on the **Non-accepted domain** widget will take you to the **Non-accepted domain** report.</span></span>

<span data-ttu-id="c04f0-110">默认情况下，将显示所有受影响的连接器的活动。</span><span class="sxs-lookup"><span data-stu-id="c04f0-110">By default, the activity for all affected connectors is shown.</span></span> <span data-ttu-id="c04f0-111">如果单击 **"显示数据"，** 可以从下拉列表中选择特定连接器。</span><span class="sxs-lookup"><span data-stu-id="c04f0-111">If you click **Show data for**, you can select a specific connector from the dropdown.</span></span>

<span data-ttu-id="c04f0-112">如果将鼠标悬停在 () 的数据点上，你将看到连接器的邮件总数。</span><span class="sxs-lookup"><span data-stu-id="c04f0-112">If you hover over a data point (day) in the chart, you'll see the total number of messages for the connector.</span></span>

![非接受域报告中的报告视图](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a><span data-ttu-id="c04f0-114">非接受域报告的详细信息表视图</span><span class="sxs-lookup"><span data-stu-id="c04f0-114">Details table view for the Non-accepted domain report</span></span>

<span data-ttu-id="c04f0-115">如果单击 **视图中的"** 查看详细信息报表视图，将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="c04f0-115">If you click **View details table** in a report view, the following information is shown:</span></span>

- <span data-ttu-id="c04f0-116">"日期"</span><span class="sxs-lookup"><span data-stu-id="c04f0-116">**Date**</span></span>
- <span data-ttu-id="c04f0-117">**入站连接器名称**</span><span class="sxs-lookup"><span data-stu-id="c04f0-117">**Inbound connector name**</span></span>
- <span data-ttu-id="c04f0-118">**发件人域**</span><span class="sxs-lookup"><span data-stu-id="c04f0-118">**Sender domain**</span></span>
- <span data-ttu-id="c04f0-119">**邮件计数**</span><span class="sxs-lookup"><span data-stu-id="c04f0-119">**Message count**</span></span>
- <span data-ttu-id="c04f0-120">**示例邮件**：受影响邮件示例的邮件 ID。</span><span class="sxs-lookup"><span data-stu-id="c04f0-120">**Sample messages**: The message IDs of a sample of affected messages.</span></span>

<span data-ttu-id="c04f0-121">如果在 **详细信息表** 视图中单击"筛选器"，可以指定开始日期和 **结束日期的日期范围**。 </span><span class="sxs-lookup"><span data-stu-id="c04f0-121">If you click **Filters** in a details table view, you can specify a date range with **Start date** and **End date**.</span></span>

<span data-ttu-id="c04f0-122">若要将特定日期范围的报告通过电子邮件发送给一个或多个收件人，请单击"请求 **下载"。**</span><span class="sxs-lookup"><span data-stu-id="c04f0-122">To email the report for a specific date range to one or more recipients, click **Request download**.</span></span>

<span data-ttu-id="c04f0-123">当您在表中选择一行时，将显示一个包含以下信息的飞出图：</span><span class="sxs-lookup"><span data-stu-id="c04f0-123">When you select a row in the table, a flyout appears with the following information:</span></span>

- <span data-ttu-id="c04f0-124">"日期"</span><span class="sxs-lookup"><span data-stu-id="c04f0-124">**Date**</span></span>
- <span data-ttu-id="c04f0-125">**入站连接器名称**</span><span class="sxs-lookup"><span data-stu-id="c04f0-125">**Inbound connector name**</span></span>
- <span data-ttu-id="c04f0-126">**发件人域**</span><span class="sxs-lookup"><span data-stu-id="c04f0-126">**Sender domain**</span></span>
- <span data-ttu-id="c04f0-127">**邮件计数**</span><span class="sxs-lookup"><span data-stu-id="c04f0-127">**Message count**</span></span>
- <span data-ttu-id="c04f0-128">**示例邮件**：可以单击 **"查看示例邮件** " [以查看受影响邮件](message-trace-scc.md) 示例的邮件跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="c04f0-128">**Sample messages**: You can click **View sample messages** to see the [message trace](message-trace-scc.md) results for a sample of the affected messages.</span></span>

![在"未接受域"报告中的"详细信息"表视图中选择行后的详细信息飞出](../../media/mfi-non-accepted-domain-report-details-flyout.png)

<span data-ttu-id="c04f0-130">若要返回到报告视图，请单击"**查看报告"。**</span><span class="sxs-lookup"><span data-stu-id="c04f0-130">To go back to the reports view, click **View report**.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c04f0-131">相关主题</span><span class="sxs-lookup"><span data-stu-id="c04f0-131">Related topics</span></span>

<span data-ttu-id="c04f0-132">有关邮件流仪表板中其他见解的信息，请参阅安全与合规中心& [见解](mail-flow-insights-v2.md)。</span><span class="sxs-lookup"><span data-stu-id="c04f0-132">For information about other insights in the Mail flow dashboard, see [Mail flow insights in the Security & Compliance Center](mail-flow-insights-v2.md).</span></span>
