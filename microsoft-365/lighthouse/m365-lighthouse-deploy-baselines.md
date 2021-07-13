---
title: 部署Microsoft 365 Lighthouse基线
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: 对于托管服务提供商 (MSP) 使用Microsoft 365 Lighthouse，了解如何部署Microsoft 365 Lighthouse基线。
ms.openlocfilehash: 0bda7edec2a200e51e734db64e2b703a027e57bb
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2021
ms.locfileid: "53395076"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a><span data-ttu-id="b44ae-103">部署Microsoft 365 Lighthouse基线</span><span class="sxs-lookup"><span data-stu-id="b44ae-103">Deploy Microsoft 365 Lighthouse baselines</span></span> 

> [!NOTE]
> <span data-ttu-id="b44ae-104">本文中所述的功能在预览版中，可能会更改，并且仅对满足要求 [的合作伙伴可用](m365-lighthouse-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b44ae-104">The features described in this article are in Preview, are subject to change, and are only available to partners who meet the [requirements](m365-lighthouse-requirements.md).</span></span> <span data-ttu-id="b44ae-105">如果你的组织没有此Microsoft 365 Lighthouse，请参阅[注册Microsoft 365 Lighthouse。](m365-lighthouse-sign-up.md)</span><span class="sxs-lookup"><span data-stu-id="b44ae-105">If your organization does not have Microsoft 365 Lighthouse, see [Sign up for Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).</span></span>

<span data-ttu-id="b44ae-106">Microsoft 365 Lighthouse基线，您可以部署标准托管租户配置，以确保租户用户、设备和数据的安全。</span><span class="sxs-lookup"><span data-stu-id="b44ae-106">Microsoft 365 Lighthouse baselines let you deploy standard managed tenant configurations to secure tenant users, devices, and data.</span></span> <span data-ttu-id="b44ae-107">有六种默认基线配置符合标准Microsoft 365 Lighthouse：</span><span class="sxs-lookup"><span data-stu-id="b44ae-107">There are six default baseline configurations that come standard with Microsoft 365 Lighthouse:</span></span>

- <span data-ttu-id="b44ae-108">要求管理员使用 MFA</span><span class="sxs-lookup"><span data-stu-id="b44ae-108">Require MFA for admins</span></span>
- <span data-ttu-id="b44ae-109">要求最终用户使用 MFA</span><span class="sxs-lookup"><span data-stu-id="b44ae-109">Require MFA for end users</span></span>
- <span data-ttu-id="b44ae-110">阻止旧式身份验证</span><span class="sxs-lookup"><span data-stu-id="b44ae-110">Block Legacy Authentication</span></span>
- <span data-ttu-id="b44ae-111">在 Azure AD Microsoft Endpoint Manager中设置设备注册</span><span class="sxs-lookup"><span data-stu-id="b44ae-111">Set up Device Enrollment in Microsoft Endpoint Manager – Azure AD Join</span></span>
- <span data-ttu-id="b44ae-112">为设备配置 Defender 防病毒Windows策略</span><span class="sxs-lookup"><span data-stu-id="b44ae-112">Configure Defender Anti-virus policy for Windows devices</span></span>
- <span data-ttu-id="b44ae-113">为设备配置Windows策略</span><span class="sxs-lookup"><span data-stu-id="b44ae-113">Configure Compliance Policy for Windows devices</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="b44ae-114">准备工作</span><span class="sxs-lookup"><span data-stu-id="b44ae-114">Before you begin</span></span>

<span data-ttu-id="b44ae-115">确保你和客户租户满足要求[for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md)中列出的要求。</span><span class="sxs-lookup"><span data-stu-id="b44ae-115">Make sure you and your customer tenants meet the requirements listed in [Requirements for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).</span></span>

## <a name="learn-more-about-the-default-baseline"></a><span data-ttu-id="b44ae-116">详细了解默认基线</span><span class="sxs-lookup"><span data-stu-id="b44ae-116">Learn more about the default baseline</span></span>

<span data-ttu-id="b44ae-117">从 **左侧导航** 窗格中选择"比较基准"以打开"比较基准"页。</span><span class="sxs-lookup"><span data-stu-id="b44ae-117">Select **Baselines** from the left navigation pane to open the Baselines page.</span></span> <span data-ttu-id="b44ae-118">你将看到默认基线已添加到默认租户组， (所有租户) 。</span><span class="sxs-lookup"><span data-stu-id="b44ae-118">You'll see that the default baseline has already been added to the Default tenant group (all tenants).</span></span> <span data-ttu-id="b44ae-119">若要查看默认基线配置，请选择" **查看比较基准** "以打开"默认比较基准"页。</span><span class="sxs-lookup"><span data-stu-id="b44ae-119">To view the default baseline configurations, select **View baseline** to open the Default baseline page.</span></span> <span data-ttu-id="b44ae-120">配置作为部署步骤列出。</span><span class="sxs-lookup"><span data-stu-id="b44ae-120">The configurations are listed as deployment steps.</span></span> <span data-ttu-id="b44ae-121">选择任意部署步骤以查看部署详细信息和用户影响。</span><span class="sxs-lookup"><span data-stu-id="b44ae-121">Select any of the deployment steps to view deployment details and user impact.</span></span>

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Default baseline page.>。":::

## <a name="deploy-a-baseline-configuration"></a><span data-ttu-id="b44ae-123">部署基线配置</span><span class="sxs-lookup"><span data-stu-id="b44ae-123">Deploy a baseline configuration</span></span>  

1. <span data-ttu-id="b44ae-124">在左侧导航页中，选择"租户"以查看已载入租户的列表。</span><span class="sxs-lookup"><span data-stu-id="b44ae-124">In the left navigation page, select **Tenants** to view a list of your onboarded tenants.</span></span>

2. <span data-ttu-id="b44ae-125">选择要将基线配置部署到的租户。</span><span class="sxs-lookup"><span data-stu-id="b44ae-125">Select the tenant you want to deploy the baseline configuration to.</span></span>

3. <span data-ttu-id="b44ae-126">选择 **"部署计划** "选项卡以查看基线中已添加到租户部署计划的所有部署步骤。</span><span class="sxs-lookup"><span data-stu-id="b44ae-126">Select the **Deployment plan** tab to see all the deployment steps from the baseline that have been added to the tenant's deployment plan.</span></span>

4. <span data-ttu-id="b44ae-127">选择部署步骤以打开部署步骤页。</span><span class="sxs-lookup"><span data-stu-id="b44ae-127">Select a deployment step to open the deployment step page.</span></span>

5. <span data-ttu-id="b44ae-128">选择 **"应用** "将所选部署步骤应用到租户。</span><span class="sxs-lookup"><span data-stu-id="b44ae-128">Select **Apply** to apply the selected deployment step to the tenant.</span></span> <span data-ttu-id="b44ae-129">如果部署步骤指示"此操作需要手动步骤"，请确保完成手动步骤，以便正确应用部署步骤。</span><span class="sxs-lookup"><span data-stu-id="b44ae-129">If the deployment step indicates "This action requires a manual step", make sure to complete the manual step so the deployment step is applied correctly.</span></span>

## <a name="related-content"></a><span data-ttu-id="b44ae-130">相关内容</span><span class="sxs-lookup"><span data-stu-id="b44ae-130">Related content</span></span>

<span data-ttu-id="b44ae-131">[使用基线部署标准租户配置的](m365-lighthouse-deploying-standard-tenant-configurations-overview.md) 概述 (文章) </span><span class="sxs-lookup"><span data-stu-id="b44ae-131">[Overview of using baselines to deploy standard tenant configurations](m365-lighthouse-deploying-standard-tenant-configurations-overview.md) (article)</span></span>\
<span data-ttu-id="b44ae-132">[Microsoft 365 Lighthouse常见问题](m365-lighthouse-faq.yml) (文章) </span><span class="sxs-lookup"><span data-stu-id="b44ae-132">[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)</span></span>