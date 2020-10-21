---
title: 管理自助注册订阅
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- commerce
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
description: 了解如何为你的组织管理免费的自助服务注册订阅。
ms.openlocfilehash: fb70d0c40d4358abc227c8f6ff4a0e0dce1a7265
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2020
ms.locfileid: "48647827"
---
# <a name="manage-self-service-sign-up-subscriptions"></a><span data-ttu-id="864c4-103">管理自助注册订阅</span><span class="sxs-lookup"><span data-stu-id="864c4-103">Manage self-service sign-up subscriptions</span></span>

## <a name="what-are-self-service-sign-up-subscriptions"></a><span data-ttu-id="864c4-104">什么是自助式注册订阅？</span><span class="sxs-lookup"><span data-stu-id="864c4-104">What are self-service sign-up subscriptions?</span></span>

<span data-ttu-id="864c4-105">您的组织中的用户可以注册的有限数量的免费自助注册订阅。</span><span class="sxs-lookup"><span data-stu-id="864c4-105">There are a limited number of free self-service sign-up subscriptions that users in your organization can sign up for.</span></span> <span data-ttu-id="864c4-106">用户只能注册，并对自己使用自助注册订阅。</span><span class="sxs-lookup"><span data-stu-id="864c4-106">A user can only sign up for and use a self-service sign-up subscription for themselves.</span></span> <span data-ttu-id="864c4-107">这些订阅显示在 " **产品** " 页面上，标记为 " **免费**"，并显示 "这是公司中的用户激活的免费订阅" 一条注释。</span><span class="sxs-lookup"><span data-stu-id="864c4-107">These subscriptions appear on the **Your products** page, are marked as **Free**, and have a note that says, "This is a free subscription activated by users in your company."</span></span> <span data-ttu-id="864c4-108">您可以通过阻止用户进行注册以及删除用户已注册的免费订阅来管理自助注册订阅。</span><span class="sxs-lookup"><span data-stu-id="864c4-108">You can manage self-service sign-up subscriptions by blocking users from signing up, and by deleting free subscriptions that users have signed up for.</span></span> <span data-ttu-id="864c4-109">有关自助注册和可用订阅的详细信息，请参阅 [在组织中使用自助服务注册](../../admin/misc/self-service-sign-up.md)。</span><span class="sxs-lookup"><span data-stu-id="864c4-109">For more information about self-service sign up and the available subscriptions, see [Using self-service sign up in your organization](../../admin/misc/self-service-sign-up.md).</span></span>

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a><span data-ttu-id="864c4-110">这些订阅与自助服务购买订阅有何不同？</span><span class="sxs-lookup"><span data-stu-id="864c4-110">How are these subscriptions different from self-service purchase subscriptions?</span></span>

<span data-ttu-id="864c4-111">自助注册订阅是免费的，可用于比自助服务购买订阅更大的产品列表。</span><span class="sxs-lookup"><span data-stu-id="864c4-111">Self-service sign-up subscriptions are free, and are available for a larger list of products than self-service purchase subscriptions.</span></span> <span data-ttu-id="864c4-112">当用户注册自助服务购买订阅时，他们负责付费。</span><span class="sxs-lookup"><span data-stu-id="864c4-112">When a user signs up for a self-service purchase subscription, they are responsible for paying for it.</span></span> <span data-ttu-id="864c4-113">此外，自助式购买订阅仅适用于 Power Platform 产品 (Power BI、电源应用和电源自动) 。</span><span class="sxs-lookup"><span data-stu-id="864c4-113">Also, self-service purchase subscriptions are only available for Power Platform products (Power BI, Power Apps, and Power Automate).</span></span> <span data-ttu-id="864c4-114">有关详细信息，请参阅 [自助式购买常见问题解答](self-service-purchase-faq.md)。</span><span class="sxs-lookup"><span data-stu-id="864c4-114">For more information, see [Self-service purchase FAQ](self-service-purchase-faq.md).</span></span>

## <a name="block-users-from-signing-up"></a><span data-ttu-id="864c4-115">阻止用户注册</span><span class="sxs-lookup"><span data-stu-id="864c4-115">Block users from signing up</span></span>

<span data-ttu-id="864c4-116">将 [**set-msolcompanysettings**](https://docs.microsoft.com/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0) Cmdlet 与 **AllowAdHocSubscriptions** 参数一起使用，可控制用户是否可以注册自助服务注册订阅。</span><span class="sxs-lookup"><span data-stu-id="864c4-116">You use the [**Set-MsolCompanySettings**](https://docs.microsoft.com/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0) cmdlet with the **AllowAdHocSubscriptions** parameter to control whether users can sign up for self-service sign-up subscriptions.</span></span> <span data-ttu-id="864c4-117">有关详细信息，请参阅 [如何控制自助服务设置？](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)</span><span class="sxs-lookup"><span data-stu-id="864c4-117">For more information, see [How do I control self-service settings?](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)</span></span>

## <a name="delete-a-self-service-sign-up-subscription"></a><span data-ttu-id="864c4-118">删除自助注册订阅</span><span class="sxs-lookup"><span data-stu-id="864c4-118">Delete a self-service sign-up subscription</span></span>

> [!IMPORTANT]
> <span data-ttu-id="864c4-119">删除自助注册订阅时，将阻止所有用户访问其数据和电子邮件，并删除所有数据和电子邮件。</span><span class="sxs-lookup"><span data-stu-id="864c4-119">When you delete a self-service sign-up subscription, you block all users from accessing their data and email and delete all data and email.</span></span>

1. <span data-ttu-id="864c4-120">在管理中心中，转到 **“账单”** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">“你的产品”</a>页面。</span><span class="sxs-lookup"><span data-stu-id="864c4-120">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Your products</a> page.</span></span>
2. <span data-ttu-id="864c4-121">查找要删除的自助注册订阅。</span><span class="sxs-lookup"><span data-stu-id="864c4-121">Find the self-service sign-up subscription that you want to delete.</span></span> <span data-ttu-id="864c4-122">在 " **设置" & "操作** " 部分，选择 " **删除订阅**"。</span><span class="sxs-lookup"><span data-stu-id="864c4-122">In the **Settings & Actions** section, select **Delete subscription**.</span></span>
3. <span data-ttu-id="864c4-123">在 " **删除订阅** " 窗格中，选中 "" 复选框，然后选择 " **删除订阅**"。</span><span class="sxs-lookup"><span data-stu-id="864c4-123">In the **Delete subscription** pane, select the check box, then select **Delete subscription**.</span></span>

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a><span data-ttu-id="864c4-124">我有一个可阻止目录删除的自助服务注册订阅</span><span class="sxs-lookup"><span data-stu-id="864c4-124">I have a self-service sign-up subscription that blocks directory deletion</span></span>

<span data-ttu-id="864c4-125">单个用户可以注册的自助注册产品也可以在 Azure AD 目录中创建来宾用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="864c4-125">The self-service sign-up products that individual users can sign up for also create a guest user for authentication in your Azure AD directory.</span></span> <span data-ttu-id="864c4-126">为避免数据丢失，这些自助服务产品将阻止目录删除，直到从目录中完全删除。</span><span class="sxs-lookup"><span data-stu-id="864c4-126">To avoid data loss, these self-service products block directory deletions until they're fully deleted from the directory.</span></span> <span data-ttu-id="864c4-127">它们只能由 Azure AD 管理员删除。有关详细信息，请参阅 [删除 Azure Active directory 中的目录](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-delete-howto)。</span><span class="sxs-lookup"><span data-stu-id="864c4-127">They can be deleted only by the Azure AD admin. For more information, see [Delete a directory in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-delete-howto).</span></span>