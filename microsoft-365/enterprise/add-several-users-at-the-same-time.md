---
title: 同时将多个用户添加到 Microsoft 365-管理员帮助
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: '了解如何从电子表格或其他 CSV 格式的文件中的列表向 Microsoft 365 for business 中添加多个用户。 观看 YouTube 上的视频，说明如何将帐户添加到 Microsoft 365。 在此过程结束时，拥有帐户的每位用户都将拥有一个 Microsoft 365 邮箱。 '
ms.openlocfilehash: a970fbfa28214543e34011f1310742c6fb811d09
ms.sourcegitcommit: 34ebec8e2bd54ba3d4ccfd9724797665c965c17f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071509"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a><span data-ttu-id="00358-105">同时将多个用户添加到 Microsoft 365-管理员帮助</span><span class="sxs-lookup"><span data-stu-id="00358-105">Add several users at the same time to Microsoft 365 - Admin Help</span></span>

<span data-ttu-id="00358-106">团队中的每个人都需要用户帐户，才能登录并访问 Microsoft 365 服务，例如电子邮件和 Office。</span><span class="sxs-lookup"><span data-stu-id="00358-106">Each person on your team needs a user account before they can sign in and access Microsoft 365 services, such as email and Office.</span></span> <span data-ttu-id="00358-107">如果有很多人，则可以从 Excel 电子表格或以 CSV 格式保存的其他文件中一次添加所有帐户。</span><span class="sxs-lookup"><span data-stu-id="00358-107">If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format.</span></span> [<span data-ttu-id="00358-108">不确定哪种 CSV 格式？</span><span class="sxs-lookup"><span data-stu-id="00358-108">Not sure what CSV format is?</span></span>](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> <span data-ttu-id="00358-109">如果未使用新的 Microsoft 365 管理中心，可通过选择“ **试用新的管理中心** ”切换按钮（位于主页顶部）将其打开。</span><span class="sxs-lookup"><span data-stu-id="00358-109">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a><span data-ttu-id="00358-110">在 Microsoft 365 管理中心中添加多个用户</span><span class="sxs-lookup"><span data-stu-id="00358-110">Add multiple users in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="00358-111">使用工作或学校帐户登录 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="00358-111">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="00358-112">在 "管理中心" 中，选择 " **用户** \> **活动用户** "。</span><span class="sxs-lookup"><span data-stu-id="00358-112">In the admin center, choose **Users** \> **Active users**.</span></span>

3. <span data-ttu-id="00358-113">选择 " **添加多个用户** "。</span><span class="sxs-lookup"><span data-stu-id="00358-113">Select **Add multiple users**.</span></span>

4. <span data-ttu-id="00358-114">在 " **导入多个用户** " 面板上，您可以选择下载带有或不带填充样本数据的示例 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="00358-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    <span data-ttu-id="00358-115">您的电子表格需要包含与示例 (用户名、名字等) 中的 **完全相同的列标题** 。</span><span class="sxs-lookup"><span data-stu-id="00358-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, and so on).</span></span> <span data-ttu-id="00358-116">如果使用模板，请在文本编辑工具（如记事本）中打开它，并考虑仅保留第1行中的所有数据，并且仅在第2行和更低的行中输入数据。</span><span class="sxs-lookup"><span data-stu-id="00358-116">If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="00358-117">您的电子表格还需要包含用户名的值 (如 bob@contoso.com) ，以及与每个用户的 Bob 凯利)  (类似的显示名称。</span><span class="sxs-lookup"><span data-stu-id="00358-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="00358-118">在框中输入文件路径，或选择 " **浏览** " 浏览 CSV 文件位置，然后选择 " **验证** "。</span><span class="sxs-lookup"><span data-stu-id="00358-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
  
    <span data-ttu-id="00358-119">如果文件有问题，则会在面板中显示该问题。</span><span class="sxs-lookup"><span data-stu-id="00358-119">If there are problems with the file, the problem is displayed in the panel.</span></span> <span data-ttu-id="00358-120">您还可以下载日志文件。</span><span class="sxs-lookup"><span data-stu-id="00358-120">You can also download a log file.</span></span>
    
5. <span data-ttu-id="00358-121">在 " **设置用户选项** " 对话框中，您可以设置登录状态，并选择将分配给所有用户的产品许可证。</span><span class="sxs-lookup"><span data-stu-id="00358-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="00358-122">在 " **查看您的结果** " 对话框中，您可以选择将结果发送给您自己或其他用户 (密码将以纯文本) ，并且您可以查看已创建的用户数，以及是否需要购买更多许可证以分配给某些新用户。</span><span class="sxs-lookup"><span data-stu-id="00358-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="00358-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="00358-123">Next steps</span></span>
<span data-ttu-id="00358-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="00358-124"><a name="bk_preview"> </a></span></span>

- <span data-ttu-id="00358-125">现在，这些人拥有帐户，需要在 [电脑或 Mac 上下载并安装或重新安装 Microsoft 365 或 Office 2016](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)。</span><span class="sxs-lookup"><span data-stu-id="00358-125">Now that these people have accounts, they need to [Download and install or reinstall Microsoft 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="00358-126">你的团队中的每个人都可以在最高5台电脑或 Mac 上安装 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="00358-126">Each person on your team can install Microsoft 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="00358-127">每个人还可以在最大5个平板电脑和5个电话（例如 Iphone、Ipad 和 Android 电话和平板电脑）上的 [移动设备上设置 Office 应用和电子邮件](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) 。</span><span class="sxs-lookup"><span data-stu-id="00358-127">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="00358-128">这样一来，他们就可以从任何位置编辑 Office 文件。</span><span class="sxs-lookup"><span data-stu-id="00358-128">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="00358-129">有关安装步骤的端到端列表，请参阅 [设置 Microsoft 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) 。</span><span class="sxs-lookup"><span data-stu-id="00358-129">See [Set up Microsoft 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a><span data-ttu-id="00358-130">有关如何将用户添加到 Microsoft 365 的详细信息</span><span class="sxs-lookup"><span data-stu-id="00358-130">More information about how to add users to Microsoft 365</span></span>
<span data-ttu-id="00358-131"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="00358-131"><a name="bk_preview"> </a></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="00358-132">不确定哪种 CSV 格式？</span><span class="sxs-lookup"><span data-stu-id="00358-132">Not sure what CSV format is?</span></span>
<span data-ttu-id="00358-133"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="00358-133"><a name="__toc316652088"> </a></span></span>

<span data-ttu-id="00358-134">CSV 文件是一个包含以逗号分隔的值的文件。</span><span class="sxs-lookup"><span data-stu-id="00358-134">A CSV file is a file with comma separated values.</span></span> <span data-ttu-id="00358-135">您可以使用任何文本编辑器或电子表格程序（如 Excel）创建或编辑此类文件。</span><span class="sxs-lookup"><span data-stu-id="00358-135">You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="00358-136">您可以将 [此示例电子表格](https://www.microsoft.com/download/details.aspx?id=45485) 作为起始点下载。</span><span class="sxs-lookup"><span data-stu-id="00358-136">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point.</span></span> <span data-ttu-id="00358-137">请记住，Microsoft 365 要求在第一行中有列标题，因此不要将其替换为其他内容。</span><span class="sxs-lookup"><span data-stu-id="00358-137">Remember that Microsoft 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="00358-138">使用新名称保存该文件，并指定 CSV 格式。</span><span class="sxs-lookup"><span data-stu-id="00358-138">Save the file with a new name, and specify CSV format.</span></span>
  
![如何将 Excel 中的文件保存为 CSV 格式的图像](../media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="00358-140">保存文件时，您可能会收到提示，如果您以 CSV 格式保存文件，则工作簿中的某些功能将丢失。</span><span class="sxs-lookup"><span data-stu-id="00358-140">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format.</span></span> <span data-ttu-id="00358-141">这没关系。</span><span class="sxs-lookup"><span data-stu-id="00358-141">This is okay.</span></span> <span data-ttu-id="00358-142">单击" **是** "即可继续。</span><span class="sxs-lookup"><span data-stu-id="00358-142">Click **Yes** to continue.</span></span> 
  
![您可能会收到的提示的图片，询问您是否确实要将文件保存为 CSV 格式](../media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="00358-144">有关设置电子表格格式的提示</span><span class="sxs-lookup"><span data-stu-id="00358-144">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="00358-145"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="00358-145"><a name="__toc314595848"> </a></span></span>

- <span data-ttu-id="00358-146">**是否需要与示例电子表格中的列标题相同？**</span><span class="sxs-lookup"><span data-stu-id="00358-146">**Do I need the same column headings as in the sample spreadsheet?**</span></span> <span data-ttu-id="00358-147">是。</span><span class="sxs-lookup"><span data-stu-id="00358-147">Yes.</span></span> <span data-ttu-id="00358-148">示例电子表格在第一行中包含列标题。</span><span class="sxs-lookup"><span data-stu-id="00358-148">The sample spreadsheet contains column headings in the first row.</span></span> <span data-ttu-id="00358-149">这些标题是必需的。</span><span class="sxs-lookup"><span data-stu-id="00358-149">These headings are required.</span></span> <span data-ttu-id="00358-150">对于要添加到 Microsoft 365 中的每个用户，在标题下创建一行。</span><span class="sxs-lookup"><span data-stu-id="00358-150">For each user you want to add to Microsoft 365, create a row under the heading.</span></span> <span data-ttu-id="00358-151">如果添加、更改或删除任何列标题，Microsoft 365 可能无法从文件中的信息创建用户。</span><span class="sxs-lookup"><span data-stu-id="00358-151">If you add, change, or delete any of the column headings, Microsoft 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="00358-152">**如果我没有每个用户所需的全部信息，该怎么办？**</span><span class="sxs-lookup"><span data-stu-id="00358-152">**What if I don't have all the information required for each user?**</span></span> <span data-ttu-id="00358-153">用户名和显示名称是必需的，并且您无法添加不包含此信息的新用户。</span><span class="sxs-lookup"><span data-stu-id="00358-153">The user name and display name are required, and you cannot add a new user without this information.</span></span> <span data-ttu-id="00358-154">如果没有其他信息（如传真），您可以使用空格加上逗号，以指示该字段应保留为空。</span><span class="sxs-lookup"><span data-stu-id="00358-154">If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="00358-155">**电子表格是否可以小到多？**</span><span class="sxs-lookup"><span data-stu-id="00358-155">**How small or large can the spreadsheet be?**</span></span> <span data-ttu-id="00358-156">电子表格必须至少有两行。</span><span class="sxs-lookup"><span data-stu-id="00358-156">The spreadsheet must have at least two rows.</span></span> <span data-ttu-id="00358-157">一个用于列标题 (用户数据列标签) ，另一个用于用户。</span><span class="sxs-lookup"><span data-stu-id="00358-157">One is for the column headings (the user data column label) and one for the user.</span></span> <span data-ttu-id="00358-158">行数不能超过251。</span><span class="sxs-lookup"><span data-stu-id="00358-158">You cannot have more than 251 rows.</span></span> <span data-ttu-id="00358-159">如果需要导入多于250个用户，可以创建多个电子表格。</span><span class="sxs-lookup"><span data-stu-id="00358-159">If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="00358-160">**我可以使用哪些语言？**</span><span class="sxs-lookup"><span data-stu-id="00358-160">**What languages can I use?**</span></span> <span data-ttu-id="00358-161">创建电子表格时，可以输入任何语言或字符形式的用户数据列标签，但不能更改标签的顺序，如示例中所示。</span><span class="sxs-lookup"><span data-stu-id="00358-161">When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample.</span></span> <span data-ttu-id="00358-162">然后，可以使用任何语言或字符将条目输入到字段中，并将文件保存为 Unicode 或 UTF-8 格式。</span><span class="sxs-lookup"><span data-stu-id="00358-162">You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="00358-163">**如果我要从不同的国家或地区添加用户，该怎么办？**</span><span class="sxs-lookup"><span data-stu-id="00358-163">**What if I'm adding users from different countries or regions?**</span></span> <span data-ttu-id="00358-164">为每个区域创建单独的电子表格。</span><span class="sxs-lookup"><span data-stu-id="00358-164">Create a separate spreadsheet for each area.</span></span> <span data-ttu-id="00358-165">您需要逐步完成每个电子表格的 "批量添加用户" 向导，为所使用的文件中包含的所有用户提供一个位置。</span><span class="sxs-lookup"><span data-stu-id="00358-165">You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="00358-166">**对我可以使用的字符数是否有限制？**</span><span class="sxs-lookup"><span data-stu-id="00358-166">**Is there a limit to the number of characters I can use?**</span></span> <span data-ttu-id="00358-167">下表显示了示例电子表格中每个用户数据列标签和最大字符长度。</span><span class="sxs-lookup"><span data-stu-id="00358-167">The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="00358-168">**用户数据列标签**</span><span class="sxs-lookup"><span data-stu-id="00358-168">**User data column label**</span></span>|<span data-ttu-id="00358-169">**最大字符长度**</span><span class="sxs-lookup"><span data-stu-id="00358-169">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="00358-170"> (必需的用户名) </span><span class="sxs-lookup"><span data-stu-id="00358-170">User Name (Required)</span></span>  <br/> |<span data-ttu-id="00358-171">79，其中包括 at 符号 ( @ ) ，格式为 \<extension\> name@domain。</span><span class="sxs-lookup"><span data-stu-id="00358-171">79 including the at sign (@), in the format name@domain.\<extension\>.</span></span> <span data-ttu-id="00358-172">用户的别名不能超过50个字符，并且域名不能超过48个字符。</span><span class="sxs-lookup"><span data-stu-id="00358-172">The user's alias cannot exceed 50 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="00358-173">名字</span><span class="sxs-lookup"><span data-stu-id="00358-173">First Name</span></span>  <br/> |<span data-ttu-id="00358-174">64</span><span class="sxs-lookup"><span data-stu-id="00358-174">64</span></span>  <br/> |
|<span data-ttu-id="00358-175">姓氏</span><span class="sxs-lookup"><span data-stu-id="00358-175">Last Name</span></span>  <br/> |<span data-ttu-id="00358-176">64</span><span class="sxs-lookup"><span data-stu-id="00358-176">64</span></span>  <br/> |
|<span data-ttu-id="00358-177"> (必需的显示名称) </span><span class="sxs-lookup"><span data-stu-id="00358-177">Display Name (required)</span></span>  <br/> |<span data-ttu-id="00358-178">256</span><span class="sxs-lookup"><span data-stu-id="00358-178">256</span></span>  <br/> |
|<span data-ttu-id="00358-179">职务</span><span class="sxs-lookup"><span data-stu-id="00358-179">Job Title</span></span>  <br/> |<span data-ttu-id="00358-180">64</span><span class="sxs-lookup"><span data-stu-id="00358-180">64</span></span>  <br/> |
|<span data-ttu-id="00358-181">Department</span><span class="sxs-lookup"><span data-stu-id="00358-181">Department</span></span>  <br/> |<span data-ttu-id="00358-182">64</span><span class="sxs-lookup"><span data-stu-id="00358-182">64</span></span>  <br/> |
|<span data-ttu-id="00358-183">办公室号码</span><span class="sxs-lookup"><span data-stu-id="00358-183">Office Number</span></span>  <br/> |<span data-ttu-id="00358-184">128</span><span class="sxs-lookup"><span data-stu-id="00358-184">128</span></span>  <br/> |
|<span data-ttu-id="00358-185">办公室电话</span><span class="sxs-lookup"><span data-stu-id="00358-185">Office Phone</span></span>  <br/> |<span data-ttu-id="00358-186">64</span><span class="sxs-lookup"><span data-stu-id="00358-186">64</span></span>  <br/> |
|<span data-ttu-id="00358-187">Mobile Phone － 移动电话</span><span class="sxs-lookup"><span data-stu-id="00358-187">Mobile Phone</span></span>  <br/> |<span data-ttu-id="00358-188">64</span><span class="sxs-lookup"><span data-stu-id="00358-188">64</span></span>  <br/> |
|<span data-ttu-id="00358-189">Fax</span><span class="sxs-lookup"><span data-stu-id="00358-189">Fax</span></span>  <br/> |<span data-ttu-id="00358-190">64</span><span class="sxs-lookup"><span data-stu-id="00358-190">64</span></span>  <br/> |
|<span data-ttu-id="00358-191">地址</span><span class="sxs-lookup"><span data-stu-id="00358-191">Address</span></span>  <br/> |<span data-ttu-id="00358-192">1023</span><span class="sxs-lookup"><span data-stu-id="00358-192">1023</span></span>  <br/> |
|<span data-ttu-id="00358-193">市/县</span><span class="sxs-lookup"><span data-stu-id="00358-193">City</span></span>  <br/> |<span data-ttu-id="00358-194">128</span><span class="sxs-lookup"><span data-stu-id="00358-194">128</span></span>  <br/> |
|<span data-ttu-id="00358-195">省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="00358-195">State or Province</span></span>  <br/> |<span data-ttu-id="00358-196">128</span><span class="sxs-lookup"><span data-stu-id="00358-196">128</span></span>  <br/> |
|<span data-ttu-id="00358-197">邮政编码</span><span class="sxs-lookup"><span data-stu-id="00358-197">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="00358-198">40</span><span class="sxs-lookup"><span data-stu-id="00358-198">40</span></span>  <br/> |
|<span data-ttu-id="00358-199">国家或地区</span><span class="sxs-lookup"><span data-stu-id="00358-199">Country or Region</span></span>  <br/> |<span data-ttu-id="00358-200">128</span><span class="sxs-lookup"><span data-stu-id="00358-200">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a><span data-ttu-id="00358-201">将用户添加到 Microsoft 365 时仍遇到问题？</span><span class="sxs-lookup"><span data-stu-id="00358-201">Still having problems when adding users to Microsoft 365?</span></span>

- <span data-ttu-id="00358-202">**请仔细检查电子表格的格式是否正确。**</span><span class="sxs-lookup"><span data-stu-id="00358-202">**Double-check that the spreadsheet is formatted correctly.**</span></span> <span data-ttu-id="00358-203">检查列标题以确保它们与示例文件中的标题相匹配。</span><span class="sxs-lookup"><span data-stu-id="00358-203">Check the column headings to make sure they match the headings in the sample file.</span></span> <span data-ttu-id="00358-204">请确保遵循字符长度的规则，并使用逗号分隔每个字段。</span><span class="sxs-lookup"><span data-stu-id="00358-204">Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="00358-205">**如果你在 Microsoft 365 中未立即看到新用户，请等待几分钟。**</span><span class="sxs-lookup"><span data-stu-id="00358-205">**If you don't see the new users in Microsoft 365 right away, wait a few minutes.**</span></span> <span data-ttu-id="00358-206">在 Microsoft 365 中的所有服务之间进行更改可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="00358-206">It can take a little while for changes to go across all the services in Microsoft 365.</span></span> 
    
## <a name="related-articles"></a><span data-ttu-id="00358-207">相关文章</span><span class="sxs-lookup"><span data-stu-id="00358-207">Related articles</span></span>

[<span data-ttu-id="00358-208">将用户逐个或批量添加到 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="00358-208">Add users individually or in bulk to Microsoft 365</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)




