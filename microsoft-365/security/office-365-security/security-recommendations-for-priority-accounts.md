---
title: 有关安全建议，包括Microsoft 365、优先级帐户、Office 365中的优先级帐户、Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-protecthve
description: 管理员可以了解如何提升安全设置，并使用报告、警报和调查，以在组织中Microsoft 365帐户。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e7617dd5af6a7e3b66fb33818208f01c8d8a338e
ms.sourcegitcommit: fa9efab24a84f71fec7d001f2ad8949125fa8eee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2021
ms.locfileid: "53055252"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a><span data-ttu-id="ac1ba-103">针对企业中的优先级帐户的安全Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ac1ba-103">Security recommendations for priority accounts in Microsoft 365</span></span>

<span data-ttu-id="ac1ba-104">并非所有用户帐户都有权访问相同的公司信息。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-104">Not all user accounts have access to the same company information.</span></span> <span data-ttu-id="ac1ba-105">某些帐户有权访问敏感信息，如财务数据、产品开发信息、合作伙伴对关键生成系统的访问权限等。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-105">Some accounts have access to sensitive information, such as financial data, product development information, partner access to critical build systems, and more.</span></span> <span data-ttu-id="ac1ba-106">如果泄露，有权访问高度机密信息的帐户将构成严重的威胁。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-106">If compromised, accounts that have access to highly confidential information pose a serious threat.</span></span> <span data-ttu-id="ac1ba-107">我们将这些类型的帐户称为 _"优先级帐户"。_</span><span class="sxs-lookup"><span data-stu-id="ac1ba-107">We call these types of accounts _priority accounts_.</span></span> <span data-ttu-id="ac1ba-108">优先级帐户包括 (，但不限于) CEO、COS、CFO、基础结构管理员帐户、生成系统帐户等。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-108">Priority accounts include (but aren't limited to) CEOs, CISOs, CFOs, infrastructure admin accounts, build system accounts, and more.</span></span>

<span data-ttu-id="ac1ba-109">对于攻击者，为普通用户或未知用户转换随机网络的普通网络钓鱼攻击效率很低。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-109">For attackers, ordinary phishing attacks that cast a random net for ordinary or unknown users are inefficient.</span></span> <span data-ttu-id="ac1ba-110">另一方面，_以_ 优先级帐户为目标的网络钓鱼或钓鱼攻击对攻击者来说非常具有攻击性。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-110">On the other hand, _spear phishing_ or _whaling_ attacks that target priority accounts are very rewarding for attackers.</span></span> <span data-ttu-id="ac1ba-111">因此，优先级帐户需要比普通保护更强大，以帮助防止帐户泄露。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-111">So, priority accounts require stronger than ordinary protection to help prevent account compromise.</span></span>

<span data-ttu-id="ac1ba-112">Microsoft 365和 Microsoft Defender for Office 365包含多个关键功能，这些功能可为优先帐户提供额外的安全层。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-112">Microsoft 365 and Microsoft Defender for Office 365 contain several key features that provide additional layers of security for your priority accounts.</span></span> <span data-ttu-id="ac1ba-113">本文介绍这些功能及其使用方法。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-113">This article describes these capabilities and how to use them.</span></span>

![图标表单中的安全建议摘要](../../media/security-recommendations-for-priority-users.png)

<br>

****

|<span data-ttu-id="ac1ba-115">任务</span><span class="sxs-lookup"><span data-stu-id="ac1ba-115">Task</span></span>|<span data-ttu-id="ac1ba-116">所有Office 365 企业版计划</span><span class="sxs-lookup"><span data-stu-id="ac1ba-116">All Office 365 Enterprise plans</span></span>|<span data-ttu-id="ac1ba-117">Microsoft 365 E3</span><span class="sxs-lookup"><span data-stu-id="ac1ba-117">Microsoft 365 E3</span></span>|<span data-ttu-id="ac1ba-118">Microsoft 365 E5</span><span class="sxs-lookup"><span data-stu-id="ac1ba-118">Microsoft 365 E5</span></span>|
|---|:---:|:---:|:---:|
|[<span data-ttu-id="ac1ba-119">提高优先级帐户的登录安全性</span><span class="sxs-lookup"><span data-stu-id="ac1ba-119">Increase sign-in security for priority accounts</span></span>](#increase-sign-in-security-for-priority-accounts)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[<span data-ttu-id="ac1ba-123">对优先级帐户使用严格预设安全策略</span><span class="sxs-lookup"><span data-stu-id="ac1ba-123">Use Strict preset security policies for priority accounts</span></span>](#use-strict-preset-security-policies-for-priority-accounts)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[<span data-ttu-id="ac1ba-127">将用户标记应用于优先级帐户</span><span class="sxs-lookup"><span data-stu-id="ac1ba-127">Apply user tags to priority accounts</span></span>](#apply-user-tags-to-priority-accounts)|||![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[<span data-ttu-id="ac1ba-129">监视警报、报告和检测中的优先级帐户</span><span class="sxs-lookup"><span data-stu-id="ac1ba-129">Monitor priority accounts in alerts, reports, and detections</span></span>](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[<span data-ttu-id="ac1ba-131">培训用户</span><span class="sxs-lookup"><span data-stu-id="ac1ba-131">Train users</span></span>](#train-users)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Included](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|

> [!NOTE]
> <span data-ttu-id="ac1ba-135">有关保护管理员帐户 (特权 _帐户_) ，请参阅 [本主题](/azure/architecture/framework/security/critical-impact-accounts)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-135">For information about securing _privileged accounts_ (admin accounts), see [this topic](/azure/architecture/framework/security/critical-impact-accounts).</span></span>

## <a name="increase-sign-in-security-for-priority-accounts"></a><span data-ttu-id="ac1ba-136">提高优先级帐户的登录安全性</span><span class="sxs-lookup"><span data-stu-id="ac1ba-136">Increase sign-in security for priority accounts</span></span>

<span data-ttu-id="ac1ba-137">优先级帐户需要更高的登录安全性。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-137">Priority accounts require increased sign-in security.</span></span> <span data-ttu-id="ac1ba-138">通过要求使用 MFA 身份验证和禁用 (身份验证协议，) 登录安全性。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-138">You can increase their sign-in security by requiring multi-factor authentication (MFA) and disabling legacy authentication protocols.</span></span>

<span data-ttu-id="ac1ba-139">有关说明，请参阅步骤 [1。使用 MFA 提高远程工作者的登录安全性](../../solutions/empower-people-to-work-remotely-secure-sign-in.md)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-139">For instructions, see [Step 1. Increase sign-in security for remote workers with MFA](../../solutions/empower-people-to-work-remotely-secure-sign-in.md).</span></span> <span data-ttu-id="ac1ba-140">尽管本文介绍的是远程工作者，但相同的概念也适用于优先用户。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-140">Although this article is about remote workers, the same concepts apply to priority users.</span></span>

<span data-ttu-id="ac1ba-141">**注意**：我们强烈建议你针对所有优先级用户全局禁用旧版身份验证协议，如上一篇文章中所述。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-141">**Note**: We strongly recommend that you globally disable legacy authentication protocols for all priority users as described in the previous article.</span></span> <span data-ttu-id="ac1ba-142">如果您的业务要求阻止您这样做，Exchange Online以下控件来帮助限制旧身份验证协议的范围：</span><span class="sxs-lookup"><span data-stu-id="ac1ba-142">If your business requirements prevent you from doing so, Exchange Online offers the following controls to help limit the scope of legacy authentication protocols:</span></span>

- <span data-ttu-id="ac1ba-143">您可以使用[Exchange Online](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online)中的身份验证[](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)策略和客户端访问规则来阻止或允许特定用户使用基本身份验证和旧版身份验证协议，如 POP3、IMAP4 和经过身份验证的 SMTP。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-143">You can use [authentication policies](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) and [Client Access Rules](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) in Exchange Online to block or allow Basic authentication and legacy authentication protocols like POP3, IMAP4, and authenticated SMTP for specific users.</span></span>

- <span data-ttu-id="ac1ba-144">可以在单个邮箱上禁用 POP3 和 IMAP4 访问。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-144">You can disable POP3 and IMAP4 access on individual mailboxes.</span></span> <span data-ttu-id="ac1ba-145">您可以在组织一级禁用已验证的 SMTP，并启用它到仍然需要它的特定邮箱上。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-145">You can disable authenticated SMTP at the organizational level and enable it on specific mailboxes that still require it.</span></span> <span data-ttu-id="ac1ba-146">有关说明，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="ac1ba-146">For instructions, see the following articles:</span></span>
  - [<span data-ttu-id="ac1ba-147">为用户启用或禁用 POP3 或 IMAP4 访问</span><span class="sxs-lookup"><span data-stu-id="ac1ba-147">Enable or Disable POP3 or IMAP4 access for a user</span></span>](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [<span data-ttu-id="ac1ba-148">启用或禁用 SMTP AUTH (身份验证的客户端 SMTP) </span><span class="sxs-lookup"><span data-stu-id="ac1ba-148">Enable or disable authenticated client SMTP submission (SMTP AUTH)</span></span>](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

<span data-ttu-id="ac1ba-149">还值得一提的是，Exchange Online 中正对 Exchange Web 服务 (EWS) 、Exchange ActiveSync、POP3、IMAP4 和远程 PowerShell 弃用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-149">It's also worth noting that Basic authentication is in the process of being deprecated in Exchange Online for Exchange Web Services (EWS), Exchange ActiveSync, POP3, IMAP4, and remote PowerShell.</span></span> <span data-ttu-id="ac1ba-150">有关详细信息，请参阅此 [博客文章](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-150">For details, see this [blog post](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).</span></span>

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a><span data-ttu-id="ac1ba-151">对优先级帐户使用严格预设安全策略</span><span class="sxs-lookup"><span data-stu-id="ac1ba-151">Use Strict preset security policies for priority accounts</span></span>

<span data-ttu-id="ac1ba-152">优先级用户需要针对 EOP Exchange Online Protection (和 Defender for) 中提供的各种Office 365。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-152">Priority users require more stringent actions for the various protections that are available in Exchange Online Protection (EOP) and Defender for Office 365.</span></span>

<span data-ttu-id="ac1ba-153">例如，不应将分类为垃圾邮件的邮件发送到"垃圾邮件"文件夹，而是应在这些邮件用于优先级帐户时隔离这些相同的邮件。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-153">For example, instead of delivering messages that were classified as spam to the Junk Email folder, you should quarantine those same messages if they're intended for priority accounts.</span></span>

<span data-ttu-id="ac1ba-154">可以通过在预设安全策略中使用 Strict 配置文件，对优先级帐户实施此严格方法。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-154">You can implement this stringent approach for priority accounts by using the Strict profile in preset security policies.</span></span>

<span data-ttu-id="ac1ba-155">预设安全策略是一个方便且集中的位置，用于将我们建议的严格策略设置应用于 EOP 和 Defender for Office 365。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-155">Preset security policies are a convenient and central location to apply our recommended Strict policy settings for all of the protections in EOP and Defender for Office 365.</span></span> <span data-ttu-id="ac1ba-156">有关详细信息，请参阅[Preset security policies in EOP and Microsoft Defender for Office 365](preset-security-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-156">For more information, see [Preset security policies in EOP and Microsoft Defender for Office 365](preset-security-policies.md).</span></span>

<span data-ttu-id="ac1ba-157">有关严格策略设置与默认策略和标准策略设置之间如何不同的详细信息，请参阅[EOP](recommended-settings-for-eop-and-office365.md)和 Microsoft Defender 的推荐设置Office 365安全。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-157">For details about how the Strict policy settings differ from the default and Standard policy settings, see [Recommended settings for EOP and Microsoft Defender for Office 365 security](recommended-settings-for-eop-and-office365.md).</span></span>

## <a name="apply-user-tags-to-priority-accounts"></a><span data-ttu-id="ac1ba-158">将用户标记应用于优先级帐户</span><span class="sxs-lookup"><span data-stu-id="ac1ba-158">Apply user tags to priority accounts</span></span>

<span data-ttu-id="ac1ba-159">作为 Microsoft 365 E5 或加载项订阅) 的一部分，Microsoft Defender for Office 365 计划 2 (中的用户标记是一种在报告和事件调查中快速标识和分类特定用户或用户组的方法。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-159">User tags in Microsoft Defender for Office 365 Plan 2 (as part of Microsoft 365 E5 or an add-on subscription) are a way to quickly identify and classify specific users or groups of users in reports and incident investigations.</span></span>

<span data-ttu-id="ac1ba-160">**优先级帐户** 是一种内置用户标记 (称为系统标记) ，可用于标识涉及优先帐户的事件和警报。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-160">**Priority accounts** is a type of built-in user tag (known as a _system tag_) that you can use to identify incidents and alerts that involve priority accounts.</span></span> <span data-ttu-id="ac1ba-161">有关优先级帐户 **详细信息，** 请参阅管理和 [监视优先级帐户](../../admin/setup/priority-accounts.md)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-161">For more information about **priority accounts**, see [Manage and monitor priority accounts](../../admin/setup/priority-accounts.md).</span></span>

<span data-ttu-id="ac1ba-162">还可以创建自定义标记以进一步标识和分类优先级帐户。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-162">You can also create custom tags to further identify and classify your priority accounts.</span></span> <span data-ttu-id="ac1ba-163">有关详细信息，请参阅用户 [标记](user-tags.md)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-163">For more information, see [User tags](user-tags.md).</span></span> <span data-ttu-id="ac1ba-164">可以在与自定义 **用户 (** 相同的) 管理系统标记的优先级帐户。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-164">You can manage **priority accounts** (system tags) in the same interface as custom user tags.</span></span>

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a><span data-ttu-id="ac1ba-165">监视警报、报告和检测中的优先级帐户</span><span class="sxs-lookup"><span data-stu-id="ac1ba-165">Monitor priority accounts in alerts, reports, and detections</span></span>

<span data-ttu-id="ac1ba-166">保护并标记优先用户后，可以使用 EOP 和 Defender for Office 365 中的可用报告、警报和调查来快速识别涉及优先帐户的事件或检测。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-166">After you secure and tag your priority users, you can use the available reports, alerts, and investigations in EOP and Defender for Office 365 to quickly identify incidents or detections that involve priority accounts.</span></span> <span data-ttu-id="ac1ba-167">下表介绍了支持用户标记的功能。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-167">The features that support user tags are described in the following table.</span></span>

<br>

****

|<span data-ttu-id="ac1ba-168">功能</span><span class="sxs-lookup"><span data-stu-id="ac1ba-168">Feature</span></span>|<span data-ttu-id="ac1ba-169">说明</span><span class="sxs-lookup"><span data-stu-id="ac1ba-169">Description</span></span>|
|---|---|
|<span data-ttu-id="ac1ba-170">警报</span><span class="sxs-lookup"><span data-stu-id="ac1ba-170">Alerts</span></span>|<span data-ttu-id="ac1ba-171">受影响用户的用户标记在门户的警报页面上可见并Microsoft 365 Defender筛选器。 </span><span class="sxs-lookup"><span data-stu-id="ac1ba-171">The user tags of affected users are visible and available as filters on the **Alerts** page in the Microsoft 365 Defender portal.</span></span> <span data-ttu-id="ac1ba-172">有关详细信息，请参阅 [查看警报](../../compliance/alert-policies.md#viewing-alerts)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-172">For more information, see [Viewing alerts](../../compliance/alert-policies.md#viewing-alerts).</span></span>|
|<span data-ttu-id="ac1ba-173">资源管理器</span><span class="sxs-lookup"><span data-stu-id="ac1ba-173">Explorer</span></span> <p> <span data-ttu-id="ac1ba-174">实时检测</span><span class="sxs-lookup"><span data-stu-id="ac1ba-174">Real-time detections</span></span>|<span data-ttu-id="ac1ba-175">在 **资源管理器** (Defender for Office 365 计划 2) 或实时检测 **(** Defender for Office 365 计划 1) 中，用户标记显示在"电子邮件"网格视图和"电子邮件详细信息"飞出控件中。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-175">In **Explorer** (Defender for Office 365 Plan 2) or **Real-time detections** (Defender for Office 365 Plan 1), user tags are visible in the Email grid view and the Email details flyout.</span></span> <span data-ttu-id="ac1ba-176">用户标记还可作为可筛选属性使用。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-176">User tags are also available as a filterable property.</span></span> <span data-ttu-id="ac1ba-177">有关详细信息，请参阅资源管理器  [中的标记](threat-explorer.md#tags-in-threat-explorer)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-177">For more information, see  [Tags in Explorer](threat-explorer.md#tags-in-threat-explorer).</span></span>|
|<span data-ttu-id="ac1ba-178">市场活动视图</span><span class="sxs-lookup"><span data-stu-id="ac1ba-178">Campaign Views</span></span>|<span data-ttu-id="ac1ba-179">用户标记是 Microsoft Defender for Office 365 计划 2 的"市场活动视图"中的许多可筛选属性之一。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-179">User tags are one of many filterable properties in Campaign Views in Microsoft Defender for Office 365 Plan 2.</span></span> <span data-ttu-id="ac1ba-180">有关详细信息，请参阅 Campaign [Views](campaigns.md)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-180">For more information, see [Campaign Views](campaigns.md).</span></span>|
|<span data-ttu-id="ac1ba-181">威胁防护状态报告</span><span class="sxs-lookup"><span data-stu-id="ac1ba-181">Threat protection status report</span></span>|<span data-ttu-id="ac1ba-182">在威胁防护状态报告中的几乎所有视图和详细信息表中，你可以按优先级帐户 **筛选结果**。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-182">In virtually all of the views and detail tables in the **Threat protection status report**, you can filter the results by **priority accounts**.</span></span> <span data-ttu-id="ac1ba-183">有关详细信息，请参阅威胁 [防护状态报告](view-email-security-reports.md#threat-protection-status-report)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-183">For more information, see [Threat protection status report](view-email-security-reports.md#threat-protection-status-report).</span></span>|
|<span data-ttu-id="ac1ba-184">优先级帐户的电子邮件问题报告</span><span class="sxs-lookup"><span data-stu-id="ac1ba-184">Email issues for priority accounts report</span></span>|<span data-ttu-id="ac1ba-185">EAC Exchange 管理中心 (**中的**"优先级帐户的电子邮件问题) 包含有关优先级帐户的未送达和延迟 **邮件的信息**。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-185">The **Email issues for priority accounts** report in the Exchange admin center (EAC) contains information about undelivered and delayed messages for **priority accounts**.</span></span> <span data-ttu-id="ac1ba-186">有关详细信息，请参阅优先级 [帐户的电子邮件问题报告](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-186">For more information, see [Email issues for priority accounts report](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).</span></span>|
|

## <a name="train-users"></a><span data-ttu-id="ac1ba-187">培训用户</span><span class="sxs-lookup"><span data-stu-id="ac1ba-187">Train users</span></span>

<span data-ttu-id="ac1ba-188">使用优先帐户培训用户可帮助节省这些用户和安全运营团队的时间和沮丧。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-188">Training users with priority accounts can help save those users and your security operations team much time and frustration.</span></span> <span data-ttu-id="ac1ba-189">不为人知的用户不太可能打开可疑电子邮件中的附件或单击链接，并且他们更有可能避免可疑网站。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-189">Savvy users are less likely to open attachments or click links in questionable email messages, and they are more likely to avoid suspicious websites.</span></span>

<span data-ttu-id="ac1ba-190">美国国家/地区 [学校网络安全](https://www.belfercenter.org/CyberPlaybook) 宣传活动手册提供了在组织中建立强大的安全意识文化的指导，包括培训用户识别网络钓鱼攻击。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-190">The Harvard Kennedy School [Cybersecurity Campaign Handbook](https://www.belfercenter.org/CyberPlaybook) provides excellent guidance for establishing a strong culture of security awareness within your organization, including training users to identify phishing attacks.</span></span>

<span data-ttu-id="ac1ba-191">Microsoft 365提供了以下资源来帮助通知贵组织的用户：</span><span class="sxs-lookup"><span data-stu-id="ac1ba-191">Microsoft 365 provides the following resources to help inform users in your organization:</span></span>

<br>

****

|<span data-ttu-id="ac1ba-192">概念</span><span class="sxs-lookup"><span data-stu-id="ac1ba-192">Concept</span></span>|<span data-ttu-id="ac1ba-193">资源</span><span class="sxs-lookup"><span data-stu-id="ac1ba-193">Resources</span></span>|<span data-ttu-id="ac1ba-194">说明</span><span class="sxs-lookup"><span data-stu-id="ac1ba-194">Description</span></span>|
|---|---|---|
|<span data-ttu-id="ac1ba-195">Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ac1ba-195">Microsoft 365</span></span>|[<span data-ttu-id="ac1ba-196">可自定义的学习路径</span><span class="sxs-lookup"><span data-stu-id="ac1ba-196">Customizable learning pathways</span></span>](/office365/customlearning/)|<span data-ttu-id="ac1ba-197">这些资源可帮助您将针对组织用户的培训整合在一起。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-197">These resources can help you put together training for users in your organization.</span></span>|
|<span data-ttu-id="ac1ba-198">Microsoft 365 安全中心</span><span class="sxs-lookup"><span data-stu-id="ac1ba-198">Microsoft 365 security</span></span>|[<span data-ttu-id="ac1ba-199">Learning模块：使用内置的智能安全保护组织，Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ac1ba-199">Learning module: Secure your organization with built-in, intelligent security from Microsoft 365</span></span>](/learn/modules/security-with-microsoft-365)|<span data-ttu-id="ac1ba-200">本模块使您能够描述Microsoft 365功能如何协同工作，并阐明这些安全功能的好处。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-200">This module enables you to describe how Microsoft 365 security features work together and to articulate the benefits of these security features.</span></span>|
|<span data-ttu-id="ac1ba-201">多重身份验证</span><span class="sxs-lookup"><span data-stu-id="ac1ba-201">Multi-factor authentication</span></span>|[<span data-ttu-id="ac1ba-202">两步验证：什么是附加验证页面？</span><span class="sxs-lookup"><span data-stu-id="ac1ba-202">Two-step verification: What is the additional verification page?</span></span>](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|<span data-ttu-id="ac1ba-203">本文帮助最终用户了解什么是多重身份验证以及为什么在组织中使用的多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-203">This article helps end users understand what multi-factor authentication is and why it's being used at your organization.</span></span>|
|<span data-ttu-id="ac1ba-204">攻击模拟培训</span><span class="sxs-lookup"><span data-stu-id="ac1ba-204">Attack simulation training</span></span>|[<span data-ttu-id="ac1ba-205">开始使用攻击模拟培训</span><span class="sxs-lookup"><span data-stu-id="ac1ba-205">Get started using Attack simulation training</span></span>](attack-simulation-training-get-started.md)|<span data-ttu-id="ac1ba-206">Microsoft Defender for Office 365 计划 2 中的攻击模拟培训允许管理员配置、启动和跟踪针对特定用户组的模拟网络钓鱼攻击。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-206">Attack simulation training in Microsoft Defender for Office 365 Plan 2 allows admin to configure, launch, and track simulated phishing attacks against specific groups of users.</span></span>|

<span data-ttu-id="ac1ba-207">此外，Microsoft 建议用户执行本文中描述的操作：保护帐户和设备免受 [黑客和恶意软件的攻击](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6)。</span><span class="sxs-lookup"><span data-stu-id="ac1ba-207">In addition, Microsoft recommends that users take the actions described in this article: [Protect your account and devices from hackers and malware](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6).</span></span> <span data-ttu-id="ac1ba-208">这些操作包括：</span><span class="sxs-lookup"><span data-stu-id="ac1ba-208">These actions include:</span></span>

- <span data-ttu-id="ac1ba-209">使用强密码</span><span class="sxs-lookup"><span data-stu-id="ac1ba-209">Using strong passwords</span></span>
- <span data-ttu-id="ac1ba-210">保护设备</span><span class="sxs-lookup"><span data-stu-id="ac1ba-210">Protecting devices</span></span>
- <span data-ttu-id="ac1ba-211">为非托管设备Windows 10 Mac 电脑 (安全功能) </span><span class="sxs-lookup"><span data-stu-id="ac1ba-211">Enabling security features on Windows 10 and Mac PCs (for unmanaged devices)</span></span>

## <a name="see-also"></a><span data-ttu-id="ac1ba-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac1ba-212">See also</span></span>

[<span data-ttu-id="ac1ba-213">宣布在 Microsoft Defender 中为用户Office 365</span><span class="sxs-lookup"><span data-stu-id="ac1ba-213">Announcing Priority Account Protection in Microsoft Defender for Office 365</span></span>](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
