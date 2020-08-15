---
title: 使用 PowerShell 禁用对 Microsoft 365 服务的访问
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 在本文中，我们将了解如何使用 PowerShell 来禁用用户对 Microsoft 365 服务的访问权限。
ms.openlocfilehash: 292bda3b380b9ce3947b2427288da4f16198bb51
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687810"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>使用 PowerShell 禁用对 Microsoft 365 服务的访问

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

向 Microsoft 365 帐户分配许可计划中的许可证后，该许可证中的用户将可以使用 Microsoft 365 服务。 但是，您可以控制用户可以访问的 Microsoft 365 服务。 例如，即使许可证允许访问 SharePoint Online 服务，也可以禁用对它的访问。 您可以使用 PowerShell 针对特定许可计划禁用对任意数量的服务的访问：

- 单个帐户。
- 一组帐户。
- 组织中的所有帐户。

>[!Note]
>有 Microsoft 365 服务依赖项可以阻止您在其他服务依赖于指定的服务时禁用该服务。
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

接下来，使用此命令查看可用的许可计划，也称为 "AccountSkuIds"：

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

有关详细信息，请参阅 [使用 PowerShell 查看许可证和服务](view-licenses-and-services-with-microsoft-365-powershell.md)。
    
若要查看本主题中的过程的前后结果，请参阅 [使用 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-microsoft-365-powershell.md)。
    
PowerShell 脚本可自动执行本主题中描述的过程。 具体来说，该脚本允许您查看和禁用 Microsoft 365 组织中的服务，包括 Sway。 有关详细信息，请参阅 [使用 PowerShell 禁用对 Sway 的访问](disable-access-to-sway-with-microsoft-365-powershell.md)。
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>针对特定用户禁用特定许可计划的特定 Microsoft 365 服务
  
若要为用户禁用特定许可计划的一组特定的 Microsoft 365 服务，请执行以下步骤：
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>步骤1：使用以下语法确定许可计划中不需要的服务：
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

下面的示例创建一个 **LicenseOptions** 对象，该对象禁用名为 `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) 的许可计划中的 Office 和 SharePoint Online services。
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>步骤2：在一个或多个用户上使用步骤1中的 **LicenseOptions** 对象。
    
若要创建一个已禁用服务的新帐户，请使用以下语法：
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

下面的示例为 Allie Bellew 创建了一个新帐户，该帐户分配许可证并禁用步骤1中所述的服务。
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

有关在 PowerShell for Microsoft 365 中创建用户帐户的详细信息，请参阅 [Create user accounts With powershell](create-user-accounts-with-microsoft-365-powershell.md)。
    
若要禁用现有授权用户的服务，请使用下面的语法：
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

本示例对用户 BelindaN@litwareinc.com 禁用服务。
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

若要禁用步骤1中对所有现有许可用户所述的服务，请从 **get-msolaccountsku** cmdlet (（如 **litwareinc： ENTERPRISEPACK**) ）中指定 Microsoft 365 计划的名称，然后运行以下命令：
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 如果使用 **get-msoluser** cmdlet，而不使用 _All_ 参数，则仅返回前500个用户帐户。

若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：
    
**方法1。基于现有帐户属性筛选帐户** 

为此，请使用以下语法：
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

下面的示例为美国的销售部门中的用户禁用服务。
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**方法2：使用特定帐户的列表** 

若要完成此操作，请执行以下步骤：
    
1. 创建一个文本文件，在它的每一行上包含一个帐户，如下所示：
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   在此示例中，文本文件为 C： \\ 我的文档 \\Accounts.txt。
    
2. 运行以下命令：
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

如果要对多个许可计划禁用服务访问，请针对每个许可计划重复上述说明，以确保：

- 已为用户帐户分配许可计划。
- 要禁用的服务在许可计划中可用。

若要在向用户分配许可计划时为其禁用 Microsoft 365 服务，请参阅在 [分配用户许可证时禁用对服务的访问](disable-access-to-services-while-assigning-user-licenses.md)。

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>将许可计划中的所有服务分配给用户帐户

对于已禁用服务的用户帐户，您可以使用以下命令为特定许可计划启用所有服务：

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>相关主题

[使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[使用 PowerShell 管理 Microsoft 365](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[PowerShell for Microsoft 365 入门](getting-started-with-microsoft-365-powershell.md)
