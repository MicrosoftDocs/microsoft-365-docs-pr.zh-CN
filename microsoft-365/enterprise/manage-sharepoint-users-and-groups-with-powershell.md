---
title: 使用 PowerShell 管理 SharePoint Online 用户和组
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 本文将了解如何使用 PowerShell for Microsoft 365管理 SharePoint Online 用户、组和网站。
ms.openlocfilehash: 823c5fdc9af178a2e8ea8f0ca4c63fbfa4673dd8
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2021
ms.locfileid: "53289051"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a><span data-ttu-id="e092e-103">使用 PowerShell 管理 SharePoint Online 用户和组</span><span class="sxs-lookup"><span data-stu-id="e092e-103">Manage SharePoint Online users and groups with PowerShell</span></span>

<span data-ttu-id="e092e-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="e092e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e092e-105">如果你是使用SharePoint或组的大型列表的联机管理员，并且希望使用更简单的方式来管理它们，可以使用 PowerShell 进行Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="e092e-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use PowerShell for Microsoft 365.</span></span>

<span data-ttu-id="e092e-106">在开始之前，本主题中的过程需要您连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="e092e-106">Before you begin, the procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="e092e-107">有关说明，请参阅[连接 SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)</span><span class="sxs-lookup"><span data-stu-id="e092e-107">For instructions, see [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="e092e-108">获取网站、组和用户的列表</span><span class="sxs-lookup"><span data-stu-id="e092e-108">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="e092e-p102">开始管理用户和组之前，你需要获取网站、组和用户的列表。然后可以使用此信息完成本文中的示例。</span><span class="sxs-lookup"><span data-stu-id="e092e-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

<span data-ttu-id="e092e-111">使用此命令获取租户中的网站列表：</span><span class="sxs-lookup"><span data-stu-id="e092e-111">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

<span data-ttu-id="e092e-112">使用此命令获取租户中的组列表：</span><span class="sxs-lookup"><span data-stu-id="e092e-112">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

<span data-ttu-id="e092e-113">使用此命令获取租户中的用户列表：</span><span class="sxs-lookup"><span data-stu-id="e092e-113">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="e092e-114">将用户添加到网站集管理员组</span><span class="sxs-lookup"><span data-stu-id="e092e-114">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="e092e-115">可以使用 cmdlet 将用户添加到网站集 `Set-SPOUser` 上的网站集管理员列表中。</span><span class="sxs-lookup"><span data-stu-id="e092e-115">You use the `Set-SPOUser` cmdlet to add a user to the list of Site Collection Administrators on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="e092e-116">若要使用这些命令，请将引号内的所有内容（包括 < 和 > 字符）替换为正确的名称。</span><span class="sxs-lookup"><span data-stu-id="e092e-116">To use these commands, replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="e092e-117">例如，这组命令将 Opal Castillo (用户名 opalc) 添加到 Contoso 租赁的 ContosoTest 网站集上的网站集管理员列表中：</span><span class="sxs-lookup"><span data-stu-id="e092e-117">For example, this set of commands adds Opal Castillo (user name opalc) to the list of Site Collection Administrators on the ContosoTest site collection in the Contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="e092e-118">可以将这些命令复制并粘贴到 记事本 中，将 $tenant、$site 和 $user 的变量值从环境中更改为实际值，然后将其粘贴到 SharePoint Online 命令行管理程序窗口中以运行它们。</span><span class="sxs-lookup"><span data-stu-id="e092e-118">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="e092e-119">将用户添加到其他网站集组</span><span class="sxs-lookup"><span data-stu-id="e092e-119">Add a user to other site collection groups</span></span>

<span data-ttu-id="e092e-120">在此任务中，我们将使用 cmdlet 将用户添加到网站 `Add-SPOUser` SharePoint组。</span><span class="sxs-lookup"><span data-stu-id="e092e-120">In this task, we'll use the `Add-SPOUser` cmdlet to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="e092e-121">例如，让我们将一 (用户名称) 添加到 contoso 租赁中 ContosoTest 网站集的审核员组中：</span><span class="sxs-lookup"><span data-stu-id="e092e-121">For example, let's add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="e092e-122">创建网站集组</span><span class="sxs-lookup"><span data-stu-id="e092e-122">Create a site collection group</span></span>

<span data-ttu-id="e092e-123">您可以使用 `New-SPOSiteGroup` cmdlet 创建新的组SharePoint组并将其添加到网站集。</span><span class="sxs-lookup"><span data-stu-id="e092e-123">You use the `New-SPOSiteGroup` cmdlet to create a new SharePoint group and add it to a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="e092e-124">以后可以使用 cmdlet 更新组属性，如权限 `Set-SPOSiteGroup` 级别。</span><span class="sxs-lookup"><span data-stu-id="e092e-124">Group properties, such as permission levels, can be updated later by using the `Set-SPOSiteGroup` cmdlet.</span></span>

<span data-ttu-id="e092e-125">例如，让我们向 contoso 租赁中的 contosotest 网站集添加具有"仅查看"权限的审核员组：</span><span class="sxs-lookup"><span data-stu-id="e092e-125">For example, let's add the Auditors group with View Only permissions to the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="e092e-126">从组中删除用户</span><span class="sxs-lookup"><span data-stu-id="e092e-126">Remove users from a group</span></span>

<span data-ttu-id="e092e-p103">有时必须从某个网站甚至是所有网站删除用户。员工可能从一个部门转移到另一个部门，或离开公司。在 UI 中可以很容易地对一个员工进行这样的操作，但如果是将整个部门从一个网站移动到另一个网站，这并非易事。</span><span class="sxs-lookup"><span data-stu-id="e092e-p103">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="e092e-130">但是，通过使用 SharePoint命令行管理程序和 CSV 文件，这非常简单快捷。</span><span class="sxs-lookup"><span data-stu-id="e092e-130">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="e092e-131">在本任务中，将使用 Windows PowerShell 将用户从一个网站集安全组删除。</span><span class="sxs-lookup"><span data-stu-id="e092e-131">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="e092e-132">然后使用 CSV 文件从不同的网站删除大量用户。</span><span class="sxs-lookup"><span data-stu-id="e092e-132">Then you'll use a CSV file and remove lots of users from different sites.</span></span>

<span data-ttu-id="e092e-133">我们将使用"Remove-SPOUser"cmdlet 从网站集组中删除单个 Microsoft 365 用户，以便我们可以看到命令语法。</span><span class="sxs-lookup"><span data-stu-id="e092e-133">We'll be using the 'Remove-SPOUser' cmdlet to remove a single Microsoft 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="e092e-134">语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="e092e-134">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="e092e-135">例如，让我们从 contoso 租赁的 contosotest 网站集中的网站集审核员组中删除一个为"一名"的"一名"。</span><span class="sxs-lookup"><span data-stu-id="e092e-135">For example, let's remove Bobby Overby from the site collection Auditors group in the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="e092e-p106">假定我们要将 Bobby 从他当前所在的所有组中删除。方法如下：</span><span class="sxs-lookup"><span data-stu-id="e092e-p106">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="e092e-138">这只是一个示例。</span><span class="sxs-lookup"><span data-stu-id="e092e-138">This is just an example.</span></span> <span data-ttu-id="e092e-139">除非确实需要将用户从每个组中删除（例如，用户离开公司），否则不应运行此命令。</span><span class="sxs-lookup"><span data-stu-id="e092e-139">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="e092e-140">自动化管理大型用户和组列表</span><span class="sxs-lookup"><span data-stu-id="e092e-140">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="e092e-141">若要向网站添加大量帐户SharePoint授予权限，可以使用 Microsoft 365 管理中心、单个 PowerShell 命令或 PowerShell CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="e092e-141">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="e092e-142">在这些选择中，CSV 文件是自动执行此任务的最快方法。</span><span class="sxs-lookup"><span data-stu-id="e092e-142">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="e092e-143">基本过程是，创建具有与 Windows PowerShell 脚本所需的参数对应的标头（列）的 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="e092e-143">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="e092e-144">你可以轻松地在列表中创建此类Excel，然后导出为 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="e092e-144">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="e092e-145">然后使用 Windows PowerShell 脚本循环访问 CSV 文件中的记录（行），将用户添加到组，将组添加到网站。</span><span class="sxs-lookup"><span data-stu-id="e092e-145">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span>

<span data-ttu-id="e092e-146">例如，让我们创建一个 CSV 文件来定义一组网站集、组和权限。</span><span class="sxs-lookup"><span data-stu-id="e092e-146">For example, let's create a CSV file to define a group of site collections, groups, and permissions.</span></span> <span data-ttu-id="e092e-147">接下来将创建一个 CSV 文件，将用户填充到组中。</span><span class="sxs-lookup"><span data-stu-id="e092e-147">Next, we will create a CSV file to populate the groups with users.</span></span> <span data-ttu-id="e092e-148">最后，要创建并运行一个简单的 Windows PowerShell 脚本，此脚本将创建并填充组。</span><span class="sxs-lookup"><span data-stu-id="e092e-148">Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="e092e-149">第一个 CSV 文件将一个或多个组添加到一个或多个网站集，并具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="e092e-149">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

<span data-ttu-id="e092e-150">标头：</span><span class="sxs-lookup"><span data-stu-id="e092e-150">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

<span data-ttu-id="e092e-151">项目：</span><span class="sxs-lookup"><span data-stu-id="e092e-151">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="e092e-152">示例文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="e092e-152">Here is an example file:</span></span>

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="e092e-153">第二个 CSV 文件将一个或多个用户添加到一个或多个组，并具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="e092e-153">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

<span data-ttu-id="e092e-154">标头：</span><span class="sxs-lookup"><span data-stu-id="e092e-154">Header:</span></span>

```powershell
Group,LoginName,Site
```

<span data-ttu-id="e092e-155">项目：</span><span class="sxs-lookup"><span data-stu-id="e092e-155">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="e092e-156">示例文件如下所示：</span><span class="sxs-lookup"><span data-stu-id="e092e-156">Here is an example file:</span></span>

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

<span data-ttu-id="e092e-157">然后必须将这两个 CSV 文件保存到驱动器。</span><span class="sxs-lookup"><span data-stu-id="e092e-157">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="e092e-158">下面是使用 CSV 文件以及添加权限和组成员身份的示例命令：</span><span class="sxs-lookup"><span data-stu-id="e092e-158">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="e092e-159">脚本导入 CSV 文件内容并使用列中的值填充 **New-SPOSiteGroup** 和 **Add-SPOUser** 命令的参数。</span><span class="sxs-lookup"><span data-stu-id="e092e-159">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="e092e-160">在我们的示例中，我们会将其保存到驱动器 C 上的O365Admin 文件夹中，但您可以将其保存到任何需要的位置。</span><span class="sxs-lookup"><span data-stu-id="e092e-160">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="e092e-161">现在，让我们使用同一 CSV 文件删除不同网站中多个组的一组人员。</span><span class="sxs-lookup"><span data-stu-id="e092e-161">Now, let's remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="e092e-162">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="e092e-162">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="e092e-163">生成用户报告</span><span class="sxs-lookup"><span data-stu-id="e092e-163">Generate user reports</span></span>

<span data-ttu-id="e092e-p114">您可能想要获取一些网站的简单报告，并显示这些网站的用户、权限级别及其他属性。语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="e092e-p114">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="e092e-p115">将可以获取这三个网站的数据，并将这些数据写入本地驱动器上的文本文件。请注意，–Append 参数会将新内容添加到现有文件。</span><span class="sxs-lookup"><span data-stu-id="e092e-p115">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="e092e-168">例如，我们在 Contoso1 租户的 ContosoTest、TeamSite01 和 Project01 网站上运行报告：</span><span class="sxs-lookup"><span data-stu-id="e092e-168">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="e092e-169">请注意，我们只需更改 $site **变量。**</span><span class="sxs-lookup"><span data-stu-id="e092e-169">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="e092e-170">the **$tenant** variable keeps its value through all three runs of the command.</span><span class="sxs-lookup"><span data-stu-id="e092e-170">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="e092e-p117">但是，如果要对每个网站进行此操作，应该怎么做？通过使用以下命令，您无需键入所有这些网站就可以进行操作：</span><span class="sxs-lookup"><span data-stu-id="e092e-p117">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="e092e-173">此报告相当简单，你可以添加更多代码以创建更多特定报告或包括更多详细信息的报告。</span><span class="sxs-lookup"><span data-stu-id="e092e-173">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="e092e-174">但是，这应该让你了解如何使用 SharePoint Online 命令行管理程序在 SharePoint Online 环境中管理用户。</span><span class="sxs-lookup"><span data-stu-id="e092e-174">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="e092e-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e092e-175">See also</span></span>

[<span data-ttu-id="e092e-176">连接到 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="e092e-176">Connect to SharePoint Online PowerShell</span></span>](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[<span data-ttu-id="e092e-177">使用 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e092e-177">Manage SharePoint Online with PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="e092e-178">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e092e-178">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)

[<span data-ttu-id="e092e-179">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="e092e-179">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)
