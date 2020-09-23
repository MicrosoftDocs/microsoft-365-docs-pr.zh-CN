---
title: 使用 PowerShell 删除 Microsoft 365 用户帐户
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: 在本文中，您将了解如何在 PowerShell 中使用不同的模块来删除 Microsoft 365 用户帐户。
ms.openlocfilehash: 0c13b57c13fb3d01d648438a5d6973fea8b9db67
ms.sourcegitcommit: c1ee4ed3c5826872b57339e1e1aa33b4d2209711
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "48235438"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="409ca-103">使用 PowerShell 删除 Microsoft 365 用户帐户</span><span class="sxs-lookup"><span data-stu-id="409ca-103">Delete Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="409ca-104">可以使用适用于 Microsoft 365 的 PowerShell 删除和还原用户帐户。</span><span class="sxs-lookup"><span data-stu-id="409ca-104">You can use PowerShell for Microsoft 365 to delete and restore a user account.</span></span>

>[!Note]
><span data-ttu-id="409ca-105">了解如何使用 Microsoft 365 管理中心[还原用户帐户](https://docs.microsoft.com/microsoft-365/admin/add-users/restore-user)。</span><span class="sxs-lookup"><span data-stu-id="409ca-105">[Learn how to restore a user account](https://docs.microsoft.com/microsoft-365/admin/add-users/restore-user) with the Microsoft 365 admin center.</span></span> <span data-ttu-id="409ca-106">有关其他资源的列表，请参阅 [管理用户和组](https://docs.microsoft.com/microsoft-365/admin/add-users/)。</span><span class="sxs-lookup"><span data-stu-id="409ca-106">For a list of additional resources, see [Manage users and groups](https://docs.microsoft.com/microsoft-365/admin/add-users/).</span></span>
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="409ca-107">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="409ca-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="409ca-108">首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="409ca-108">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="409ca-109">连接后，使用下列语法删除单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="409ca-109">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="409ca-110">本示例将删除用户帐户 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="409ca-110">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="409ca-111">**AzureADUser** cmdlet 中的 **-ObjectID**参数可接受帐户的登录名（也称为 "用户主体名称"）或帐户的对象 ID。</span><span class="sxs-lookup"><span data-stu-id="409ca-111">The **-ObjectID** parameter in the **Remove-AzureADUser** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="409ca-112">若要显示基于用户名的帐户名称，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="409ca-112">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="409ca-113">本示例显示名为 Caleb Sills 的用户的帐户名。</span><span class="sxs-lookup"><span data-stu-id="409ca-113">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="409ca-114">若要删除基于用户显示名称的帐户，请使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="409ca-114">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="409ca-115">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="409ca-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="409ca-p102">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块删除用户帐户时，该帐户不会被永久删除。可以在 30 天内还原已删除的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="409ca-p102">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="409ca-118">首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="409ca-118">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="409ca-119">若要删除一个用户帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="409ca-119">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
><span data-ttu-id="409ca-120">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="409ca-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="409ca-121">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="409ca-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="409ca-122">本示例删除用户帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="409ca-122">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="409ca-123">若要在 30 天的宽限期内还原已删除的用户帐户，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="409ca-123">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="409ca-124">本示例还原已删除的帐户 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="409ca-124">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="409ca-125">**注意：**</span><span class="sxs-lookup"><span data-stu-id="409ca-125">**Notes:**</span></span>
  
- <span data-ttu-id="409ca-126">若要查看可以还原的已删除用户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="409ca-126">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="409ca-127">如果用户帐户的初始用户主体名称已被另一个帐户使用，那么在还原用户帐户时，请使用 _NewUserPrincipalName_ 参数而不是 _UserPrincipalName_ 来指定一个不同的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="409ca-127">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="409ca-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="409ca-128">See also</span></span>

[<span data-ttu-id="409ca-129">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="409ca-129">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="409ca-130">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="409ca-130">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="409ca-131">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="409ca-131">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)
