---
title: 多地理位置环境中的 SharePoint 存储配额
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: 了解SharePoint多地理位置环境中配置存储配额，以及如何由 SharePoint Online 管理员管理配额。
ms.openlocfilehash: 0843407e7926027e28cdd1f5893c4aafec4e1cd5
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "53230087"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="92d5a-103">多地理位置环境中的 SharePoint 存储配额</span><span class="sxs-lookup"><span data-stu-id="92d5a-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="92d5a-104">默认情况下，多地理位置环境中的所有地理位置具有相同的可用租户存储配额。</span><span class="sxs-lookup"><span data-stu-id="92d5a-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="92d5a-105">使用 SharePoint 地理位置存储配额设置，你可以管理每个地理位置的存储配额。</span><span class="sxs-lookup"><span data-stu-id="92d5a-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="92d5a-106">为地理位置分配存储配额时，该配额将成为可用于该地理位置的最大存储量，并将从可用租户存储配额扣除该配额。</span><span class="sxs-lookup"><span data-stu-id="92d5a-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="92d5a-107">然后，将在未分配特定存储配额的已配置地理位置之间共享剩余的可用租户存储配额。</span><span class="sxs-lookup"><span data-stu-id="92d5a-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="92d5a-108">SharePoint Online 管理员可通过连接到中心位置来为任何地理位置分配 SharePoint 存储配额。</span><span class="sxs-lookup"><span data-stu-id="92d5a-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="92d5a-109">附属位置的地理位置管理员可查看存储配额，但无法分配。</span><span class="sxs-lookup"><span data-stu-id="92d5a-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="92d5a-110">为地理位置配置存储配额</span><span class="sxs-lookup"><span data-stu-id="92d5a-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="92d5a-111">使用 [Microsoft SharePoint Online 模块](https://www.microsoft.com/download/details.aspx?id=35588)，并连接到中心位置来为地理位置分配存储配额。</span><span class="sxs-lookup"><span data-stu-id="92d5a-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/download/details.aspx?id=35588) and connect to the central location to allocate the storage quota for a geo location.</span></span>

<span data-ttu-id="92d5a-112">若要为某个位置分配存储配额，请运行 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="92d5a-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>
```

<span data-ttu-id="92d5a-113">若要查看当前地理位置的存储配额，请运行：</span><span class="sxs-lookup"><span data-stu-id="92d5a-113">To view Storage Quota for the current geo location, run:</span></span>

```powershell
Get-SPOGeoStorageQuota
```

![显示 Get-SPOGeoStorageQuota cmdlet 的 PowerShell 窗口的屏幕截图](../media/multi-geo-storage-quota.png)

<span data-ttu-id="92d5a-115">若要查看所有地理位置的存储配额，请运行：</span><span class="sxs-lookup"><span data-stu-id="92d5a-115">To view Storage Quota for all geo locations, run:</span></span>

```powershell
Get-SPOGeoStorageQuota -AllLocations
```

<span data-ttu-id="92d5a-116">若要为某个地理位置删除分配的存储配额，请设置 `StorageQuota value = 0`：</span><span class="sxs-lookup"><span data-stu-id="92d5a-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0
```
