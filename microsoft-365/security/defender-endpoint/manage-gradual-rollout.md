---
title: 管理 Microsoft Defender 更新的逐步推出过程
description: 了解逐步更新过程和控件
keywords: 更新， 更新过程， 控件， 发布
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fac6205e3045828cf2bbcc27a9a8020c3d63186c
ms.sourcegitcommit: ccbdf2638fc6646bfb89450169953f4c3ce4b9b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "53105605"
---
#  <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a><span data-ttu-id="fce1f-104">管理 Microsoft Defender 更新的逐步推出过程</span><span class="sxs-lookup"><span data-stu-id="fce1f-104">Manage the gradual rollout process for Microsoft Defender updates</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


<span data-ttu-id="fce1f-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="fce1f-105">**Applies to:**</span></span>

- [<span data-ttu-id="fce1f-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="fce1f-106">Microsoft Defender for Endpoint</span></span>](/microsoft-365/security/defender-endpoint/)


<span data-ttu-id="fce1f-107">确保客户端组件是最新的，以提供关键保护功能和防止攻击，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="fce1f-107">It is important to ensure that client components are up-to-date to deliver critical protection capabilities and prevent attacks.</span></span>

<span data-ttu-id="fce1f-108">功能通过多个组件提供：</span><span class="sxs-lookup"><span data-stu-id="fce1f-108">Capabilities are provided through several components:</span></span> 

- [<span data-ttu-id="fce1f-109">终结点检测&响应</span><span class="sxs-lookup"><span data-stu-id="fce1f-109">Endpoint Detection & Response</span></span>](overview-endpoint-detection-response.md) 
- <span data-ttu-id="fce1f-110">[具有云保护](microsoft-defender-antivirus-in-windows-10.md#microsoft-defender-antivirus-your-next-generation-protection)[的下一代保护](cloud-protection-microsoft-defender-antivirus.md)</span><span class="sxs-lookup"><span data-stu-id="fce1f-110">[Next-generation protection](microsoft-defender-antivirus-in-windows-10.md#microsoft-defender-antivirus-your-next-generation-protection) with [cloud-delivered protection](cloud-protection-microsoft-defender-antivirus.md)</span></span> 
- [<span data-ttu-id="fce1f-111">攻击面减少</span><span class="sxs-lookup"><span data-stu-id="fce1f-111">Attack Surface Reduction</span></span>](overview-attack-surface-reduction.md)

<span data-ttu-id="fce1f-112">使用逐步发布过程每月发布一次更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-112">Updates are released monthly using a gradual release process.</span></span> <span data-ttu-id="fce1f-113">此过程有助于启用早期故障检测，以在影响发生时捕获影响，并快速在更大推出前解决它。</span><span class="sxs-lookup"><span data-stu-id="fce1f-113">This process helps to enable early failure detection to catch impact as it occurs and address it quickly before a larger rollout.</span></span> 

> [!NOTE]
> <span data-ttu-id="fce1f-114">若要详细了解如何控制日常定义更新，请参阅计划Microsoft Defender 防病毒[定义更新 - Windows安全|Microsoft Docs](manage-protection-update-schedule-microsoft-defender-antivirus.md)。定义更新确保下一代保护可以抵御新威胁，即使云提供的保护对终结点不可用。</span><span class="sxs-lookup"><span data-stu-id="fce1f-114">For more information on how to control daily definition updates, see [Schedule Microsoft Defender Antivirus definition updates - Windows security | Microsoft Docs](manage-protection-update-schedule-microsoft-defender-antivirus.md). Definition updates ensure that next-generation protection can defend against new threats, even if cloud-delivered protection is not available to the endpoint.</span></span>

## <a name="microsoft-gradual-rollout-model"></a><span data-ttu-id="fce1f-115">Microsoft 逐步推出模型</span><span class="sxs-lookup"><span data-stu-id="fce1f-115">Microsoft gradual rollout model</span></span>

<span data-ttu-id="fce1f-116">每月 Defender 更新遵循以下逐步推出模型：</span><span class="sxs-lookup"><span data-stu-id="fce1f-116">The following gradual rollout model is followed for monthly Defender updates:</span></span>

1. <span data-ttu-id="fce1f-117">第一版向 Beta 渠道订阅者发布。</span><span class="sxs-lookup"><span data-stu-id="fce1f-117">The first release goes out to Beta channel subscribers.</span></span>
2. <span data-ttu-id="fce1f-118">在验证、反馈和修复后，我们以限制方式开始逐步推出过程，并首先预览频道订阅者。</span><span class="sxs-lookup"><span data-stu-id="fce1f-118">After validation, feedback, and fixes, we start the gradual rollout process in a throttled way and to Preview channel subscribers first.</span></span>
3. <span data-ttu-id="fce1f-119">然后，我们向全球其余总体发布更新，从 10% 到 100% 向外扩展。</span><span class="sxs-lookup"><span data-stu-id="fce1f-119">We then proceed to release the update to the rest of the global population, scaling out from 10-100%.</span></span>

<span data-ttu-id="fce1f-120">我们的工程师持续监视影响并上报任何问题，以根据需要创建修补程序。</span><span class="sxs-lookup"><span data-stu-id="fce1f-120">Our engineers continuously monitor impact and escalate any issues to create a fix as needed.</span></span>

## <a name="how-to-customize-your-internal-deployment-process"></a><span data-ttu-id="fce1f-121">如何自定义内部部署过程</span><span class="sxs-lookup"><span data-stu-id="fce1f-121">How to customize your internal deployment process</span></span>

<span data-ttu-id="fce1f-122">如果你的计算机从 Windows 更新接收 Defender 更新，逐步推出过程可能会导致你的某些计算机接收 Defender 更新早于其他计算机。</span><span class="sxs-lookup"><span data-stu-id="fce1f-122">If your machines are receiving Defender updates from Windows Update, the gradual rollout process may result in some of your machines receiving Defender updates sooner than others.</span></span> <span data-ttu-id="fce1f-123">以下部分介绍如何定义一种策略，该策略允许自动更新通过利用更新通道配置以不同方式流向特定设备组。</span><span class="sxs-lookup"><span data-stu-id="fce1f-123">The following section explains how to define a strategy that will allow automatic updates to flow differently to specific groups of devices by leveraging update channel configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="fce1f-124">在规划自己的逐步发布时，请确保始终有一些设备订阅到预览频道和分步频道。</span><span class="sxs-lookup"><span data-stu-id="fce1f-124">When planning for your own gradual release, please make sure to always have a selection of devices subscribed to the preview and staged channels.</span></span> <span data-ttu-id="fce1f-125">这将为组织和 Microsoft 提供防止或查找并修复特定于你的环境的问题的机会。</span><span class="sxs-lookup"><span data-stu-id="fce1f-125">This will provide your organization as well as Microsoft the opportunity to prevent or find and fix issues specific to your environment.</span></span>

<span data-ttu-id="fce1f-126">例如，对于通过 WSUS) 或 Microsoft Endpoint Configuration Manager (MECM) 接收更新的计算机，所有 Windows 更新可以使用更多选项，包括适用于终结点的 Microsoft Defender 选项。 Windows Server Update Services (</span><span class="sxs-lookup"><span data-stu-id="fce1f-126">For machines receiving updates through, for example, Windows Server Update Services (WSUS) or Microsoft Endpoint Configuration Manager (MECM), more options are available to all Windows updates, including options  for Microsoft Defender for Endpoint.</span></span>

- <span data-ttu-id="fce1f-127">若要详细了解如何使用 WSUS、MECM 等解决方案管理更新的分发和应用程序，请参阅管理 Microsoft Defender 防病毒 更新和应用基线 - Windows[安全|Microsoft Docs](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates)。</span><span class="sxs-lookup"><span data-stu-id="fce1f-127">Read more about how to use a solution like WSUS, MECM to manage the distribution and application of updates at [Manage Microsoft Defender Antivirus updates and apply baselines - Windows security | Microsoft Docs](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).</span></span>

## <a name="update-channels-for-monthly-updates"></a><span data-ttu-id="fce1f-128">每月更新的更新频道</span><span class="sxs-lookup"><span data-stu-id="fce1f-128">Update channels for monthly updates</span></span>

<span data-ttu-id="fce1f-129">你可以将计算机分配给更新频道，以定义计算机接收每月引擎和平台更新的节奏。</span><span class="sxs-lookup"><span data-stu-id="fce1f-129">You can assign a machine to an update channel to define the cadence in which a machine receives monthly engine and platform updates.</span></span>

<span data-ttu-id="fce1f-130">若要详细了解如何配置更新，请参阅为 Microsoft Defender 更新创建自定义 [逐步推出过程](configure-updates.md)。</span><span class="sxs-lookup"><span data-stu-id="fce1f-130">For more information on how to configure updates, see [Create a custom gradual rollout process for Microsoft Defender updates](configure-updates.md).</span></span>

<span data-ttu-id="fce1f-131">以下更新频道可用：</span><span class="sxs-lookup"><span data-stu-id="fce1f-131">The following update channels are available:</span></span>

| <span data-ttu-id="fce1f-132">频道名称</span><span class="sxs-lookup"><span data-stu-id="fce1f-132">Channel name</span></span>  | <span data-ttu-id="fce1f-133">说明</span><span class="sxs-lookup"><span data-stu-id="fce1f-133">Description</span></span>  | <span data-ttu-id="fce1f-134">应用程序</span><span class="sxs-lookup"><span data-stu-id="fce1f-134">Application</span></span>  |
|-|-|-|
| <span data-ttu-id="fce1f-135">Beta 渠道 - 预发布</span><span class="sxs-lookup"><span data-stu-id="fce1f-135">Beta Channel - Prerelease</span></span>  | <span data-ttu-id="fce1f-136">在其他人之前测试更新</span><span class="sxs-lookup"><span data-stu-id="fce1f-136">Test updates before others</span></span>  | <span data-ttu-id="fce1f-137">设置为此频道的设备将是第一个接收新每月更新的设备。</span><span class="sxs-lookup"><span data-stu-id="fce1f-137">Devices set to this channel will be the first to receive new monthly updates.</span></span> <span data-ttu-id="fce1f-138">选择 Beta 渠道以参与识别问题并报告给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="fce1f-138">Select Beta Channel to participate in identifying and reporting issues to Microsoft.</span></span> <span data-ttu-id="fce1f-139">默认情况下，Windows预览体验计划中的设备订阅到此频道。</span><span class="sxs-lookup"><span data-stu-id="fce1f-139">Devices in the Windows Insider Program are subscribed to this channel by default.</span></span> <span data-ttu-id="fce1f-140">仅在测试环境中使用。</span><span class="sxs-lookup"><span data-stu-id="fce1f-140">For use in test environments only.</span></span>  |
| <span data-ttu-id="fce1f-141">当前频道（预览）</span><span class="sxs-lookup"><span data-stu-id="fce1f-141">Current Channel (Preview)</span></span>  | <span data-ttu-id="fce1f-142">在逐步发布 **期间提前获取** 当前频道更新</span><span class="sxs-lookup"><span data-stu-id="fce1f-142">Get Current Channel updates **earlier** during gradual release</span></span>  | <span data-ttu-id="fce1f-143">在逐步发布周期中，将最早向设置为此频道的设备提供更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-143">Devices set to this channel will be offered updates earliest during the gradual release cycle.</span></span> <span data-ttu-id="fce1f-144">建议用于预生产/验证环境。</span><span class="sxs-lookup"><span data-stu-id="fce1f-144">Suggested for pre-production/validation environments.</span></span>  |
| <span data-ttu-id="fce1f-145">当前频道 (分步) </span><span class="sxs-lookup"><span data-stu-id="fce1f-145">Current Channel (Staged)</span></span>  | <span data-ttu-id="fce1f-146">在逐步发布期间获取当前频道更新</span><span class="sxs-lookup"><span data-stu-id="fce1f-146">Get Current Channel updates later during gradual release</span></span>  | <span data-ttu-id="fce1f-147">设备将在逐步发布周期的稍后阶段提供更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-147">Devices will be offered updates later during the gradual release cycle.</span></span> <span data-ttu-id="fce1f-148">建议应用于设备总体中具有代表性的较小部分 (大约 10%) 。</span><span class="sxs-lookup"><span data-stu-id="fce1f-148">Suggested to apply to a small, representative part of your device population (~10%).</span></span>  |
| <span data-ttu-id="fce1f-149">Current Channel (Broad) </span><span class="sxs-lookup"><span data-stu-id="fce1f-149">Current Channel (Broad)</span></span> | <span data-ttu-id="fce1f-150">在逐步发布结束时获取更新</span><span class="sxs-lookup"><span data-stu-id="fce1f-150">Get updates at the end of gradual release</span></span>  | <span data-ttu-id="fce1f-151">仅在逐步发布周期完成后，才向设备提供更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-151">Devices will be offered updates only after the gradual release cycle completes.</span></span> <span data-ttu-id="fce1f-152">建议应用于生产总体中的一组广泛的设备 (大约 10-100%) 。</span><span class="sxs-lookup"><span data-stu-id="fce1f-152">Suggested to apply to a broad set of devices in your production population (~10-100%).</span></span>  |
| <span data-ttu-id="fce1f-153"> (默认) </span><span class="sxs-lookup"><span data-stu-id="fce1f-153">(default)</span></span>  |   | <span data-ttu-id="fce1f-154">如果禁用或不配置此策略，设备将保留在当前频道 (默认) ：在逐步发布周期内自动保持最新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-154">If you disable or do not configure this policy, the device will remain in Current Channel (Default): Stay up to date automatically during the gradual release cycle.</span></span> <span data-ttu-id="fce1f-155">适用于大多数设备。</span><span class="sxs-lookup"><span data-stu-id="fce1f-155">Suitable for most devices.</span></span>  |

### <a name="update-channels-for-daily-definition-updates"></a><span data-ttu-id="fce1f-156">更新每日定义更新的频道</span><span class="sxs-lookup"><span data-stu-id="fce1f-156">Update channels for daily definition updates</span></span>

<span data-ttu-id="fce1f-157">还可以将计算机分配给频道，以定义接收每日定义更新的节奏。</span><span class="sxs-lookup"><span data-stu-id="fce1f-157">You can also assign a machine to a channel to define the cadence in which it receives daily definition updates.</span></span> <span data-ttu-id="fce1f-158">请注意，与每月进程不同，没有 Beta 渠道，并且此逐步发布周期每天发生多次。</span><span class="sxs-lookup"><span data-stu-id="fce1f-158">Note that unlike the monthly process, there is no Beta channel and this gradual release cycle occurs multiple times a day.</span></span>
  
| <span data-ttu-id="fce1f-159">频道名称</span><span class="sxs-lookup"><span data-stu-id="fce1f-159">Channel name</span></span>  | <span data-ttu-id="fce1f-160">说明</span><span class="sxs-lookup"><span data-stu-id="fce1f-160">Description</span></span>  | <span data-ttu-id="fce1f-161">应用程序</span><span class="sxs-lookup"><span data-stu-id="fce1f-161">Application</span></span>  |
|-|-|-|
| <span data-ttu-id="fce1f-162">当前频道 (分步) </span><span class="sxs-lookup"><span data-stu-id="fce1f-162">Current Channel (Staged)</span></span>  | <span data-ttu-id="fce1f-163">在逐步发布期间获取当前频道更新</span><span class="sxs-lookup"><span data-stu-id="fce1f-163">Get Current Channel updates later during gradual release</span></span>  | <span data-ttu-id="fce1f-164">设备将在逐步发布周期的稍后阶段提供更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-164">Devices will be offered updates later during the gradual release cycle.</span></span> <span data-ttu-id="fce1f-165">建议应用于设备总体中具有代表性的较小部分 (大约 10%) 。</span><span class="sxs-lookup"><span data-stu-id="fce1f-165">Suggested to apply to a small, representative part of your device population (~10%).</span></span>  |
| <span data-ttu-id="fce1f-166">Current Channel (Broad) </span><span class="sxs-lookup"><span data-stu-id="fce1f-166">Current Channel (Broad)</span></span> | <span data-ttu-id="fce1f-167">在逐步发布结束时获取更新</span><span class="sxs-lookup"><span data-stu-id="fce1f-167">Get updates at the end of gradual release</span></span>  | <span data-ttu-id="fce1f-168">设备将在逐步发布周期后提供更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-168">Devices will be offered updates after the gradual release cycle.</span></span> <span data-ttu-id="fce1f-169">最适合仅接收有限更新的数据中心计算机。</span><span class="sxs-lookup"><span data-stu-id="fce1f-169">Best for datacenter machines that only receive limited updates.</span></span> <span data-ttu-id="fce1f-170">注意：此设置适用于所有 Defender 更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-170">Note: this setting applies to all Defender updates.</span></span>  |
| <span data-ttu-id="fce1f-171"> (默认) </span><span class="sxs-lookup"><span data-stu-id="fce1f-171">(default)</span></span>  |   | <span data-ttu-id="fce1f-172">如果禁用或不配置此策略，设备将保留在当前频道 (默认) ：在逐步发布周期内自动保持最新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-172">If you disable or do not configure this policy, the device will remain in Current Channel (Default): Stay up to date automatically during the gradual release cycle.</span></span> <span data-ttu-id="fce1f-173">适用于大多数设备</span><span class="sxs-lookup"><span data-stu-id="fce1f-173">Suitable for most devices</span></span>  |

> [!NOTE]
> <span data-ttu-id="fce1f-174">如果你希望强制更新最新的签名，而不是利用时间延迟，你将需要首先删除此策略。</span><span class="sxs-lookup"><span data-stu-id="fce1f-174">In case you wish to force an update to the newest signature instead of leveraging the time delay, you will need to remove this policy first.</span></span>

## <a name="update-guidance"></a><span data-ttu-id="fce1f-175">更新指南</span><span class="sxs-lookup"><span data-stu-id="fce1f-175">Update guidance</span></span>

<span data-ttu-id="fce1f-176">在大多数情况下，使用 Windows 更新时的建议配置是允许终结点在到达时接收和应用每月 Defender 更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-176">In most cases, the recommended configuration when using Windows Update is to allow endpoints to receive and apply monthly Defender updates as they arrive.</span></span> <span data-ttu-id="fce1f-177">这可在保护与与它们可以引入的更改相关联的可能影响之间提供最佳平衡。</span><span class="sxs-lookup"><span data-stu-id="fce1f-177">This provides the best balance between protection and possible impact associated with the changes they can introduce.</span></span>

<span data-ttu-id="fce1f-178">对于需要更受控逐步推出自动 Defender 更新的环境，请考虑使用部署组的方法：</span><span class="sxs-lookup"><span data-stu-id="fce1f-178">For environments where there is a need for a more controlled gradual rollout of automatic Defender updates, consider an approach with deployment groups:</span></span>

1. <span data-ttu-id="fce1f-179">参加 Windows预览体验计划，或将一组设备分配到 Beta 渠道。</span><span class="sxs-lookup"><span data-stu-id="fce1f-179">Participate in the Windows Insider program or assign a group of devices to the Beta Channel.</span></span>
2. <span data-ttu-id="fce1f-180">指定选择加入预览频道（通常是验证环境）的试点组，以尽早接收新更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-180">Designate a pilot group that opts-in to Preview Channel, typically validation environments, to receive new updates early.</span></span>
3. <span data-ttu-id="fce1f-181">指定一组计算机，这些计算机稍后在逐步推出期间从 Staged 频道接收更新。</span><span class="sxs-lookup"><span data-stu-id="fce1f-181">Designate a group of machines that receive updates later during the gradual rollout from Staged channel.</span></span> <span data-ttu-id="fce1f-182">通常，这代表大约占总体的 10%。</span><span class="sxs-lookup"><span data-stu-id="fce1f-182">Typically, this would be a representative ~10% of the population.</span></span>
4. <span data-ttu-id="fce1f-183">指定一组在逐步发布周期完成后接收更新的计算机。</span><span class="sxs-lookup"><span data-stu-id="fce1f-183">Designate a group of machines that receive updates after the gradual release cycle completes.</span></span> <span data-ttu-id="fce1f-184">这些通常是重要的生产系统。</span><span class="sxs-lookup"><span data-stu-id="fce1f-184">These are typically important production systems.</span></span>

<span data-ttu-id="fce1f-185">对于其余设备，默认设置是在 Microsoft 逐步推出过程中收到新更新，无需进一步配置。</span><span class="sxs-lookup"><span data-stu-id="fce1f-185">For the remainder of devices, the default setting is to receive new updates as they arrive during the Microsoft gradual rollout process and no further configuration is required.</span></span> 

<span data-ttu-id="fce1f-186">采用此模型：</span><span class="sxs-lookup"><span data-stu-id="fce1f-186">Adopting this model:</span></span>
- <span data-ttu-id="fce1f-187">允许你在早期版本到达生产环境之前测试它们</span><span class="sxs-lookup"><span data-stu-id="fce1f-187">Allows you to test early releases before they reach a production environment</span></span> 
- <span data-ttu-id="fce1f-188">确保生产环境仍收到定期更新，并确保防范关键威胁。</span><span class="sxs-lookup"><span data-stu-id="fce1f-188">Ensure the production environment still receives regular updates and ensure protection against critical threats.</span></span>

## <a name="management-tools"></a><span data-ttu-id="fce1f-189">管理工具</span><span class="sxs-lookup"><span data-stu-id="fce1f-189">Management tools</span></span>
<span data-ttu-id="fce1f-190">若要为每月更新创建自己的自定义逐步推出过程，可以使用以下工具：</span><span class="sxs-lookup"><span data-stu-id="fce1f-190">To create your own custom gradual rollout process for monthly updates, you can use the following tools:</span></span>

- <span data-ttu-id="fce1f-191">组策略</span><span class="sxs-lookup"><span data-stu-id="fce1f-191">Group policy</span></span>
- <span data-ttu-id="fce1f-192">Microsoft Endpoint Manager</span><span class="sxs-lookup"><span data-stu-id="fce1f-192">Microsoft Endpoint Manager</span></span>
- <span data-ttu-id="fce1f-193">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fce1f-193">PowerShell</span></span>

<span data-ttu-id="fce1f-194">有关如何使用这些工具的详细信息，请参阅为 Microsoft [Defender 更新创建自定义逐步推出过程](configure-updates.md)。</span><span class="sxs-lookup"><span data-stu-id="fce1f-194">For details on how to use these tools, see [Create a custom gradual rollout process for Microsoft Defender updates](configure-updates.md).</span></span>