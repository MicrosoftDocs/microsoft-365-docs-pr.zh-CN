---
title: 配置 Microsoft 365 多地理位置电子数据展示
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
localization_priority: Normal
ms.collection: Strat_SP_gtc
description: 了解如何使用 Region 参数配置电子数据展示，以便在 Microsoft 365 多地理位置的附属位置使用。
ms.openlocfilehash: d1d66a9e7953b540e318c8364bdcb8d72654b482
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2020
ms.locfileid: "48636801"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="6f289-103">Microsoft 365 多地理位置电子数据展示配置</span><span class="sxs-lookup"><span data-stu-id="6f289-103">Microsoft 365 Multi-Geo eDiscovery configuration</span></span>

<span data-ttu-id="6f289-104">[高级电子数据展示功能](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20) 允许多地理电子数据展示管理员搜索所有信息，而无需使用 "区域" 安全筛选器。</span><span class="sxs-lookup"><span data-stu-id="6f289-104">[Advanced eDiscovery capabilities](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20) allow a multi-geo eDiscovery administrator to search all of the geos without needing to utilize a "Region" security filter.</span></span> <span data-ttu-id="6f289-105">将数据导出到多地理位置租户的中央位置的 Azure 实例。</span><span class="sxs-lookup"><span data-stu-id="6f289-105">Data is exported to the Azure instance of the central location of the multi-geo tenant.</span></span> 

<span data-ttu-id="6f289-106">如果没有高级电子数据展示功能，则多地理位置租户的电子数据展示管理者或管理员将能够仅在该租户的中心位置执行电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="6f289-106">Without advanced eDiscovery capabilities, an eDiscovery manager or administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant.</span></span> <span data-ttu-id="6f289-107">若要支持对附属位置进行电子数据展示的能力，可通过 PowerShell 获取一个新的合规性安全筛选器参数，名为 "Region"。</span><span class="sxs-lookup"><span data-stu-id="6f289-107">To support the ability to conduct eDiscovery for satellite locations, a new compliance security filter parameter named "Region" is available via PowerShell.</span></span> <span data-ttu-id="6f289-108">此参数可由其中心位置在北美、欧洲或亚太地区的租户使用。</span><span class="sxs-lookup"><span data-stu-id="6f289-108">This parameter can be used by tenants whose central location is in North America, Europe, or Asia Pacific.</span></span> <span data-ttu-id="6f289-109">对于其中心位置不在北美、欧洲或亚太地区且需要跨卫星地理位置执行电子数据展示的租户，建议使用高级电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="6f289-109">Advanced eDiscovery is recommended for tenants whose central location is not in North America, Europe, or Asia Pacific and who need to perform eDiscovery across satellite geo locations.</span></span> 

<span data-ttu-id="6f289-110">Microsoft 365 全局管理员必须分配电子数据展示管理者权限，以允许其他人员执行电子数据展示，并在其适用的合规性安全筛选器中分配“Region”参数，以便将要进行电子数据展示的区域指定为附属位置，否则，不会对该附属位置执行任何电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="6f289-110">The Microsoft 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a "Region" parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="6f289-p103">当为特定附属位置设置电子数据展示管理者或管理员角色时，电子数据展示管理者或管理员将只能对位于该附属位置的 SharePoint 网站和 OneDrive 网站执行电子数据展示搜索操作。如果电子数据展示管理者或管理员尝试搜索指定附属位置以外的 SharePoint 或 OneDrive 网站，将不返回任何结果。此外，当某个附属位置的电子数据展示管理者或管理员触发导出时，数据将导出到该地区的 Azure 实例。通过禁止跨受控界限导出内容，将有助于组织保持合规性。</span><span class="sxs-lookup"><span data-stu-id="6f289-p103">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="6f289-115">如果需要电子数据展示管理者搜索多个 SharePoint 附属位置，将需要为电子数据展示管理者创建另一个用户帐户，以指定 OneDrive 或 SharePoint 网站所在的备用附属位置。</span><span class="sxs-lookup"><span data-stu-id="6f289-115">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

<span data-ttu-id="6f289-116">针对区域设置合规性安全筛选器：</span><span class="sxs-lookup"><span data-stu-id="6f289-116">To set the Compliance Security Filter for a Region:</span></span>

1. [<span data-ttu-id="6f289-117">连接到 Microsoft 365 安全与合规中心 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f289-117">Connect to Microsoft 365 Security & Compliance Center PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)

2. <span data-ttu-id="6f289-118">使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="6f289-118">Use the following syntax:</span></span>

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   <span data-ttu-id="6f289-119">例如：</span><span class="sxs-lookup"><span data-stu-id="6f289-119">For example:</span></span>

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

<span data-ttu-id="6f289-120">请参阅 [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/new-compliancesecurityfilter) 一文了解其他参数和语法。</span><span class="sxs-lookup"><span data-stu-id="6f289-120">See the [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/new-compliancesecurityfilter) article for additional parameters and syntax.</span></span>
