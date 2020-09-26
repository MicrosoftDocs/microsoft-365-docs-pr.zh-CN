---
title: 创建保留标签并在应用中应用它们来保留或删除内容
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 介绍了如何创建和发布保留标签，以便能够在应用中应用它们，从而保留所需内容，并删除不需要内容
ms.openlocfilehash: 478a0d9952d8e8e33ef88926ba2415276338c193
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "48198511"
---
# <a name="create-retention-labels-and-apply-them-in-apps"></a><span data-ttu-id="4e46d-103">创建保留标签并在应用中应用它们</span><span class="sxs-lookup"><span data-stu-id="4e46d-103">Create retention labels and apply them in apps</span></span>

><span data-ttu-id="4e46d-104">*[Microsoft 365 安全性与合规性许可指南](https://aka.ms/ComplianceSD)。*</span><span class="sxs-lookup"><span data-stu-id="4e46d-104">*[Microsoft 365 licensing guidance for security & compliance](https://aka.ms/ComplianceSD).*</span></span>

> [!NOTE]
> <span data-ttu-id="4e46d-105">此方案受所有保留标签配置（包括 [规章记录](records-management.md#records)）的支持。</span><span class="sxs-lookup"><span data-stu-id="4e46d-105">This scenario is supported for all retention label configurations, including [regulatory records](records-management.md#records).</span></span>

<span data-ttu-id="4e46d-106">请参阅以下信息来帮助你创建和发布[保留标签](retention.md)，然后向文档和电子邮件应用它们。</span><span class="sxs-lookup"><span data-stu-id="4e46d-106">Use the following information to help you create and publish [retention labels](retention.md), and then apply them to documents and emails.</span></span>

<span data-ttu-id="4e46d-107">保留标签有助于在项（文档或电子邮件）级别保留所需内容，并删除不需要内容。</span><span class="sxs-lookup"><span data-stu-id="4e46d-107">Retention labels help you retain what you need and delete what you don't at the item level (document or email).</span></span> <span data-ttu-id="4e46d-108">它们还用于将项声明为记录，作为 Microsoft 365 数据的[记录管理](records-management.md)解决方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e46d-108">They are also used to declare an item as a record as part of a [records management](records-management.md) solution for your Microsoft 365 data.</span></span>

<span data-ttu-id="4e46d-109">使保留标签对组织中的人员可用以便对内容进行分类的过程分为两个步骤：</span><span class="sxs-lookup"><span data-stu-id="4e46d-109">Making retention labels available to people in your organization so that they can classify content is a two-step process:</span></span> 

1. <span data-ttu-id="4e46d-110">创建保留标签</span><span class="sxs-lookup"><span data-stu-id="4e46d-110">Create the retention labels</span></span>

2. <span data-ttu-id="4e46d-111">使用保留标签策略发布保留标签</span><span class="sxs-lookup"><span data-stu-id="4e46d-111">Publish the retention labels by using a retention label policy</span></span>
  
![标签角色和任务的关系图](../media/4082bc7d-c04c-4b9a-8a26-7f12565d3311.png)

<span data-ttu-id="4e46d-113">请按照以下说明来执行两个管理步骤。</span><span class="sxs-lookup"><span data-stu-id="4e46d-113">Use the following instructions for the two admin steps.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="4e46d-114">准备工作</span><span class="sxs-lookup"><span data-stu-id="4e46d-114">Before you begin</span></span>

<span data-ttu-id="4e46d-115">组织的全局管理员拥有创建和编辑保留标签及其策略的完全权限。</span><span class="sxs-lookup"><span data-stu-id="4e46d-115">The global admin for your organization has full permissions to create and edit retention labels and their policies.</span></span> <span data-ttu-id="4e46d-116">如果你没有以全局管理员身份登录，请参阅[创建和管理保留策略和保留标签所需的权限](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels)。</span><span class="sxs-lookup"><span data-stu-id="4e46d-116">If you aren't signing in as a global admin, see [Permissions required to create and manage retention policies and retention labels](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels).</span></span>

## <a name="how-to-create-and-publish-retention-labels"></a><span data-ttu-id="4e46d-117">如何创建和发布保留标签</span><span class="sxs-lookup"><span data-stu-id="4e46d-117">How to create and publish retention labels</span></span>

<span data-ttu-id="4e46d-118">首先，创建保留标签。</span><span class="sxs-lookup"><span data-stu-id="4e46d-118">First, create your retention labels.</span></span> <span data-ttu-id="4e46d-119">然后，创建标签策略，让标签可以在应用中应用。</span><span class="sxs-lookup"><span data-stu-id="4e46d-119">Then create a label policy to make the labels available to apply in apps.</span></span>

<span data-ttu-id="4e46d-120">创建和配置保留标签的位置取决于你是否使用记录管理。</span><span class="sxs-lookup"><span data-stu-id="4e46d-120">Where you create and configure your retention labels depend on whether you're using records management or not.</span></span> <span data-ttu-id="4e46d-121">针对这两种情况提供了说明。</span><span class="sxs-lookup"><span data-stu-id="4e46d-121">Instructions are provided for both scenarios.</span></span>

### <a name="step-1-create-retention-labels"></a><span data-ttu-id="4e46d-122">第 1 步：创建保留标签</span><span class="sxs-lookup"><span data-stu-id="4e46d-122">Step 1: Create retention labels</span></span>

1. <span data-ttu-id="4e46d-123">在 [Microsoft 365 合规中心](https://compliance.microsoft.com/)，导航到以下位置之一：</span><span class="sxs-lookup"><span data-stu-id="4e46d-123">In the [Microsoft 365 compliance center](https://compliance.microsoft.com/), navigate to one of the following locations:</span></span>
    
    - <span data-ttu-id="4e46d-124">如果你正在使用记录管理：</span><span class="sxs-lookup"><span data-stu-id="4e46d-124">If you are using records management:</span></span>
        - <span data-ttu-id="4e46d-125">“**解决方案**” > “**记录管理**” > “**文件计划**”选项卡 > + “**创建标签**” > “**保留标签**”</span><span class="sxs-lookup"><span data-stu-id="4e46d-125">**Solutions** > **Records management** > **File plan** tab > **+ Create a label** > **Retention label**</span></span>
        
    - <span data-ttu-id="4e46d-126">如果你没有使用记录管理：</span><span class="sxs-lookup"><span data-stu-id="4e46d-126">If you are not using records management:</span></span>
       - <span data-ttu-id="4e46d-127">“**解决方案**” > “**信息治理**” > “**标签**”选项卡 > +“**创建标签**”</span><span class="sxs-lookup"><span data-stu-id="4e46d-127">**Solutions** > **Information governance** > **Labels** tab > + **Create a label**</span></span>
    
    <span data-ttu-id="4e46d-128">没有立即看到你的选项？</span><span class="sxs-lookup"><span data-stu-id="4e46d-128">Don't immediately see your option?</span></span> <span data-ttu-id="4e46d-129">首先选择“**全部显示**”。</span><span class="sxs-lookup"><span data-stu-id="4e46d-129">First select **Show all**.</span></span> 

2. <span data-ttu-id="4e46d-130">按照向导中的提示进行操作。</span><span class="sxs-lookup"><span data-stu-id="4e46d-130">Follow the prompts in the wizard.</span></span> <span data-ttu-id="4e46d-131">如果你正在使用记录管理：</span><span class="sxs-lookup"><span data-stu-id="4e46d-131">If you are using records management:</span></span>
    
    - <span data-ttu-id="4e46d-132">有关文件计划描述符的信息，请参阅[使用文件计划管理保留标签](file-plan-manager.md)</span><span class="sxs-lookup"><span data-stu-id="4e46d-132">For information about the file plan descriptors, see [Use file plan to manage retention labels](file-plan-manager.md)</span></span>
    
    - <span data-ttu-id="4e46d-133">若要使用保留标签来声明记录，请选择 **“将项目标记为记录”**，或者 **“将项目标记为合规性记录”**。</span><span class="sxs-lookup"><span data-stu-id="4e46d-133">To use the retention label to declare records, select **Mark items as records**, or **Mark items as regulatory records**.</span></span> <span data-ttu-id="4e46d-134">有关详细信息，请参阅[配置保留标签以声明记录](declare-records.md#configuring-retention-labels-to-declare-records)。</span><span class="sxs-lookup"><span data-stu-id="4e46d-134">For more information, see [Configuring retention labels to declare records](declare-records.md#configuring-retention-labels-to-declare-records).</span></span>

3. <span data-ttu-id="4e46d-135">创建标签后，你会看到发布标签、自动应用标签或仅保存标签的选项，请选择“**现在仅保存标签**”，然后选择“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="4e46d-135">After you have created the label and you see the options to publish the label, auto-apply the label, or just save the label: Select **Just save the label for now**, and then select **Done**.</span></span>

4. <span data-ttu-id="4e46d-136">重复这些步骤以创建更多标签。</span><span class="sxs-lookup"><span data-stu-id="4e46d-136">Repeat these steps to create more labels.</span></span>

<span data-ttu-id="4e46d-137">若要编辑现有标签，请将其选中，然后选择“**编辑标签**”来启动“编辑保留向导”，这个向导使你能够更改来自第 2 步的标签说明和任何[符合条件的设置](#updating-retention-labels-and-their-policies)。</span><span class="sxs-lookup"><span data-stu-id="4e46d-137">To edit an existing label, select it, and then select the **Edit label** option to start the Edit retention wizard that lets you change the label descriptions and any [eligible settings](#updating-retention-labels-and-their-policies) from step 2.</span></span>

### <a name="step-2-publish-retention-labels"></a><span data-ttu-id="4e46d-138">第 2 步：发布保留标签</span><span class="sxs-lookup"><span data-stu-id="4e46d-138">Step 2: Publish retention labels</span></span>

<span data-ttu-id="4e46d-139">发布保留标签，以便用户可以在 SharePoint 和 Outlook 等应用中应用它们。</span><span class="sxs-lookup"><span data-stu-id="4e46d-139">Publish retention labels so that they can be applied by users in apps, such as SharePoint and Outlook.</span></span>

1. <span data-ttu-id="4e46d-140">在 [Microsoft 365 合规中心](https://compliance.microsoft.com/)，导航到以下位置之一：</span><span class="sxs-lookup"><span data-stu-id="4e46d-140">In the [Microsoft 365 compliance center](https://compliance.microsoft.com/), navigate to one of the following locations:</span></span>
    
    - <span data-ttu-id="4e46d-141">如果你正在使用记录管理：</span><span class="sxs-lookup"><span data-stu-id="4e46d-141">If you are using records management:</span></span>
        - <span data-ttu-id="4e46d-142">“**解决方案**” > “**记录管理**”> >“**标签策略**”选项卡 >“**发布标签**”</span><span class="sxs-lookup"><span data-stu-id="4e46d-142">**Solutions** > **Records management** > > **Label policies** tab > **Publish labels**</span></span>
    
    - <span data-ttu-id="4e46d-143">如果你没有使用记录管理：</span><span class="sxs-lookup"><span data-stu-id="4e46d-143">If you are not using records management:</span></span>
        - <span data-ttu-id="4e46d-144">“**解决方案**” > “**信息治理**” > “**标签策略**”选项卡 >“**发布标签**”</span><span class="sxs-lookup"><span data-stu-id="4e46d-144">**Solutions** > **Information governance** > **Label policies** tab > **Publish labels**</span></span>
    
    <span data-ttu-id="4e46d-145">没有立即看到你的选项？</span><span class="sxs-lookup"><span data-stu-id="4e46d-145">Don't immediately see your option?</span></span> <span data-ttu-id="4e46d-146">首先选择“**全部显示**”。</span><span class="sxs-lookup"><span data-stu-id="4e46d-146">First select **Show all**.</span></span> 

2. <span data-ttu-id="4e46d-147">按照向导中的提示进行操作。</span><span class="sxs-lookup"><span data-stu-id="4e46d-147">Follow the prompts in the wizard.</span></span>
    
    <span data-ttu-id="4e46d-148">有关保留标签支持的位置的信息，请参阅[保留标签和位置](retention.md#retention-label-policies-and-locations)部分。</span><span class="sxs-lookup"><span data-stu-id="4e46d-148">For information about the locations supported by retention labels, see the [Retention labels and locations](retention.md#retention-label-policies-and-locations) section.</span></span> 

<span data-ttu-id="4e46d-149">若要编辑现有的保留标签策略（策略类型是“**发布**”）"，请选择它，然后选择“**编辑**”选项，以启动“编辑保留策略”。</span><span class="sxs-lookup"><span data-stu-id="4e46d-149">To edit an existing retention label policy (the policy type is **Publish**), select it, and then select the **Edit** option to start the Edit retention policy.</span></span> <span data-ttu-id="4e46d-150">此向导可用于更改来自第 2 步的策略描述和任何[符合条件的设置](#updating-retention-labels-and-their-policies)。</span><span class="sxs-lookup"><span data-stu-id="4e46d-150">This wizard lets you change the policy description and any [eligible settings](#updating-retention-labels-and-their-policies) from step 2.</span></span>


## <a name="when-retention-labels-become-available-to-apply"></a><span data-ttu-id="4e46d-151">当保留标签可应用时</span><span class="sxs-lookup"><span data-stu-id="4e46d-151">When retention labels become available to apply</span></span>

<span data-ttu-id="4e46d-152">如果你将保留标签发布到 SharePoint 或 OneDrive，这些标签通常会在 1 天内出现，以供最终用户选择。</span><span class="sxs-lookup"><span data-stu-id="4e46d-152">If you publish retention labels to SharePoint or OneDrive, those labels  typically appear for end users to select within one day.</span></span> <span data-ttu-id="4e46d-153">不过，最长可能需要 7 天才能显示。</span><span class="sxs-lookup"><span data-stu-id="4e46d-153">However, allow up to seven days.</span></span> 

<span data-ttu-id="4e46d-154">如果你将保留标签发布到 Exchange，这些保留标签最长可能需要 7 天才能向最终用户显示，并且邮箱至少必须包含 10MB 数据。</span><span class="sxs-lookup"><span data-stu-id="4e46d-154">If you publish retention labels to Exchange, it can take up to seven days for those retention labels to appear for end users, and the mailbox must contain at least 10 MB of data.</span></span>

<span data-ttu-id="4e46d-155">例如：</span><span class="sxs-lookup"><span data-stu-id="4e46d-155">For example:</span></span>
  
![手动标签生效时间关系图](../media/b19f3a10-f625-45bf-9a53-dd14df02ae7c.png)
  

### <a name="how-to-check-on-the-status-of-retention-labels-published-to-exchange"></a><span data-ttu-id="4e46d-157">如何检查发布到 Exchange 的保留标签的状态</span><span class="sxs-lookup"><span data-stu-id="4e46d-157">How to check on the status of retention labels published to Exchange</span></span>

<span data-ttu-id="4e46d-158">在 Exchange Online 中，保留标签通过每 7 天运行一次的进程向最终用户提供。</span><span class="sxs-lookup"><span data-stu-id="4e46d-158">In Exchange Online, retention labels are made available to end users by a process that runs every seven days.</span></span> <span data-ttu-id="4e46d-159">通过 Powershell，可看到此进程上次运行的时间，并进而确定其再次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="4e46d-159">By using PowerShell, you can see when this process last ran and therefore identify when it will run again.</span></span>
  
1. <span data-ttu-id="4e46d-160">[连接到 Exchange Online PowerShell](https://go.microsoft.com/fwlink/?linkid=799773)。</span><span class="sxs-lookup"><span data-stu-id="4e46d-160">[Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?linkid=799773).</span></span>
    
2. <span data-ttu-id="4e46d-161">运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="4e46d-161">Run these commands.</span></span>
    
   ```powershell
   $logProps = Export-MailboxDiagnosticLogs <user> -ExtendedProperties
   ```

   ```powershell
   $xmlprops = [xml]($logProps.MailboxLog)
   ```

   ```powershell
   $xmlprops.Properties.MailboxTable.Property | ? {$_.Name -like "ELC*"}   ```

In the results, the `ELCLastSuccessTimeStamp` (UTC) property shows when the system last processed your mailbox. If it has not happened since the time you created the policy, the labels are not going to appear. To force processing, run  `Start-ManagedFolderAssistant -Identity <user>`.
    
If labels aren't appearing in Outlook on the web and you think they should be, make sure to clear the cache in your browser (CTRL+F5).
    

## How to apply published retention labels

Use the following sections to learn how published retention labels can be applied in apps:

- [Manually apply retention labels](#manually-apply-retention-labels)

- [Applying a default retention label to all content in a SharePoint library, folder, or document set](#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set)

- [Automatically applying a retention label to email by using rules](#automatically-applying-a-retention-label-to-email-by-using-rules)

### Manually apply retention labels 

End users, as well as administrators, can manually apply retention labels from the following locations:  

- Outlook and Outlook on the web
    
- OneDrive
    
- SharePoint
    
- Microsoft 365 groups (both the group site and group mailbox in Outlook on the web)
    
Use the following sections to understand how to apply retention labels. 

#### Applying retention labels in Outlook

To label an item in the Outlook desktop client, select the item. On the **Home** tab on the ribbon, click **Assign Policy**, and then choose the retention label. 
  
![Assign Policy button](../media/30684dea-dd73-4e4a-9185-8e29f403b6ca.png)
  
You can also right-click an item, click **Assign Policy** in the context menu, and then choose the retention label. 

After the retention label is applied, you can view that retention label and what action it takes at the top of the item. If an email has a retention label applied that has an associated retention period, you can see at a glance when the email expires.
  
You can also apply retention labels to folders, in which case:
  
- All items in the folder automatically get the same retention label, **except** for items that have had a retention label applied explicitly to them. Explicitly labeled items keep their existing retention label. For more information, see [The principles of retention, or what takes precedence?](retention.md#the-principles-of-retention-or-what-takes-precedence) section on this page. 
    
- If you change or remove the default retention label for a folder, the retention label's also changed or removed for all items in the folder, **except** items with explicitly assigned retention labels. 
    
- If you move an item with a default retention label from one folder to another folder with a different default retention label, the item gets the new default retention label.
    
- If you move an item with a default retention label from one folder to another folder with no default retention label, the old default retention label is removed.

#### Applying retention labels in Outlook on the web

To label an item in Outlook on the web, right-click the item \> **Assign policy** \> choose the retention label. 
  
![Assign policy menu in Outlook on the web](../media/146a23cf-e478-4595-b2e8-f707fc4e6ea3.png)
  
After the retention label is applied, you can view that retention label and what action it takes at the top of the item. If an email is classified and has an associated retention period, you can know at a glance when the email will expire.
  
![Label assigned to email in Outlook on the web](../media/16f6c91b-5eab-4574-9d13-6d12be00a783.png)
  
As with Outlook on the web, you can also apply retention labels to folders. 

#### Applying retention labels in OneDrive and SharePoint

To label a document (including OneNote files) in OneDrive or SharePoint, select the item \> in the upper-right corner, choose **Open the details pane**![Information pane icon](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) \> **Apply retention label** \> choose the retention label. 
  
You can also apply a retention label to a folder or document set, and you can set a [default retention label for a document library](#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set).
  
![Apply label list for an item in SharePoint](../media/151cc83c-da57-45b0-9cd1-fd2f28a31083.png)
  
After a retention label is applied to an item, you can view it in the details pane when that item's selected.
  
![Applied label shown in Details pane](../media/d06e585e-29f7-4c8c-afef-629c97268b8e.png)
  
For SharePoint, but not OneDrive, you can create a view of the library that contains the **Labels** column or **Item is a Record** column. This view lets you see at a glance the retention labels assigned to all items and which items are records. Note, however, that you can't filter the view by the **Item is a Record** column. For instructions how to add columns, see [Show or hide columns in a list or library](https://support.microsoft.com/en-us/office/show-or-hide-columns-in-a-list-or-library-b820db0d-9e3e-4ff9-8b8b-0b2dbefa87e2).


#### Applying retention labels in Microsoft 365 groups

When you publish retention labels to Microsoft 365 groups ([formerly Office 365 groups](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)), the retention labels appear in both the group site and group mailbox in Outlook on the web. The experience of applying a retention label to content is identical to that for email and documents.

To retain content for a Microsoft 365 group, use the **Office 365 groups** location. Even though a Microsoft 365 group has an Exchange mailbox, a retention policy that includes the entire Exchange location won't include content in Microsoft 365 group mailboxes.

In addition, it's not possible to use the Exchange location to include or exclude a specific group mailbox. Although the Exchange location initially allows a group mailbox to be selected, when you try to save the retention policy, you receive an error that "RemoteGroupMailbox" is not a valid selection for the Exchange location.
  
First, create and configure the sensitivity labels that you want to make available for apps and other services. For example, the labels you want users to see and apply from Office apps. 

Then, create one or more label policies that contain the labels and policy settings that you configure. It's the label policy that publishes the labels and settings for your chosen users and locations.

### Applying a default retention label to all content in a SharePoint library, folder, or document set

This method requires retention labels to be published to a retention label policy.

In addition to enabling people to apply a retention label to individual documents, you can also apply a default retention label to a SharePoint library, folder, or document set, so that all documents in that location get the default retention label.
  
For a document library, this is done on the **Library settings** page for a document library. When you choose the default retention label, you can also choose to apply it to existing items in the library. 
  
For example, if you have a tag for marketing materials, and you know a specific document library contains only that type of content, you can make the Marketing Materials tag the default for all documents in that library.
  
![Apply label option on library Settings page](../media/0787d651-63dc-43b4-8768-716a5ecc64ec.png)
  
If you apply a default retention label to existing items in the library, folder, or document set:
  
- All items in the library, folder, or document set automatically get the same retention label, **except** for items that have had a retention label applied explicitly to them (such as records). Explicitly labeled items keep their existing label. For more information, see the below section on [The principles of retention, or what takes precedence](retention.md#the-principles-of-retention-or-what-takes-precedence).
    
- If you change or remove the default retention label for a library, folder, or document set, the retention label is also changed or removed for all items in the library, folder, or document set, **except** items with explicit retention labels (such as records).
    
- If you move an item with a default retention label from one site collection, library, folder, or document set to another site collection, library, folder, or document set that has a different label, the item keeps its existing default retention label, even if the new location has a different default retention label. If the item does not have a label before moving, it will take on the default retention label of the new location.

**Records:** If you apply a default record label to a library, folder, or document set, then a record label is applied to all the individual items within those locations. When you move a new item into a location with a record label, that item is labeled a record. However, if you change the default retention label to a label that doesn't declare content as a record, that action does not remove the record label from the individual items; those items retain their record label. Only a site collection admin can explicitly remove or change the retention label of record items.

For more information about retention labels that declare content as a record, see [Records](records-management.md#records).

### Automatically applying a retention label to email by using rules

In Outlook, you can create rules to apply a retention label.
  
For example, you can create a rule that applies a specific retention label to all messages sent to or from a specific distribution group.
  
To create a rule, right-click an item \> **Rules** \> **Create Rule** \> **Advanced Options** \> **Rules Wizard** \> **apply retention policy**.
  
![Rules wizard with option to apply retention policies](../media/eeb2407c-15b6-4224-99cf-e0a00034d8ea.png)

Although the UI refers to retention policies, it's your retention labels that display here and can be selected, not your retention policies.

## Updating retention labels and their policies

When you edit a retention label or retention label policy, and the retention label or policy is already applied to content, your updated settings will automatically be applied to this content in addition to content that's newly identified.

Some settings can't be changed after the label or policy is created and saved, which include:
- The retention settings except the retention period, unless you've configured the label to retain or delete the content based on when it was created.
- The option to classify as a record.

## Next steps

Event-based retention is another supported scenario for retention labels. For more information, see the following articles:

- [Start retention when an event occurs](event-driven-retention.md)
- [Automate event-based retention](automate-event-driven-retention.md)
- [Use retention labels to manage the lifecycle of documents stored in SharePoint](auto-apply-retention-labels-scenario.md)
