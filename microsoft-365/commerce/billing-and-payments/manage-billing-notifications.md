---
title: 管理计费通知和发票附件
f1.keywords:
- CSH
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
ms.custom:
- okr_SMB
- AdminSurgePortfolio
- commerce
search.appverid:
- MET150
description: 了解如何管理接收帐单通知电子邮件和发票附件的人。
ms.openlocfilehash: f0811c5d027d042b5114c9e05c698dab1e08763b
ms.sourcegitcommit: babbba2b5bf69fd3facde2905ec024b753dcd1b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2021
ms.locfileid: "50515217"
---
# <a name="manage-billing-notifications-and-invoice-attachments"></a><span data-ttu-id="36617-103">管理计费通知和发票附件</span><span class="sxs-lookup"><span data-stu-id="36617-103">Manage billing notifications and invoice attachments</span></span>

<span data-ttu-id="36617-104">通过 **"** 帐单通知"页，你可以管理接收组织帐单通知电子邮件的人。</span><span class="sxs-lookup"><span data-stu-id="36617-104">The **Billing notifications** page lets you manage who receives billing notification emails for your organization.</span></span> <span data-ttu-id="36617-105">该页面还提供将组织发票作为电子邮件附件 [接收的选项](#receive-your-organizations-invoices-as-email-attachments)。</span><span class="sxs-lookup"><span data-stu-id="36617-105">The page also provides the option to [receive your organization's invoices as email attachments](#receive-your-organizations-invoices-as-email-attachments).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="36617-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="36617-106">Before you begin</span></span>

<span data-ttu-id="36617-107">你必须是全局管理员才能执行本文中所述的步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-107">You must be a Global admin to do the steps described in this article.</span></span> <span data-ttu-id="36617-108">计费管理员可以进行其中一些更改，如以下各节所述。</span><span class="sxs-lookup"><span data-stu-id="36617-108">Billing admins can make some of these changes, as noted in the sections below.</span></span> <span data-ttu-id="36617-109">有关详细信息，请参阅 [关于管理员角色](../../admin/add-users/about-admin-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="36617-109">For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).</span></span>

## <a name="change-the-language-you-receive-email-in"></a><span data-ttu-id="36617-110">更改接收电子邮件的语言</span><span class="sxs-lookup"><span data-stu-id="36617-110">Change the language you receive email in</span></span>

> [!NOTE]
> <span data-ttu-id="36617-111">帐单管理员还可以执行本节中的步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-111">Billing admins can also do the steps in this section.</span></span>

<span data-ttu-id="36617-112">帐单通知电子邮件以组织的首选语言发送。</span><span class="sxs-lookup"><span data-stu-id="36617-112">Billing notification emails are sent in your organization’s preferred language.</span></span> <span data-ttu-id="36617-113">若要更改首选语言，请使用以下步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-113">To change the preferred language, use the following steps.</span></span>

1. <span data-ttu-id="36617-114">在 Microsoft 365 管理中心，转到"**计费**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">通知"</a>页。</span><span class="sxs-lookup"><span data-stu-id="36617-114">In the Microsoft 365 admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">Billing notifications</a> page.</span></span>
2. <span data-ttu-id="36617-115">在"**帐单通知设置**"部分，选择 **"编辑通知设置"。**</span><span class="sxs-lookup"><span data-stu-id="36617-115">In the **Billing notification settings** section, select **Edit notification settings**.</span></span>
3. <span data-ttu-id="36617-116">在 **"计费通知设置**"窗格中，在 **"** 首选语言"下，选择想要使用的语言，然后选择"**保存"。**</span><span class="sxs-lookup"><span data-stu-id="36617-116">In the **Billing notification settings** pane, under **Preferred language** select the language you want to use, then select **Save**.</span></span>

## <a name="change-who-receives-billing-notifications"></a><span data-ttu-id="36617-117">更改接收帐单通知的人</span><span class="sxs-lookup"><span data-stu-id="36617-117">Change who receives billing notifications</span></span>

<span data-ttu-id="36617-118">组织的帐单通知将发送到每个全局管理员和帐单管理员的主电子邮件地址和备用电子邮件地址。若要更改哪些用户具有全局管理员或帐单管理员角色，请使用以下步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-118">Your organization's billing notifications are sent to the primary and alternate email address of every Global and Billing admin. To change which users have the Global or Billing admin role, use the following steps.</span></span>

### <a name="assign-admin-roles-by-using-the-billing-notifications-page"></a><span data-ttu-id="36617-119">使用"计费通知"页分配管理员角色</span><span class="sxs-lookup"><span data-stu-id="36617-119">Assign admin roles by using the Billing notifications page</span></span>

1. <span data-ttu-id="36617-120">在管理中心中，转到“**账单**”  >  “<a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">账单通知</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="36617-120">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">Billing notifications</a> page.</span></span>
2. <span data-ttu-id="36617-121">在 **"管理员接收帐单通知**"部分，在说明文本中选择"计费管理员 **"或"** 全局管理员"链接。</span><span class="sxs-lookup"><span data-stu-id="36617-121">In the **Admins receiving billing notifications** section, select the **Billing administrator** or **Global administrator** link in the description text.</span></span>
3. <span data-ttu-id="36617-122">在右侧窗格中的"已分配 **管理员"** 选项卡上，选择"**添加"。**</span><span class="sxs-lookup"><span data-stu-id="36617-122">In the right pane, on the **Assigned admins** tab, select **Add**.</span></span>
4. <span data-ttu-id="36617-123">在 **"添加管理员** "窗格中，键入显示名称或用户名，然后从建议列表中选择用户。</span><span class="sxs-lookup"><span data-stu-id="36617-123">In the **Add admins** pane, type the user’s display name or username, and then select the user from the list of suggestions.</span></span>
5. <span data-ttu-id="36617-124">添加多个用户，直到完成。</span><span class="sxs-lookup"><span data-stu-id="36617-124">Add multiple users until you’re done.</span></span>
6. <span data-ttu-id="36617-125">选择“保存”。</span><span class="sxs-lookup"><span data-stu-id="36617-125">Select **Save**.</span></span> <span data-ttu-id="36617-126">用户将添加到已分配的管理员列表中。</span><span class="sxs-lookup"><span data-stu-id="36617-126">The user is added to the list of assigned admins.</span></span>

### <a name="remove-admin-roles-by-using-the-billing-notifications-page"></a><span data-ttu-id="36617-127">使用"计费通知"页删除管理员角色</span><span class="sxs-lookup"><span data-stu-id="36617-127">Remove admin roles by using the Billing notifications page</span></span>

1. <span data-ttu-id="36617-128">在管理中心中，转到“**账单**”  >  “<a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">账单通知</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="36617-128">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">Billing notifications</a> page.</span></span>
2. <span data-ttu-id="36617-129">在 **"管理员接收帐单通知**"部分，在说明文本中选择"计费管理员 **"或"** 全局管理员"链接。</span><span class="sxs-lookup"><span data-stu-id="36617-129">In the **Admins receiving billing notifications** section, select the **Billing administrator** or **Global administrator** link in the description text.</span></span>
3. <span data-ttu-id="36617-130">在右侧窗格中的"已分配管理员 **"选项卡上**，选择要从角色中删除的用户，然后选择"删除 **"。**</span><span class="sxs-lookup"><span data-stu-id="36617-130">In the right pane, on the **Assigned admins** tab, select the users to remove from the role, and then select **Remove**.</span></span>
4. <span data-ttu-id="36617-131">在确认框中，选择"删除 **"。**</span><span class="sxs-lookup"><span data-stu-id="36617-131">In the confirmation box, select **Remove**.</span></span> <span data-ttu-id="36617-132">将从分配的管理员列表中删除用户。</span><span class="sxs-lookup"><span data-stu-id="36617-132">The user is removed from the list of assigned admins.</span></span>

## <a name="change-the-email-addresses-for-admins"></a><span data-ttu-id="36617-133">更改管理员的电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="36617-133">Change the email addresses for admins</span></span>

<span data-ttu-id="36617-134">若要更改组织中其他管理员的主电子邮件地址和备用电子邮件地址，请使用以下步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-134">To change the primary and alternate email address of other admins in your organization, use the following steps.</span></span>

> [!NOTE]
> <span data-ttu-id="36617-135">计费管理员可以更改自己的主电子邮件地址和备用电子邮件地址，但不能更改其他管理员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="36617-135">Billing admins can change their own primary and alternate email addresses, but not for other admins.</span></span>

1. <span data-ttu-id="36617-136">在管理中心中，转到“**账单**”  >  “<a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">账单通知</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="36617-136">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">Billing notifications</a> page.</span></span>
2. <span data-ttu-id="36617-137">在 **"管理员接收帐单通知"部分中** ，选择一个名称。</span><span class="sxs-lookup"><span data-stu-id="36617-137">In the **Admins receiving billing notifications** section, select a name.</span></span>
3. <span data-ttu-id="36617-138">在右侧窗格中，根据需要添加或更新主电子邮件地址和备用电子邮件地址，然后选择"保存 **"。**</span><span class="sxs-lookup"><span data-stu-id="36617-138">In the right pane, add or update the primary and alternate email address as needed, then select **Save**.</span></span>

## <a name="change-your-organizations-contact-email"></a><span data-ttu-id="36617-139">更改组织的联系人电子邮件</span><span class="sxs-lookup"><span data-stu-id="36617-139">Change your organization's contact email</span></span>

<span data-ttu-id="36617-140">除了全局管理员和帐单管理员外，我们还向组织的联系人电子邮件地址发送帐单通知。</span><span class="sxs-lookup"><span data-stu-id="36617-140">In addition to your Global and Billing admins, we send billing notifications to your organization's contact email address.</span></span> <span data-ttu-id="36617-141">若要更改电子邮件地址，请使用以下步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-141">To change the email address, use the following steps.</span></span>

1. <span data-ttu-id="36617-142">在管理中心中，转到“**账单**”  >  “<a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">账单通知</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="36617-142">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">Billing notifications</a> page.</span></span>
2. <span data-ttu-id="36617-143">在 **"接收计费通知的组织联系人"下**，选择组织联系人。</span><span class="sxs-lookup"><span data-stu-id="36617-143">Under **Organization contact receiving billing notifications**, select the organization contact.</span></span>
3. <span data-ttu-id="36617-144">在右侧窗格中，键入想要使用的电子邮件地址，然后选择"保存 **"。**</span><span class="sxs-lookup"><span data-stu-id="36617-144">In the right pane, type the email address that you want to use, then select **Save**.</span></span>

## <a name="receive-your-organizations-invoices-as-email-attachments"></a><span data-ttu-id="36617-145">以电子邮件附件接收组织的发票</span><span class="sxs-lookup"><span data-stu-id="36617-145">Receive your organization's invoices as email attachments</span></span>

> [!NOTE]
> <span data-ttu-id="36617-146">帐单管理员还可以执行本节中的步骤。</span><span class="sxs-lookup"><span data-stu-id="36617-146">Billing admins can also do the steps in this section.</span></span>

<span data-ttu-id="36617-147">在准备好新发票时，可以将组织的发票副本作为 PDF 文件附加到发票通知电子邮件中。</span><span class="sxs-lookup"><span data-stu-id="36617-147">You can have a copy of your organization's invoice attached as a PDF file to invoice notification emails when a new invoice is ready.</span></span> <span data-ttu-id="36617-148">使用以下步骤接收作为附件的发票。</span><span class="sxs-lookup"><span data-stu-id="36617-148">Use the following steps to receive invoices as attachments.</span></span>

1. <span data-ttu-id="36617-149">在管理中心中，转到“**账单**”  >  “<a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">账单通知</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="36617-149">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">Billing notifications</a> page.</span></span>
2. <span data-ttu-id="36617-150">在 **"帐单通知设置"下**，**选择"编辑通知设置"。**</span><span class="sxs-lookup"><span data-stu-id="36617-150">Under **Billing notification settings**, select **Edit notification settings**.</span></span>
3. <span data-ttu-id="36617-151">在 **"帐单通知设置**"窗格中的 **"将 PDF 附加到发票** 电子邮件"下，选中复选框，然后选择"保存 **"。**</span><span class="sxs-lookup"><span data-stu-id="36617-151">In the **Billing notification settings** pane, under **Attach a PDF to your invoice emails**, check the checkbox, then select **Save**.</span></span>

<span data-ttu-id="36617-152">若要随时停止接收发票附件，请按照上述步骤操作，并清除步骤 3 中的"将 **PDF** 附加到发票电子邮件"复选框。</span><span class="sxs-lookup"><span data-stu-id="36617-152">To stop receiving the invoice attachment at any time, follow the steps above and clear the **Attach a PDF to your invoice  emails** checkbox in step 3.</span></span>

## <a name="what-if-i-have-a-billing-profile"></a><span data-ttu-id="36617-153">如果我有计费配置文件，该做什么？</span><span class="sxs-lookup"><span data-stu-id="36617-153">What if I have a billing profile?</span></span>

<span data-ttu-id="36617-154">如果你有计费配置文件，则本文中介绍的一些步骤对于你的某些订阅可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="36617-154">If you have a billing profile, some of the steps described in this article might be slightly different for some of your subscriptions.</span></span> <span data-ttu-id="36617-155">本节介绍这些差异。</span><span class="sxs-lookup"><span data-stu-id="36617-155">This section describes those differences.</span></span> [<span data-ttu-id="36617-156">我如何知道我是否具有计费配置文件？</span><span class="sxs-lookup"><span data-stu-id="36617-156">How do I know if I have a billing profile?</span></span>](manage-billing-profiles.md)

### <a name="who-receives-billing-notifications"></a><span data-ttu-id="36617-157">谁接收帐单通知？</span><span class="sxs-lookup"><span data-stu-id="36617-157">Who receives Billing notifications?</span></span>

<span data-ttu-id="36617-158">帐单通知电子邮件将发送到分配了以下角色之一的用户的主电子邮件地址和备用电子邮件地址：</span><span class="sxs-lookup"><span data-stu-id="36617-158">Billing notification emails are sent to the primary and alternate email addresses for users who are assigned one of the following roles:</span></span>

- <span data-ttu-id="36617-159">计费配置文件所有者</span><span class="sxs-lookup"><span data-stu-id="36617-159">Billing profile owner</span></span>
- <span data-ttu-id="36617-160">计费配置文件参与者</span><span class="sxs-lookup"><span data-stu-id="36617-160">Billing profile contributor</span></span>
- <span data-ttu-id="36617-161">发票经理</span><span class="sxs-lookup"><span data-stu-id="36617-161">Invoice manager</span></span>

<span data-ttu-id="36617-162">若要了解有关计费配置文件角色以及如何管理它们的信息，请参阅了解 Azure 中的 [Microsoft 客户协议管理角色](https://docs.microsoft.com/azure/cost-management-billing/manage/understand-mca-roles)。</span><span class="sxs-lookup"><span data-stu-id="36617-162">To learn more about billing profile roles and how to manage them, see [Understand Microsoft Customer Agreement administrative roles in Azure](https://docs.microsoft.com/azure/cost-management-billing/manage/understand-mca-roles).</span></span>

<span data-ttu-id="36617-163">若要更改接收组织帐单通知的用户，请使用以下步骤更改分配给用户的角色。</span><span class="sxs-lookup"><span data-stu-id="36617-163">To change who receives your organization’s billing notifications, use the following steps to change the roles assigned to users.</span></span>

1. <span data-ttu-id="36617-164">在管理中心，转到"帐单&  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">付款</a>页面。</span><span class="sxs-lookup"><span data-stu-id="36617-164">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Bills & payments</a> page.</span></span>
2. <span data-ttu-id="36617-165">在" **计费配置文件"** 选项卡上，选择计费配置文件。</span><span class="sxs-lookup"><span data-stu-id="36617-165">On the **Billing profile** tab, select a billing profile.</span></span>
3. <span data-ttu-id="36617-166">在"**计费配置文件角色**"部分中，为计费配置文件所有者、计费配置文件参与者或发票经理分配 **或删除角色**。</span><span class="sxs-lookup"><span data-stu-id="36617-166">In the **Billing profile roles** section, assign or remove roles for **Billing profile owner**, **Billing profile contributor**, or **Invoice manager**.</span></span>

### <a name="receive-invoices-as-email-attachments"></a><span data-ttu-id="36617-167">接收发票作为电子邮件附件</span><span class="sxs-lookup"><span data-stu-id="36617-167">Receive invoices as email attachments</span></span>

<span data-ttu-id="36617-168">若要将发票作为发票通知的附件接收，请使用以下步骤为特定计费配置文件启用此设置。</span><span class="sxs-lookup"><span data-stu-id="36617-168">To receive your invoices as attachments to your invoice notifications, use the following steps to turn on this setting for a specific billing profile.</span></span>

1. <span data-ttu-id="36617-169">在管理中心，转到"帐单&  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">付款</a>页面。</span><span class="sxs-lookup"><span data-stu-id="36617-169">In the admin center, go to the **Billing** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Bills & payments</a> page.</span></span>
2. <span data-ttu-id="36617-170">选择 **"计费配置文件"** 选项卡，然后从列表中选择计费配置文件。</span><span class="sxs-lookup"><span data-stu-id="36617-170">Select the **Billing profiles** tab, then select a billing profile from the list.</span></span>
3. <span data-ttu-id="36617-171">在计费配置文件详细信息页面上，在"**获取电子邮件附件中的** 发票"下，将开关 **切换到"打开"。**</span><span class="sxs-lookup"><span data-stu-id="36617-171">On the billing profile details page, under **Get invoices in email attachments**, switch the toggle to **On**.</span></span>

## <a name="related-content"></a><span data-ttu-id="36617-172">相关内容</span><span class="sxs-lookup"><span data-stu-id="36617-172">Related content</span></span>

<span data-ttu-id="36617-173">[查看帐单或发票 (](view-your-bill-or-invoice.md) 文章) </span><span class="sxs-lookup"><span data-stu-id="36617-173">[View your bill or invoice](view-your-bill-or-invoice.md) (article)</span></span>\
<span data-ttu-id="36617-174">[了解 Microsoft 365 商业版](understand-your-invoice2.md) 帐单或 (文章) </span><span class="sxs-lookup"><span data-stu-id="36617-174">[Understand your bill or invoice for Microsoft 365 for business](understand-your-invoice2.md) (article)</span></span>\
<span data-ttu-id="36617-175">[添加用户并同时分配许可证 (](../../admin/add-users/add-users.md) 文章) </span><span class="sxs-lookup"><span data-stu-id="36617-175">[Add users and assign licenses at the same time](../../admin/add-users/add-users.md) (article)</span></span>