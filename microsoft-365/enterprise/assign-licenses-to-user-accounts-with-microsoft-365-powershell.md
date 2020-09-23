---
title: 使用 PowerShell 将 Microsoft 365 许可证分配给用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: 在本文中，我们将了解如何使用 PowerShell 将 Microsoft 365 许可证分配给未经许可的用户。
ms.openlocfilehash: f042f8109bf9ac9b634bc66509c60a5181fb1af6
ms.sourcegitcommit: c1ee4ed3c5826872b57339e1e1aa33b4d2209711
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "48235614"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>使用 PowerShell 将 Microsoft 365 许可证分配给用户帐户

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

用户在向其帐户分配许可计划中的许可证之前，不能使用任何 Microsoft 365 服务。 您可以使用 PowerShell 将许可证快速分配给未经许可的帐户。 

>[!Note]
>必须为用户帐户分配一个位置。 您可以从 Microsoft 365 管理中心或 PowerShell 中的用户帐户的属性中执行此操作。
>

>[!Note]
>了解如何使用 Microsoft 365 管理中心向[用户帐户分配许可证](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)。 有关其他资源的列表，请参阅 [管理用户和组](https://docs.microsoft.com/microsoft-365/admin/add-users/)。
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下来，使用此命令列出租户的许可证计划。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，获取要向其添加许可证（也称为 "用户主体名称" (UPN) ）的帐户的登录名。

接下来，请确保已为用户帐户分配了使用位置。

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

如果没有分配的使用位置，则可以使用以下命令分配一个：

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

最后，指定用户登录名和许可证计划名称，并运行这些命令。

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

运行 `Get-MsolAccountSku` 命令以查看组织中每个计划中可用的许可计划和可用许可证的数量。 每个计划中可用的许可证数量是**ActiveUnits**  -  **WarningUnits**  -  **ConsumedUnits**。 有关许可计划、许可证和服务的详细信息，请参阅 [使用 PowerShell 查看许可证和服务](view-licenses-and-services-with-microsoft-365-powershell.md)。

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

若要在组织中查找未授权帐户，请运行此命令。

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

只能将许可证分配给其 **UsageLocation** 属性设置为有效的 ISO 3166-1 alpha-2 国家/地区代码的用户帐户。 例如，US 代表美国，FR 代表法国。 某些 Microsoft 365 服务在某些国家/地区不可用。 有关详细信息，请参阅[关于许可证限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
若要查找不具有 **UsageLocation** 值的帐户，请运行此命令。

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

若要设置帐户的 **UsageLocation** 值，请运行此命令。

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

例如：

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
如果使用 **Get-MsolUser** cmdlet，而未使用 **-All** 参数，只返回前 500 个帐户。

### <a name="assigning-licenses-to-user-accounts"></a>向用户帐户分配许可证
    
若要将许可证分配给用户，请在 PowerShell 中使用以下命令。
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

本示例将 **litwareinc： ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给未经许可的 **用户 \@ belindan litwareinc.com**：
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要将许可证分配给所有未经许可的用户，请运行此命令。
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>您无法使用相同的许可计划为用户分配多个许可证。 如果没有足够可用的许可证，将按照 **Get-MsolUser** cmdlet 返回的顺序为用户分配许可证，直到可用许可证用尽。
>

此示例将 **litwareinc： ENTERPRISEPACK** (Office 365 企业版 E3) 许可计划中的许可证分配给所有未经许可的用户：
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

本示例将这些相同的许可证分配给美国的销售部门中未经许可的用户：
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell for Graph 模块将用户移动到其他订阅 (许可证计划) 

首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
接下来，获取要对其进行切换订阅（也称为用户主体名称 (UPN) ）的用户帐户的登录名。

接下来，使用此命令列出租户 (许可证计划) 的订阅。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，使用这些命令列出用户帐户当前拥有的订阅。

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

确定用户当前已 (FROM 订阅) 的订阅，以及用户将移动到的订阅 (到订阅) 。

最后，指定 TO 和 FROM 订阅名称 (SKU 部件号) 并运行这些命令。

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

您可以使用这些命令验证用户帐户的订阅更改。

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>另请参阅

[使用 PowerShell 管理用户帐户、许可证和组](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[使用 PowerShell 管理 Microsoft 365](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[PowerShell for Microsoft 365 入门](getting-started-with-microsoft-365-powershell.md)
