---
title: 攻击模拟培训部署注意事项和常见问题解答
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: 管理员可以了解有关 Microsoft 365 E5 或 Microsoft Defender for Office 365 计划 2 组织中攻击模拟和培训的部署注意事项和常见问题。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b57252252d8a22ade4b8e1a18f42d7fdce91324e
ms.sourcegitcommit: 375168ee66be862cf3b00f2733c7be02e63408cf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "50454710"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a><span data-ttu-id="59458-103">攻击模拟培训部署注意事项和常见问题解答</span><span class="sxs-lookup"><span data-stu-id="59458-103">Attack simulation training deployment considerations and FAQ</span></span>

<span data-ttu-id="59458-104">攻击模拟培训现已 [普遍提供](https://techcommunity.microsoft.com/t5/microsoft-security-and/attack-simulation-training-in-microsoft-defender-for-office-365/ba-p/2037291)。</span><span class="sxs-lookup"><span data-stu-id="59458-104">Attack simulation training is now [generally available](https://techcommunity.microsoft.com/t5/microsoft-security-and/attack-simulation-training-in-microsoft-defender-for-office-365/ba-p/2037291).</span></span> <span data-ttu-id="59458-105">利用攻击模拟培训，Microsoft 365 E5 或 Microsoft Defender for Office 365 计划 2 组织可以度量和管理社会工程风险，方法为允许创建和管理由实际、已取消武器化网络钓鱼有效负载的网络钓鱼模拟。</span><span class="sxs-lookup"><span data-stu-id="59458-105">Attack simulation training enables Microsoft 365 E5 or Microsoft Defender for Office 365 Plan 2 organizations to measure and manage social engineering risk by allowing the creation and management of phishing simulations that are powered by real-world, de-weaponized phishing payloads.</span></span> <span data-ttu-id="59458-106">与 Terranova 安全性合作提供的超目标培训可帮助提高知识并改变员工行为。</span><span class="sxs-lookup"><span data-stu-id="59458-106">Hyper-targeted training, delivered in partnership with Terranova security, helps improve knowledge and change employee behavior.</span></span>

<span data-ttu-id="59458-107">有关攻击模拟培训入门的信息，请参阅使用攻击模拟 [培训入门](attack-simulation-training-get-started.md)。</span><span class="sxs-lookup"><span data-stu-id="59458-107">For more information about getting started with Attack simulation training, see [Get started using Attack simulation training](attack-simulation-training-get-started.md).</span></span>

<span data-ttu-id="59458-108">尽管整个模拟创建和计划体验设计为可自由流动且无冲突，但企业规模运行模拟通常需要规划。</span><span class="sxs-lookup"><span data-stu-id="59458-108">While the whole simulation creation and scheduling experience has been designed to be free-flowing and frictionless, running simulations at an enterprise scale often requires planning.</span></span> <span data-ttu-id="59458-109">本文有助于解决客户在其自己的环境中运行模拟时所看到的特定挑战。</span><span class="sxs-lookup"><span data-stu-id="59458-109">This article helps address specific challenges that we see as our customers run simulations in their own environments.</span></span>

## <a name="issues-with-end-user-experiences"></a><span data-ttu-id="59458-110">最终用户体验问题</span><span class="sxs-lookup"><span data-stu-id="59458-110">Issues with end user experiences</span></span>

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a><span data-ttu-id="59458-111">Google 安全浏览阻止的网络钓鱼模拟 URL</span><span class="sxs-lookup"><span data-stu-id="59458-111">Phishing simulation URLs blocked by Google Safe Browsing</span></span>

<span data-ttu-id="59458-112">URL 信誉服务可能会将攻击模拟培训使用的一个或多个 URL 标识为不安全。</span><span class="sxs-lookup"><span data-stu-id="59458-112">A URL reputation service might identify one or more of the URLs that are used by Attack simulation training as unsafe.</span></span> <span data-ttu-id="59458-113">Google Chrome 中的 Google 安全浏览会阻止某些带有欺骗性网站提前 **消息的** 模拟网络钓鱼 URL。</span><span class="sxs-lookup"><span data-stu-id="59458-113">Google Safe Browsing in Google Chrome blocks some of the simulated phishing URLs with a **Deceptive site ahead** message.</span></span> <span data-ttu-id="59458-114">虽然我们与许多 URL 信誉供应商合作，始终允许我们的模拟 URL，但我们并不总是具有完全覆盖。</span><span class="sxs-lookup"><span data-stu-id="59458-114">While we work with many URL reputation vendors to always allow our simulation URLs, we don't always have full coverage.</span></span>

![Google Chrome 中的欺骗性网站提前警告](../../media/attack-sim-chrome-deceptive-site-message.png)

<span data-ttu-id="59458-116">请注意，此问题不会影响 Microsoft Edge。</span><span class="sxs-lookup"><span data-stu-id="59458-116">Note that this issue does not affect Microsoft Edge.</span></span>

<span data-ttu-id="59458-117">作为规划阶段的一部分，请务必在网络钓鱼活动中使用 URL 之前检查受支持的 Web 浏览器中 URL 的可用性。</span><span class="sxs-lookup"><span data-stu-id="59458-117">As part of the planning phase, be sure to check the availability of the URL in your supported web browsers before you use the URL in a phishing campaign.</span></span> <span data-ttu-id="59458-118">如果 Google 安全浏览阻止 URL，请按照[](https://support.google.com/chrome/a/answer/7532419)Google 的本指南操作，以允许访问 URL。</span><span class="sxs-lookup"><span data-stu-id="59458-118">If the URLs are blocked by Google Safe Browsing, [follow this guidance](https://support.google.com/chrome/a/answer/7532419) from Google to allow access to the URLs.</span></span>

<span data-ttu-id="59458-119">有关 [攻击模拟培训当前](attack-simulation-training-get-started.md) 使用的 URL 列表，请参阅使用攻击模拟培训入门。</span><span class="sxs-lookup"><span data-stu-id="59458-119">Refer to [Get started using Attack simulation training](attack-simulation-training-get-started.md) for the list of URLs that are currently used by Attack simulation training.</span></span>

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a><span data-ttu-id="59458-120">网络代理解决方案和筛选器驱动程序阻止的网络钓鱼模拟和管理 URL</span><span class="sxs-lookup"><span data-stu-id="59458-120">Phishing simulation and admin URLs blocked by network proxy solutions and filter drivers</span></span>

<span data-ttu-id="59458-121">中间安全设备或筛选器可能会阻止或删除网络钓鱼模拟 URL 和管理 URL。</span><span class="sxs-lookup"><span data-stu-id="59458-121">Both phishing simulation URLs and admin URLs might be blocked or dropped by your intermediate security devices or filters.</span></span> <span data-ttu-id="59458-122">例如：</span><span class="sxs-lookup"><span data-stu-id="59458-122">For example:</span></span>

- <span data-ttu-id="59458-123">防火墙</span><span class="sxs-lookup"><span data-stu-id="59458-123">Firewalls</span></span>
- <span data-ttu-id="59458-124">Web 应用程序防火墙 (WAF) 解决方案</span><span class="sxs-lookup"><span data-stu-id="59458-124">Web Application Firewall (WAF) solutions</span></span>
- <span data-ttu-id="59458-125">例如，第三方筛选器 (例如，内核模式筛选器) </span><span class="sxs-lookup"><span data-stu-id="59458-125">Third-party filter drivers (for example, kernel mode filters)</span></span>

<span data-ttu-id="59458-126">尽管我们在此层中发现很少客户被阻止，但确实会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="59458-126">While we have seen few customers being blocked at this layer, it does happen.</span></span> <span data-ttu-id="59458-127">如果遇到问题，请考虑将以下 URL 配置为绕过安全设备或筛选器的扫描（如果需要）：</span><span class="sxs-lookup"><span data-stu-id="59458-127">If you encounter problems, consider configuring the following URLs to bypass scanning by your security devices or filters as required:</span></span>

- <span data-ttu-id="59458-128">使用攻击模拟培训入门中所述的模拟网络钓鱼[URL。](attack-simulation-training-get-started.md)</span><span class="sxs-lookup"><span data-stu-id="59458-128">The simulated phishing URLs as described in [Get started using Attack simulation training](attack-simulation-training-get-started.md).</span></span>
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a><span data-ttu-id="59458-129">未向所有目标用户传递模拟消息</span><span class="sxs-lookup"><span data-stu-id="59458-129">Simulation messages not delivered to all targeted users</span></span>

<span data-ttu-id="59458-130">实际接收模拟电子邮件的用户数可能小于模拟的目标用户数。</span><span class="sxs-lookup"><span data-stu-id="59458-130">It's possible that the number of users who actually receive the simulation email messages is less than the number of users who were targeted by the simulation.</span></span> <span data-ttu-id="59458-131">作为目标验证的一部分，将排除以下类型的用户：</span><span class="sxs-lookup"><span data-stu-id="59458-131">The following types of users will be excluded as part of target validation:</span></span>

- <span data-ttu-id="59458-132">收件人电子邮件地址无效。</span><span class="sxs-lookup"><span data-stu-id="59458-132">Invalid recipient email addresses.</span></span>
- <span data-ttu-id="59458-133">来宾用户。</span><span class="sxs-lookup"><span data-stu-id="59458-133">Guest users.</span></span>
- <span data-ttu-id="59458-134">在 Azure Active Directory 中不再处于活动状态的用户 (Azure AD) 。</span><span class="sxs-lookup"><span data-stu-id="59458-134">Users that are no longer active in Azure Active Directory (Azure AD).</span></span>

<span data-ttu-id="59458-135">只有具有有效邮箱的有效非来宾用户才能包含在模拟中。</span><span class="sxs-lookup"><span data-stu-id="59458-135">Only valid, non-guest users with a valid mailbox will be included in simulations.</span></span> <span data-ttu-id="59458-136">如果使用通讯组或启用邮件的安全组作为目标用户，可以使用[Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)中的[Get-DistributionGroupMember](https://docs.microsoft.com/powershell/module/exchange/get-distributiongroupmember) cmdlet 查看和验证通讯组成员。</span><span class="sxs-lookup"><span data-stu-id="59458-136">If you use distribution groups or mail-enabled security groups to target users, you can use the [Get-DistributionGroupMember](https://docs.microsoft.com/powershell/module/exchange/get-distributiongroupmember) cmdlet in [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) to view and validate distribution group members.</span></span>

## <a name="issues-with-attack-simulation-training-reporting"></a><span data-ttu-id="59458-137">攻击模拟培训报告问题</span><span class="sxs-lookup"><span data-stu-id="59458-137">Issues with Attack simulation training reporting</span></span>

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a><span data-ttu-id="59458-138">攻击模拟培训报告不包含任何活动详细信息</span><span class="sxs-lookup"><span data-stu-id="59458-138">Attack simulation training reports do not contain any activity details</span></span>

<span data-ttu-id="59458-139">攻击模拟培训附带丰富的可操作见解，可让你了解员工的威胁准备进度。</span><span class="sxs-lookup"><span data-stu-id="59458-139">Attack simulation training comes with rich, actionable insights that keep you informed of the threat readiness progress of your employees.</span></span> <span data-ttu-id="59458-140">如果攻击模拟培训报告未填充数据，请验证审核日志搜索是否在你的组织中打开 (默认情况下是否) 。</span><span class="sxs-lookup"><span data-stu-id="59458-140">If Attack simulation training reports are not populated with data, verify that audit log search is turned on in your organization (it's on by default).</span></span>

<span data-ttu-id="59458-141">攻击模拟培训需要审核日志搜索，以便可以捕获、记录和重新读取事件。</span><span class="sxs-lookup"><span data-stu-id="59458-141">Audit log search is required by Attack simulation training so events can be captured, recorded, and read back.</span></span> <span data-ttu-id="59458-142">关闭审核日志搜索对攻击模拟培训产生以下后果：</span><span class="sxs-lookup"><span data-stu-id="59458-142">Turning off audit log search has the following consequences for Attack simulation training:</span></span>

- <span data-ttu-id="59458-143">报告数据并非在所有报告中都可用。</span><span class="sxs-lookup"><span data-stu-id="59458-143">Reporting data is not available across all reports.</span></span> <span data-ttu-id="59458-144">报告将显示为空。</span><span class="sxs-lookup"><span data-stu-id="59458-144">The reports will appear empty.</span></span>
- <span data-ttu-id="59458-145">由于数据不可用，因此将阻止培训工作分配。</span><span class="sxs-lookup"><span data-stu-id="59458-145">Training assignments are blocked, because data is not available.</span></span>

<span data-ttu-id="59458-146">若要打开审核日志，请参阅打开 [审核日志或关闭搜索](../../compliance/turn-audit-log-search-on-or-off.md)。</span><span class="sxs-lookup"><span data-stu-id="59458-146">To turn on audit log search, see [Turn audit log search on or off](../../compliance/turn-audit-log-search-on-or-off.md).</span></span>

> [!NOTE]
> <span data-ttu-id="59458-147">空活动详细信息也可能由未分配给用户的 E5 许可证导致。</span><span class="sxs-lookup"><span data-stu-id="59458-147">Empty activity details can also be caused by no E5 licenses being assigned to users.</span></span> <span data-ttu-id="59458-148">确认至少向活动用户分配了一个 E5 许可证，以确保捕获和记录报告事件。</span><span class="sxs-lookup"><span data-stu-id="59458-148">Verify at least one E5 license is assigned to an active user to ensure that reporting events are captured and recorded.</span></span>

### <a name="simulation-reports-are-not-updated-immediately"></a><span data-ttu-id="59458-149">模拟报告不会立即更新</span><span class="sxs-lookup"><span data-stu-id="59458-149">Simulation reports are not updated immediately</span></span>

<span data-ttu-id="59458-150">详细的模拟报告不会在启动市场活动后立即更新。</span><span class="sxs-lookup"><span data-stu-id="59458-150">Detailed simulation reports are not updated immediately after you launch a campaign.</span></span> <span data-ttu-id="59458-151">不要担心;此行为是预期行为。</span><span class="sxs-lookup"><span data-stu-id="59458-151">Don't worry; this behavior is expected.</span></span>

<span data-ttu-id="59458-152">每个模拟活动都有一个生命周期。</span><span class="sxs-lookup"><span data-stu-id="59458-152">Every simulation campaign has a lifecycle.</span></span> <span data-ttu-id="59458-153">首次创建模拟时，模拟将 **位于计划** 状态。</span><span class="sxs-lookup"><span data-stu-id="59458-153">When first created, the simulation is in the **Scheduled** state.</span></span> <span data-ttu-id="59458-154">模拟开始时，它将转换为 **正在进行状态。**</span><span class="sxs-lookup"><span data-stu-id="59458-154">When the simulation starts, it transitions to the **In progress** state.</span></span> <span data-ttu-id="59458-155">完成后，模拟将转换为"已完成 **"** 状态。</span><span class="sxs-lookup"><span data-stu-id="59458-155">When completed, the simulation transitions to the **Completed** state.</span></span>

<span data-ttu-id="59458-156">当模拟状态为 **计划** 时，模拟报告将大部分为空。</span><span class="sxs-lookup"><span data-stu-id="59458-156">While a simulation is in the **Scheduled** state, the simulation reports will be mostly empty.</span></span> <span data-ttu-id="59458-157">在此阶段，模拟引擎将解析目标用户电子邮件地址、展开通讯组、从列表中删除来宾用户等：</span><span class="sxs-lookup"><span data-stu-id="59458-157">During this stage, the simulation engine is resolving the target user email addresses, expanding distribution groups, removing guest users from the list, etc.:</span></span>

![计划状态中的报告](../../media/attack-sim-empty-reporting.png)

<span data-ttu-id="59458-159">模拟进入进行阶段后，你将注意到开始进入报告的信息：</span><span class="sxs-lookup"><span data-stu-id="59458-159">Once the simulation enters the **In progress** stage, you will notice information starting to trickle into the reporting:</span></span>

![正在报告状态](../../media/attack-sim-in-progress.png)

<span data-ttu-id="59458-161">转换到"正在进行"状态后，可能需要 30 分钟才能更新各个 **模拟报告。**</span><span class="sxs-lookup"><span data-stu-id="59458-161">It can take up to 30 minutes for the individual simulation reports to update after the transition to the **In progress** state.</span></span> <span data-ttu-id="59458-162">报告数据将继续生成，直到模拟达到 **"已完成** "状态。</span><span class="sxs-lookup"><span data-stu-id="59458-162">The report data continues to build until the simulation reaches the **Completed** state.</span></span> <span data-ttu-id="59458-163">报告更新以以下间隔发生：</span><span class="sxs-lookup"><span data-stu-id="59458-163">Reporting updates occur at the following intervals:</span></span>

- <span data-ttu-id="59458-164">前 60 分钟每 10 分钟一次。</span><span class="sxs-lookup"><span data-stu-id="59458-164">Every 10 minutes for the first 60 minutes.</span></span>
- <span data-ttu-id="59458-165">60 分钟后每 15 分钟一次，直到 2 天。</span><span class="sxs-lookup"><span data-stu-id="59458-165">Every 15 minutes after 60 minutes until 2 days.</span></span>
- <span data-ttu-id="59458-166">2 天到 7 天后每 30 分钟一次。</span><span class="sxs-lookup"><span data-stu-id="59458-166">Every 30 minutes after 2 days until 7 days.</span></span>
- <span data-ttu-id="59458-167">7 天后每 60 分钟一次。</span><span class="sxs-lookup"><span data-stu-id="59458-167">Every 60 minutes after 7 days.</span></span>

<span data-ttu-id="59458-168">"概述 **"页上** 的小部件提供了组织基于模拟的安全状态在一段时间的快速快照。</span><span class="sxs-lookup"><span data-stu-id="59458-168">Widgets on the **Overview** page provide a quick snapshot of your organization's simulation-based security posture over time.</span></span> <span data-ttu-id="59458-169">由于这些小组件反映了整体安全状况和随着时间的过去，因此在每个模拟活动完成后会更新它们。</span><span class="sxs-lookup"><span data-stu-id="59458-169">Because these widgets reflect your overall security posture and journey over time, they're updated after each simulation campaign is completed.</span></span>

> [!NOTE]
> <span data-ttu-id="59458-170">您可以在 **各种报告页面上** 使用"导出"选项来提取数据。</span><span class="sxs-lookup"><span data-stu-id="59458-170">You can use the **Export** option on the various reporting pages to extract data.</span></span>

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a><span data-ttu-id="59458-171">用户报告为网络钓鱼的邮件不会显示在模拟报告中</span><span class="sxs-lookup"><span data-stu-id="59458-171">Messages reported as phishing by users aren't appearing in simulation reports</span></span>

<span data-ttu-id="59458-172">攻击模拟器培训中的模拟报告提供有关用户活动的详细信息。</span><span class="sxs-lookup"><span data-stu-id="59458-172">Simulation reports in Attack simulator training provide details on user activity.</span></span> <span data-ttu-id="59458-173">例如：</span><span class="sxs-lookup"><span data-stu-id="59458-173">For example:</span></span>

- <span data-ttu-id="59458-174">单击邮件中链接的用户。</span><span class="sxs-lookup"><span data-stu-id="59458-174">Users who clicked on the link in the message.</span></span>
- <span data-ttu-id="59458-175">放弃其凭据的用户。</span><span class="sxs-lookup"><span data-stu-id="59458-175">Users who gave up their credentials.</span></span>
- <span data-ttu-id="59458-176">将邮件报告为网络钓鱼的用户。</span><span class="sxs-lookup"><span data-stu-id="59458-176">Users who reported the message as phishing.</span></span>

<span data-ttu-id="59458-177">如果用户报告为网络钓鱼的邮件未在攻击模拟培训模拟报告中捕获，则可能有 Exchange 邮件流规则 (也称为传输规则) ，该规则阻止将报告的邮件送达 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="59458-177">If messages that users reported as phishing aren't captured in Attack simulation training simulation reports, there might be an Exchange mail flow rule (also known as a transport rule) that's blocking the delivery of the reported messages to Microsoft.</span></span> <span data-ttu-id="59458-178">验证任何邮件流规则是否未阻止发送到以下电子邮件地址：</span><span class="sxs-lookup"><span data-stu-id="59458-178">Verify that any mail flow rules aren't blocking delivery to the following email addresses:</span></span>

- <span data-ttu-id="59458-179">junk@office365.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="59458-179">junk@office365.microsoft.com</span></span>
- <span data-ttu-id="59458-180">abuse@messaging.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="59458-180">abuse@messaging.microsoft.com</span></span>
- <span data-ttu-id="59458-181">phish@office365.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="59458-181">phish@office365.microsoft.com</span></span>
- <span data-ttu-id="59458-182">不可 \_ junk@office365.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="59458-182">not\_junk@office365.microsoft.com</span></span>

## <a name="other-frequently-asked-questions"></a><span data-ttu-id="59458-183">其他常见问题</span><span class="sxs-lookup"><span data-stu-id="59458-183">Other frequently asked questions</span></span>

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a><span data-ttu-id="59458-184">问：针对模拟市场活动的目标用户的建议方法是什么？</span><span class="sxs-lookup"><span data-stu-id="59458-184">Q: What is the recommended method to target users for simulation campaigns?</span></span>

<span data-ttu-id="59458-185">答：目标用户可以使用多个选项：</span><span class="sxs-lookup"><span data-stu-id="59458-185">A: Several options are available to target users:</span></span>

- <span data-ttu-id="59458-186">包括当前 (用户数少于 40，000 的组织可用的所有用户) 。</span><span class="sxs-lookup"><span data-stu-id="59458-186">Include all users (currently available to organizations with less than 40,000 users).</span></span>
- <span data-ttu-id="59458-187">选择特定用户。</span><span class="sxs-lookup"><span data-stu-id="59458-187">Choose specific users.</span></span>
- <span data-ttu-id="59458-188">从 CSV 文件选择用户。</span><span class="sxs-lookup"><span data-stu-id="59458-188">Select users from a CSV file.</span></span>
- <span data-ttu-id="59458-189">基于 Azure AD 组的目标。</span><span class="sxs-lookup"><span data-stu-id="59458-189">Azure AD group-based targeting.</span></span>

<span data-ttu-id="59458-190">我们发现，目标用户由 Azure AD 组标识的市场活动通常更易于管理。</span><span class="sxs-lookup"><span data-stu-id="59458-190">We've found that campaigns where the targeted users are identified by Azure AD groups are generally easier to manage.</span></span>

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a><span data-ttu-id="59458-191">问：从 CSV 导入或添加用户时，目标用户是否有限制？</span><span class="sxs-lookup"><span data-stu-id="59458-191">Q: Are there any limits in targeting users while importing from a CSV or adding users?</span></span>

<span data-ttu-id="59458-192">答：从 CSV 文件导入收件人或向模拟添加单个收件人的限制为 40，000。</span><span class="sxs-lookup"><span data-stu-id="59458-192">A: The limit for importing recipients from a CSV file or adding individual recipients to a simulation is 40,000.</span></span>

<span data-ttu-id="59458-193">收件人可以是单个用户或组。</span><span class="sxs-lookup"><span data-stu-id="59458-193">A recipient can be an individual user or a group.</span></span> <span data-ttu-id="59458-194">一个组可能包含数百或数千个收件人，因此不会对单个用户的数量设置实际限制。</span><span class="sxs-lookup"><span data-stu-id="59458-194">A group might contain hundreds or thousands of recipients, so an actual limit isn't placed on the number of individual users.</span></span>

<span data-ttu-id="59458-195">管理大型 CSV 文件或添加多个单个收件人可能很麻烦。</span><span class="sxs-lookup"><span data-stu-id="59458-195">Managing a large CSV file or adding many individual recipients can be cumbersome.</span></span> <span data-ttu-id="59458-196">使用 Azure AD 组将简化模拟的总体管理。</span><span class="sxs-lookup"><span data-stu-id="59458-196">Using Azure AD groups will simplify the overall management of the simulation.</span></span>

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a><span data-ttu-id="59458-197">问：Microsoft 是否提供其他语言的负载？</span><span class="sxs-lookup"><span data-stu-id="59458-197">Q: Does Microsoft provide payloads in other languages?</span></span>

<span data-ttu-id="59458-198">答：目前，有 5 个可用的本地化有效负载。</span><span class="sxs-lookup"><span data-stu-id="59458-198">A: Currently, there are 5 localized payloads available.</span></span> <span data-ttu-id="59458-199">我们已注意到，现有有效负载到其他语言的任何直接或机器翻译都会导致不准确和相关性降低。</span><span class="sxs-lookup"><span data-stu-id="59458-199">We've noticed than any direct or machine translations of existing payloads to other languages will lead to inaccuracies and decreased relevance.</span></span>

<span data-ttu-id="59458-200">也就是说，可以使用自定义有效负载创作体验，以你选择的语言创建自己的有效负载。</span><span class="sxs-lookup"><span data-stu-id="59458-200">That being said, you can create your own payload in the language of your choice using the custom payload authoring experience.</span></span> <span data-ttu-id="59458-201">我们还强烈建议你收集用于面向特定地理位置用户的现有有效负载。</span><span class="sxs-lookup"><span data-stu-id="59458-201">We also strongly recommend that you harvest existing payloads that were used to target users in a specific geography.</span></span> <span data-ttu-id="59458-202">换句话说，让攻击者本地化内容。</span><span class="sxs-lookup"><span data-stu-id="59458-202">In other words, let the attackers localize the content for you.</span></span>

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a><span data-ttu-id="59458-203">问：如何切换到其他语言以用于我的管理门户和培训体验？</span><span class="sxs-lookup"><span data-stu-id="59458-203">Q: How can I switch to other languages for my admin portal and training experience?</span></span>

<span data-ttu-id="59458-204">答：在 Microsoft 365 或 Office 365 中，语言配置是特定于每个用户帐户的集中式配置。</span><span class="sxs-lookup"><span data-stu-id="59458-204">A: In Microsoft 365 or Office 365, language configuration is specific and centralized for each user account.</span></span> <span data-ttu-id="59458-205">有关如何更改语言设置的说明，请参阅在 Microsoft [365 商业](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b)版中更改显示语言和时区。</span><span class="sxs-lookup"><span data-stu-id="59458-205">For instructions on how to change your language setting, see [Change your display language and time zone in Microsoft 365 for Business](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).</span></span>

<span data-ttu-id="59458-206">请注意，配置更改可能需要 30 分钟才能在所有服务之间同步。</span><span class="sxs-lookup"><span data-stu-id="59458-206">Note that the configuration change might take up to 30 minutes to synchronize across all services.</span></span>

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a><span data-ttu-id="59458-207">问：在启动功能齐全的市场活动之前，我能否触发测试模拟以了解其外观？</span><span class="sxs-lookup"><span data-stu-id="59458-207">Q: Can I trigger a test simulation to understand what it looks like prior to launching a full-fledged campaign?</span></span>

<span data-ttu-id="59458-208">答：可以！</span><span class="sxs-lookup"><span data-stu-id="59458-208">A: Yes you can!</span></span> <span data-ttu-id="59458-209">在 **向导中创建新** 模拟的最后一个"审阅模拟"页上，有一个发送 **测试的选项**。</span><span class="sxs-lookup"><span data-stu-id="59458-209">On the very last **Review Simulation** page in the wizard to create a new simulation, there's an option to **Send a test**.</span></span> <span data-ttu-id="59458-210">此选项将向当前登录的用户发送示例网络钓鱼模拟消息。</span><span class="sxs-lookup"><span data-stu-id="59458-210">This option will send a sample phishing simulation message to the currently logged in user.</span></span> <span data-ttu-id="59458-211">在收件箱中验证网络钓鱼邮件后，可以提交模拟。</span><span class="sxs-lookup"><span data-stu-id="59458-211">After you validate the phishing message in your Inbox, you can submit the simulation.</span></span>

![在"审阅模拟"页上发送测试按钮](../../media/attack-sim-review-simulation-page.png)

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a><span data-ttu-id="59458-213">问：作为同一模拟市场活动的一部分，我能否将属于不同租户的用户作为目标？</span><span class="sxs-lookup"><span data-stu-id="59458-213">Q: Can I target users that belong to a different tenant as part of the same simulation campaign?</span></span>

<span data-ttu-id="59458-214">答：不可以。</span><span class="sxs-lookup"><span data-stu-id="59458-214">A: No.</span></span> <span data-ttu-id="59458-215">目前不支持跨租户模拟。</span><span class="sxs-lookup"><span data-stu-id="59458-215">Currently, cross-tenant simulations are not supported.</span></span> <span data-ttu-id="59458-216">验证所有目标用户是否都在同一租户中。</span><span class="sxs-lookup"><span data-stu-id="59458-216">Verify that all of your targeted users are in the same tenant.</span></span> <span data-ttu-id="59458-217">任何跨租户用户或来宾用户都将从模拟市场活动中排除。</span><span class="sxs-lookup"><span data-stu-id="59458-217">Any cross-tenant users or guest users will be excluded from the simulation campaign.</span></span>

### <a name="q-how-does-region-aware-delivery-work"></a><span data-ttu-id="59458-218">问：区域感知传递如何工作？</span><span class="sxs-lookup"><span data-stu-id="59458-218">Q: How does region aware delivery work?</span></span>

<span data-ttu-id="59458-219">答：区域感知传递使用目标用户邮箱的 TimeZone 属性和"之前"逻辑来确定何时传递邮件。</span><span class="sxs-lookup"><span data-stu-id="59458-219">A: Region aware delivery uses the TimeZone attribute of the targeted user's mailbox and 'not before' logic to determine when to deliver the message.</span></span> <span data-ttu-id="59458-220">例如，请考虑以下方案：</span><span class="sxs-lookup"><span data-stu-id="59458-220">For example, consider the following scenario:</span></span>

- <span data-ttu-id="59458-221">在太平洋时区 (UTC-8) 的上午 7：00，管理员创建并计划一个活动，以在当天上午 9：00 开始。</span><span class="sxs-lookup"><span data-stu-id="59458-221">At 7:00 AM in the Pacific time zone (UTC-8), an admin creates and schedules a campaign to start at 9:00 AM on the same day.</span></span>
- <span data-ttu-id="59458-222">UserA 位于 UTC-5 (东部时区) 。</span><span class="sxs-lookup"><span data-stu-id="59458-222">UserA is in the Eastern time zone (UTC-5).</span></span>
- <span data-ttu-id="59458-223">UserB 也位于太平洋时区。</span><span class="sxs-lookup"><span data-stu-id="59458-223">UserB is also in the Pacific time zone.</span></span>

<span data-ttu-id="59458-224">同一天上午 9：00，模拟消息将发送到 UserB。</span><span class="sxs-lookup"><span data-stu-id="59458-224">At 9:00 AM on the same day, the simulation message is sent to UserB.</span></span> <span data-ttu-id="59458-225">通过区域感知传递，邮件不会在同一天发送给 UserA，因为太平洋时间上午 9：00 是东部时间晚上 12：00。</span><span class="sxs-lookup"><span data-stu-id="59458-225">With region-aware delivery, the message is not sent to UserA on the same day, because 9:00 AM Pacific time is 12:00 PM Eastern time.</span></span> <span data-ttu-id="59458-226">相反，邮件会于第二天东部时间上午 9：00 发送到 UserA。</span><span class="sxs-lookup"><span data-stu-id="59458-226">Instead, the message is sent to UserA at 9:00 AM Eastern time on the following day.</span></span>

<span data-ttu-id="59458-227">因此，在启用了区域感知传递的市场活动的首次运行中，可能会显示模拟邮件仅发送给特定时区的用户。</span><span class="sxs-lookup"><span data-stu-id="59458-227">So, on the initial run of a campaign with region aware delivery enabled, it might appear that the simulation message was sent only to users in a specific time zone.</span></span> <span data-ttu-id="59458-228">但是，随着时间的推移，越来越多的用户进入范围，目标用户将会增加。</span><span class="sxs-lookup"><span data-stu-id="59458-228">But, as time passes and more users come into scope, the targeted users will increase.</span></span>