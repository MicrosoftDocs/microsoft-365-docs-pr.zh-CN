---
title: 使用解决方案管理Microsoft 365合同
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: 05/10/2021
ms.prod: microsoft-365-enterprise
ms.collection: m365solution-managecontracts
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: 了解如何使用 Syntex、Microsoft 365 和 SharePoint 的 Microsoft Teams 解决方案管理Power Automate。
ms.openlocfilehash: 806ea9fd048dec198a19fa79f3b60f3f3cb81018
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "52281081"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a><span data-ttu-id="d85cb-103">使用解决方案管理Microsoft 365合同</span><span class="sxs-lookup"><span data-stu-id="d85cb-103">Manage contracts using a Microsoft 365 solution</span></span>

<span data-ttu-id="d85cb-104">本文介绍如何使用组织的 Syntex 和 SharePoint 组件为组织创建Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="d85cb-104">This article describes how to create a contracts management solution for your organization by using SharePoint Syntex and components of Microsoft 365.</span></span> <span data-ttu-id="d85cb-105">它提供了一个框架，可帮助你计划和创建满足你独特业务需求的解决方案。</span><span class="sxs-lookup"><span data-stu-id="d85cb-105">It provides you with a framework to help you plan and create a solution that fits your unique business needs.</span></span> <span data-ttu-id="d85cb-106">即使此解决方案不满足您的整体业务需求，也可以将该解决方案的某些部分用于创建自定义合同管理解决方案。</span><span class="sxs-lookup"><span data-stu-id="d85cb-106">Even if this solution doesn't suit your business needs as a whole, parts of it can be adopted in your planning to create a custom contract management solution.</span></span>

## <a name="identify-the-business-problem"></a><span data-ttu-id="d85cb-107">确定业务问题</span><span class="sxs-lookup"><span data-stu-id="d85cb-107">Identify the business problem</span></span>

<span data-ttu-id="d85cb-108">规划合同管理系统的第一步是了解您尝试解决的问题。</span><span class="sxs-lookup"><span data-stu-id="d85cb-108">The first step in planning your contract management system is to understand the problem you're trying to solve.</span></span> <span data-ttu-id="d85cb-109">对于此解决方案，需要解决四个关键问题：</span><span class="sxs-lookup"><span data-stu-id="d85cb-109">For this solution, four key issues need to be addressed:</span></span>

- <span data-ttu-id="d85cb-110">**确定合同**。</span><span class="sxs-lookup"><span data-stu-id="d85cb-110">**Identify contracts**.</span></span> <span data-ttu-id="d85cb-111">你的组织处理许多文档，如发票、合同、工作表等。</span><span class="sxs-lookup"><span data-stu-id="d85cb-111">Your organization works with many documents, such as invoices, contracts, statements of work, and so on.</span></span>  <span data-ttu-id="d85cb-112">一些是通过电子邮件发送的数字资产，一些是通过传统邮件发送的纸张资产。</span><span class="sxs-lookup"><span data-stu-id="d85cb-112">Some are digital assets sent through email, and some are paper assets sent through traditional mail.</span></span> <span data-ttu-id="d85cb-113">您需要一种方法来识别所有其他文档中的所有客户合同，然后对这些合同进行分类。</span><span class="sxs-lookup"><span data-stu-id="d85cb-113">You need a way to identify all customer contracts from all other documents, and then classifying them as such.</span></span>

- <span data-ttu-id="d85cb-114">**跟踪合同审批的历史记录**。</span><span class="sxs-lookup"><span data-stu-id="d85cb-114">**Track the history of contract approvals**.</span></span> <span data-ttu-id="d85cb-115">贵组织需要一种可靠的方法，以查找合同是否已获得批准或拒绝，以及是否已处理付款。</span><span class="sxs-lookup"><span data-stu-id="d85cb-115">Your organization needs a reliable way to find whether contracts have been either approved or rejected, and whether payment has been processed.</span></span> 

- <span data-ttu-id="d85cb-116">**用于管理合同审批的网站**。</span><span class="sxs-lookup"><span data-stu-id="d85cb-116">**Site to manage contract approvals**.</span></span> <span data-ttu-id="d85cb-117">组织需要建立一个协作网站，所有必需的利益干系人都可以在该网站中轻松审阅合同。</span><span class="sxs-lookup"><span data-stu-id="d85cb-117">Your organization needs to set up a collaborative site in which all required stakeholders can easily review contracts.</span></span> <span data-ttu-id="d85cb-118">利益干系人应能根据需要查看整个合同，但主要考虑查看每个合同 (例如客户名称、PO 编号和总成本) 。</span><span class="sxs-lookup"><span data-stu-id="d85cb-118">Stakeholders should be able to review the whole contract if needed, but mostly care about seeing several key fields from each contract (for example, customer name, PO number, and total cost).</span></span> <span data-ttu-id="d85cb-119">利益干系人应该能够轻松批准或拒绝传入合同。</span><span class="sxs-lookup"><span data-stu-id="d85cb-119">Stakeholders should be able to easily approve or reject incoming contracts.</span></span>

- <span data-ttu-id="d85cb-120">**路由已审阅合同**。</span><span class="sxs-lookup"><span data-stu-id="d85cb-120">**Route reviewed contracts**.</span></span> <span data-ttu-id="d85cb-121">需要通过特定工作流传送已批准和已拒绝合同。</span><span class="sxs-lookup"><span data-stu-id="d85cb-121">Approved and rejected contracts need to be routed through a specific workflow.</span></span> <span data-ttu-id="d85cb-122">批准的合同需要传送给第三方应用程序进行付款处理。</span><span class="sxs-lookup"><span data-stu-id="d85cb-122">Approved contracts need to be routed to a third-party application for payment processing.</span></span> <span data-ttu-id="d85cb-123">必须传送被拒绝的合同进行其他审阅。</span><span class="sxs-lookup"><span data-stu-id="d85cb-123">Rejected contracts need to be routed for additional review.</span></span>

## <a name="overview-of-the-solution"></a><span data-ttu-id="d85cb-124">解决方案概述</span><span class="sxs-lookup"><span data-stu-id="d85cb-124">Overview of the solution</span></span>

  ![使用 Syntex、SharePoint 列表、SharePoint 列表、Teams 和 Power Automate 的解决方案关系图。](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

<span data-ttu-id="d85cb-126">此合同管理解决方案指南包括以下四个Microsoft 365：</span><span class="sxs-lookup"><span data-stu-id="d85cb-126">This contract management solution guidance includes four components of Microsoft 365:</span></span>

- <span data-ttu-id="d85cb-127">**Microsoft SharePoint Syntex：** 创建模型以标识和分类合约文件，然后从中提取相应的数据。</span><span class="sxs-lookup"><span data-stu-id="d85cb-127">**Microsoft SharePoint Syntex**: Create models to identify and classify your contract files and then extract the appropriate data from them.</span></span>

- <span data-ttu-id="d85cb-128">**Microsoft SharePoint列表**：使用新式列表SharePoint格式以业务友好格式显示合同。</span><span class="sxs-lookup"><span data-stu-id="d85cb-128">**Microsoft SharePoint lists**: Use the formatting available in modern SharePoint lists to present contracts in a business-friendly format.</span></span>

- <span data-ttu-id="d85cb-129">**Microsoft Teams：** 使用 Teams 渠道和关联选项卡的功能，让利益干系人能够审阅和管理合同。</span><span class="sxs-lookup"><span data-stu-id="d85cb-129">**Microsoft Teams**: Use the functionality of a Teams channel and associated tabs to allow your stakeholders to review and manage contracts.</span></span>

- <span data-ttu-id="d85cb-130">**Power Automate：** 使用流来指导合同完成审批过程，然后引导到第三方应用程序进行付款。</span><span class="sxs-lookup"><span data-stu-id="d85cb-130">**Power Automate**: Use flows to guide contracts through the approval process, and then to a third-party application for payment.</span></span>

### <a name="how-it-all-works"></a><span data-ttu-id="d85cb-131">一切如何工作</span><span class="sxs-lookup"><span data-stu-id="d85cb-131">How it all works</span></span>

  ![显示工作流的解决方案图表，该工作流用于上载文档、提取数据、通知利益干系人以及批准或拒绝合同。](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. <span data-ttu-id="d85cb-133">将文档上载到SharePoint库中。</span><span class="sxs-lookup"><span data-stu-id="d85cb-133">Documents are uploaded to a SharePoint document library.</span></span> <span data-ttu-id="d85cb-134">A SharePoint Syntex document understanding model has been applied to the document library.</span><span class="sxs-lookup"><span data-stu-id="d85cb-134">A SharePoint Syntex document understanding model has been applied to the document library.</span></span> <span data-ttu-id="d85cb-135">它检查每个文件，以查看是否与经过训练要查找的"合同"内容类型匹配。</span><span class="sxs-lookup"><span data-stu-id="d85cb-135">It checks each file to see if any match a "contract" content type it's trained to look for.</span></span> <span data-ttu-id="d85cb-136">如果找到匹配项，它会将文件分类为"协定"，并更新文档的内容类型。</span><span class="sxs-lookup"><span data-stu-id="d85cb-136">If it finds a match, it classifies the file as a "contract" and updates the content type for the document.</span></span>

2. <span data-ttu-id="d85cb-137">模型还会从利益干系人感兴趣的每个合同文件中提取特定数据，如客户、承包商 *和费用金额*。  </span><span class="sxs-lookup"><span data-stu-id="d85cb-137">The model also pulls out specific data from each contract file that stakeholders are interested in seeing, such as the *Client*, *Contractor*, and *Fee amount*.</span></span>

    <span data-ttu-id="d85cb-138">以下页面是模型经过训练可识别的合约示例。</span><span class="sxs-lookup"><span data-stu-id="d85cb-138">The following page is an example of a contract that the model is trained to identify.</span></span>

      ![合同示例。](../media/content-understanding/contract.png)

3. <span data-ttu-id="d85cb-140">在Microsoft Teams中，所有利益干系人都是安全Teams通道的成员，其中文档库中的所有合同都可以看到批准或拒绝。</span><span class="sxs-lookup"><span data-stu-id="d85cb-140">In Microsoft Teams, all stakeholders are members of a secure Teams channel in which all contracts in the document library are visible for approval or rejection.</span></span> <span data-ttu-id="d85cb-141">通过使用Teams功能，当需要审阅新合同时，将通知所有利益干系人。</span><span class="sxs-lookup"><span data-stu-id="d85cb-141">By using Teams functionality, all stakeholders are notified when new contracts need to be reviewed.</span></span>
 
4. <span data-ttu-id="d85cb-142">通过使用Power Automate，合同将经过审批流程在 Teams 通道中移动。</span><span class="sxs-lookup"><span data-stu-id="d85cb-142">By using Power Automate, contracts are moved through the approval process in the Teams channel.</span></span> <span data-ttu-id="d85cb-143">当成员批准合同时，合同状态更改为批准，通过 Teams 帖子通知所有成员，并创建一个行项目以显示合同已准备好付款。</span><span class="sxs-lookup"><span data-stu-id="d85cb-143">When a member approves a contract, the contract status is changed to approve, all members are notified through a Teams post, and a line item is created to show that the contract is ready for payout.</span></span> <span data-ttu-id="d85cb-144">此过程可以扩展为直接写入第三方财务应用程序进行支付。</span><span class="sxs-lookup"><span data-stu-id="d85cb-144">This process can be extended to write directly to a third-party financial application for payment.</span></span>

5.  <span data-ttu-id="d85cb-145">当成员拒绝合同时，状态将更改为"已拒绝"，并且将通过一条帖子通知所有成员Teams通知。</span><span class="sxs-lookup"><span data-stu-id="d85cb-145">When a member rejects a contract, the status is changed to rejected, and all members are notified through a Teams post.</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="d85cb-146">创建解决方案</span><span class="sxs-lookup"><span data-stu-id="d85cb-146">Create the solution</span></span>

<span data-ttu-id="d85cb-147">以下各节将详细介绍如何配置合同管理解决方案。</span><span class="sxs-lookup"><span data-stu-id="d85cb-147">The next sections will go into detail about how to configure your contracts management solution.</span></span> <span data-ttu-id="d85cb-148">它分为三个步骤：</span><span class="sxs-lookup"><span data-stu-id="d85cb-148">It's divided into three steps:</span></span>

- [<span data-ttu-id="d85cb-149">步骤 1.使用 SharePoint Syntex 标识协定文件并提取数据</span><span class="sxs-lookup"><span data-stu-id="d85cb-149">Step 1. Use SharePoint Syntex to identify contract files and extract data</span></span>](solution-manage-contracts-step1.md)
- [<span data-ttu-id="d85cb-150">步骤 2.使用Microsoft Teams创建合同管理通道</span><span class="sxs-lookup"><span data-stu-id="d85cb-150">Step 2. Use Microsoft Teams to create your contract management channel</span></span>](solution-manage-contracts-step2.md)
- [<span data-ttu-id="d85cb-151">步骤 3.使用 Power Automate 创建处理合同的流程</span><span class="sxs-lookup"><span data-stu-id="d85cb-151">Step 3. Use Power Automate to create your flow to process your contracts</span></span>](solution-manage-contracts-step3.md)