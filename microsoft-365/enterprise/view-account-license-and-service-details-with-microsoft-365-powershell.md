---
title: 使用 PowerShell Microsoft 365帐户许可证和服务详细信息
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 介绍如何使用 PowerShell 确定Microsoft 365的用户分配的服务。
ms.openlocfilehash: 163a92ec31f700aa6157e58b49e23a1cec587815
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46688179"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a><span data-ttu-id="b4f3f-103">使用 PowerShell Microsoft 365帐户许可证和服务详细信息</span><span class="sxs-lookup"><span data-stu-id="b4f3f-103">View Microsoft 365 account license and service details with PowerShell</span></span>

<span data-ttu-id="b4f3f-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="b4f3f-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b4f3f-105">在 Microsoft 365 中，许可计划 (（也称为 SK 或 Microsoft 365 计划) ）中的许可证允许用户访问为这些计划定义的 Microsoft 365 服务。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-105">In Microsoft 365, licenses from licensing plans (also called SKUs or Microsoft 365 plans) give users access to the Microsoft 365 services that are defined for those plans.</span></span> <span data-ttu-id="b4f3f-106">但是，用户可能无法访问当前分配给他们的许可证中提供的所有服务。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-106">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="b4f3f-107">可以使用 PowerShell for Microsoft 365查看用户帐户上服务的状态。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-107">You can use PowerShell for Microsoft 365 to view the status of services on user accounts.</span></span> 

<span data-ttu-id="b4f3f-108">有关许可计划、许可证和服务的信息，请参阅 [使用 PowerShell 查看许可证和服务](view-licenses-and-services-with-microsoft-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-108">For more information about licensing plans, license, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b4f3f-109">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4f3f-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b4f3f-110">首先，[连接到你的Microsoft 365租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-110">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="b4f3f-111">接下来，使用此命令列出租户的许可证计划。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="b4f3f-112">使用这些命令列出每个许可计划中可用的服务。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="b4f3f-113">使用这些命令列出分配给用户帐户的许可证。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b4f3f-114">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="b4f3f-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b4f3f-115">首先，[连接到你的Microsoft 365租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-115">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="b4f3f-116">接下来，运行此命令以列出组织中可用的许可计划。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="b4f3f-117">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="b4f3f-118">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="b4f3f-119">接下来，运行此命令以列出每个许可计划中可用的服务，并列出这些服务 (索引号) 。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-119">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="b4f3f-120">使用此命令列出分配给用户的许可证，以及这些许可证的列出顺序 (索引号) 。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-120">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="b4f3f-121">查看用户帐户的服务</span><span class="sxs-lookup"><span data-stu-id="b4f3f-121">To view services for a user account</span></span>

<span data-ttu-id="b4f3f-122">若要查看用户Microsoft 365的所有服务，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="b4f3f-122">To view all the Microsoft 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="b4f3f-123">此示例显示用户有权访问 BelindaN@litwareinc.com 的服务。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="b4f3f-124">这将显示与分配给其帐户的所有许可证关联的服务。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="b4f3f-125">此示例显示用户能够 BelindaN@litwareinc.com 分配给其帐户的第一个许可证访问的服务 (索引号为 0) 。</span><span class="sxs-lookup"><span data-stu-id="b4f3f-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="b4f3f-126">若要查看已分配多个许可证的用户的所有服务，请使用以下语法： </span><span class="sxs-lookup"><span data-stu-id="b4f3f-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="b4f3f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4f3f-127">See also</span></span>

[<span data-ttu-id="b4f3f-128">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="b4f3f-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="b4f3f-129">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b4f3f-129">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="b4f3f-130">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="b4f3f-130">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)
