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
description: 管理员可以了解如何使用安全与合规中心的邮件流仪表板中的"未接受的域"报告监视来自未在 Microsoft 365 中配置发件人域内部部署组织的邮件。 &
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6d7355af49c5810a593c5776b70cf7497b43af6b
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2021
ms.locfileid: "50287861"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a><span data-ttu-id="64064-103">安全与合规中心内&域报告</span><span class="sxs-lookup"><span data-stu-id="64064-103">Non-accepted domain report in the Security & Compliance Center</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="64064-104">**适用对象**</span><span class="sxs-lookup"><span data-stu-id="64064-104">**Applies to**</span></span>
- [<span data-ttu-id="64064-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="64064-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="64064-106">Microsoft Defender for Office 365 计划 1 和计划 2</span><span class="sxs-lookup"><span data-stu-id="64064-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](office-365-atp.md)
- [<span data-ttu-id="64064-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="64064-107">Microsoft 365 Defender</span></span>](../mtp/microsoft-threat-protection.md)

<span data-ttu-id="64064-108">安全与合规中心的邮件流仪表板中的[](mail-flow-insights-v2.md)"未接受域"报告显示有关来自内部部署电子邮件组织的邮件的信息，其中发件人的域未配置为 Microsoft 365 组织中接受的域。 [&](https://protection.office.com)</span><span class="sxs-lookup"><span data-stu-id="64064-108">The **Non-accepted domain** report in the [Mail flow dashboard](mail-flow-insights-v2.md) in the [Security & Compliance Center](https://protection.office.com) displays information about messages from your on-premises email organization where the sender's domain isn't configured as an accepted domain in your Microsoft 365 organization.</span></span>

<span data-ttu-id="64064-109">如果我们有数据可以证明这些邮件的意图是恶意的，Microsoft 365 可能会限制这些邮件。</span><span class="sxs-lookup"><span data-stu-id="64064-109">Microsoft 365 might throttle these messages if we have data to prove that the intent of these messages is malicious.</span></span> <span data-ttu-id="64064-110">因此，了解发生的情况并解决此问题非常重要。</span><span class="sxs-lookup"><span data-stu-id="64064-110">Therefore, it's important for you to understand what's happening and to fix the issue.</span></span>

![安全与合规中心中邮件流仪表板中的&小组件](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a><span data-ttu-id="64064-112">非接受域报告的报告视图</span><span class="sxs-lookup"><span data-stu-id="64064-112">Report view for the Non-accepted domain report</span></span>

<span data-ttu-id="64064-113">单击"非接受域 **"小部件上的** 图表将进入 **非接受域** 报告。</span><span class="sxs-lookup"><span data-stu-id="64064-113">Clicking the chart on the **Non-accepted domain** widget will take you to the **Non-accepted domain** report.</span></span>

<span data-ttu-id="64064-114">默认情况下，将显示所有受影响的连接器的活动。</span><span class="sxs-lookup"><span data-stu-id="64064-114">By default, the activity for all affected connectors is shown.</span></span> <span data-ttu-id="64064-115">如果单击 **"显示数据"，** 可以从下拉列表中选择特定连接器。</span><span class="sxs-lookup"><span data-stu-id="64064-115">If you click **Show data for**, you can select a specific connector from the dropdown.</span></span>

<span data-ttu-id="64064-116">如果将鼠标悬停在图表中 () 的数据点上，则会看到连接器的邮件总数。</span><span class="sxs-lookup"><span data-stu-id="64064-116">If you hover over a data point (day) in the chart, you'll see the total number of messages for the connector.</span></span>

![非接受域报告中的报告视图](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a><span data-ttu-id="64064-118">非接受域报告的详细信息表视图</span><span class="sxs-lookup"><span data-stu-id="64064-118">Details table view for the Non-accepted domain report</span></span>

<span data-ttu-id="64064-119">如果单击 **视图中的"** 查看详细信息报表视图，将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="64064-119">If you click **View details table** in a report view, the following information is shown:</span></span>

- <span data-ttu-id="64064-120">"日期"</span><span class="sxs-lookup"><span data-stu-id="64064-120">**Date**</span></span>
- <span data-ttu-id="64064-121">**入站连接器名称**</span><span class="sxs-lookup"><span data-stu-id="64064-121">**Inbound connector name**</span></span>
- <span data-ttu-id="64064-122">**发件人域**</span><span class="sxs-lookup"><span data-stu-id="64064-122">**Sender domain**</span></span>
- <span data-ttu-id="64064-123">**邮件计数**</span><span class="sxs-lookup"><span data-stu-id="64064-123">**Message count**</span></span>
- <span data-ttu-id="64064-124">**示例邮件**：受影响邮件示例的邮件的 ID。</span><span class="sxs-lookup"><span data-stu-id="64064-124">**Sample messages**: The message IDs of a sample of affected messages.</span></span>

<span data-ttu-id="64064-125">如果在 **详细信息表** 视图中单击"筛选器"，可以指定开始日期和 **结束日期的日期范围**。 </span><span class="sxs-lookup"><span data-stu-id="64064-125">If you click **Filters** in a details table view, you can specify a date range with **Start date** and **End date**.</span></span>

<span data-ttu-id="64064-126">若要将特定日期范围的报告通过电子邮件发送给一个或多个收件人，请单击"请求 **下载"。**</span><span class="sxs-lookup"><span data-stu-id="64064-126">To email the report for a specific date range to one or more recipients, click **Request download**.</span></span>

<span data-ttu-id="64064-127">在表中选择一行时，将出现一个包含以下信息的飞出图：</span><span class="sxs-lookup"><span data-stu-id="64064-127">When you select a row in the table, a flyout appears with the following information:</span></span>

- <span data-ttu-id="64064-128">"日期"</span><span class="sxs-lookup"><span data-stu-id="64064-128">**Date**</span></span>
- <span data-ttu-id="64064-129">**入站连接器名称**</span><span class="sxs-lookup"><span data-stu-id="64064-129">**Inbound connector name**</span></span>
- <span data-ttu-id="64064-130">**发件人域**</span><span class="sxs-lookup"><span data-stu-id="64064-130">**Sender domain**</span></span>
- <span data-ttu-id="64064-131">**邮件计数**</span><span class="sxs-lookup"><span data-stu-id="64064-131">**Message count**</span></span>
- <span data-ttu-id="64064-132">**示例邮件**：可以单击 **"查看示例邮件**"以查看受影响 [](message-trace-scc.md)邮件示例的邮件跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="64064-132">**Sample messages**: You can click **View sample messages** to see the [message trace](message-trace-scc.md) results for a sample of the affected messages.</span></span>

![在"非接受域"报告中的"详细信息"表视图中选择行后的详细信息飞出](../../media/mfi-non-accepted-domain-report-details-flyout.png)

<span data-ttu-id="64064-134">若要返回到报告视图，请单击"**查看报告"。**</span><span class="sxs-lookup"><span data-stu-id="64064-134">To go back to the reports view, click **View report**.</span></span>

## <a name="related-topics"></a><span data-ttu-id="64064-135">相关主题</span><span class="sxs-lookup"><span data-stu-id="64064-135">Related topics</span></span>

<span data-ttu-id="64064-136">有关邮件流仪表板中其他见解的信息，请参阅安全与合规中心& [见解](mail-flow-insights-v2.md)。</span><span class="sxs-lookup"><span data-stu-id="64064-136">For information about other insights in the Mail flow dashboard, see [Mail flow insights in the Security & Compliance Center](mail-flow-insights-v2.md).</span></span>
