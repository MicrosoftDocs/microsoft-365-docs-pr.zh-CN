---
title: 恢复用户邮箱中的已删除项目
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: 本文包含的信息可帮助管理员在清除的项目尚未从用户邮箱中永久删除的情况中恢复这些清除的项目。
ms.openlocfilehash: a4755e592182d93c37a241958ba37c95d1565cdc
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687671"
---
# <a name="recover-deleted-items-in-a-user-mailbox"></a><span data-ttu-id="f4ce5-103">恢复用户邮箱中的已删除项目</span><span class="sxs-lookup"><span data-stu-id="f4ce5-103">Recover deleted items in a user mailbox</span></span>

<span data-ttu-id="f4ce5-104">**本文适用于管理员。您是否正在尝试恢复您自己的邮箱中的已删除邮件？**</span><span class="sxs-lookup"><span data-stu-id="f4ce5-104">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?**</span></span> <span data-ttu-id="f4ce5-105">尝试执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="f4ce5-105">Try one of the following:</span></span>
- [<span data-ttu-id="f4ce5-106">在 Outlook for Windows 中恢复已删除项目</span><span class="sxs-lookup"><span data-stu-id="f4ce5-106">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="f4ce5-107">在 Outlook Web App 中恢复已删除项目或电子邮件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-107">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="f4ce5-108">在 web 上的 Outlook 中还原已删除的电子邮件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-108">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="f4ce5-109">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="f4ce5-109">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="f4ce5-110">用户是否从其 Outlook 邮箱中永久删除了项目？</span><span class="sxs-lookup"><span data-stu-id="f4ce5-110">Did a user permanently delete items from their Outlook mailbox?</span></span> <span data-ttu-id="f4ce5-111">用户希望它们回退，但无法恢复它们。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-111">The user wants them back but can't recover them.</span></span> <span data-ttu-id="f4ce5-112">如果清除的项目尚未从用户的邮箱中永久删除，则可以恢复这些清除的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-112">You may be able recover the purged items if they haven't been permanently removed from the user's mailbox.</span></span> <span data-ttu-id="f4ce5-113">为此，可以使用 Exchange Online 中的就地电子数据展示工具在用户邮箱中搜索已删除的电子邮件和其他项目（如联系人、日历约会和任务）。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-113">You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox.</span></span> <span data-ttu-id="f4ce5-114">如果找到已删除的项目，则可以将其导出到 PST 文件 (也称为 Outlook 数据文件) ，然后用户可以使用该文件将项目还原回其邮箱。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-114">If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="f4ce5-115">以下是恢复用户邮箱中已删除项目的步骤。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-115">Here are the steps for recovering deleted items in a user's mailbox.</span></span> <span data-ttu-id="f4ce5-116">这将花费多长时间？</span><span class="sxs-lookup"><span data-stu-id="f4ce5-116">How long will this take?</span></span> <span data-ttu-id="f4ce5-117">第一次可能需要20或30分钟才能完成所有步骤，具体取决于尝试恢复的项目数。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-117">The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f4ce5-118">您必须是 Microsoft 365 中的 **Exchange 管理员** 或 **全局管理员** ，或者是 exchange Online 中的 "组织管理" 角色组的成员，才能执行本文中的步骤。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-118">You have to be an **Exchange administrator** or **Global administrator** in Microsoft 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article.</span></span> <span data-ttu-id="f4ce5-119">有关详细信息，请参阅[关于 Microsoft 365 管理员角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-119">For more information, see [About Microsoft 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="f4ce5-120">步骤1：为自己分配电子数据展示权限</span><span class="sxs-lookup"><span data-stu-id="f4ce5-120">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="f4ce5-121"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="f4ce5-121"><a name="step1"> </a></span></span>

<span data-ttu-id="f4ce5-122">第一步是在 Exchange Online 中为自己分配必要的权限，以便您可以使用就地电子数据展示工具搜索用户的邮箱。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-122">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox.</span></span> <span data-ttu-id="f4ce5-123">只需执行一次此操作。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-123">You only have to do this once.</span></span> <span data-ttu-id="f4ce5-124">如果您需要在将来搜索另一个邮箱，可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-124">If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="f4ce5-125">在何处登录到使用工作或学校帐户的[Microsoft 365 的公司](https://support.microsoft.com/office/where-to-sign-into-microsoft-365-for-business-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-125">[Where to sign in to Microsoft 365 for business](https://support.microsoft.com/office/where-to-sign-into-microsoft-365-for-business-e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="f4ce5-126">在左上角的 Microsoft 365 中选择应用启动器图标， ![ ](../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) 然后单击 " **管理**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-126">Select the app launcher icon ![The app launcher icon in Microsoft 365](../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="f4ce5-127">在 Microsoft 365 管理中心的左侧导航中，展开 " **管理中心**"，然后单击 " **Exchange**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-127">In the left navigation in the Microsoft 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![管理中心列表](../media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="f4ce5-129">在 Exchange 管理中心中，单击 " **权限**"，然后单击 " **管理角色**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-129">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="f4ce5-130">在列表视图中，选择 "**发现管理**"，然后单击 "**编辑** ![ 编辑图标" ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) 。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-130">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![将自己添加到 EAC 中的 "发现管理" 角色组中](../media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="f4ce5-132">在 "**角色组**" 中的 "**成员**" 下，单击 "**添加** ![ 添加图标" ](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) 。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-132">In **Role Group**, under **Members**, click **Add**![Add icon](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="f4ce5-133">在 " **选择成员**" 中，从名称列表中选择自己，单击 " **添加**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-133">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="f4ce5-134">您还可以添加您所属的组，例如 "组织管理" 或 "TenantAdmins"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-134">You can also add a group that you are a member of, such as Organization Management or TenantAdmins.</span></span> <span data-ttu-id="f4ce5-135">如果添加一个组，则会向该组的其他成员分配运行就地电子数据展示工具所需的权限。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-135">If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="f4ce5-136">在 " **角色组**" 中，单击 " **保存**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-136">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="f4ce5-137">注销 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-137">Sign out of Microsoft 365.</span></span>
    
    <span data-ttu-id="f4ce5-138">必须先注销，然后才能开始下一步，以便新权限生效。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-138">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="f4ce5-139">发现管理角色组的成员可以访问敏感邮件内容。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-139">Members of the Discovery Management role group can access sensitive message content.</span></span> <span data-ttu-id="f4ce5-140">这包括搜索组织中的所有邮箱、预览搜索结果 (和其他邮箱项目) 、将结果复制到发现邮箱，以及将搜索结果导出到 PST 文件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-140">This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="f4ce5-141">Return to top</span><span class="sxs-lookup"><span data-stu-id="f4ce5-141">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="f4ce5-142">步骤2：在用户的邮箱中搜索已删除的项目</span><span class="sxs-lookup"><span data-stu-id="f4ce5-142">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="f4ce5-143"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="f4ce5-143"><a name="step2"> </a></span></span>

<span data-ttu-id="f4ce5-144">当您运行就地电子数据展示搜索时，搜索中的邮箱中的 "可恢复的项目" 文件夹将自动包含在搜索中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-144">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search.</span></span> <span data-ttu-id="f4ce5-145">"可恢复的项目" 文件夹是指永久删除的项目在被清除 (从邮箱中永久删除) 之前的存储位置。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-145">The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox.</span></span> <span data-ttu-id="f4ce5-146">因此，如果尚未清除某个项目，则应该能够使用就地电子数据展示工具找到它。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-146">So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="f4ce5-147">在何处登录到使用工作或学校帐户的[Microsoft 365 的公司](https://support.microsoft.com/office/where-to-sign-into-microsoft-365-for-business-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-147">[Where to sign in to Microsoft 365 for business](https://support.microsoft.com/office/where-to-sign-into-microsoft-365-for-business-e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="f4ce5-148">在左上角的 Microsoft 365 中选择应用启动器图标， ![ ](../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) 然后单击 " **管理**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-148">Select the app launcher icon ![The app launcher icon in Microsoft 365](../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="f4ce5-149">在 Microsoft 365 管理中心的左侧导航中，展开 " **管理员**"，然后单击 " **Exchange**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-149">In the left navigation in the Microsoft 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="f4ce5-150">在 Exchange 管理中心中，单击 "**合规性管理**"，单击 "**就地电子数据展示 &amp; 保留**"，然后单击 "**新建** ![ 添加图标" ](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) 。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-150">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![在 EAC 中的 "合规性管理" 页上，单击 "就地电子数据展示和保留"](../media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="f4ce5-152">在 " **名称和说明** " 页上，键入搜索 (的名称，例如，要恢复其电子邮件的用户的名称) 的名称，可选说明，然后单击 " **下一步**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-152">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="f4ce5-153">在 "**邮箱**" 页上，单击 "**指定要搜索的邮箱**"，然后单击 "**添加**" "添加" ![ 图标 ](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) 。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-153">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![单击 "指定要搜索的邮箱" 以搜索表列邮箱](../media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="f4ce5-155">查找并选择要恢复已删除电子邮件的用户的名称，单击 " **添加**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-155">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="f4ce5-156">单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-156">Click **Next**.</span></span>
    
    <span data-ttu-id="f4ce5-157">将显示 " **搜索查询** " 页。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-157">The **Search query** page is displayed.</span></span> <span data-ttu-id="f4ce5-158">你可以在此处定义搜索条件，以帮助你查找用户邮箱中缺少的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-158">This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="f4ce5-159">在“搜索查询”\*\*\*\* 页上，填写下列字段：</span><span class="sxs-lookup"><span data-stu-id="f4ce5-159">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="f4ce5-160">**包含所有内容** 选择此选项可将用户邮箱中的所有内容包含在搜索结果中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-160">**Include all content** Select this option to include all content in the user's mailbox in the search results.</span></span> <span data-ttu-id="f4ce5-161">如果您选择此选项，则无法指定其他搜索条件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-161">If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="f4ce5-162">**基于条件进行筛选** 选择此选项以指定搜索条件，包括关键词、开始和结束日期、发件人和收件人地址以及邮件类型。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-162">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![根据条件（如关键字、日期范围、收件人和邮件类型）生成搜索](../media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="f4ce5-164">**Field**</span><span class="sxs-lookup"><span data-stu-id="f4ce5-164">**Field**</span></span>|<span data-ttu-id="f4ce5-165">**使用以下各 .。。**</span><span class="sxs-lookup"><span data-stu-id="f4ce5-165">**Use this to...**</span></span>|
|:-----|:-----|
|![粉色圆圈中的数字 1](../media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="f4ce5-167">指定关键字、日期范围、收件人和邮件类型。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-167">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![粉色圆圈中的数字 2。](../media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="f4ce5-169">搜索带关键字或短语的邮件，并使用逻辑运算符（如 **and** 或 **or**）。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-169">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![粉色圆圈中的数字 3。](../media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="f4ce5-171">搜索在某个日期范围内发送或接收的邮件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-171">Search for messages sent or received within a date range.</span></span>  <br/> |
|![粉色圆圈中的数字 4。](../media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="f4ce5-173">搜索从特定人员接收或发送的邮件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-173">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![粉红色圆圈中的5号。](../media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="f4ce5-175">搜索所有邮件类型或选择特定的邮件类型。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-175">Search for all message types or select specific ones.</span></span>  <br/> |
   
   > [!TIP]
   >  <span data-ttu-id="f4ce5-176">以下是有关如何构建搜索查询以查找缺失项目的一些提示。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-176">Here are a few tips about how to build a search query to find missing items.</span></span> <span data-ttu-id="f4ce5-177">尝试从用户处获取尽可能多的信息，以帮助您创建搜索查询，以便您可以找到要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-177">Try to get as much information from the user to help you create a search query so you can find what you're looking for.</span></span> <span data-ttu-id="f4ce5-178">如果您不确定如何查找缺失的邮件，请考虑使用 " **包括所有内容** " 选项。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-178">If you are not sure how to find a missing message, consider using the **Include all content** option.</span></span> <span data-ttu-id="f4ce5-179">搜索结果将包含用户的 "可恢复的项目" 文件夹中的所有项目，包括隐藏文件夹 (称为 "清除文件夹") 包含已被用户清除的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-179">The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user.</span></span> <span data-ttu-id="f4ce5-180">然后，您可以转到步骤3，将结果复制到发现邮箱，并查看隐藏文件夹中的邮件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-180">Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder.</span></span> <span data-ttu-id="f4ce5-181">如果您知道用户最初何时发送或接收丢失的邮件，请使用 " **指定开始日期** " 和 " **指定结束日期** " 选项提供日期范围。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-181">If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range.</span></span> <span data-ttu-id="f4ce5-182">这将返回该日期范围内用户发送或接收的所有邮件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-182">This will return all messages sent or received by the user within that date range.</span></span> <span data-ttu-id="f4ce5-183">指定日期范围是缩小搜索结果范围的一种非常好的方法。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-183">Specifying a date range is a really good way to narrow the search results.</span></span> <span data-ttu-id="f4ce5-184">如果您知道缺少的电子邮件的发件人，请使用 " **发** 件人" 框指定此发件人。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-184">If you know who sent the missing email, use the **From** box to specify this sender.</span></span> <span data-ttu-id="f4ce5-185">如果要将搜索结果缩小为不同类型的邮箱项目，请单击 " **选择邮件类型**"，单击 **"选择要搜索的邮件类型**"，然后选择要搜索的特定邮件类型。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-185">If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for.</span></span> <span data-ttu-id="f4ce5-186">例如，可以仅搜索日历项目或联系人。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-186">For example, you can search only for calendar items or contacts.</span></span> <span data-ttu-id="f4ce5-187">以下是您可以搜索的不同邮件类型的屏幕截图。默认值为搜索所有邮件类型。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-187">Here's a screenshot of the different message types you can search for; the default is to search for all message types.</span></span> 
  
   <span data-ttu-id="f4ce5-188">完成**搜索查询**页后，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-188">Click **Next** when you've completed the **Search query** page.</span></span> 
    
10. <span data-ttu-id="f4ce5-189">在 " **就地保留设置** " 页上，单击 " **完成** " 以启动搜索。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-189">On the **In-Place Hold settings** page, click **Finish** to start the search.</span></span> <span data-ttu-id="f4ce5-190">若要恢复已删除的电子邮件，没有理由将用户的邮箱置于保留状态。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-190">To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="f4ce5-191">启动搜索后，Exchange 将根据您指定的条件显示搜索将返回的总大小和项目数的估计值。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-191">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="f4ce5-192">选择刚刚创建的搜索，然后单击 "**刷新** ![ 刷新" ](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) 以更新详细信息窗格中显示的信息。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-192">Select the search you just created and click **Refresh**![refresh](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane.</span></span> <span data-ttu-id="f4ce5-193">" **估计成功** 状态" 指示搜索已完成。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-193">The status of **Estimate Succeeded** indicates that the search has finished.</span></span> <span data-ttu-id="f4ce5-194">Exchange 还会根据您在步骤9中指定的搜索条件，在搜索找到的项目总数 (及其大小) 中显示估计。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-194">Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="f4ce5-195">在 "详细信息" 窗格中，单击 " **预览搜索结果** " 以查看找到的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-195">In the details pane, click **Preview search results** to view the items that were found.</span></span> <span data-ttu-id="f4ce5-196">这可能会帮助您确定要查找的项目 (s) 。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-196">This might help you identify the item(s) that you're looking for.</span></span> <span data-ttu-id="f4ce5-197">如果您在尝试恢复时发现项目 (s) ，请转到步骤4，将搜索结果导出到 PST 文件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-197">If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![单击 "预览搜索结果" 查看你尝试恢复的项目](../media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="f4ce5-199">如果找不到您要查找的内容，可以通过选择搜索，单击 "**编辑** ![ 编辑图标 ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) "，然后单击 "**搜索查询**" 来修改搜索条件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-199">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**.</span></span> <span data-ttu-id="f4ce5-200">更改搜索条件，然后重新运行搜索。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-200">Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="f4ce5-201">Return to top</span><span class="sxs-lookup"><span data-stu-id="f4ce5-201">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="f4ce5-202"> (可选) 步骤3：将搜索结果复制到发现邮箱</span><span class="sxs-lookup"><span data-stu-id="f4ce5-202">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="f4ce5-203"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="f4ce5-203"><a name="step3"> </a></span></span>

<span data-ttu-id="f4ce5-204">如果您无法通过预览搜索结果找到项目，或者如果您想要查看用户的 "可恢复的项目" 文件夹中的项目，则可以将搜索结果复制到名为 "发现邮箱" 的特殊邮箱 () 然后在 web 上的 Outlook 中打开该邮箱以查看实际项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-204">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items.</span></span> <span data-ttu-id="f4ce5-205">复制搜索结果的最佳原因是，您可以查看用户的 "可恢复的项目" 文件夹中的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-205">The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder.</span></span> <span data-ttu-id="f4ce5-206">您尝试恢复的项目很可能位于 "清除" 子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-206">More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="f4ce5-207">在 Exchange 管理中心中，转到 " **合规性管理**就地 \> **电子数据展示 &amp; 保留**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-207">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="f4ce5-208">在搜索列表中，选择您在步骤2中创建的搜索。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-208">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="f4ce5-209">单击 "**搜索** ![ 搜索 ](../media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png) "，然后从下拉列表中单击 "**复制搜索结果**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-209">Click **Search**![search](../media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![单击 "搜索"，然后单击 "复制搜索结果"](../media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="f4ce5-211">在 " **复制搜索结果** " 页上，单击 " **浏览**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-211">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![恢复已删除的项目时，不选择保留复选框](../media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="f4ce5-213">在 " **显示名称**" 下，单击 " **发现搜索邮箱**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-213">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![将搜索结果复制到默认发现搜索邮箱](../media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="f4ce5-215">发现搜索邮箱是在 Microsoft 365 组织中自动创建的默认发现邮箱。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-215">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Microsoft 365 organization.</span></span> 
  
6. <span data-ttu-id="f4ce5-216">返回到 " **复制搜索结果** " 页上，单击 " **复制** " 以开始将搜索结果复制到发现搜索邮箱的过程。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-216">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![单击 "复制" 将搜索结果复制到发现搜索邮箱](../media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="f4ce5-218">单击 "**刷新** ![ 刷新" ](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) 以更新有关显示在详细信息窗格中的复制状态的信息。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-218">Click **Refresh**![refresh](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="f4ce5-219">复制完成后，单击 " **打开** " 以打开 "发现搜索" 邮箱查看搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-219">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![单击 "打开" 转到 "发现搜索" 邮箱以查看搜索结果](../media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="f4ce5-221">复制到发现搜索邮箱的搜索结果放置在与就地电子数据展示搜索同名的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-221">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search.</span></span> <span data-ttu-id="f4ce5-222">您可以单击一个文件夹以显示该文件夹中的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-222">You can click a folder to display the items in that folder.</span></span>
    
    ![发现搜索邮箱中的搜索结果;"清除" 文件夹中的项目只能由管理员恢复](../media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="f4ce5-224">运行搜索时，也会搜索用户的 "可恢复的项目" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-224">When you run a search, the user's Recoverable Items folder is also searched.</span></span> <span data-ttu-id="f4ce5-225">这意味着，如果 "可恢复的项目" 文件夹中的项目满足搜索条件，则这些项目将包含在搜索结果中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-225">That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results.</span></span> <span data-ttu-id="f4ce5-226">"删除邮件" 文件夹中的项目是指用户通过从 "已删除邮件" 文件夹中删除项目或通过选择它并按 **Shift + Delete** (永久删除的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-226">Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**.</span></span> <span data-ttu-id="f4ce5-227">用户可以使用 Outlook 或 web 上的 Outlook 中的 "恢复已删除邮件" 工具恢复删除文件夹中的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-227">A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder.</span></span> <span data-ttu-id="f4ce5-228">"清除" 文件夹中的项目是用户使用 "恢复已删除项目" 工具清除的项目，或者是应用于邮箱的策略自动清除的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-228">Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox.</span></span> <span data-ttu-id="f4ce5-229">在这两种情况下，只有管理员才能恢复 "清除" 文件夹中的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-229">In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="f4ce5-230">如果用户无法使用 "可恢复的项目" 工具找到已删除的项目，但该项目仍是可恢复的 (意味着它没有从邮箱) 中永久删除，则很可能位于 "清除" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-230">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder.</span></span> <span data-ttu-id="f4ce5-231">因此，请务必在 "清除" 文件夹中查找要为用户尝试恢复的已删除项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-231">So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="f4ce5-232">Return to top</span><span class="sxs-lookup"><span data-stu-id="f4ce5-232">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="f4ce5-233">步骤4：将搜索结果导出到 PST 文件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-233">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="f4ce5-234"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="f4ce5-234"><a name="step4"> </a></span></span>

<span data-ttu-id="f4ce5-235">在您找到要为用户尝试恢复的项目后，下一步是将在步骤2中运行的搜索的结果导出到 PST 文件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-235">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file.</span></span> <span data-ttu-id="f4ce5-236">用户将在下一步中使用此 PST 文件，将已删除的项目还原到其邮箱。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-236">The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="f4ce5-237">在 Exchange 管理中心中，转到 " **合规性管理**就地 \> **电子数据展示 &amp; 保留**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-237">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="f4ce5-238">在搜索列表中，选择您在步骤2中创建的搜索。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-238">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="f4ce5-239">单击 " **导出到 PST 文件**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-239">Click **Export to a PST file**.</span></span>
    
    ![单击 "导出到 PST 文件"](../media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="f4ce5-241">如果系统提示您安装电子数据展示导出工具，请单击 " **运行**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-241">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="f4ce5-242">在 "电子数据展示 PST 导出" 工具中，单击 " **浏览** " 以指定要下载 PST 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-242">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![电子数据展示 PST 导出工具](../media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="f4ce5-244">您可以忽略选项以启用重复数据删除并包括不可搜索项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-244">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="f4ce5-245">单击 " **开始** " 将 PST 文件下载到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-245">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="f4ce5-246">**电子数据展示 PST 导出工具**显示有关导出过程的状态信息。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-246">The **eDiscovery PST Export Tool** displays status information about the export process.</span></span> <span data-ttu-id="f4ce5-247">导出完成后，可以在文件的下载位置访问该文件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-247">When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="f4ce5-248">Return to top</span><span class="sxs-lookup"><span data-stu-id="f4ce5-248">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="f4ce5-249">步骤5：将已恢复的项目还原到用户的邮箱</span><span class="sxs-lookup"><span data-stu-id="f4ce5-249">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="f4ce5-250"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="f4ce5-250"><a name="step5"> </a></span></span>

<span data-ttu-id="f4ce5-251">最后一步是使用在步骤4中导出的 PST 文件将已恢复的项目还原到用户的邮箱中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-251">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox.</span></span> <span data-ttu-id="f4ce5-252">将 PST 文件发送给用户后，用户将执行此步骤的其余部分，以打开 PST 文件，然后将恢复的项目移至其邮箱中的其他文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-252">After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox.</span></span> <span data-ttu-id="f4ce5-253">对于分步说明，您还可以向用户发送指向此主题的链接： [打开和关闭 Outlook 数据文件 ( .pst) ](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-253">For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span></span> <span data-ttu-id="f4ce5-254">或者，您可以使用下面的 "PST 文件" 部分向用户发送一个指向 " [还原已删除邮件](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) " 的链接，并要求他们执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-254">Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="f4ce5-255">**将 PST 文件发送给用户**</span><span class="sxs-lookup"><span data-stu-id="f4ce5-255">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="f4ce5-256">需要执行的最后一步是将在步骤4中导出的 PST 文件发送给用户。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-256">The final step that you need to perform is sending the PST file that was exported in step 4 to the user.</span></span> <span data-ttu-id="f4ce5-257">有几种方法可以实现此目的：</span><span class="sxs-lookup"><span data-stu-id="f4ce5-257">There are a few ways to do this:</span></span>
  
- <span data-ttu-id="f4ce5-258">将 PST 文件附加到电子邮件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-258">Attach the PST file to an email message.</span></span> <span data-ttu-id="f4ce5-259">如果将 Outlook 配置为阻止 PST 文件，则必须压缩该文件，然后将其附加到邮件中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-259">If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message.</span></span> <span data-ttu-id="f4ce5-260">操作步骤如下：</span><span class="sxs-lookup"><span data-stu-id="f4ce5-260">Here's how:</span></span>
    
1. <span data-ttu-id="f4ce5-261">在 Windows 资源管理器或文件资源管理器中，浏览到 PST 文件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-261">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="f4ce5-262">右键单击该文件，然后选择 " **发送到** \> **压缩 (压缩) " 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-262">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**.</span></span> <span data-ttu-id="f4ce5-263">Windows 将创建一个新的 zip 文件，并为其提供与 PST 文件相同的名称。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-263">Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="f4ce5-264">将压缩的 PST 文件附加到电子邮件，并将其发送给用户，然后可以通过单击该文件来对其进行解压缩。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-264">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="f4ce5-265">将 PST 文件复制到用户可访问和检索的共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-265">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="f4ce5-266">下一节中的步骤由用户执行，以将已删除的项目还原到其邮箱。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-266">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <a name="restoredeleteditems"></a>
<span data-ttu-id="f4ce5-267">**使用 PST 文件将已删除邮件还原到邮箱**</span><span class="sxs-lookup"><span data-stu-id="f4ce5-267">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="f4ce5-268">您必须使用 Outlook 桌面应用程序使用 PST 文件还原已删除的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-268">You have to use the Outlook desktop app to restore a deleted item by using a PST file.</span></span> <span data-ttu-id="f4ce5-269">您不能使用 Outlook Web App 或 Web 上的 Outlook 打开 PST 文件。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-269">You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="f4ce5-270">在 Outlook 2013 或 Outlook 2016 中，单击 " **文件** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-270">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="f4ce5-271">单击 " **打开 &amp; 导出**"，然后单击 " **打开 Outlook 数据文件**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-271">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="f4ce5-272">浏览到您保存管理员发送的 PST 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-272">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="f4ce5-273">选择该 PST，然后单击 " **打开**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-273">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="f4ce5-274">PST 文件显示在 Outlook 的左侧导航栏中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-274">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST 文件显示在 Outlook 的左侧导航栏中](../media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="f4ce5-276">单击箭头以展开 PST 文件以及它下面的文件夹，找到要恢复的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-276">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![在 "清除" 文件夹中查找要恢复的项目](../media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="f4ce5-278">在 "清除" 文件夹中查找要恢复的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-278">Look in the Purges folder for the item you want to recover.</span></span> <span data-ttu-id="f4ce5-279">这是清除的项目移至的隐藏文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-279">This is a hidden folder that purged items are moved to.</span></span> <span data-ttu-id="f4ce5-280">您的管理员恢复的项目很可能在此文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-280">It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="f4ce5-281">右键单击要恢复的项目，然后单击 " **移动** \> **其他文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-281">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![单击 "移动"，然后选择 "其他文件夹"](../media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="f4ce5-283">若要将项目移到收件箱中，请单击 **"收件箱**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-283">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="f4ce5-284">**提示：** 若要恢复其他类型的项目，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="f4ce5-284">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="f4ce5-285">若要恢复日历项目，请右键单击该项目，然后单击 " **移动** \> **其他文件夹** \> **日历**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-285">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="f4ce5-286">若要恢复某个联系人，请右键单击该联系人，然后单击 " **移动** \> **其他文件夹** \> **联系人**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-286">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="f4ce5-287">若要恢复某个任务，请右键单击该任务，然后单击 " **移动** \> **其他文件夹** \> **任务**"。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-287">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![选择文件夹以移动其他类型的项目](../media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
   > [!NOTE]
   > <span data-ttu-id="f4ce5-289">日历项目、联系人和任务直接位于 "清除" 文件夹中，而不是在 "日历"、"联系人" 或 "任务" 子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-289">Calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder.</span></span> <span data-ttu-id="f4ce5-290">不过，您可以按 **类型** 进行排序，以将相似类型的项目分组。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-290">However, you can sort by **Type** to group similar types of items.</span></span> 
    
8. <span data-ttu-id="f4ce5-291">完成恢复已删除项目后，右键单击左侧导航栏中的 PST 文件，然后选择 **"关闭" "pst 文件的名称"**。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-291">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="f4ce5-292">Return to top</span><span class="sxs-lookup"><span data-stu-id="f4ce5-292">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md)
  
## <a name="more-information"></a><span data-ttu-id="f4ce5-293">详细信息</span><span class="sxs-lookup"><span data-stu-id="f4ce5-293">More information</span></span>
<span data-ttu-id="f4ce5-294"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="f4ce5-294"><a name="moreinfo"> </a></span></span>

- <span data-ttu-id="f4ce5-295">如果项目的已删除项目保留期尚未过期，则用户可能会恢复永久删除的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-295">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired.</span></span> <span data-ttu-id="f4ce5-296">作为管理员，您可能已指定 "可恢复的项目" 文件夹中的项目可用于恢复的时间。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-296">As an admin you may have specified how long items in the Recoverable Items folder are available for recovery.</span></span> <span data-ttu-id="f4ce5-297">例如，可能存在一个策略，用于删除用户的 "已删除邮件" 文件夹中的30天内的任何内容，以及允许用户将 "可恢复的项目" 文件夹中的项目恢复到另一个14天的其他策略。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-297">For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days.</span></span> <span data-ttu-id="f4ce5-298">但是，在此14天之后，您可能仍可以使用本主题中的过程恢复用户邮箱中的项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-298">However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="f4ce5-299">如果项目尚未清除且已删除项目的保留期尚未过期，则用户可以恢复已删除项目。</span><span class="sxs-lookup"><span data-stu-id="f4ce5-299">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired.</span></span> <span data-ttu-id="f4ce5-300">若要帮助用户恢复邮箱中的已删除邮件，请将其指向下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="f4ce5-300">To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="f4ce5-301">在 Outlook for Windows 中恢复已删除项目</span><span class="sxs-lookup"><span data-stu-id="f4ce5-301">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="f4ce5-302">在 Outlook 2010 中恢复已删除邮件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-302">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="f4ce5-303">在 Outlook Web App 中恢复已删除项目或电子邮件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-303">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="f4ce5-304">在 web 上的 Outlook 中还原已删除的电子邮件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-304">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="f4ce5-305">在 Outlook 中恢复已删除的联系人</span><span class="sxs-lookup"><span data-stu-id="f4ce5-305">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="f4ce5-306">在 Outlook.com 中还原已删除的电子邮件</span><span class="sxs-lookup"><span data-stu-id="f4ce5-306">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="f4ce5-307">Return to top</span><span class="sxs-lookup"><span data-stu-id="f4ce5-307">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md)
  

