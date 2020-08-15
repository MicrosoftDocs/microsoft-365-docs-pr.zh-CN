---
title: 使用 PowerShell 为 Microsoft 365 用户帐户分配角色
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
description: 在本文中，了解如何快速轻松地使用适用于 Microsoft 365 的 PowerShell 向用户帐户分配角色。
ms.openlocfilehash: 4726dcea109490ff28299002bc5263aa15dca949
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687630"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a>使用 PowerShell 为 Microsoft 365 用户帐户分配角色

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

您可以使用 PowerShell for Microsoft 365 快速而轻松地向用户帐户分配角色。

>[!Note]
>若要使用 Microsoft 365 管理中心向用户帐户分配角色，请参阅 [这些说明](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)。
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，使用全局管理员帐户 [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) 。
  
接下来，确定要添加到角色中的用户帐户的登录名 (例如： fredsm@contoso.com) 。 这也称为用户主体名称 (UPN) 。

接下来，确定角色的名称。 [在 Azure Active Directory 中使用此管理员角色权限列表](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。

>[!Note]
>请注意本文中的注释。 对于 Azure AD PowerShell，某些角色名称不同。 例如，Microsoft 365 管理中心中的 "SharePoint 管理员" 角色为 Azure AD PowerShell 命名为 "SharePoint 服务管理员"。
>

接下来，填写登录名和角色名称，并运行这些命令。
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

下面的示例展示了将 SharePoint 服务管理员角色分配给 belindan@contoso.com 帐户的已完成命令集：
  
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

若要显示特定角色的用户名列表，请使用这些命令。

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

首先，使用全局管理员帐户 [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) 。
  
### <a name="for-a-single-role-change"></a>对于单个角色更改

特定用户帐户的最常见方法是使用其显示名称或电子邮件名称，也可以知道其登录名或用户主体名称 (UPN) 。

#### <a name="display-names-of-user-accounts"></a>用户帐户的显示名称

如果使用的是用户帐户的显示名称，请确定以下各项：
  
- 要配置的用户帐户。
    
    若要指定用户帐户，必须确定其显示名称。 若要获取完整的列表帐户，请使用以下命令：
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令将列出用户帐户的显示名称，按显示名称排序，一次显示一个屏幕。 您可以使用 **Where** cmdlet 将列表筛选为一个较小的集。 如以下示例所示：

   >[!Note]
   >PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令仅列出其显示名称以 "John" 开头的用户帐户。
    
- 要分配的角色。
    
    若要显示可分配给用户帐户的可用角色的列表，请使用以下命令：
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

确定帐户的显示名称和角色的名称后，请使用以下命令将角色分配给帐户：
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

复制命令并将其粘贴到记事本中。 对于 **$dispName** 和 **$roleName** 变量，请将说明文本替换为它们的值，删除这些 \< and > 字符，并保留引号。 复制修改过的行并将其粘贴到 windows PowerShell 的 Windows Azure Active Directory 模块中，以运行它们。 或者，也可以使用 (ISE) 的 Windows PowerShell 集成脚本环境。
  
下面的示例展示了已完成的命令集：
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>用户帐户的登录名

如果您用于使用用户帐户的登录名或 Upn，请确定以下事项：
  
- 用户帐户的 UPN。
    
    如果您尚不知道 UPN，请使用以下命令：
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    此命令将列出您的用户帐户的 UPN，按 UPN 排序，一次一个屏幕。 您可以使用 **Where** cmdlet 将列表筛选为一个较小的集。 如以下示例所示：
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    此命令仅列出其显示名称以 "John" 开头的用户帐户。
    
- 要分配的角色。
    
    若要显示可分配给用户帐户的可用角色的列表，请使用以下命令：
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

拥有帐户的 UPN 和角色的名称后，请使用以下命令将角色分配给帐户：
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

复制命令并将其粘贴到记事本中。 对于 **$upnName** 和 **$roleName** 变量，请将说明文本替换为它们的值，删除这些 \< and > 字符，并保留引号。 复制修改过的行并将其粘贴到 windows PowerShell 的 Windows Azure Active Directory 模块中，以运行它们。 或者，也可以使用 Windows PowerShell ISE。
  
下面的示例展示了已完成的命令集：
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>多个角色更改

对于多个角色更改，请确定以下内容：
  
- 要配置的用户帐户。 您可以使用上一节中的方法来收集显示名称或 Upn 的集合。
    
- 要分配给每个用户帐户的角色。
    
    若要显示可分配给用户帐户的可用角色的列表，请使用以下命令：
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

接下来，创建一个以逗号分隔的值 (CSV) 文本文件，该文件具有显示名称或 UPN 和角色名称字段。 可以使用 Microsoft Excel 轻松实现此目的。

以下是显示名称的示例：
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

接下来，填写 CSV 文件的位置，并在 PowerShell 命令提示符处运行生成的命令。
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

下面是 Upn 的示例：
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

接下来，填写 CSV 文件的位置，并在 PowerShell 命令提示符处运行生成的命令。
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>另请参阅

- [使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [使用 PowerShell 管理 Microsoft 365](manage-microsoft-365-with-microsoft-365-powershell.md)
- [PowerShell for Microsoft 365 入门](getting-started-with-microsoft-365-powershell.md)
