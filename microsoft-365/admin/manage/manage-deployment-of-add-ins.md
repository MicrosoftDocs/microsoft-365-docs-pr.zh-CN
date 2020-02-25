---
title: 在管理中心管理 Office 365 外接程序的部署
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: 了解如何通过在管理中心中使用集中部署将外接程序部署到组织中的用户和组。
ms.openlocfilehash: acb6febf03e40b37b167113666b3577e0b9fb61e
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "42251110"
---
# <a name="manage-deployment-of-office-365-add-ins-in-the-microsoft-365-admin-center"></a><span data-ttu-id="4ca6f-103">在 Microsoft 365 管理中心管理 Office 365 加载项的部署</span><span class="sxs-lookup"><span data-stu-id="4ca6f-103">Manage deployment of Office 365 add-ins in the Microsoft 365 admin center</span></span>

<span data-ttu-id="4ca6f-104">Office 加载项可帮助用户个性化设置文档并加速访问 Web 上的信息（请参阅[开始使用 Office 加载项](https://support.office.com/article/82e665c4-6700-4b56-a3f3-ef5441996862.aspx)）。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-104">Office add-ins help you personalize your documents and streamline the way you access information on the web (see [Start using your Office Add-in](https://support.office.com/article/82e665c4-6700-4b56-a3f3-ef5441996862.aspx)).</span></span> <span data-ttu-id="4ca6f-105">作为管理员，您可以为组织中的用户部署 Office 外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-105">As an admin, you can deploy Office add-ins for the users in your organization.</span></span> <span data-ttu-id="4ca6f-106">您可以使用 Microsoft 365 管理中心中的集中部署功能来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-106">You can do this using the Centralized Deployment feature in the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="4ca6f-107">集中部署是大多数管理员为将外接程序部署到组织内的用户和组的建议功能和功能最丰富的方式。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-107">Centralized Deployment is the recommended and most feature-rich way for most admins to deploy add-ins to users and groups within an organization.</span></span> <span data-ttu-id="4ca6f-108">若要深入了解如何确定组织是否能够支持集中部署，请参阅[确定加载项集中部署是否适用于你的 Office 365 组织](centralized-deployment-of-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-108">For more information on how to determine if your organization can support Centralized Deployment, see [Determine if Centralized Deployment of add-ins works for your Office 365 organization](centralized-deployment-of-add-ins.md).</span></span>
  
<span data-ttu-id="4ca6f-109">集中部署有以下优点：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-109">Centralized Deployment provides the following benefits:</span></span>
  
- <span data-ttu-id="4ca6f-110">全局管理员可以将外接程序直接分配给用户、通过一个组将加载项分配给多个用户，或分配给租户中的所有人。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-110">A Global admin can assign an add-in directly to a user, to multiple users via a group, or to everyone in the tenant.</span></span>
    
- <span data-ttu-id="4ca6f-p103">相关 Office 应用程序启动时，将自动为用户下载加载项。如果加载项支持加载项命令，加载项会自动显示在 Office 应用程序的"功能区"中。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p103">When the relevant Office application starts, the add-in automatically downloads for the user. If the add-in supports add-in commands, the add-in automatically appears in the Ribbon within the Office application.</span></span>
    
- <span data-ttu-id="4ca6f-113">如果管理员关闭或删除加载项，或者从 Azure Active Directory 或将外接程序分配到的组中删除了用户，外接程序将不再显示给用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-113">Add-ins will no longer appear for users if the admin turns off or deletes the add-in, or if the user is removed from Azure Active Directory or from a group that the add-in is assigned to.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="4ca6f-114">对于 Word，Excel 和 PowerPoint 使用[Sharepoint 应用程序目录](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog)将外接程序部署到本地环境中的用户，而无需连接到 Office 365 和/或支持 SharePoint 外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-114">For Word, Excel and PowerPoint use a [SharePoint App Catalog](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) to deploy add-ins to users in an on-premises environment with no connection to Office 365 and/or support for SharePoint add-ins required.</span></span> <span data-ttu-id="4ca6f-115">>  在 Outlook 中使用 Exchange 控制面板，在没有连接到 Office 365 的本地环境中进行部署。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-115">>  For Outlook use Exchange control panel to deploy in an on-premises environment without a connection to Office 365.</span></span> > 
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a><span data-ttu-id="4ca6f-116">部署 Office 外接程序的推荐方法</span><span class="sxs-lookup"><span data-stu-id="4ca6f-116">Recommended approach for deploying Office add-ins</span></span>

<span data-ttu-id="4ca6f-p105">请考虑采用分阶段方法推出加载项，帮助确保加载项部署顺利进行。推荐以下计划：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p105">Consider rolling out add-ins in a phased approach to help ensure your add-in deployment goes smoothly. We recommend the following plan:</span></span>
  
1. <span data-ttu-id="4ca6f-p106">向小部分业务利益干系人和 IT 部门成员推出加载项。评估部署是否成功，如果成功，请转到步骤 2。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p106">Roll-out the add-in to a small set of business stakeholders and members of the IT department. Evaluate if the deployment was successful, and if so, move on to step 2.</span></span>
    
2. <span data-ttu-id="4ca6f-p107">向企业内将使用加载项的较多人员推出加载项。同样，评估结果，如果一切顺利，请转至完整部署的下一步。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p107">Roll-out to a larger set of individuals within the business who will be using the add-in. Again, evaluate results and, if all went well, go to the next step of a full deployment.</span></span>
    
3. <span data-ttu-id="4ca6f-123">全面向目标受众用户推出加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-123">Full rollout to target audience of users.</span></span>
    
<span data-ttu-id="4ca6f-124">根据目标受众的规模，可能需要添加或移除推出步骤。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-124">Depending on the size of the target audience, you may want to add or remove roll-out steps.</span></span>
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a><span data-ttu-id="4ca6f-125">使用管理中心部署 Office 外接程序</span><span class="sxs-lookup"><span data-stu-id="4ca6f-125">Deploy an Office add-in using the admin center</span></span>

<span data-ttu-id="4ca6f-126">开始之前，请参阅[确定加载项集中部署是否适用于你的 Office 365 组织](centralized-deployment-of-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-126">Before you begin, see [Determine if Centralized Deployment of add-ins works for your Office 365 organization](centralized-deployment-of-add-ins.md).</span></span>

  
1. <span data-ttu-id="4ca6f-127">在管理中心中，转到 "**设置** \> **外接程序**" 页。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-127">In the admin center, go to the **Settings** \> **Add-ins** page.</span></span>
    
2. <span data-ttu-id="4ca6f-128">在页面顶部选择 "**部署加载项**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-128">Select **Deploy Add-in** at the top of the page.</span></span> <span data-ttu-id="4ca6f-129">在 "概述" 页上，选择 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-129">On the overview page, select **Next**.</span></span>
    
3. <span data-ttu-id="4ca6f-130">选择一个选项，然后按照说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-130">Select an option and follow the instructions.</span></span>
  
4. <span data-ttu-id="4ca6f-131">如果选择了从 Office 应用商店添加加载项的选项，现在可以将加载项选择。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-131">If you selected the option to add an add-in from the Office Store, you can now make your add-in selection.</span></span> <span data-ttu-id="4ca6f-132">请注意，可以按" **建议** "、" **评级** "或" **名称** "查看可用加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-132">Notice that you can view available add-ins via categories of **Suggested for you**, **Rating**, or **Name**.</span></span> <span data-ttu-id="4ca6f-133">仅可从 Office Store 添加免费加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-133">Only free add-ins are available to add from the Office Store.</span></span> <span data-ttu-id="4ca6f-134">目前尚不支持付费加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-134">Paid add-ins aren't supported currently.</span></span> <span data-ttu-id="4ca6f-135">选择你的外接程序后，你将需要同意一些其他条款和条件才能继续。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-135">Once you've selected your add-in, you will need to agree to some additional terms and conditions in order to proceed.</span></span> <br/><br/> <span data-ttu-id="4ca6f-136">注意：通过 Office 应用商店选项，无需你的干预，即可自动将对外接程序的更新和增强提供给用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-136">NOTE: With the Office Store option, updates and enhancements to the add-in will automatically be made available to users without your intervention.</span></span>

5. <span data-ttu-id="4ca6f-137">在下一页上，选择 "**所有人**"、"**特定用户/组**" 或 "**仅我**" 以指定要向其部署加载项的用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-137">On the next page, select **Everyone**, **Specific users/groups** or **Just me** to specify who the add-in is deployed to.</span></span> <span data-ttu-id="4ca6f-138">使用搜索框查找要向其部署加载项的用户或组。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-138">Use the Search box to find the users or groups who you want to deploy the add-in to.</span></span> <br/><span data-ttu-id="4ca6f-139">注意：了解适用于外接程序的其他状态。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-139">NOTE: Learn about the other states that apply to an add-in.</span></span> <span data-ttu-id="4ca6f-140">请参阅本主题后面的[加载项状态](#add-in-states)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-140">See [Add-in states](#add-in-states) later in this topic.</span></span>
  
6. <span data-ttu-id="4ca6f-141">选择“部署”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-141">Select **Deploy**.</span></span>
  
7. <span data-ttu-id="4ca6f-142">部署外接程序后，将显示绿色计时周期。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-142">A green tick will appear when the add-in has been deployed.</span></span> <span data-ttu-id="4ca6f-143">您可以按照页面上的说明测试外接程序是否已成功部署。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-143">You can follow the on-page instructions to test that the add-in has deployed successfully.</span></span>

> [!NOTE]
> <span data-ttu-id="4ca6f-144">用户可能需要重新启动 Office 以查看应用程序功能区上显示的外接程序图标。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-144">Users may need to relaunch Office to see the add-in icon appear on the ribbon of app.</span></span> <span data-ttu-id="4ca6f-145">Outlook 外接程序最长可能需要12个小时才能显示在用户的功能区上。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-145">Outlook add-ins can take up to 12 hours to appear on users' ribbons.</span></span>
    
8. <span data-ttu-id="4ca6f-146">完成后，选择 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-146">When finished, select **Next**.</span></span> <span data-ttu-id="4ca6f-147">如果只部署到自己的，则可以选择 "**更改谁有权访问外接程序**"，以便将其部署到更多用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-147">If you've deployed to just yourself, you can select **Change who has access to add-in** in order to deploy to more users.</span></span>



<span data-ttu-id="4ca6f-148">如果您已将外接程序部署到您的组织的成员之外，请按照显示的说明进行操作，以便有效地宣布加载项的部署。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-148">If you've deployed the add-in to members of your organization other than yourself, follow the instructions displayed in order to effectively announce the deployment of the add-in.</span></span> <br/><span data-ttu-id="4ca6f-149">现在，可以看到此加载项与其他应用一起显示在 Office 365 中。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-149">You now see your add-in along with other apps in Office 365.</span></span>
  
<span data-ttu-id="4ca6f-150">最好通知向其部署了加载项的用户和组，以便他们知道加载项可用。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-150">It's a good idea to inform the users and groups who you deployed the add-in to so that they know that it's available.</span></span> <span data-ttu-id="4ca6f-151">可以向他们发送电子邮件，说明何时以及如何使用加载项，并说明加载项可以如何帮助他们更好地完成工作。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-151">Consider sending an email to them that describes when and how to use the add-in and explains how the add-in can help them do their job better.</span></span> <span data-ttu-id="4ca6f-152">包含或链接到相关帮助内容或 Faq，如果用户在外接程序中遇到任何问题，则可能会有帮助。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-152">Include or link to relevant Help content or FAQs that might help if users have any problems with the add-in.</span></span>
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a><span data-ttu-id="4ca6f-153">为用户和组分配加载项时的注意事项</span><span class="sxs-lookup"><span data-stu-id="4ca6f-153">Considerations when assigning an add-in to users and groups</span></span>

<span data-ttu-id="4ca6f-p116">管理员可以为每个人或特定用户和组分配加载项。每个选项都有含义：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p116">Admins can assign an add-in to everyone or to specific users and groups. Each option has implications:</span></span>
  
- <span data-ttu-id="4ca6f-p117">**每个人**：顾名思义，此选项为租户中的每位用户分配加载项。请谨慎使用此选项，且仅应用于真正在组织中通用的加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p117">**Everyone**: As the name implies, this option assigns the add-in to every user in the tenant. Use this option sparingly and only for add-ins that are truly universal to your organization.</span></span> 
    
- <span data-ttu-id="4ca6f-p118">**用户** ：如果向单个用户分配加载项，那么为新用户部署加载项时，需要先添加该用户。这同样适用于删除用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p118">**Users**: If you assign an add-in to an individual user, then to deploy the add-in to a new user, you will need to first add that user. The same goes for removing users.</span></span> 
    
- <span data-ttu-id="4ca6f-p119">**组** ：如果为组分配加载项，添加到组的用户将自动被分配该加载项。并且，当从组中删除用户时，该用户无法再访问该加载项。在任一情况下，不需要管理员执行任何额外操作。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p119">**Groups**: If you assign an add-in to a group, users who are added to the group will automatically be assigned the add-in. And, when a user is removed from a group, the user loses access to the add-in. In either case, no additional action is required from you as the admin.</span></span> 

- <span data-ttu-id="4ca6f-163">**仅限我**：如果只向自己分配加载项，则会将外接程序仅分配给您的帐户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-163">**Just me**: If you assign an add-in to just yourself, this assigns the add-in to only your account.</span></span> <span data-ttu-id="4ca6f-164">如果您希望先测试加载项，这是理想之选。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-164">This is ideal if you wish to test out the add-in first.</span></span>
    
<span data-ttu-id="4ca6f-165">适合您的组织的选项取决于您的配置。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-165">The option that is right for your organization depends on your configuration.</span></span> <span data-ttu-id="4ca6f-166">但是，建议通过组进行分配。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-166">However, we recommend making assignments via groups.</span></span> <span data-ttu-id="4ca6f-167">作为管理员，可能会发现通过组管理加载项以及控制组成员身份更为轻松，而不是每次都更改分配的用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-167">As an admin, you might find it easier to manage add-ins using groups and control the membership of those groups rather than having to change the users assigned each time.</span></span> <span data-ttu-id="4ca6f-168">另一方面，在某些情况下，可能需要限制少数用户的访问权限，从而针对特定用户进行分配。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-168">On the other hand, in some situations, you may want to restrict access to a very small set of users and therefore make assignments to specific users.</span></span> <span data-ttu-id="4ca6f-169">因此，需要手动管理分配的用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-169">As a result, you will need to manage the assigned users manually.</span></span>
  
### <a name="add-in-states"></a><span data-ttu-id="4ca6f-170">加载项状态</span><span class="sxs-lookup"><span data-stu-id="4ca6f-170">Add-in states</span></span>

<span data-ttu-id="4ca6f-171">外接程序可以处于 "**打开**" 或 "**关闭**" 状态。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-171">An add-in can either be in the **On** or **Off** state.</span></span>
  
|<span data-ttu-id="4ca6f-172">**状态**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-172">**State**</span></span>|<span data-ttu-id="4ca6f-173">**状态出现的原因**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-173">**How the state occurs**</span></span>|<span data-ttu-id="4ca6f-174">**影响**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-174">**Impact**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4ca6f-175">**Active**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-175">**Active**</span></span>  <br/> |<span data-ttu-id="4ca6f-176">管理员上载了加载项，并将其分配给用户或组。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-176">Admin uploaded the add-in and assigned it to users or groups.</span></span>  <br/> |<span data-ttu-id="4ca6f-177">分配了加载项的用户和组可在相关客户端中看到它。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-177">Users and groups assigned to the add-in see it in the relevant clients.</span></span>  <br/> |
|<span data-ttu-id="4ca6f-178">**已禁用**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-178">**Turned off**</span></span>  <br/> |<span data-ttu-id="4ca6f-179">管理员已禁用加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-179">Admin turned off the add-in.</span></span>  <br/> |<span data-ttu-id="4ca6f-180">分配了外接程序的用户和组无法再访问它。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-180">Users and groups assigned to the add-in no longer have access to it.</span></span>  <br/> <span data-ttu-id="4ca6f-181">如果外接程序的状态更改为"可用"，则用户和组将再次有权访问它。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-181">If the add-in state is changed to Active, the users and groups will have access to it again.</span></span>  <br/> |
|<span data-ttu-id="4ca6f-182">**已删除**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-182">**Deleted**</span></span>  <br/> |<span data-ttu-id="4ca6f-183">管理员已删除加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-183">Admin deleted the add-in.</span></span>  <br/> |<span data-ttu-id="4ca6f-184">分配了加载项的用户和组无法再访问它。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-184">Users and groups assigned the add-in no longer have access to it.</span></span>  <br/> |
   
<span data-ttu-id="4ca6f-185">如果没有人再使用加载项，请考虑删除外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-185">Consider deleting an add-in if no one is using it any more.</span></span> <span data-ttu-id="4ca6f-186">如果仅在一年的特定时间段使用加载项，那么可以选择关闭加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-186">Turning off an add-in may make sense if an add-in is used only during specific times of the year.</span></span>
  
### <a name="security-of-office-add-ins"></a><span data-ttu-id="4ca6f-187">Office 加载项的安全性</span><span class="sxs-lookup"><span data-stu-id="4ca6f-187">Security of Office add-ins</span></span>

<span data-ttu-id="4ca6f-p123">Office 加载项结合了一个包含加载项相关元数据的 XML 清单文件，但最重要的是它指向包含所有代码和逻辑的 Web 应用程序。加载项的功能范围很广。例如，加载项可以：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p123">Office add-ins combine an XML manifest file that contains some metadata about the add-in, but most importantly points to a web application which contains all the code and logic. Add-ins can range in their capabilities. For example, add-ins can:</span></span>
  
- <span data-ttu-id="4ca6f-191">显示数据。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-191">Display data.</span></span>
    
- <span data-ttu-id="4ca6f-192">读取用户文档以提供上下文服务。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-192">Read a user's document to provide contextual services.</span></span>
    
- <span data-ttu-id="4ca6f-193">从用户文档读取数据并向用户文档写入数据，以便向该用户提供价值。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-193">Read and write data to and from a user's document to provide value to that user.</span></span>
    
<span data-ttu-id="4ca6f-194">若要详细了解 Office 加载项的类型和功能，请参阅 [Office Add-ins platform overview](https://go.microsoft.com/fwlink/p/?linkid=846362)（Office 加载项平台概述），尤其是"Anatomy of an Office Add-in"（Office 加载项分析）一节。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-194">For more information about the types and capabilities of Office add-ins, see [Office Add-ins platform overview](https://go.microsoft.com/fwlink/p/?linkid=846362), especially the section "Anatomy of an Office Add-in."</span></span>
  
<span data-ttu-id="4ca6f-p124">若要与用户文档进行交互，加载项需要在清单中声明需要哪些权限。五级 JavaScript API 访问权限模型为任务窗格加载项的用户提供隐私和安全性的基础。Office 应用商店 中的大多数加载项是 ReadWriteDocument 级别，几乎所有加载项均至少支持 ReadDocument 级别。有关权限级别的详细信息，请参阅 [Requesting permissions for API use in content and task pane add-ins](https://go.microsoft.com/fwlink/p/?linkid=848863)（请求在内容和任务窗格加载项中使用 API 的权限）。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p124">To interact with the user's document, the add-in needs to declare what permission it needs in the manifest. A five-level JavaScript API access-permissions model provides the basis for privacy and security for users of task pane add-ins. The majority of the add-ins in the Office Store are level ReadWriteDocument with almost all add-ins supporting at least the ReadDocument level. For more information about the permission levels, see [Requesting permissions for API use in content and task pane add-ins](https://go.microsoft.com/fwlink/p/?linkid=848863).</span></span>
  
<span data-ttu-id="4ca6f-p125">更新清单时，通常更改加载项的图标和文本。有时会更改加载项命令。但是，不会更改加载项的权限。Web 应用程序（加载项的所有代码和逻辑在其中运行）可以随时更改，这是 Web 应用程序的特性。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p125">When updating a manifest, the typical changes are to an add-in's icon and text. Occasionally, add-in commands change. However, the permissions of the add-in do not change. The web application where all the code and logic for the add-in runs can change at any time, which is the nature of web applications.</span></span>
  
<span data-ttu-id="4ca6f-202">加载项更新的情况如下：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-202">Updates for add-ins happen as follows:</span></span>
  
- <span data-ttu-id="4ca6f-p126">**业务线加载项：** 在这种情况下，管理员显式上传清单，加载项需要管理员上传新的清单文件以支持元数据的更改。相关 Office 应用程序下次启动时，该加载项会更新。Web 应用程序可以随时更改。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p126">**Line-of-business add-in:** In this case, where an admin explicitly uploaded a manifest, the add-in requires that the admin upload a new manifest file to support metadata changes. The next time the relevant Office applications start, the add-in will update. The web application can change at any time.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="4ca6f-206">管理员无需删除 LOB 加载项即可进行更新。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-206">Admin does not need to remove a LOB Add-in for doing an update.</span></span>   <span data-ttu-id="4ca6f-207">在 "外接程序" 部分中，管理员只需单击 LOB 外接程序，然后选择右下角的 "**更新" 按钮**即可。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-207">In the Add-ins section, Admin can simply click on the LOB Add-in and choose the **Update Button** in the bottom right corner.</span></span> <span data-ttu-id="4ca6f-208">仅当新外接程序的版本大于现有加载项的版本时，更新才有效。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-208">Update will work only if the version of the new add-in is greater than that of the existing add-in.</span></span>   
    
- <span data-ttu-id="4ca6f-p128">**Office 应用商店加载项：** 管理员从 Office 应用商店 中选择加载项后，如果 Office 应用商店 中更新了加载项，则该加载项会稍后以集中式部署方式更新。相关 Office 应用程序下次启动时，该加载项会更新。Web 应用程序可以随时更改。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p128">**Office Store add-in:** When an admin selected an add-in from the Office Store, if an add-in updates in the Office Store, the add-in will update later in Centralized Deployment. The next time the relevant Office applications start, the add-in will update. The web application can change at any time.</span></span> 

### <a name="edit-add-in-access"></a><span data-ttu-id="4ca6f-212">编辑外接访问</span><span class="sxs-lookup"><span data-stu-id="4ca6f-212">Edit Add-in access</span></span>

<span data-ttu-id="4ca6f-213">部署后，管理员还可以修改用户对加载项的访问权限。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-213">Post deployment, admins can also modify the user access to add-ins.</span></span>

1. <span data-ttu-id="4ca6f-214">在 "管理中心" 中，转到 "**设置** > **服务" & "加载项**" 页面。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-214">In the admin center, go to the **Settings** > **Services & add-ins** page.</span></span>

2. <span data-ttu-id="4ca6f-215">选择部署的加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-215">Select the deployed add-in.</span></span>

3. <span data-ttu-id="4ca6f-216">单击 "**有权访问**" 下的 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-216">Click on **Edit** under **Who has Access**.</span></span>
4. <span data-ttu-id="4ca6f-217">保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-217">Save the changes.</span></span>
    
### <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a><span data-ttu-id="4ca6f-218">通过在所有客户端（Outlook 除外）中关闭 Office 应用商店来阻止外接程序下载</span><span class="sxs-lookup"><span data-stu-id="4ca6f-218">Prevent add-in downloads by turning off the Office Store across all clients (Except Outlook)</span></span>

> [!NOTE]
> <span data-ttu-id="4ca6f-219">Outlook 外接程序安装由[不同的进程](https://technet.microsoft.com/library/jj943754%28v=exchg.150%29.aspx)进行管理。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-219">Outlook add-in installation is managed by a [different process](https://technet.microsoft.com/library/jj943754%28v=exchg.150%29.aspx).</span></span>

<span data-ttu-id="4ca6f-220">作为组织，您可能希望阻止从 Office 应用商店下载新的 Office 加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-220">As an organization you may wish to prevent the download of new Office add-ins from the Office Store.</span></span> <span data-ttu-id="4ca6f-221">这可与集中部署结合使用，以确保仅向组织中的用户部署组织批准的外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-221">This can be used in conjunction with Centralized Deployment to ensure that only organization-approved add-ins are deployed to users within your organization.</span></span>
  
<span data-ttu-id="4ca6f-222">若要关闭加载项获取，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-222">To turn off add-in acquisition:</span></span>
  
1. <span data-ttu-id="4ca6f-223">在管理中心，转到“**设置**”\> [服务和加载项](https://go.microsoft.com/fwlink/p/?linkid=2053743)页面。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-223">In the admin center, go to the **Settings** \> [Services &amp; add-ins](https://go.microsoft.com/fwlink/p/?linkid=2053743) page.</span></span>
    
3. <span data-ttu-id="4ca6f-224">选择 "**用户拥有的应用和服务**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-224">Select **User owned apps and services**.</span></span>
    
4. <span data-ttu-id="4ca6f-225">清除 "允许用户访问 Office 应用商店" 选项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-225">Clear the option to let users access the Office store.</span></span>

<span data-ttu-id="4ca6f-226">这将阻止所有用户从存储中获取以下外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-226">This will prevent all users from acquiring the following add-ins from the store.</span></span>
  
- <span data-ttu-id="4ca6f-227">Word、Excel 和 PowerPoint 2016 的外接程序来自：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-227">Add-ins for Word, Excel, and PowerPoint 2016 from:</span></span>
    
  - <span data-ttu-id="4ca6f-228">Windows</span><span class="sxs-lookup"><span data-stu-id="4ca6f-228">Windows</span></span>
    
  - <span data-ttu-id="4ca6f-229">Mac</span><span class="sxs-lookup"><span data-stu-id="4ca6f-229">Mac</span></span>
    
  - <span data-ttu-id="4ca6f-230">Office</span><span class="sxs-lookup"><span data-stu-id="4ca6f-230">Office</span></span>
    
  - <span data-ttu-id="4ca6f-231">iOS （仅限 iPad）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-231">iOS (iPad only)</span></span>
    
- <span data-ttu-id="4ca6f-232">从**AppSource**中开始的收购</span><span class="sxs-lookup"><span data-stu-id="4ca6f-232">Acquisitions starting within **AppSource**</span></span>
    
- <span data-ttu-id="4ca6f-233">Office 365 中的外接程序</span><span class="sxs-lookup"><span data-stu-id="4ca6f-233">Add-ins within Office 365</span></span>
    
<span data-ttu-id="4ca6f-234">尝试访问应用商店的用户将看到以下消息：**抱歉，Office 365 已配置为阻止单独购买 Office 应用商店外接程序。**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-234">A user who tries to access the store will see the following message: **Sorry, Office 365 has been configured to prevent individual acquisition of Office Store add-ins.**</span></span>
  
<span data-ttu-id="4ca6f-235">以下版本提供了对 Office 应用商店关闭的支持：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-235">Support for turning off the Office Store is available in the following versions:</span></span>
  
- <span data-ttu-id="4ca6f-236">Windows： 16.0.9001-当前可用。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-236">Windows: 16.0.9001 - Currently available.</span></span>
    
- <span data-ttu-id="4ca6f-237">Mac： 16.10.18011401-当前可用。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-237">Mac: 16.10.18011401 - Currently available.</span></span>
    
- <span data-ttu-id="4ca6f-238">iOS： 2.9.18010804-当前可用。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-238">iOS: 2.9.18010804 - Currently available.</span></span>
    
- <span data-ttu-id="4ca6f-239">Web 当前可用。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-239">The web - Currently available.</span></span>
    
<span data-ttu-id="4ca6f-240">这不会阻止管理员使用集中部署从 Office 应用商店分配外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-240">This does not prevent an administrator from using Centralized Deployment to assign an add-in from the Office Store.</span></span>
  
<span data-ttu-id="4ca6f-241">若要阻止用户使用 Microsoft 帐户登录，可以将登录限制为仅使用组织帐户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-241">To prevent a user from signing in with a Microsoft account, you can restrict logon to use only the organizational account.</span></span> <span data-ttu-id="4ca6f-242">有关详细信息，请参阅[此处](https://technet.microsoft.com/library/jj683102%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-242">For more information, look [here](https://technet.microsoft.com/library/jj683102%28v=office.16%29.aspx).</span></span>
 
  
## <a name="minors-and-acquiring-add-ins-from-the-store"></a><span data-ttu-id="4ca6f-243">向应用商店中的未成年人和收购外接程序</span><span class="sxs-lookup"><span data-stu-id="4ca6f-243">Minors and acquiring add-ins from the Store</span></span>

<span data-ttu-id="4ca6f-244">一般数据保护条例（GDPR）是一种欧洲联合法规，生效时间可能为25，2018。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-244">The General Data Protection Regulation (GDPR) is a European Union regulation that becomes effective May 25, 2018.</span></span> <span data-ttu-id="4ca6f-245">它向用户提供对其数据的权限并加以保护。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-245">It gives users rights to and protection of their data.</span></span> <span data-ttu-id="4ca6f-246">GDPR 的其中一个方面是，未成年人的个人数据不能发送给其家长或监护人尚未批准的当事人。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-246">One of the aspects of the GDPR is that minors cannot have their personal data sent to parties that their parent or guardian hasn't approved.</span></span> <span data-ttu-id="4ca6f-247">定义为次要的特定年龄取决于个人所在的区域。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-247">The specific age defined as a minor depends on the region where the individual is located.</span></span>
  
<span data-ttu-id="4ca6f-248">具有关于家长同意的法令法规的地区包括美国、韩国、英国和欧盟。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-248">Regions that have statutory regulations about parental consent include the United States, South Korea, the United Kingdom, and the European Union.</span></span> <span data-ttu-id="4ca6f-249">对于这些区域，将阻止（通过 Azure Active Directory）从存储中获取任何新的 Office 外接程序，并运行之前获取的外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-249">For those regions, a minor will be blocked (via Azure Active Directory) from getting any new Office add-ins from the Store and running add-ins that were previously acquired.</span></span> <span data-ttu-id="4ca6f-250">对于没有法令法规的国家/地区，将不提供下载限制。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-250">For countries without statutory regulations, there will be no download restrictions.</span></span>
  
<span data-ttu-id="4ca6f-251">根据 Azure Active Directory 中指定的数据，将用户确定为次要用户。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-251">A user is determined to be a minor based on data specified in Azure Active Directory.</span></span> <span data-ttu-id="4ca6f-252">租户管理员负责声明法律年龄组和该用户的家长同意。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-252">The tenant admin is responsible for declaring the legal age group and the parental consent for that user.</span></span>
  
<span data-ttu-id="4ca6f-253">如果父/监护人同意使用特定的外接程序，则租户管理员可以使用集中部署将该外接程序部署到所有已同意的未成年人。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-253">If the parent/guardian consents to a minor using a specific add-In, then the tenant admin can use centralized deployment to deploy that add-In to all minors who have consent.</span></span>
  
<span data-ttu-id="4ca6f-254">若要符合 GDPR 的要求，您需要确保在学校/组织中部署以下 Office 内部版本之一。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-254">To be GDPR compliant for minors you need to ensure that one of following builds of Office is deployed in your school/organization.</span></span>
  
 <span data-ttu-id="4ca6f-255">**对于 Word、Excel、PowerPoint 和 Project**：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-255">**For Word, Excel, PowerPoint, and Project**:</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="4ca6f-256">**平台**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-256">**Platform**</span></span> <br/> |<span data-ttu-id="4ca6f-257">**内部版本号**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-257">**Build number**</span></span> <br/> |
|<span data-ttu-id="4ca6f-258">Office 2016 专业增强版每月 for Windows</span><span class="sxs-lookup"><span data-stu-id="4ca6f-258">Office 2016 ProPlus Monthly for Windows</span></span>  <br/> |<span data-ttu-id="4ca6f-259">9001.2138</span><span class="sxs-lookup"><span data-stu-id="4ca6f-259">9001.2138</span></span>   <br/> |
|<span data-ttu-id="4ca6f-260">Office 2016 专业增强版半年</span><span class="sxs-lookup"><span data-stu-id="4ca6f-260">Office 2016 ProPlus Semi-Annual</span></span>  <br/> |<span data-ttu-id="4ca6f-261">8431.2159</span><span class="sxs-lookup"><span data-stu-id="4ca6f-261">8431.2159</span></span>  <br/> |
|<span data-ttu-id="4ca6f-262">Office 2016 for Windows</span><span class="sxs-lookup"><span data-stu-id="4ca6f-262">Office 2016 for Windows</span></span>  <br/> |<span data-ttu-id="4ca6f-263">16.0.4672.1000</span><span class="sxs-lookup"><span data-stu-id="4ca6f-263">16.0.4672.1000</span></span>  <br/> |
|<span data-ttu-id="4ca6f-264">Office 2013 for Windows</span><span class="sxs-lookup"><span data-stu-id="4ca6f-264">Office 2013 for Windows</span></span>  <br/> |<span data-ttu-id="4ca6f-265">15.0.5023.1000</span><span class="sxs-lookup"><span data-stu-id="4ca6f-265">15.0.5023.1000</span></span>  <br/> |
|<span data-ttu-id="4ca6f-266">Office 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="4ca6f-266">Office 2016 for Mac</span></span>  <br/> |<span data-ttu-id="4ca6f-267">16.11.18020200</span><span class="sxs-lookup"><span data-stu-id="4ca6f-267">16.11.18020200</span></span>  <br/> |
|<span data-ttu-id="4ca6f-268">适用于 iOS 的 Office 2016 （仅限 ipad）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-268">Office 2016 for iOS (ipad only)</span></span>  <br/> |<span data-ttu-id="4ca6f-269">2.12.18032600</span><span class="sxs-lookup"><span data-stu-id="4ca6f-269">2.12.18032600</span></span>  <br/> |
|<span data-ttu-id="4ca6f-270">Office 网页版</span><span class="sxs-lookup"><span data-stu-id="4ca6f-270">Office for the web</span></span>  <br/> |<span data-ttu-id="4ca6f-271">不适用</span><span class="sxs-lookup"><span data-stu-id="4ca6f-271">N/A</span></span>  <br/> |
   
 <span data-ttu-id="4ca6f-272">**对于 Outlook**：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-272">**For Outlook**:</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="4ca6f-273">**平台**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-273">**Platform**</span></span> <br/> |<span data-ttu-id="4ca6f-274">**内部版本号**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-274">**Build number**</span></span> <br/> |
|<span data-ttu-id="4ca6f-275">适用于 Windows 的 Outlook 2016 （MSI）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-275">Outlook 2016 for Windows (MSI)</span></span>  <br/> |<span data-ttu-id="4ca6f-276">生成不 TBD</span><span class="sxs-lookup"><span data-stu-id="4ca6f-276">Build No TBD</span></span>  <br/> |
|<span data-ttu-id="4ca6f-277">适用于 Windows 的 Outlook 2016 （C2R）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-277">Outlook 2016 for Windows (C2R)</span></span>  <br/> |<span data-ttu-id="4ca6f-278">16.0.9323.1000</span><span class="sxs-lookup"><span data-stu-id="4ca6f-278">16.0.9323.1000</span></span>  <br/> |
|<span data-ttu-id="4ca6f-279">Office 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="4ca6f-279">Office 2016 for Mac</span></span>  <br/> |<span data-ttu-id="4ca6f-280">16.0.9318.1000</span><span class="sxs-lookup"><span data-stu-id="4ca6f-280">16.0.9318.1000</span></span>  <br/> |
|<span data-ttu-id="4ca6f-281">适用于 iOS 的 Outlook mobile</span><span class="sxs-lookup"><span data-stu-id="4ca6f-281">Outlook mobile for iOS</span></span>  <br/> |<span data-ttu-id="4ca6f-282">2.75.0</span><span class="sxs-lookup"><span data-stu-id="4ca6f-282">2.75.0</span></span>  <br/> |
|<span data-ttu-id="4ca6f-283">Outlook mobile for Android</span><span class="sxs-lookup"><span data-stu-id="4ca6f-283">Outlook mobile for Android</span></span>  <br/> |<span data-ttu-id="4ca6f-284">2.2.145</span><span class="sxs-lookup"><span data-stu-id="4ca6f-284">2.2.145</span></span>  <br/> |
|<span data-ttu-id="4ca6f-285">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="4ca6f-285">Outlook.com</span></span>  <br/> |<span data-ttu-id="4ca6f-286">不适用</span><span class="sxs-lookup"><span data-stu-id="4ca6f-286">N/A</span></span>  <br/> |
   
 <span data-ttu-id="4ca6f-287">**Office 2013 要求**</span><span class="sxs-lookup"><span data-stu-id="4ca6f-287">**Office 2013 requirements**</span></span>
  
<span data-ttu-id="4ca6f-288">Word、Excel 和 PowerPoint 2013 for Windows 将支持相同的次要检查（如果已启用 Active Directory 身份验证库（ADAL））。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-288">Word, Excel, and PowerPoint 2013 for Windows will support the same minor checks if Active Directory Authentication Library (ADAL) is enabled.</span></span> <span data-ttu-id="4ca6f-289">有两种合规性选项，如下所述。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-289">There are two options for compliance, as explained next.</span></span>
  
- <span data-ttu-id="4ca6f-290">**启用 ADAL**。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-290">**Enable ADAL**.</span></span> <span data-ttu-id="4ca6f-291">本文介绍如何为 Office 2013 启用 ADAL：通过 office[客户端使用 office 365 新式验证](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-291">This article explains how to enable ADAL for Office 2013: [Using Office 365 modern authentication with Office clients](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a).</span></span><br/><span data-ttu-id="4ca6f-292">您还需要将注册表项设置为启用 ADAL，如在[Windows 设备上为 Office 2013 启用新式验证](../security-and-compliance/enable-modern-authentication.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-292">You also need to set the registry keys to enable ADAL as explained in [Enable Modern Authentication for Office 2013 on Windows devices](../security-and-compliance/enable-modern-authentication.md).</span></span><br/><span data-ttu-id="4ca6f-293">此外，还需要为 Office 2013 安装以下四月份更新：</span><span class="sxs-lookup"><span data-stu-id="4ca6f-293">Additionally, you need to install the following April updates for Office 2013:</span></span>
    
  - [<span data-ttu-id="4ca6f-294">Office 2013 安全更新说明：4月10日，2018</span><span class="sxs-lookup"><span data-stu-id="4ca6f-294">Description of the security update for Office 2013: April 10, 2018</span></span>](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [<span data-ttu-id="4ca6f-295">2018年4月3日，Office 2013 更新（KB4018333）</span><span class="sxs-lookup"><span data-stu-id="4ca6f-295">April 3, 2018, update for Office 2013 (KB4018333)</span></span>](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- <span data-ttu-id="4ca6f-296">**不启用 ADAL**。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-296">**Don't enable ADAL**.</span></span> <span data-ttu-id="4ca6f-297">如果无法在 Office 2013 中启用 ADAL，我们建议使用组策略关闭 office 客户端的存储。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-297">If you're unable to enable ADAL in Office 2013, then our recommendation is to use Group Policy to turn off the Store for the office clients.</span></span> <span data-ttu-id="4ca6f-298">有关如何关闭 "Office 相关应用程序" 设置的信息位于[此处](https://technet.microsoft.com/library/cc178992.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-298">Information on how to turn off the app for Office settings is located [here](https://technet.microsoft.com/library/cc178992.aspx).</span></span>
    
## <a name="end-user-experience-with-add-ins"></a><span data-ttu-id="4ca6f-299">加载项最终用户体验</span><span class="sxs-lookup"><span data-stu-id="4ca6f-299">End user experience with add-ins</span></span>

<span data-ttu-id="4ca6f-p137">部署加载项后，最终用户就可开始在 Office 应用程序中使用此加载项（请参阅[开始使用 Office 加载项](https://support.office.com/article/82e665c4-6700-4b56-a3f3-ef5441996862.aspx)）。加载项会显示在所有加载项支持的平台上。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p137">Now that you've deployed the add-in, your end users can start using it in their Office applications (see [Start using your Office Add-in](https://support.office.com/article/82e665c4-6700-4b56-a3f3-ef5441996862.aspx)). The add-in will appear on all platforms that the add-in supports.</span></span>
  
<span data-ttu-id="4ca6f-p138">如果加载项支持加载项命令，则 Office 功能区上会显示命令。在以下示例中，显示" **引文** "加载项的" **搜索引文** "命令。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-p138">If the add-in supports add-in commands, the commands appear on the Office ribbon. In the following example, the command **Search Citation** appears for the **Citations** add-in.</span></span> 

![带有搜索引文的 Office 功能区](../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
<span data-ttu-id="4ca6f-305">如果部署的外接程序不支持外接程序命令，或者如果您想要查看所有部署的加载项，可以通过**我的外接**程序查看它们。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-305">If the deployed add-in doesn't support add-in commands or if you want to view all deployed add-ins, you can view them via **My Add-ins**.</span></span> 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a><span data-ttu-id="4ca6f-306">在 Word 2016、Excel 2016 或 PowerPoint 2016 中</span><span class="sxs-lookup"><span data-stu-id="4ca6f-306">In Word 2016, Excel 2016, or PowerPoint 2016</span></span>

1. <span data-ttu-id="4ca6f-307">选择 **" \>插入我的外接程序"**。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-307">Select **Insert \> My Add-ins**.</span></span> 
    
2. <span data-ttu-id="4ca6f-308">选择 Office 加载项窗口中的" **由管理员管理** "选项卡。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-308">Select the **Admin Managed** tab in the Office Add-ins window.</span></span> 
    
3. <span data-ttu-id="4ca6f-309">双击先前部署的加载项（在本例中是" **引文** "）。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-309">Double-click the add-in you deployed earlier (in this example, **Citations** ).</span></span> <br/><span data-ttu-id="4ca6f-310">!["Office 外接程序" 页的 "管理托管" 选项卡](../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)</span><span class="sxs-lookup"><span data-stu-id="4ca6f-310">![Admin Managed tab of the Office Add-ins page](../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)</span></span>
  
### <a name="in-outlook"></a><span data-ttu-id="4ca6f-311">在 Outlook 中</span><span class="sxs-lookup"><span data-stu-id="4ca6f-311">In Outlook</span></span>

1. <span data-ttu-id="4ca6f-312">在 "**主页**" 功能区上，选择 "**获取外接程序**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-312">On the **Home** ribbon, select **Get Add-ins**.</span></span><br/><span data-ttu-id="4ca6f-313">![Outlook 中的'应用商店'按钮](../media/getaddinsicon.png)</span><span class="sxs-lookup"><span data-stu-id="4ca6f-313">![Store button in Outlook](../media/getaddinsicon.png)</span></span>
  
2. <span data-ttu-id="4ca6f-314">在左侧导航中选择 "**管理员管理**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-314">Select **Admin-managed** in the left nav.</span></span>

## <a name="delete-the-add-in"></a><span data-ttu-id="4ca6f-315">删除加载项</span><span class="sxs-lookup"><span data-stu-id="4ca6f-315">Delete the add-in</span></span>

<span data-ttu-id="4ca6f-316">您还可以删除已部署的外接程序。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-316">You can also delete an add-in that was deployed.</span></span>

1. <span data-ttu-id="4ca6f-317">在 "管理中心" 中，转到 "**设置** > **服务" & "加载项**" 页面。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-317">In the admin center, go to the **Settings** > **Services & add-ins** page.</span></span>

2. <span data-ttu-id="4ca6f-318">选择部署的加载项。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-318">Select the deployed add-in.</span></span>

3. <span data-ttu-id="4ca6f-319">单击 "**删除加载项**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-319">Click on **Delete Add-In**.</span></span> <span data-ttu-id="4ca6f-320">移除右下角的外接端按钮。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-320">Remove the Add-in button on the bottom right corner.</span></span>
4. <span data-ttu-id="4ca6f-321">验证您的选择，然后选择 "**删除外接程序**"。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-321">Validate your selections, and choose **Remove add-in**.</span></span>
  
## <a name="learn-more"></a><span data-ttu-id="4ca6f-322">了解更多</span><span class="sxs-lookup"><span data-stu-id="4ca6f-322">Learn more</span></span>

<span data-ttu-id="4ca6f-323">深入了解如何创建和构建 [Office 加载项](https://go.microsoft.com/fwlink/p/?linkid=846362)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-323">Learn more about creating and building [Office Add-ins](https://go.microsoft.com/fwlink/p/?linkid=846362).</span></span>
  
<span data-ttu-id="4ca6f-324">[使用集中部署 PowerShell cmdlet 管理外接程序](https://support.office.com/article/94f4e86d-b8e5-42dd-b558-e6092f830ec9)。</span><span class="sxs-lookup"><span data-stu-id="4ca6f-324">[Use Centralized Deployment PowerShell cmdlets to manage add-ins](https://support.office.com/article/94f4e86d-b8e5-42dd-b558-e6092f830ec9).</span></span>
  
[<span data-ttu-id="4ca6f-325">疑难解答：用户看不到外接程序</span><span class="sxs-lookup"><span data-stu-id="4ca6f-325">Troubleshoot: User not seeing add-ins</span></span>](https://docs.microsoft.com/office365/troubleshoot/access-management/user-not-seeing-add-ins)
