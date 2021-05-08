---
title: 步骤 4 - 向另一名员工授予OneDrive和Outlook权限
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: 按照以下步骤为另一名员工授予对前员工的数据OneDrive Outlook访问权限。
ms.openlocfilehash: 451f8f7f50098c280e3925ef4efe5ad491ac54fa
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244161"
---
# <a name="step-4---give-another-employee-access-to-onedrive-and-outlook-data"></a><span data-ttu-id="badf7-103">步骤 4 - 向另一名员工授予OneDrive和Outlook权限</span><span class="sxs-lookup"><span data-stu-id="badf7-103">Step 4 - Give another employee access to OneDrive and Outlook data</span></span>

<span data-ttu-id="badf7-104">当员工离开组织时，你将希望访问其 OneDrive 并Outlook数据，备份数据，并选择是否将该数据授予其他员工。</span><span class="sxs-lookup"><span data-stu-id="badf7-104">When an employee leaves your organization, you'll want to access their OneDrive and Outlook data, back it up, and choose whether to give it to another employee.</span></span>
  
## <a name="access-a-former-users-onedrive-documents"></a><span data-ttu-id="badf7-105">访问以前用户的OneDrive文档</span><span class="sxs-lookup"><span data-stu-id="badf7-105">Access a former user's OneDrive documents</span></span>

<span data-ttu-id="badf7-106">如果您删除用户的许可证但不删除帐户，您可以为自己授予访问用户许可证中的内容OneDrive。</span><span class="sxs-lookup"><span data-stu-id="badf7-106">If you remove a user's license but don't delete the account, you can give yourself access to the content in the user's OneDrive.</span></span> <span data-ttu-id="badf7-107">如果删除用户帐户，则默认情况下你有 30 天的时间访问前用户OneDrive数据。</span><span class="sxs-lookup"><span data-stu-id="badf7-107">If you delete the user's account, you have 30 days by default to access the former user's OneDrive data.</span></span> <span data-ttu-id="badf7-108">[了解如何为已删除OneDrive设置保留时间](/onedrive/set-retention)。</span><span class="sxs-lookup"><span data-stu-id="badf7-108">[Learn how to set the OneDrive retention for deleted users](/onedrive/set-retention).</span></span> <span data-ttu-id="badf7-109">如果您在此时间内[没有还原用户帐户，则](/office365/admin/add-users/restore-user)其OneDrive内容将被删除。</span><span class="sxs-lookup"><span data-stu-id="badf7-109">If you don't [restore a user account](/office365/admin/add-users/restore-user) within this time, their OneDrive content is deleted.</span></span>

<span data-ttu-id="badf7-110">若要保留以前用户OneDrive文件，请首先向自己授予OneDrive访问权限，然后移动要保留的文件。</span><span class="sxs-lookup"><span data-stu-id="badf7-110">To preserve a former user's OneDrive files, first give yourself access to their OneDrive, and then move the files you want to keep.</span></span>

1. <span data-ttu-id="badf7-111">在管理中心，转到“**用户**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">活动用户</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="badf7-111">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.</span></span>  

2. <span data-ttu-id="badf7-112">选择用户。</span><span class="sxs-lookup"><span data-stu-id="badf7-112">Select a user.</span></span>

3. <span data-ttu-id="badf7-113">在右侧窗格中，选择 **"OneDrive"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-113">In the right pane, select **OneDrive**.</span></span> <span data-ttu-id="badf7-114">在 **"获取对文件的访问权限"下**，**选择"创建指向文件的链接"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-114">Under **Get access to files**, select **Create link to files**.</span></span>

4. <span data-ttu-id="badf7-115">选择链接以打开文件位置。</span><span class="sxs-lookup"><span data-stu-id="badf7-115">Select the link to open the file location.</span></span> <span data-ttu-id="badf7-116">将文件下载到计算机，或选择"移动到"或"复制"以将这些文件移动或复制到您自己的OneDrive或复制到共享库。</span><span class="sxs-lookup"><span data-stu-id="badf7-116">Download the files to your computer, or select **Move to** or **Copy to** to move or copy them to your own OneDrive or to a shared library.</span></span>

> [!NOTE]
> <span data-ttu-id="badf7-117">一次可以移动或复制多达 500 MB 的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="badf7-117">You can move or copy up to 500 MB of files and folders at a time.</span></span><br/>
> <span data-ttu-id="badf7-118">在移动或复制具有版本历史记录的文档时，只会移动最新版本。</span><span class="sxs-lookup"><span data-stu-id="badf7-118">When you move or copy documents that have version history, only the latest version is moved.</span></span>  

### <a name="revoke-admin-access-to-a-users-onedrive"></a><span data-ttu-id="badf7-119">撤销管理员对用户权限OneDrive</span><span class="sxs-lookup"><span data-stu-id="badf7-119">Revoke admin access to a user's OneDrive</span></span>

<span data-ttu-id="badf7-120">您可以向自己授予对用户网站中OneDrive的访问权限，但您可能想要在不再需要该内容时删除您的访问权限。</span><span class="sxs-lookup"><span data-stu-id="badf7-120">You can give yourself access to the content in a user's OneDrive, but you may want to remove your access when you no longer need it.</span></span>

1. <span data-ttu-id="badf7-121">以全局<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">管理员或管理员</a>管理员SharePoint管理中心。</span><span class="sxs-lookup"><span data-stu-id="badf7-121">Sign in to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">admin center</a> as a global admin or SharePoint admin.</span></span>

    <span data-ttu-id="badf7-122">如果您收到一条消息，指出您无权访问管理中心，则表明您组织中没有管理员权限。</span><span class="sxs-lookup"><span data-stu-id="badf7-122">If you get a message that you don't have permission to access the admin center, then you don't have administrator permissions in your organization.</span></span>

2. <span data-ttu-id="badf7-123">在左窗格中，选择"管理 **中心** \> **SharePoint"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-123">In the left pane, select **Admin centers** \> **SharePoint**.</span></span> <span data-ttu-id="badf7-124">（你可能需要选择“**全部显示**”以查看管理中心列表）。</span><span class="sxs-lookup"><span data-stu-id="badf7-124">(You might need to select **Show all** to see the list of admin centers.)</span></span>

3. <span data-ttu-id="badf7-125">如果显示经典SharePoint管理中心，请选择页面顶部的"现在打开它"以打开SharePoint管理中心。</span><span class="sxs-lookup"><span data-stu-id="badf7-125">If the classic SharePoint admin center appears, select **Open it now** at the top of the page to open the SharePoint admin center.</span></span>

4. <span data-ttu-id="badf7-126">在左窗格中，选择"**更多功能"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-126">In the left pane, select **More features**.</span></span>

5. <span data-ttu-id="badf7-127">在 **"用户配置文件"下**，选择"打开 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-127">Under **User profiles**, select **Open**.</span></span>

6. <span data-ttu-id="badf7-128">在 **"人员**"下，选择 **"管理用户配置文件"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-128">Under **People**, select **Manage User Profiles**.</span></span>

7. <span data-ttu-id="badf7-129">输入用户的名称，然后选择"查找 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-129">Enter the user's name and select **Find**.</span></span>

8. <span data-ttu-id="badf7-130">右键单击用户，然后选择"管理 **网站集所有者"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-130">Right-click the user, and then choose **Manage site collection owners**.</span></span>

9. <span data-ttu-id="badf7-131">删除不再需要访问用户数据的用户，然后选择"确定 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-131">Remove the person who no longer needs access to the user's data, and then select **OK**.</span></span>

## <a name="access-the-outlook-data-of-a-former-user"></a><span data-ttu-id="badf7-132">访问Outlook用户的数据</span><span class="sxs-lookup"><span data-stu-id="badf7-132">Access the Outlook data of a former user</span></span>

<span data-ttu-id="badf7-133">若要保存以前员工的电子邮件、日历、任务和联系人，将信息导出到 Outlook 数据文件 (.pst) 。</span><span class="sxs-lookup"><span data-stu-id="badf7-133">To save the email messages, calendar, tasks, and contacts of the former employee, export the information to an Outlook Data File (.pst).</span></span>
  
1. <span data-ttu-id="badf7-134">[将前员工的电子邮件添加到](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b)你的邮箱Outlook (如果你重置用户密码，你可以将其[](reset-passwords.md)设置为仅你知道) </span><span class="sxs-lookup"><span data-stu-id="badf7-134">[Add the former employee's email](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b) to your Outlook (If you [reset the user's password](reset-passwords.md), you can set it to something only you know.)</span></span>

2. <span data-ttu-id="badf7-135">在Outlook中，选择"文件 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-135">In Outlook, select **File**.</span></span>

    ![这是功能区在自定义Outlook 2016。](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. <span data-ttu-id="badf7-137">选择 **"打开 &amp; 导出** \> **导入/导出"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-137">Select **Open &amp; Export** \> **Import/Export**.</span></span>

    ![导入/导出 Backstage 视图中运行命令](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. <span data-ttu-id="badf7-139">选择 **"导出到文件"，** 然后选择"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-139">Select **Export to a file**, and then select **Next**.</span></span>

    ![导入和导出向导中的"导出到文件"选项](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. <span data-ttu-id="badf7-141">选择 **Outlook数据文件 (.pst) "，** 然后选择"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-141">Select **Outlook Data File (.pst)**, and then select **Next**.</span></span>

6. <span data-ttu-id="badf7-142">通过选择名称或电子邮件地址（如 Mailbox - Anne Weiler 或 anne@contoso.com）选择要导出的帐户。</span><span class="sxs-lookup"><span data-stu-id="badf7-142">Select the account you want to export by selecting the name or email address, such as Mailbox - Anne Weiler or anne@contoso.com.</span></span> <span data-ttu-id="badf7-143">如果要导出帐户中的所有内容，包括邮件、日历、联系人、任务和备注，请确保选中"包括子文件夹"复选框。 </span><span class="sxs-lookup"><span data-stu-id="badf7-143">If you want to export everything in your account, including mail, calendar, contacts, tasks, and notes, make sure the **Include subfolders** check box is selected.</span></span>

    > [!NOTE]
    > <span data-ttu-id="badf7-144">可以一次导出一个帐户。</span><span class="sxs-lookup"><span data-stu-id="badf7-144">You can export one account at a time.</span></span> <span data-ttu-id="badf7-145">如果要导出多个帐户，在导出一个帐户后，重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="badf7-145">If you want to export multiple accounts, after one account is exported, repeat these steps.</span></span>
  
    ![导出Outlook"数据文件"对话框，其中选中了顶部文件夹并选中了"包含子文件夹"](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. <span data-ttu-id="badf7-147">选择“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="badf7-147">Select **Next**.</span></span>

8. <span data-ttu-id="badf7-148">选择 **"浏览**"选择保存Outlook文件 (.pst) 。</span><span class="sxs-lookup"><span data-stu-id="badf7-148">Select **Browse** to select where to save the Outlook Data File (.pst).</span></span> <span data-ttu-id="badf7-149">键入  *文件名，* 然后选择" **确定"** 继续。</span><span class="sxs-lookup"><span data-stu-id="badf7-149">Type a  *file name*, and then select **OK** to continue.</span></span>

    > [!NOTE]
    > <span data-ttu-id="badf7-150">如果之前使用过导出，则显示上一个文件夹位置和文件名。</span><span class="sxs-lookup"><span data-stu-id="badf7-150">If you've used export before, the previous folder location and file name appear.</span></span> <span data-ttu-id="badf7-151">在选择  *"确定"之前，*  键入其他 **文件名**。</span><span class="sxs-lookup"><span data-stu-id="badf7-151">Type a  *different file name*  before selecting **OK**.</span></span>
  
9. <span data-ttu-id="badf7-152">如果要导出到现有 Outlook 数据文件 (.pst)，请在" **选项**"下指定文件中已存在导出项目时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="badf7-152">If you are exporting to an existing Outlook Data File (.pst), under **Options**, specify what to do when exporting items that already exist in the file.</span></span>

10. <span data-ttu-id="badf7-153">选择 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="badf7-153">Select **Finish**.</span></span>

<span data-ttu-id="badf7-154">Outlook，除非已创建新的 Outlook Data File (.pst) 或使用了密码保护的文件，否则将立即开始导出。</span><span class="sxs-lookup"><span data-stu-id="badf7-154">Outlook begins the export immediately unless a new Outlook Data File (.pst) is created or a password-protected file is used.</span></span>
  
- <span data-ttu-id="badf7-155">如果要创建一个Outlook.pst (.pst) ，则可选密码可以帮助保护文件。</span><span class="sxs-lookup"><span data-stu-id="badf7-155">If you're creating an Outlook Data File (.pst), an optional password can help protect the file.</span></span> <span data-ttu-id="badf7-156">当出现 **"Outlook数据文件**"对话框时，在"密码"和"验证密码"框中键入密码，然后选择"确定 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-156">When the **Create Outlook Data File** dialog box appears, type the  *password*  in the **Password** and **Verify Password** boxes, and then select **OK**.</span></span> <span data-ttu-id="badf7-157">在 **"Outlook数据文件密码**"对话框中，键入 *密码*，然后选择"确定 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-157">In the **Outlook Data File Password** dialog box, type the  *password*, and then select **OK**.</span></span>

- <span data-ttu-id="badf7-158">如果要导出到受密码保护的现有 Outlook 数据文件 (.pst) ，请在 **"Outlook** 数据文件密码"对话框中，键入密码，然后选择"确定 **"。** </span><span class="sxs-lookup"><span data-stu-id="badf7-158">If you're exporting to an existing Outlook Data File (.pst) that is password protected, in the **Outlook Data File Password** dialog box, type the  *password*, and then select **OK**.</span></span>

<span data-ttu-id="badf7-159">请参阅如何在 Outlook 2010 中将电子邮件、联系人和日历导出或备份到 Outlook [.pst](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91)文件。</span><span class="sxs-lookup"><span data-stu-id="badf7-159">See how to [Export or backup email, contacts, and calendar to an Outlook .pst file](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) in Outlook 2010.</span></span>

  > [!NOTE]
  > <span data-ttu-id="badf7-160">默认情况下，您的电子邮件在 12 个月内脱机可用。</span><span class="sxs-lookup"><span data-stu-id="badf7-160">By default, your email is available offline for a period of 12 months.</span></span> <span data-ttu-id="badf7-161">如果需要，请参阅如何 [增加脱机可用的数据](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized)。</span><span class="sxs-lookup"><span data-stu-id="badf7-161">If required, see how to [increase the data available offline](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized).</span></span>

### <a name="give-another-user-access-to-a-former-users-email"></a><span data-ttu-id="badf7-162">向其他用户授予对以前用户的电子邮件的访问权限</span><span class="sxs-lookup"><span data-stu-id="badf7-162">Give another user access to a former user's email</span></span>

<span data-ttu-id="badf7-163">若要向另一名员工授予对前员工的电子邮件、日历、任务和联系人的访问权限，将信息导入另一个员工的Outlook收件箱。</span><span class="sxs-lookup"><span data-stu-id="badf7-163">To give access to the email messages, calendar, tasks, and contacts of the former employee to another employee, import the information to another employee's Outlook inbox.</span></span>

> [!NOTE]
> <span data-ttu-id="badf7-164">还可以将 [以前用户的邮箱转换为](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) 共享邮箱，或将以前员工的电子邮件转发 [给另一名员工](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox)。</span><span class="sxs-lookup"><span data-stu-id="badf7-164">You can also [convert the former user's mailbox to a shared mailbox](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) or [forward a former employee's email to another employee](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox).</span></span>

1. <span data-ttu-id="badf7-165">In Outlook， go to **File** \> **Open &amp; Export** \> **导入/导出**.</span><span class="sxs-lookup"><span data-stu-id="badf7-165">In Outlook, go to **File** \> **Open &amp; Export** \> **Import/Export**.</span></span>

    <span data-ttu-id="badf7-166">这将启动导入和导出向导。</span><span class="sxs-lookup"><span data-stu-id="badf7-166">This starts the Import and Export Wizard.</span></span>

2. <span data-ttu-id="badf7-167">选择 **"从另一个程序或文件导入**"，然后选择"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-167">Select **Import from another program or file**, and then select **Next**.</span></span>

    ![导入和导出向导](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. <span data-ttu-id="badf7-169">选择 **Outlook数据文件 (.pst) "，** 然后选择"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-169">Select **Outlook Data File (.pst)**, and select **Next**.</span></span>

4. <span data-ttu-id="badf7-170">浏览到要导入的 .pst 文件。</span><span class="sxs-lookup"><span data-stu-id="badf7-170">Browse to the .pst file you want to import.</span></span>

5. <span data-ttu-id="badf7-171">在 **"选项**"下，选择如何处理重复项</span><span class="sxs-lookup"><span data-stu-id="badf7-171">Under **Options**, choose how you want to deal with duplicates</span></span>

6. <span data-ttu-id="badf7-172">选择“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="badf7-172">Select **Next**.</span></span>

7. <span data-ttu-id="badf7-173">如果将密码分配给 Outlook.pst (.pst) ，请输入密码，然后选择"确定 **"。**</span><span class="sxs-lookup"><span data-stu-id="badf7-173">If a password was assigned to the Outlook Data File (.pst), enter the password, and then select **OK**.</span></span>

8. <span data-ttu-id="badf7-174">设置用于导入项目的选项。</span><span class="sxs-lookup"><span data-stu-id="badf7-174">Set the options for importing items.</span></span> <span data-ttu-id="badf7-175">默认设置通常不需要更改。</span><span class="sxs-lookup"><span data-stu-id="badf7-175">The default settings usually don't need to be changed.</span></span>

9. <span data-ttu-id="badf7-176">选择 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="badf7-176">Select **Finish**.</span></span>

> [!NOTE]
> <span data-ttu-id="badf7-177">访问现有用户的邮箱和电子邮件数据的步骤OneDrive相同。</span><span class="sxs-lookup"><span data-stu-id="badf7-177">The steps remain the same for accessing an existing user's OneDrive and email data.</span></span>

> [!TIP]
> <span data-ttu-id="badf7-178">如果希望仅导入或还原 Outlook Data File (.pst) 中的几个项目，可以打开 Outlook 数据文件。</span><span class="sxs-lookup"><span data-stu-id="badf7-178">If you want to import or restore only a few items from an Outlook Data File (.pst), you can open the Outlook Data File.</span></span> <span data-ttu-id="badf7-179">然后，在导航窗格中，将项目从Outlook数据文件文件夹拖动到现有Outlook文件夹中。</span><span class="sxs-lookup"><span data-stu-id="badf7-179">Then, in the navigation pane, drag the items from Outlook Data File folders to your existing Outlook folders.</span></span> 

## <a name="related-articles"></a><span data-ttu-id="badf7-180">相关文章</span><span class="sxs-lookup"><span data-stu-id="badf7-180">Related articles</span></span>

[<span data-ttu-id="badf7-181">在帐户上添加OneDrive管理员</span><span class="sxs-lookup"><span data-stu-id="badf7-181">Add and remove admins on a OneDrive account</span></span>](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive)

[<span data-ttu-id="badf7-182">还原已删除OneDrive</span><span class="sxs-lookup"><span data-stu-id="badf7-182">Restore a deleted OneDrive</span></span>](/onedrive/restore-deleted-onedrive)
  
[<span data-ttu-id="badf7-183">OneDrive 保留和删除</span><span class="sxs-lookup"><span data-stu-id="badf7-183">OneDrive retention and deletion</span></span>](/onedrive/retention-and-deletion)