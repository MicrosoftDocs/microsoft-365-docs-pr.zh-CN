---
title: 使用 PowerShell 为 Microsoft 365 用户帐户分配角色
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 在本文中，了解如何快速轻松地使用适用于 Microsoft 365 的 PowerShell 向用户帐户分配管理员角色。
ms.openlocfilehash: 1486c86172cd34e6e88f8cd02d003967518bcdb7
ms.sourcegitcommit: 3b1bd8aa1430bc9565743a446bbc27b199f30f73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "48655943"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="e1c6b-103">使用 PowerShell 将管理员角色分配给 Microsoft 365 用户帐户</span><span class="sxs-lookup"><span data-stu-id="e1c6b-103">Assign admin roles to Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="e1c6b-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="e1c6b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e1c6b-105">您可以使用 PowerShell for Microsoft 365 快速轻松地将管理员角色分配给用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-105">You can quickly and easily assign admin roles to user accounts using PowerShell for Microsoft 365.</span></span>

>[!Note]
><span data-ttu-id="e1c6b-106">了解如何使用 Microsoft 365 管理中心向[用户帐户分配管理员角色](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-106">[Learn how to assign admin roles to user accounts](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles) with the Microsoft 365 admin center.</span></span> <span data-ttu-id="e1c6b-107">有关其他资源的列表，请参阅 [管理用户和组](https://docs.microsoft.com/microsoft-365/admin/add-users/)。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-107">For a list of additional resources, see [Manage users and groups](https://docs.microsoft.com/microsoft-365/admin/add-users/).</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e1c6b-108">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1c6b-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e1c6b-109">首先，使用全局管理员帐户 [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-109">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="e1c6b-110">接下来，确定要添加到角色中的用户帐户的登录名 (例如： fredsm@contoso.com) 。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-110">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="e1c6b-111">这也称为用户主体名称 (UPN) 。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-111">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="e1c6b-112">接下来，确定管理员角色的名称。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-112">Next, determine the name of the admin role.</span></span> <span data-ttu-id="e1c6b-113">[在 Azure Active Directory 中使用此管理员角色权限列表](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-113">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="e1c6b-114">请注意本文中的注释。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-114">Pay attention to the notes in this article.</span></span> <span data-ttu-id="e1c6b-115">对于 Azure AD PowerShell，某些角色名称不同。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-115">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="e1c6b-116">例如，Microsoft 365 管理中心中的 "SharePoint 管理员" 角色为 Azure AD PowerShell 命名为 "SharePoint 服务管理员"。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-116">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="e1c6b-117">接下来，填写登录名和角色名称，并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-117">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<admin role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="e1c6b-118">下面的示例展示了将 SharePoint 服务管理员管理员角色分配给 belindan@contoso.com 帐户的已完成命令集：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-118">Here is an example of a completed command set that assigns the SharePoint Service Administrator admin role to the belindan@contoso.com account:</span></span>
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="e1c6b-119">若要显示特定管理员角色的用户名列表，请使用这些命令。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-119">To display the list of user names for a specific admin role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e1c6b-120">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="e1c6b-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e1c6b-121">首先，使用全局管理员帐户 [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-121">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="e1c6b-122">对于单个角色更改</span><span class="sxs-lookup"><span data-stu-id="e1c6b-122">For a single role change</span></span>

<span data-ttu-id="e1c6b-123">特定用户帐户的最常见方法是使用其显示名称或电子邮件名称，也可以知道其登录名或用户主体名称 (UPN) 。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-123">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="e1c6b-124">用户帐户的显示名称</span><span class="sxs-lookup"><span data-stu-id="e1c6b-124">Display names of user accounts</span></span>

<span data-ttu-id="e1c6b-125">如果使用的是用户帐户的显示名称，请确定以下各项：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-125">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="e1c6b-126">要配置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-126">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="e1c6b-127">若要指定用户帐户，必须确定其显示名称。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-127">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="e1c6b-128">若要获取完整的列表帐户，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-128">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="e1c6b-129">此命令将列出用户帐户的显示名称，按显示名称排序，一次显示一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-129">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="e1c6b-130">您可以使用 **Where** cmdlet 将列表筛选为一个较小的集。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-130">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="e1c6b-131">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-131">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="e1c6b-132">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-132">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e1c6b-133">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-133">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="e1c6b-134">此命令仅列出其显示名称以 "John" 开头的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="e1c6b-135">要分配的角色。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-135">The role you want to assign.</span></span>
    
    <span data-ttu-id="e1c6b-136">若要显示可分配给用户帐户的可用管理员角色的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-136">To display the list of available admin roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="e1c6b-137">确定帐户的显示名称和管理员角色的名称后，请使用以下命令将角色分配给帐户：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-137">Once you have determined the Display Name of the account and the Name of the admin role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="e1c6b-138">复制命令并将其粘贴到记事本中。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-138">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="e1c6b-139">对于 **$dispName** 和 **$roleName** 变量，请将说明文本替换为它们的值，删除这些 \< and > 字符，并保留引号。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-139">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="e1c6b-140">复制修改过的行并将其粘贴到 windows PowerShell 的 Windows Azure Active Directory 模块中，以运行它们。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-140">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="e1c6b-141">或者，也可以使用 (ISE) 的 Windows PowerShell 集成脚本环境。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-141">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="e1c6b-142">下面的示例展示了已完成的命令集：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-142">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="e1c6b-143">用户帐户的登录名</span><span class="sxs-lookup"><span data-stu-id="e1c6b-143">Sign-in names of user accounts</span></span>

<span data-ttu-id="e1c6b-144">如果您用于使用用户帐户的登录名或 Upn，请确定以下事项：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-144">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="e1c6b-145">用户帐户的 UPN。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-145">The user account's UPN.</span></span>
    
    <span data-ttu-id="e1c6b-146">如果您尚不知道 UPN，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-146">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="e1c6b-147">此命令将列出您的用户帐户的 UPN，按 UPN 排序，一次一个屏幕。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-147">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="e1c6b-148">您可以使用 **Where** cmdlet 将列表筛选为一个较小的集。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-148">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="e1c6b-149">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-149">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="e1c6b-150">此命令仅列出其显示名称以 "John" 开头的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-150">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="e1c6b-151">要分配的角色。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-151">The role you want to assign.</span></span>
    
    <span data-ttu-id="e1c6b-152">若要显示可分配给用户帐户的可用角色的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-152">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="e1c6b-153">拥有帐户的 UPN 和角色的名称后，请使用以下命令将角色分配给帐户：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-153">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="e1c6b-154">复制命令并将其粘贴到记事本中。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-154">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="e1c6b-155">对于 **$upnName** 和 **$roleName** 变量，请将说明文本替换为它们的值，删除这些 \< and > 字符，并保留引号。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-155">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="e1c6b-156">复制修改过的行并将其粘贴到 windows PowerShell 的 Windows Azure Active Directory 模块中，以运行它们。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-156">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="e1c6b-157">或者，也可以使用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-157">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="e1c6b-158">下面的示例展示了已完成的命令集：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-158">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="e1c6b-159">多个角色更改</span><span class="sxs-lookup"><span data-stu-id="e1c6b-159">Multiple role changes</span></span>

<span data-ttu-id="e1c6b-160">对于多个角色更改，请确定以下内容：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-160">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="e1c6b-161">要配置的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-161">Which user accounts that you want to configure.</span></span> <span data-ttu-id="e1c6b-162">您可以使用上一节中的方法来收集显示名称或 Upn 的集合。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-162">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="e1c6b-163">要分配给每个用户帐户的角色。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-163">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="e1c6b-164">若要显示可分配给用户帐户的可用角色的列表，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-164">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="e1c6b-165">接下来，创建一个以逗号分隔的值 (CSV) 文本文件，该文件具有显示名称或 UPN 和角色名称字段。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-165">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="e1c6b-166">可以使用 Microsoft Excel 轻松实现此目的。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-166">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="e1c6b-167">以下是显示名称的示例：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-167">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="e1c6b-168">接下来，填写 CSV 文件的位置，并在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-168">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="e1c6b-169">下面是 Upn 的示例：</span><span class="sxs-lookup"><span data-stu-id="e1c6b-169">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="e1c6b-170">接下来，填写 CSV 文件的位置，并在 PowerShell 命令提示符处运行生成的命令。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-170">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="e1c6b-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1c6b-171">See also</span></span>

- [<span data-ttu-id="e1c6b-172">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="e1c6b-172">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [<span data-ttu-id="e1c6b-173">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e1c6b-173">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
- [<span data-ttu-id="e1c6b-174">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="e1c6b-174">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)
