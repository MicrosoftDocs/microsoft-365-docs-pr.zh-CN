---
title: 使用 PowerShell 配置 Microsoft 365 用户帐户属性
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
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 配置 Microsoft 365 租户中单个或多个用户帐户的属性。
ms.openlocfilehash: 6a435b3981efa8d8c2be7f6d983a1d062237f0db
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687550"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a><span data-ttu-id="6ef67-103">使用 PowerShell 配置 Microsoft 365 用户帐户属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-103">Configure Microsoft 365 user account properties with PowerShell</span></span>

<span data-ttu-id="6ef67-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="6ef67-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="6ef67-105">虽然您可以使用 Microsoft 365 管理中心配置 Microsoft 365 租户的用户帐户的属性，但您也可以使用 PowerShell 并执行 Microsoft 365 管理中心无法执行的某些操作。</span><span class="sxs-lookup"><span data-stu-id="6ef67-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Microsoft 365 tenant, you can also use PowerShell and do some things that the Microsoft 365 admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="6ef67-106">使用用于图表模块的 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ef67-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="6ef67-107">若要为使用 Azure Active Directory PowerShell for Graph 模块的用户帐户配置属性，请使用 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="6ef67-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="6ef67-108">首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="6ef67-108">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="6ef67-109">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-109">Change properties for a specific user account</span></span>

<span data-ttu-id="6ef67-110">使用 **-ObjectID** 参数标识帐户，并使用其他参数设置或更改特定属性。</span><span class="sxs-lookup"><span data-stu-id="6ef67-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="6ef67-111">下面列出了最常见的参数。</span><span class="sxs-lookup"><span data-stu-id="6ef67-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="6ef67-112">-部门 " \<department name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="6ef67-113">-DisplayName " \<full user name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="6ef67-114">-FacsimilieTelephoneNumber " \<fax number> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="6ef67-115">-GivenName " \<user first name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="6ef67-116">-姓 " \<user last name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="6ef67-117">-移动 " \<mobile phone number> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="6ef67-118">-JobTitle " \<job title> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="6ef67-119">-PreferredLanguage " \<language> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="6ef67-120">-StreetAddress " \<street address> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="6ef67-121">-市/县 " \<city name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="6ef67-122">-状态 " \<state name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="6ef67-123">- \<postal code> 邮政编码 "</span><span class="sxs-lookup"><span data-stu-id="6ef67-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="6ef67-124">-国家/地区 " \<country name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="6ef67-125">-TelephoneNumber " \<office phone number> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="6ef67-126">-UsageLocation " \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="6ef67-127">这是 ISO 3166-1 alpha-2 (A2) 双字母国家或地区代码。</span><span class="sxs-lookup"><span data-stu-id="6ef67-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="6ef67-128">有关其他参数，请参阅 [AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="6ef67-129">若要显示用户帐户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6ef67-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="6ef67-130">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6ef67-130">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="6ef67-131">获取用户帐户上的所有信息 (**AzureADUser**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-131">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-132">按字母顺序对用户主体名称列表进行排序 (**对 UserPrincipalName 进行排序**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-132">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-133">仅显示每个帐户的 "用户主体名称" 属性 (**选择 "UserPrincipalName**) "。</span><span class="sxs-lookup"><span data-stu-id="6ef67-133">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>

- <span data-ttu-id="6ef67-134">每次显示一屏 (**更**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-134">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="6ef67-135">此命令将列出你的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="6ef67-135">This command will list all of your accounts.</span></span> <span data-ttu-id="6ef67-136">如果要根据其显示名称显示帐户的用户主体名称 (名字和姓氏) ，请填写下面的 **$userName** 变量 (删除 \< and > 字符) ，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6ef67-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6ef67-137">本示例显示名为 Caleb Sills 的用户帐户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="6ef67-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6ef67-138">通过使用 **$upn** 变量，可以根据各个帐户的显示名称对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="6ef67-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="6ef67-139">下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="6ef67-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="6ef67-140">更改所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-140">Change properties for all user accounts</span></span>

<span data-ttu-id="6ef67-141">若要更改所有用户的属性，您可以使用 **AzureADUser** 和 **AzureADUser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="6ef67-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="6ef67-142">下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="6ef67-142">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="6ef67-143">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6ef67-143">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="6ef67-144">获取用户帐户上的所有信息 (**AzureADUser**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-144">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-145">将用户位置设置为 "法国 (**AzureADUser-UsageLocation" "FR"**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-145">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="6ef67-146">更改特定用户帐户集的属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="6ef67-147">若要更改特定用户帐户集的属性，您可以使用 **AzureADUser**、 **Where**和 **AzureADUser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="6ef67-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="6ef67-148">下面的示例将会计部门的所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="6ef67-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="6ef67-149">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6ef67-149">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="6ef67-150">获取用户帐户上的所有信息 (**AzureADUser**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-150">Get all of the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-151">查找其 "部门" 属性设置为 "记帐" 的所有用户帐户 (**其中 {$ _。部门-eq "记帐"}**) 并将生成的信息发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-151">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-152">将用户位置设置为 "法国 (**AzureADUser-UsageLocation" "FR"**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-152">Set the user location to France (**Set-AzureADUser -UsageLocation "FR"**).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6ef67-153">使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="6ef67-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6ef67-154">若要使用适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块配置用户帐户的属性，请使用 **get-msoluser** cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="6ef67-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="6ef67-155">首先， [连接到 Microsoft 365 租户](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="6ef67-155">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="6ef67-156">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="6ef67-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="6ef67-157">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="6ef67-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="6ef67-158">更改特定用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-158">Change properties for a specific user account</span></span>

<span data-ttu-id="6ef67-159">若要配置特定用户帐户的属性，请使用 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet 并指定要设置或更改的属性。</span><span class="sxs-lookup"><span data-stu-id="6ef67-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="6ef67-160">您可以使用 **-UserPrincipalName** 参数标识帐户，并使用其他参数设置或更改特定属性。</span><span class="sxs-lookup"><span data-stu-id="6ef67-160">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="6ef67-161">下面是最常见的参数的列表。</span><span class="sxs-lookup"><span data-stu-id="6ef67-161">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="6ef67-162">-市/县 " \<city name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="6ef67-163">-国家/地区 " \<country name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="6ef67-164">-部门 " \<department name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="6ef67-165">-DisplayName " \<full user name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="6ef67-166">-传真 " \<fax number> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="6ef67-167">-FirstName " \<user first name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="6ef67-168">-LastName " \<user last name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="6ef67-169">-MobilePhone " \<mobile phone number> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="6ef67-170">-Office " \<office location> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="6ef67-171">-PhoneNumber " \<office phone number> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="6ef67-172">- \<postal code> 邮政编码 "</span><span class="sxs-lookup"><span data-stu-id="6ef67-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="6ef67-173">-PreferredLanguage " \<language> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="6ef67-174">-状态 " \<state name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="6ef67-175">-StreetAddress " \<street address> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="6ef67-176">-标题 " \<title name> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="6ef67-177">-UsageLocation " \<2-character country or region code> "</span><span class="sxs-lookup"><span data-stu-id="6ef67-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="6ef67-178">这是 ISO 3166-1 alpha-2 (A2) 双字母国家或地区代码。</span><span class="sxs-lookup"><span data-stu-id="6ef67-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="6ef67-179">有关其他参数，请参阅 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-179">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="6ef67-180">若要查看所有用户的用户主体名称，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6ef67-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="6ef67-181">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6ef67-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="6ef67-182">获取用户帐户上的所有信息 (**get-msoluser**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-182">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-183">按字母顺序对用户主体名称列表进行排序 (**对 UserPrincipalName 进行排序**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-183">Sort the list of User Principal Names alphabetically (**Sort UserPrincipalName**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-184">仅显示每个帐户的 "用户主体名称" 属性 (**选择 "UserPrincipalName**) "。</span><span class="sxs-lookup"><span data-stu-id="6ef67-184">Display just the User Principal Name property for each account (**Select UserPrincipalName**).</span></span>
    
- <span data-ttu-id="6ef67-185">每次显示一屏 (**更**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-185">Display them one screen at a time (**More**).</span></span>
    
<span data-ttu-id="6ef67-186">此命令将列出你的所有帐户。</span><span class="sxs-lookup"><span data-stu-id="6ef67-186">This command will list all of your accounts.</span></span> <span data-ttu-id="6ef67-187">如果要根据其显示名称显示帐户的用户主体名称 (名字和姓氏) ，请填写下面的 **$userName** 变量 (删除 \< and > 字符) ，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6ef67-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6ef67-188">本示例显示名为 Caleb Sills 的用户的用户主体名称。</span><span class="sxs-lookup"><span data-stu-id="6ef67-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="6ef67-189">通过使用 **$upn** 变量，可以根据各个帐户的显示名称对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="6ef67-189">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="6ef67-190">下面的示例展示了如何将 Belinda Newman 的使用位置设置为华北，但指定了她的显示名称而不是她的用户主体名称：</span><span class="sxs-lookup"><span data-stu-id="6ef67-190">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="6ef67-191">更改所有用户帐户的属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-191">Change properties for all user accounts</span></span>

<span data-ttu-id="6ef67-p110">要更改所有用户的属性，您可以将 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 结合使用。下面的示例将所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="6ef67-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="6ef67-194">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6ef67-194">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="6ef67-195">获取用户帐户上的所有信息 (**get-msoluser**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-195">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-196">将用户位置设置为 "法国 (**get-msoluser-UsageLocation" "FR"**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-196">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="6ef67-197">更改特定用户帐户集的属性</span><span class="sxs-lookup"><span data-stu-id="6ef67-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="6ef67-198">若要更改特定用户帐户集的属性，您可以使用 **get-msoluser**、 **Where**和 **get-msoluser** cmdlet 的组合。</span><span class="sxs-lookup"><span data-stu-id="6ef67-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="6ef67-199">下面的示例将会计部门的所有用户的使用地点更改为法国：</span><span class="sxs-lookup"><span data-stu-id="6ef67-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="6ef67-200">此命令指示 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6ef67-200">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="6ef67-201">获取用户帐户上的所有信息 (**get-msoluser**) 并将其发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-201">Get all of the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-202">查找其 "部门" 属性设置为 "记帐" 的所有用户帐户 (**其中 {$ _。部门-eq "记帐"}**) 并将生成的信息发送到下一个命令 (**|**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-202">Find all of the user accounts that have their Department property set to "Accounting" (**Where {$_.Department -eq "Accounting"}**) and send the resulting information to the next command (**|**).</span></span>
    
- <span data-ttu-id="6ef67-203">将用户位置设置为 "法国 (**get-msoluser-UsageLocation" "FR"**) 。</span><span class="sxs-lookup"><span data-stu-id="6ef67-203">Set the user location to France (**Set-MsolUser -UsageLocation "FR"**).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="6ef67-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ef67-204">See also</span></span>

[<span data-ttu-id="6ef67-205">使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="6ef67-205">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="6ef67-206">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="6ef67-206">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="6ef67-207">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="6ef67-207">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)
