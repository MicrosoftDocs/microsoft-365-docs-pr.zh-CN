---
title: 将 OneDrive 站点移动到其他地理位置
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
description: 查找有关将 OneDrive 站点移动到不同地理位置的信息，包括如何安排网站移动和向用户传达预期。
ms.openlocfilehash: 59b3fb47fd195967e7af056c7a71fb4e736471d1
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687563"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="91591-103">将 OneDrive 站点移动到其他地理位置</span><span class="sxs-lookup"><span data-stu-id="91591-103">Move a OneDrive site to a different geo location</span></span> 

<span data-ttu-id="91591-p101">使用 OneDrive 地域移动时，您可以将用户的 OneDrive 移到其他地理位置。OneDrive 地理位置移动由 SharePoint Online 管理员或 Microsoft 365 全局管理员执行。在开始 OneDrive 地域移动之前，请务必通知用户其 OneDrive 正在移动，并建议在移动的持续时间内关闭所有文件。 (如果用户在移动过程中使用 Office 客户端打开了文档，则在移动完成后，将需要将文档保存到新位置。 ) 如果需要，可以将移动安排在将来的时间。</span><span class="sxs-lookup"><span data-stu-id="91591-p101">With OneDrive geo move, you can move a user's OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Microsoft 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="91591-p102">OneDrive 服务使用 Azure Blob 存储来存储内容。与用户的 OneDrive 关联的存储 blob 将在目标 OneDrive 的40天内从源位置移动到目标地理位置，以供用户使用。一旦目标 OneDrive 可用，将立即还原对用户的 OneDrive 的访问。</span><span class="sxs-lookup"><span data-stu-id="91591-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user's OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user's OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="91591-p103">在 OneDrive 异地移动窗口期间（约 2-6 小时），用户的 OneDrive 将被设置为只读。用户仍可通过 OneDrive 同步客户端访问其文件或访问其在 SharePoint Online 中的 OneDrive 站点。OneDrive 异地移动完成后，当用户导航到 Microsoft 365 应用启动器中的 OneDrive 时，将被自动连接到他们在目标地理位置中的 OneDrive。同步客户端将自动从新位置开始同步。</span><span class="sxs-lookup"><span data-stu-id="91591-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Microsoft 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="91591-115">执行本文中的步骤需要安装 [Microsoft SharePoint Online PowerShell 模块](https://www.microsoft.com/download/details.aspx?id=35588)。</span><span class="sxs-lookup"><span data-stu-id="91591-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="91591-116">向用户传达</span><span class="sxs-lookup"><span data-stu-id="91591-116">Communicating to your users</span></span>

<span data-ttu-id="91591-p104">如果在地理位置之间移动 OneDrive 网站，请务必向用户传达预期内容。这有助于减少用户混淆并联系支持人员。移动前向用户发送电子邮件，让他们了解以下信息：</span><span class="sxs-lookup"><span data-stu-id="91591-p104">When moving OneDrive sites between geo locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="91591-120">移动应该开始的时间和需要花费的时长</span><span class="sxs-lookup"><span data-stu-id="91591-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="91591-121">其 OneDrive 要移动到的地理位置和用于访问新位置的 URL</span><span class="sxs-lookup"><span data-stu-id="91591-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="91591-122">移动期间，他们应关闭文件，不进行任何编辑。</span><span class="sxs-lookup"><span data-stu-id="91591-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="91591-123">文件权限和共享不会因移动而更改。</span><span class="sxs-lookup"><span data-stu-id="91591-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="91591-124">[多地理位置环境中的用户体验](multi-geo-user-experience.md)预期将呈现的内容</span><span class="sxs-lookup"><span data-stu-id="91591-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="91591-125">移动成功后，务必向用户发送电子邮件，告知他们可在 OneDrive 中恢复工作。</span><span class="sxs-lookup"><span data-stu-id="91591-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="scheduling-onedrive-site-moves"></a><span data-ttu-id="91591-126">安排 OneDrive 网站移动</span><span class="sxs-lookup"><span data-stu-id="91591-126">Scheduling OneDrive site moves</span></span>

<span data-ttu-id="91591-p105">可以提前安排 OneDrive 网站移动（在本文后面介绍）。建议先通过少数用户验证工作流和通信策略。如果你对该过程感到满意，可以按如下方式安排移动：</span><span class="sxs-lookup"><span data-stu-id="91591-p105">You can schedule OneDrive site moves in advance (described later in this article). We recommend that you start with a small number of users to validate your workflows and communication strategies. Once you are comfortable with the process, you can schedule moves as follows:</span></span>

- <span data-ttu-id="91591-130">一次最多可以安排 4,000 次移动。</span><span class="sxs-lookup"><span data-stu-id="91591-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="91591-131">移动开始后，可以安排更多移动操作，在在队列及任何给定时间内最多有 4,000 个待处理移动。</span><span class="sxs-lookup"><span data-stu-id="91591-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
- <span data-ttu-id="91591-132">可移动的最大 OneDrive 大小为 1 太字节 (1 TB)。</span><span class="sxs-lookup"><span data-stu-id="91591-132">The maximum size of a OneDrive that can be moved is 1 terabyte (1 TB).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="91591-133">移动 OneDrive 网站</span><span class="sxs-lookup"><span data-stu-id="91591-133">Moving a OneDrive site</span></span>

<span data-ttu-id="91591-p106">若要执行 OneDrive geo 移动，租户管理员必须先将用户的首选数据位置设置 (PDL) 到相应的地理位置。设置了 PDL 后，请等待至少24小时，以便在开始 OneDrive geo 移动之前跨地理位置同步 PDL 更新。</span><span class="sxs-lookup"><span data-stu-id="91591-p106">To perform a OneDrive geo move, the tenant administrator must first set the user's Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="91591-136">使用 geo 移动 cmdlet 时，请使用以下语法在用户的当前 OneDrive 地理位置连接到 SPO 服务：</span><span class="sxs-lookup"><span data-stu-id="91591-136">When using the geo move cmdlets, connect to SPO Service at the user's current OneDrive geo location, using the following syntax:</span></span>

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="91591-137">例如：若要移动 OneDrive 的用户 "Matt@contosoenergy.onmicrosoft.com"，请连接到 EUR SharePoint 管理中心，因为用户的 OneDrive 在 EUR 地理位置：</span><span class="sxs-lookup"><span data-stu-id="91591-137">For example: To move OneDrive of user 'Matt@contosoenergy.onmicrosoft.com', connect to EUR SharePoint Admin center as the user's OneDrive is in EUR geo location:</span></span>

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![显示 connect-sposervice cmdlet 的 PowerShell 窗口的屏幕截图](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="91591-139">验证环境</span><span class="sxs-lookup"><span data-stu-id="91591-139">Validating the environment</span></span>

<span data-ttu-id="91591-140">在启动 OneDrive 异地移动前，我们建议验证环境。</span><span class="sxs-lookup"><span data-stu-id="91591-140">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="91591-141">要确保所有地理位置都可兼容，请运行：</span><span class="sxs-lookup"><span data-stu-id="91591-141">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCrossCompatibilityStatus`

<span data-ttu-id="91591-142">你将会看到可以在其中移动的地理位置和天气内容列表将显示为“兼容”。</span><span class="sxs-lookup"><span data-stu-id="91591-142">You will see a list of your geo locations and whether content can be moved between will be denoted as "Compatible".</span></span> <span data-ttu-id="91591-143">如果命令返回“不兼容”，请稍后重新验证状态。</span><span class="sxs-lookup"><span data-stu-id="91591-143">If the command returns "Incompatible" please retry validating the status at a later date.</span></span>

<span data-ttu-id="91591-144">举例来说，如果 OneDrive 包含子网站，则不能移动它。</span><span class="sxs-lookup"><span data-stu-id="91591-144">If a OneDrive contains a subsite, for example, it cannot be moved.</span></span> <span data-ttu-id="91591-145">你可以将 Start-SPOUserAndContentMove cmdlet 与 -ValidationOnly 参数结合使用，以验证 OneDrive 是否可以移动：</span><span class="sxs-lookup"><span data-stu-id="91591-145">You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="91591-p109">如果 OneDrive 可以移动，则返回“成功”，如果存在阻止 OneDrive 移动的法定保留或子网站，则返回“失败”。验证 OneDrive 可以移动后，即可开始移动。</span><span class="sxs-lookup"><span data-stu-id="91591-p109">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="91591-148">启动 OneDrive 异地移动</span><span class="sxs-lookup"><span data-stu-id="91591-148">Start a OneDrive geo move</span></span>

<span data-ttu-id="91591-149">若要开始移动，请运行：</span><span class="sxs-lookup"><span data-stu-id="91591-149">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="91591-150">使用以下参数：</span><span class="sxs-lookup"><span data-stu-id="91591-150">Using these parameters:</span></span>

-   <span data-ttu-id="91591-151">_UserPrincipalName_ – 要移动其 OneDrive 的用户的 UPN。</span><span class="sxs-lookup"><span data-stu-id="91591-151">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="91591-p110">_DestinationDataLocation_ –需要移动 OneDrive 的地理位置。此位置应与用户的首选数据位置相同。</span><span class="sxs-lookup"><span data-stu-id="91591-p110">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user's preferred data location.</span></span>

<span data-ttu-id="91591-154">例如，若要将 matt@contosoenergy.onmicrosoft.com 的 OneDrive 从 EUR 移动到 AUS，请运行：</span><span class="sxs-lookup"><span data-stu-id="91591-154">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![显示 Start-SPOUserAndContentMove cmdlet 的 PowerShell 窗口的屏幕截图](../media/move-onedrive-between-geo-locations-image2.png)

<span data-ttu-id="91591-156">若要设置在以后执行的异地移动，请使用以下参数之一：</span><span class="sxs-lookup"><span data-stu-id="91591-156">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="91591-p111">_PreferredMoveBeginDate_ – 可能在此指定的时间内开始移动。必须使用协调世界时 (UTC) 指定时间。</span><span class="sxs-lookup"><span data-stu-id="91591-p111">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="91591-p112">_PreferredMoveEndDate_ – 可能在此指定的时间内完成移动。必须使用协调世界时 (UTC) 指定时间。</span><span class="sxs-lookup"><span data-stu-id="91591-p112">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="91591-161">取消 OneDrive 异地移动</span><span class="sxs-lookup"><span data-stu-id="91591-161">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="91591-162">您可以停止用户 OneDrive 的 geo 移动，只要移动不是在进行中，或者使用 cmdlet 完成：</span><span class="sxs-lookup"><span data-stu-id="91591-162">You can stop the geo move of a user's OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="91591-163">其中 _UserPrincipalName_ 是你想要停止移动其 OneDrive 的用户的 UPN。</span><span class="sxs-lookup"><span data-stu-id="91591-163">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="91591-164">确定当前状态</span><span class="sxs-lookup"><span data-stu-id="91591-164">Determining current status</span></span>

<span data-ttu-id="91591-165">您可以使用 SPOUserAndContentMoveState cmdlet 检查您连接到的地理位置的 OneDrive 异地移动的状态。</span><span class="sxs-lookup"><span data-stu-id="91591-165">You can check the status of a OneDrive geo move in or out of the geo that you're connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="91591-166">下表描述了这些移动状态。</span><span class="sxs-lookup"><span data-stu-id="91591-166">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="91591-167"><strong>状态</strong></span><span class="sxs-lookup"><span data-stu-id="91591-167"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="91591-168"><strong>说明</strong></span><span class="sxs-lookup"><span data-stu-id="91591-168"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="91591-169">NotStarted</span><span class="sxs-lookup"><span data-stu-id="91591-169">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="91591-170">移动尚未开始。</span><span class="sxs-lookup"><span data-stu-id="91591-170">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91591-171">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="91591-171">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="91591-172">移动正在进行中，状态为以下之一：验证 (1/4)、备份 (2/4)、还原 (3/4)、清除 (4/4)。</span><span class="sxs-lookup"><span data-stu-id="91591-172">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="91591-173">Success</span><span class="sxs-lookup"><span data-stu-id="91591-173">Success</span></span></td>
<td align="left"><span data-ttu-id="91591-174">移动已成功完成。</span><span class="sxs-lookup"><span data-stu-id="91591-174">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91591-175">Failed</span><span class="sxs-lookup"><span data-stu-id="91591-175">Failed</span></span></td>
<td align="left"><span data-ttu-id="91591-176">移动失败。</span><span class="sxs-lookup"><span data-stu-id="91591-176">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="91591-177">若要查找特定用户移动的状态，请使用 UserPrincipalName 参数：</span><span class="sxs-lookup"><span data-stu-id="91591-177">To find the status of a specific user's move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="91591-178">若要查找您要连接到的地理位置的所有移动的状态，请使用 MoveState 参数和以下值之一： NotStarted、InProgress、Success、Failed、All。</span><span class="sxs-lookup"><span data-stu-id="91591-178">To find the status of all of the moves in or out of the geo location that you're connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="91591-179">此外，还可以添加 `-Verbose` 参数，以获取移动状态更为详细的说明。</span><span class="sxs-lookup"><span data-stu-id="91591-179">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="91591-180">用户体验</span><span class="sxs-lookup"><span data-stu-id="91591-180">User Experience</span></span>

<span data-ttu-id="91591-p113">在用户的 OneDrive 被移动到其他地理位置时，OneDrive 用户应会注意到最小的中断。除了在移动期间的简要只读状态以外，一旦移动完成，现有链接和权限即可继续按预期运行。</span><span class="sxs-lookup"><span data-stu-id="91591-p113">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="91591-183">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="91591-183">OneDrive for Business</span></span>

<span data-ttu-id="91591-p114">在移动过程中，用户的 OneDrive 设置为只读。移动完成后，当用户导航到 OneDrive 时，会将用户定向到其在新地理位置的 OneDrive： Microsoft 365 应用启动器或 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="91591-p114">While the move is in progress the user's OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Microsoft 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="91591-186">OneDrive 内容权限</span><span class="sxs-lookup"><span data-stu-id="91591-186">Permissions on OneDrive content</span></span>

<span data-ttu-id="91591-187">拥有 OneDrive 内容权限的用户将继续在移动过程中和完成后访问内容。</span><span class="sxs-lookup"><span data-stu-id="91591-187">Users with permissions to OneDrive content will continue to have access to the content during the move and after it's complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="91591-188">OneDrive 同步客户端</span><span class="sxs-lookup"><span data-stu-id="91591-188">OneDrive Sync Client</span></span> 

<span data-ttu-id="91591-p115">OneDrive 异地移动完成后，OneDrive 同步客户端将自动检测同步并将其无缝转移到新的 OneDrive 位置。用户无需重新登录或执行任何其他操作。（需要 17.3.6943.0625 版或更高版本同步客户端。）</span><span class="sxs-lookup"><span data-stu-id="91591-p115">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="91591-192">如果用户在 OneDrive 异地移动进行时更新文件，则同步客户端将告知用户“在移动过程中，文件上传处于待定状态”。</span><span class="sxs-lookup"><span data-stu-id="91591-192">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="91591-193">共享链接</span><span class="sxs-lookup"><span data-stu-id="91591-193">Sharing links</span></span> 

<span data-ttu-id="91591-194">OneDrive 异地移动完成后，被移动文件的现有共享链接将自动重定向到新地理位置。</span><span class="sxs-lookup"><span data-stu-id="91591-194">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="91591-195">OneNote 体验</span><span class="sxs-lookup"><span data-stu-id="91591-195">OneNote Experience</span></span> 

<span data-ttu-id="91591-p116">OneDrive 异地移动完成后，OneNote win32 客户端和 UWP（通用）应用将自动检测笔记本并将其无缝同步到新的 OneDrive 位置。用户无需重新登录或执行任何其他操作。对用户唯一可见的指示符是，当 OneDrive 异地移动进行时，笔记本同步可能失败。以下 OneNote 客户端版本提供了此体验：</span><span class="sxs-lookup"><span data-stu-id="91591-p116">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="91591-200">OneNote win32 – 版本 16.0.8326.2096（及更高版本）</span><span class="sxs-lookup"><span data-stu-id="91591-200">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="91591-201">OneNote UWP – 版本16.0.8431.1006（及更高版本）</span><span class="sxs-lookup"><span data-stu-id="91591-201">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="91591-202">OneNote 移动应用 – 版本 16.0.8431.1011（及更高版本）</span><span class="sxs-lookup"><span data-stu-id="91591-202">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="91591-203">Teams 应用</span><span class="sxs-lookup"><span data-stu-id="91591-203">Teams app</span></span>

<span data-ttu-id="91591-p117">在 OneDrive 异地移动完成后，用户将可以访问其在 Teams 应用上的 OneDrive 文件。此外，在异地移动前通过 Teams 聊天从其 OneDrive 中共享的文件将可在移动完成后继续使用。</span><span class="sxs-lookup"><span data-stu-id="91591-p117">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="91591-206">OneDrive for Business 移动应用 (iOS)</span><span class="sxs-lookup"><span data-stu-id="91591-206">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="91591-207">在 OneDrive 异地移动完成后，用户需要在 iOS 移动应用上注销并重新登录，以同步到新的 OneDrive 位置。</span><span class="sxs-lookup"><span data-stu-id="91591-207">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="91591-208">现有已关注组和网站</span><span class="sxs-lookup"><span data-stu-id="91591-208">Existing followed groups and sites</span></span>

<span data-ttu-id="91591-p118">已关注的网站和组将显示在用户的 OneDrive 中，而不考虑其地理位置。驻留在另一个地理位置的网站和组将在一个单独的选项卡中打开。</span><span class="sxs-lookup"><span data-stu-id="91591-p118">Followed sites and groups will show up in the user's OneDrive regardless of their geo location. Sites and groups hosted in another geo location will open in a separate tab.</span></span>

### <a name="delve-geo-url-updates"></a><span data-ttu-id="91591-211">Delve Geo URL 更新</span><span class="sxs-lookup"><span data-stu-id="91591-211">Delve Geo URL updates</span></span>

<span data-ttu-id="91591-212">只有在将用户的 OneDrive 移动到新地理位置之后，才会将用户发送到与自己的 PDL 相对应的 Delve 地理位置。</span><span class="sxs-lookup"><span data-stu-id="91591-212">Users will be sent to the Delve geo corresponding to their PDL only after their OneDrive has been moved to the new geo.</span></span>
