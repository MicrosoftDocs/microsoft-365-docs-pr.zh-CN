---
title: OneDrive 和 SharePoint Online 中的多地理位置功能
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 利用 OneDrive Online 中的多地理位置功能将 Microsoft 365 的触及范围扩展到多个地理区域。
ms.openlocfilehash: 405f876317a6cec6defdf3f1a49b0dc32ac0add2
ms.sourcegitcommit: f7fbf45af64c5c0727fd5eaab309d20ad097a483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2021
ms.locfileid: "53362278"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="5b11f-103">OneDrive 和 SharePoint Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="5b11f-103">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>

<span data-ttu-id="5b11f-104">OneDrive 和 SharePoint Online 中的多地理位置功能支持控制共享资源，如 SharePoint 团队网站和存储在指定地理位置的其余 Microsoft 365 组邮箱。</span><span class="sxs-lookup"><span data-stu-id="5b11f-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of shared resources like SharePoint team sites and Microsoft 365 Group mailboxes stored at rest in a specified geo location.</span></span>

<span data-ttu-id="5b11f-105">每个用户、组邮箱和 SharePoint 站点都有一个首选数据位置 (PDL)，表示要在其中存储相关数据的地理位置。</span><span class="sxs-lookup"><span data-stu-id="5b11f-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="5b11f-106">可将用户的个人数据（Exchange 邮箱和 OneDrive）以及用户创建的任何 Microsoft 365 组或 SharePoint 站点存储在指定地理位置，以满足数据驻留要求。</span><span class="sxs-lookup"><span data-stu-id="5b11f-106">Users' personal data (Exchange mailbox and OneDrive) along with any Microsoft 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="5b11f-107">你可以[为每个地理位置指定不同的管理员](add-a-sharepoint-geo-admin.md)。</span><span class="sxs-lookup"><span data-stu-id="5b11f-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="5b11f-108">用户在使用 Microsoft 365 服务（包括 Office 应用程序、OneDrive 和搜索）时将能获得无缝体验。</span><span class="sxs-lookup"><span data-stu-id="5b11f-108">Users get a seamless experience when using Microsoft 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="5b11f-109">有关详细信息，请参阅[多地理位置环境中的用户体验](multi-geo-user-experience.md)。</span><span class="sxs-lookup"><span data-stu-id="5b11f-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="5b11f-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="5b11f-110">OneDrive</span></span>

<span data-ttu-id="5b11f-111">管理员可依据用户的 PDL 配置每个用户的 OneDrive，或[将其移至](move-onedrive-between-geo-locations.md)附属位置。</span><span class="sxs-lookup"><span data-stu-id="5b11f-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="5b11f-112">个人文件随后保留在该地理位置中，不过可以将这些文件与其他地理位置中的用户共享。</span><span class="sxs-lookup"><span data-stu-id="5b11f-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sharepoint-sites-and-groups"></a><span data-ttu-id="5b11f-113">SharePoint 网站和组</span><span class="sxs-lookup"><span data-stu-id="5b11f-113">SharePoint Sites and Groups</span></span>

<span data-ttu-id="5b11f-114">可通过 SharePoint 管理中心管理多地理位置功能。</span><span class="sxs-lookup"><span data-stu-id="5b11f-114">Management of the Multi-Geo feature is available through the SharePoint admin center.</span></span> <span data-ttu-id="5b11f-115">可在[相应的博客文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)中找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="5b11f-115">Detailed information can be found in the [corresponding blog post](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).</span></span>

<span data-ttu-id="5b11f-116">当用户在多地理环境中创建与 SharePoint 组连接的网站时，他们的 PDL 将用于确定网站及其关联的组邮箱的创建地理位置。</span><span class="sxs-lookup"><span data-stu-id="5b11f-116">When a user creates a SharePoint group-connected site in a multi-geo environment, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="5b11f-117">（如果尚未设置用户的 PDL 值，或已将其设置为未配置为附属位置的地理位置，则会在中心位置创建站点和邮箱。）</span><span class="sxs-lookup"><span data-stu-id="5b11f-117">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="5b11f-118">Microsoft 365、Exchange、OneDrive、SharePoint 和 Teams 服务不是多地理位置服务。</span><span class="sxs-lookup"><span data-stu-id="5b11f-118">Microsoft 365 services other than Exchange, OneDrive, SharePoint, and Teams are not Multi-Geo.</span></span> <span data-ttu-id="5b11f-119">但是Microsoft 365创建的所有组都将使用创建者的 PDL 及其 Exchange 组邮箱进行配置，SharePoint 站点将在相应的地理位置中预配。</span><span class="sxs-lookup"><span data-stu-id="5b11f-119">However, Microsoft 365 Groups that are created by these services will be configured with the PDL of the creator and their Exchange Group mailbox, SharePoint site are provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="5b11f-120">管理多地理位置环境</span><span class="sxs-lookup"><span data-stu-id="5b11f-120">Managing the multi-geo environment</span></span>

<span data-ttu-id="5b11f-121">多地理位置环境的设置和管理是通过 SharePoint 管理中心完成的。</span><span class="sxs-lookup"><span data-stu-id="5b11f-121">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![SharePoint 管理中心中地理位置页面的屏幕截图](../media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="5b11f-123">（诸如移动 SharePoint 站点或 OneDrive 站点的某些操作需要 Microsoft PowerShell。）</span><span class="sxs-lookup"><span data-stu-id="5b11f-123">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="5b11f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b11f-124">See also</span></span>

[<span data-ttu-id="5b11f-125">SharePoint 和 Microsoft 365 组中的多地理位置</span><span class="sxs-lookup"><span data-stu-id="5b11f-125">Multi-Geo in SharePoint and Microsoft 365 Groups</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[<span data-ttu-id="5b11f-126">管理多地理位置环境</span><span class="sxs-lookup"><span data-stu-id="5b11f-126">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="5b11f-127">多地理位置环境中的 SharePoint 存储配额</span><span class="sxs-lookup"><span data-stu-id="5b11f-127">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="5b11f-128">在多地理位置环境中管理 Exchange Online 邮箱</span><span class="sxs-lookup"><span data-stu-id="5b11f-128">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
