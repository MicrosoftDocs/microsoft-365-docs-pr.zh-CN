---
title: 模拟见解
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: 管理员可以了解模拟见解的工作原理。 他们可以快速确定哪些发件人从没有通过 SPF、DKIM 或 DMARC 身份验证检查 (向组织合法发送电子邮件) 。
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a11dd30030ccce886abd50ff72b5a09b10938ece
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "52535755"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a><span data-ttu-id="57ee9-104">Defender for Office 365 中的模拟见解</span><span class="sxs-lookup"><span data-stu-id="57ee9-104">Impersonation insight in Defender for Office 365</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="57ee9-105">**适用对象**</span><span class="sxs-lookup"><span data-stu-id="57ee9-105">**Applies to**</span></span>
- [<span data-ttu-id="57ee9-106">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="57ee9-106">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="57ee9-107">Microsoft Defender for Office 365 计划 1 和计划 2</span><span class="sxs-lookup"><span data-stu-id="57ee9-107">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="57ee9-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="57ee9-108">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

> [!NOTE]
> <span data-ttu-id="57ee9-109">本文中所述的功能在预览版中，可能会更改，并且并非在所有组织中都可用。</span><span class="sxs-lookup"><span data-stu-id="57ee9-109">The features described in this article are in Preview, are subject to change, and are not available in all organizations.</span></span>

<span data-ttu-id="57ee9-110">模拟是电子邮件发件人看起来与真实或预期的发件人电子邮件地址非常相似的地方。</span><span class="sxs-lookup"><span data-stu-id="57ee9-110">Impersonation is where the sender of an email message looks very similar to a real or expected sender email address.</span></span> <span data-ttu-id="57ee9-111">攻击者经常在网络钓鱼或其他类型的攻击中模拟发件人电子邮件地址，以赢得收件人的信任。</span><span class="sxs-lookup"><span data-stu-id="57ee9-111">Attackers often user impersonated sender email addresses in phishing or other types of attacks in an effort to gain the trust of the recipient.</span></span> <span data-ttu-id="57ee9-112">基本上有两种类型的模拟：</span><span class="sxs-lookup"><span data-stu-id="57ee9-112">There are basically two types of impersonation:</span></span>

- <span data-ttu-id="57ee9-113">**域模拟**：lila@contoso.com，模拟发件人的电子邮件地址将 lila@ćóntoso.com。</span><span class="sxs-lookup"><span data-stu-id="57ee9-113">**Domain impersonation**: Instead of lila@contoso.com, the impersonated sender's email address is lila@ćóntoso.com.</span></span>
- <span data-ttu-id="57ee9-114">**用户模拟**：michelle@contoso.com，模拟发件人的电子邮件地址将 rnichell@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="57ee9-114">**User impersonation**: Instead of michelle@contoso.com, the impersonated sender's email address is rnichell@contoso.com.</span></span>

<span data-ttu-id="57ee9-115">域模拟不同于域 [欺骗](anti-spoofing-protection.md)，因为模拟的域通常是真实的注册域。</span><span class="sxs-lookup"><span data-stu-id="57ee9-115">Domain impersonation is different from [domain spoofing](anti-spoofing-protection.md), because the impersonated domain is typically a real, registered domain.</span></span> <span data-ttu-id="57ee9-116">来自模拟域中的发件人的邮件可以而且通常通过常规电子邮件身份验证检查，以识别 SPF、DKIM 和 DMARC (欺骗) 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-116">Messages from senders in the impersonated domain can and often do pass regular email authentication checks that would otherwise identify spoofing attempts (SPF, DKIM, and DMARC).</span></span>

<span data-ttu-id="57ee9-117">模拟保护是反网络钓鱼策略设置的一部分，) 专用于 Microsoft Defender for Office 365。</span><span class="sxs-lookup"><span data-stu-id="57ee9-117">Impersonation protection is part of the anti-phishing policy settings) that are exclusive to Microsoft Defender for Office 365.</span></span> <span data-ttu-id="57ee9-118">有关这些设置详细信息，请参阅 Microsoft Defender for Office 365 中的防钓鱼[策略中的模拟Office 365。](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</span><span class="sxs-lookup"><span data-stu-id="57ee9-118">For more information about these settings, see [Impersonation settings in anti-phishing policies in Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).</span></span>

<span data-ttu-id="57ee9-119">您可以使用模拟见解快速识别来自已配置为用于模拟保护的模拟发件人或发件人域的邮件。</span><span class="sxs-lookup"><span data-stu-id="57ee9-119">You can use the impersonation insight to quickly identify messages from impersonated senders or sender domains that you've configured for impersonation protection.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="57ee9-120">开始前，有必要了解什么？</span><span class="sxs-lookup"><span data-stu-id="57ee9-120">What do you need to know before you begin?</span></span>

- <span data-ttu-id="57ee9-121">安全与合规中心的打开网址为 <https://protection.office.com/>。</span><span class="sxs-lookup"><span data-stu-id="57ee9-121">You open the Security & Compliance Center at <https://protection.office.com/>.</span></span> <span data-ttu-id="57ee9-122">若要直接转到"反网络钓鱼"页面上的模拟 **见解** ，请使用 <https://protection.office.com/antiphishing> 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-122">To go directly to the impersonation insight on the **Anti-phishing** page, use <https://protection.office.com/antiphishing>.</span></span>

- <span data-ttu-id="57ee9-123">必须分配有 Office 365 安全与合规中心内的权限，才能执行本文中的步骤：</span><span class="sxs-lookup"><span data-stu-id="57ee9-123">You need to be assigned permissions in the Security & Compliance Center before you can do the procedures in this article:</span></span>
  - <span data-ttu-id="57ee9-124">**组织管理**</span><span class="sxs-lookup"><span data-stu-id="57ee9-124">**Organization Management**</span></span>
  - <span data-ttu-id="57ee9-125">**安全管理员**</span><span class="sxs-lookup"><span data-stu-id="57ee9-125">**Security Administrator**</span></span>
  - <span data-ttu-id="57ee9-126">**安全读者**</span><span class="sxs-lookup"><span data-stu-id="57ee9-126">**Security Reader**</span></span>
  - <span data-ttu-id="57ee9-127">**全局读取者**</span><span class="sxs-lookup"><span data-stu-id="57ee9-127">**Global Reader**</span></span>

  <span data-ttu-id="57ee9-128">有关详细信息，请参阅[安全与合规中心中的权限](permissions-in-the-security-and-compliance-center.md)。</span><span class="sxs-lookup"><span data-stu-id="57ee9-128">For more information, see [Permissions in the Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>

  <span data-ttu-id="57ee9-129">**注意**：将用户添加到 Microsoft 365 管理中心的相应 Azure Active Directory 角色会为用户提供安全与合规中心中所需的权限&以及安全与合规中心中其他功能Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="57ee9-129">**Note**: Adding users to the corresponding Azure Active Directory role in the Microsoft 365 admin center gives users the required permissions in the Security & Compliance Center _and_ permissions for other features in Microsoft 365.</span></span> <span data-ttu-id="57ee9-130">有关详细信息，请参阅 [关于管理员角色](../../admin/add-users/about-admin-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="57ee9-130">For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).</span></span>

- <span data-ttu-id="57ee9-131">在 Microsoft Defender for Office 365 中的防钓鱼策略中启用和配置Office 365。</span><span class="sxs-lookup"><span data-stu-id="57ee9-131">You enable and configure impersonation protection in anti-phishing policies in Microsoft Defender for Office 365.</span></span> <span data-ttu-id="57ee9-132">默认情况下不启用模拟保护。</span><span class="sxs-lookup"><span data-stu-id="57ee9-132">Impersonation protection is not enabled by default.</span></span> <span data-ttu-id="57ee9-133">有关详细信息，请参阅 Configure [anti-phishing policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="57ee9-133">For more information, see [Configure anti-phishing policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).</span></span>

## <a name="open-the-impersonation-insight-in-the-security--compliance-center"></a><span data-ttu-id="57ee9-134">在安全与合规中心打开模拟&见解</span><span class="sxs-lookup"><span data-stu-id="57ee9-134">Open the impersonation insight in the Security & Compliance Center</span></span>

1. <span data-ttu-id="57ee9-135">在安全&合规中心，转到"**威胁管理** \> **策略** \> **""防钓鱼"。**</span><span class="sxs-lookup"><span data-stu-id="57ee9-135">In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **Anti-phishing**.</span></span>

2. <span data-ttu-id="57ee9-136">在主要的 **"反网络钓鱼"页面上**，模拟见解如下所示：</span><span class="sxs-lookup"><span data-stu-id="57ee9-136">On the main **Anti-phishing page**, the impersonation insight looks like this:</span></span>

   <span data-ttu-id="57ee9-137">此见解有两种模式：</span><span class="sxs-lookup"><span data-stu-id="57ee9-137">This insight has two modes:</span></span>

    - <span data-ttu-id="57ee9-138">**见解模式**：如果在任何防钓鱼策略中启用和配置了模拟保护，则此见解将显示过去七天内来自模拟发件人的检测到的邮件数。</span><span class="sxs-lookup"><span data-stu-id="57ee9-138">**Insight mode**: If impersonation protection is enabled and configured in any anti-phishing policies, the insight shows the number of detected messages from impersonated senders over the past seven days.</span></span> <span data-ttu-id="57ee9-139">这是所有反网络钓鱼策略中所有检测到的模拟发件人总数。</span><span class="sxs-lookup"><span data-stu-id="57ee9-139">This is the total of all detected impersonated senders from all anti-phishing policies.</span></span>
    - <span data-ttu-id="57ee9-140">**如果模式**：如果未在任何活动的反网络钓鱼策略中启用和配置模拟保护，则此见解将展示我们的模拟保护功能在过去七天内检测到的邮件数。</span><span class="sxs-lookup"><span data-stu-id="57ee9-140">**What if mode**: If impersonation protection is not enabled and configured in any active anti-phishing policies, the insight shows you how many messages *would* have been detected by our impersonation protection capabilities over the past seven days.</span></span>

   <span data-ttu-id="57ee9-141">无论哪种方式 **，"域模拟**"都显示来自受保护域中发件人的邮件数，而"用户模拟"显示来自受保护用户的邮件数。</span><span class="sxs-lookup"><span data-stu-id="57ee9-141">Either way, **Domains impersonated** shows the number of messages from senders in protected domains, while **Users impersonated** shows the number of messages from protected users.</span></span>

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a><span data-ttu-id="57ee9-142">查看有关来自模拟域中发件人的邮件的信息</span><span class="sxs-lookup"><span data-stu-id="57ee9-142">View information about messages from senders in impersonated domains</span></span>

<span data-ttu-id="57ee9-143">在模拟见解上，单击"**模拟的域"。**</span><span class="sxs-lookup"><span data-stu-id="57ee9-143">On the impersonation insight, click **Domains impersonated**.</span></span> <span data-ttu-id="57ee9-144">打开 **的"模拟** 见解"页包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="57ee9-144">The **Impersonation insight** page that opens contains the following information:</span></span>

- <span data-ttu-id="57ee9-145">**发件人** 域：模拟域，用于发送电子邮件的域。</span><span class="sxs-lookup"><span data-stu-id="57ee9-145">**Sender Domain**: The impersonating domain, which is the domain that was used to send the email message.</span></span> 
- <span data-ttu-id="57ee9-146">**邮件计数**：过去 7 天内来自模拟发件人域的邮件数。</span><span class="sxs-lookup"><span data-stu-id="57ee9-146">**Message count**: The number of messages from impersonating sender domain over the last 7 days.</span></span>
- <span data-ttu-id="57ee9-147">**模拟类型**：此值显示模拟帐户的检测 (例如，**地址中的域) 。**</span><span class="sxs-lookup"><span data-stu-id="57ee9-147">**Impersonation type**: This value shows the detected location of the impersonation (for example, **Domain in address**).</span></span>
- <span data-ttu-id="57ee9-148">**模拟 (域) ：** 模拟域，它应非常类似于在反网络钓鱼策略中配置为进行模拟保护的域。</span><span class="sxs-lookup"><span data-stu-id="57ee9-148">**Impersonated domain(s)**: The impersonated domain, which should closely resemble the domain that's configured for impersonation protection in the anti-phishing policy.</span></span>
- <span data-ttu-id="57ee9-149">**域类型**：此值是 **内部域** 的公司域或自定义 **域** 的自定义域。</span><span class="sxs-lookup"><span data-stu-id="57ee9-149">**Domain type**: This value is **Company domain** for internal domains or **Custom domain** for custom domains.</span></span>
- <span data-ttu-id="57ee9-150">**策略**：检测到模拟域的防钓鱼策略。</span><span class="sxs-lookup"><span data-stu-id="57ee9-150">**Policy**: The anti-phishing policy that detected the impersonated domain.</span></span>
- <span data-ttu-id="57ee9-151">**允许模拟**：下列值之一：</span><span class="sxs-lookup"><span data-stu-id="57ee9-151">**Allowed to impersonate**: One of the following values:</span></span>
  - <span data-ttu-id="57ee9-152">**是**：域配置为受信任的域 (反垃圾邮件策略中的) 保护的例外。</span><span class="sxs-lookup"><span data-stu-id="57ee9-152">**Yes**: The domain was configured as trusted domain (an exception for impersonation protection) in the anti-spam policy.</span></span> <span data-ttu-id="57ee9-153">检测到来自模拟域中发件人的邮件，但允许。</span><span class="sxs-lookup"><span data-stu-id="57ee9-153">Messages from senders in the impersonated domain were detected, but allowed.</span></span>
  - <span data-ttu-id="57ee9-154">**否**：域配置为在反垃圾邮件策略中提供模拟保护。</span><span class="sxs-lookup"><span data-stu-id="57ee9-154">**No**: The domain was configured for impersonation protection in the anti-spam policy.</span></span> <span data-ttu-id="57ee9-155">根据反垃圾邮件策略中模拟域的操作，检测到来自模拟域中的发件人的邮件并据此操作。</span><span class="sxs-lookup"><span data-stu-id="57ee9-155">Messages from senders in the impersonated domain were detected and acted upon based on the action for impersonated domains in the anti-spam policy.</span></span>

<span data-ttu-id="57ee9-156">您可以单击所选列标题对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="57ee9-156">You can click selected column headings to sort the results.</span></span>

<span data-ttu-id="57ee9-157">若要筛选结果，可以使用"筛选域"框输入以逗号分隔的值列表来筛选结果。</span><span class="sxs-lookup"><span data-stu-id="57ee9-157">To filter the results, you can use the **Filter domain** box to enter a comma-separated list of values to filter the results.</span></span>

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a><span data-ttu-id="57ee9-158">查看有关来自模拟域中发件人的邮件的详细信息</span><span class="sxs-lookup"><span data-stu-id="57ee9-158">View details about messages from senders in impersonated domains</span></span>

<span data-ttu-id="57ee9-159">在" **模拟见解** "页上，选择一个可用行。</span><span class="sxs-lookup"><span data-stu-id="57ee9-159">On the **Impersonation insight** page, select one of the available rows.</span></span> <span data-ttu-id="57ee9-160">显示的详细信息飞出包含以下信息和功能：</span><span class="sxs-lookup"><span data-stu-id="57ee9-160">The details flyout that appears contains the following information and features:</span></span>

- <span data-ttu-id="57ee9-161">**要修改的选择模拟策略**：选择要修改的受影响的防钓鱼策略。</span><span class="sxs-lookup"><span data-stu-id="57ee9-161">**Selection impersonation policy to modify**: Select the affected anti-phishing policy that you want to modify.</span></span> <span data-ttu-id="57ee9-162">只有策略中定义了模拟域的策略才可用。</span><span class="sxs-lookup"><span data-stu-id="57ee9-162">Only polices where the impersonated domain is defined in the policy are available.</span></span> <span data-ttu-id="57ee9-163">参考上一页，查看哪个策略实际负责根据收件人 (以及策略的优先级来检测模拟) 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-163">Refer to the previous page to see which policy was actually responsible for detecting the impersonated domain (likely based on the recipient and the priority of the policy).</span></span>

- <span data-ttu-id="57ee9-164">添加到允许 **的** 模拟列表：使用此开关添加或删除所选防钓鱼策略的"受信任的发件人和域 **(** 模拟) 例外"中的发件人：</span><span class="sxs-lookup"><span data-stu-id="57ee9-164">**Add to the allowed to impersonation list**: Use this toggle to add or remove the sender from the **Trusted senders and domains** (impersonation exceptions) for the anti-phishing policy that you selected:</span></span>
  - <span data-ttu-id="57ee9-165">如果 **此条目的"允许模拟** "值为 **"否**"，则开关处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="57ee9-165">If the **Allowed to impersonate** value for this entry was **No**, the toggle is off.</span></span> <span data-ttu-id="57ee9-166">若要通过模拟保护使此域中的所有发件人免于评估，将开关滑动到"打开"： ![ 打开切换 ](../../media/scc-toggle-on.png) 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-166">To exempt all senders in this domain from evaluation by impersonation protection, slide the toggle to on: ![Toggle on](../../media/scc-toggle-on.png).</span></span> <span data-ttu-id="57ee9-167">该域将添加到反网络钓鱼策略的模拟保护设置中的"受信任的域"列表中。</span><span class="sxs-lookup"><span data-stu-id="57ee9-167">The domain is added to the **Trusted domains** list in the impersonation protection settings of the anti-phishing policy.</span></span>
  - <span data-ttu-id="57ee9-168">如果 **此条目的"允许模拟** "值为 **"是**"，则切换处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="57ee9-168">If the **Allowed to impersonate** value for this entry was **Yes**, the toggle is on.</span></span> <span data-ttu-id="57ee9-169">若要通过模拟保护使此域中的所有发件人返回评估，请切换为关闭： ![ 切换为关闭 ](../../media/scc-toggle-off.png) 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-169">To return all senders in this domain to evaluation by impersonation protection, slide the toggle to off: ![Toggle off](../../media/scc-toggle-off.png).</span></span> <span data-ttu-id="57ee9-170">该域将从反 **网络钓鱼** 策略的模拟保护设置中的"受信任的域"列表中删除。</span><span class="sxs-lookup"><span data-stu-id="57ee9-170">The domain is removed from the **Trusted domains** list in the impersonation protection settings of the anti-phishing policy.</span></span>

- <span data-ttu-id="57ee9-171">我们为什么捕获到此。</span><span class="sxs-lookup"><span data-stu-id="57ee9-171">Why we caught this.</span></span>
- <span data-ttu-id="57ee9-172">需要执行哪些工作。</span><span class="sxs-lookup"><span data-stu-id="57ee9-172">What you need to do.</span></span>
- <span data-ttu-id="57ee9-173">列出模拟域的域摘要。</span><span class="sxs-lookup"><span data-stu-id="57ee9-173">A domain summary that list the impersonated domain.</span></span>
- <span data-ttu-id="57ee9-174">WhoIs 有关发件人的数据。</span><span class="sxs-lookup"><span data-stu-id="57ee9-174">WhoIs data about the sender.</span></span>
- <span data-ttu-id="57ee9-175">打开威胁资源管理器 [以查看有关](threat-explorer.md) 发件人的其他详细信息的链接。</span><span class="sxs-lookup"><span data-stu-id="57ee9-175">A link to open [Threat Explorer](threat-explorer.md) to see additional details about the sender.</span></span>
- <span data-ttu-id="57ee9-176">来自已传递到组织的同一发件人的类似邮件。</span><span class="sxs-lookup"><span data-stu-id="57ee9-176">Similar messages from the same sender that were delivered to your organization.</span></span>

## <a name="view-information-about-messages-from-impersonated-senders"></a><span data-ttu-id="57ee9-177">查看有关来自模拟发件人的邮件的信息</span><span class="sxs-lookup"><span data-stu-id="57ee9-177">View information about messages from impersonated senders</span></span>

<span data-ttu-id="57ee9-178">在模拟见解上，单击"**模拟的用户"。**</span><span class="sxs-lookup"><span data-stu-id="57ee9-178">On the impersonation insight, click **Users impersonated**.</span></span> <span data-ttu-id="57ee9-179">打开 **的"模拟** 见解"页包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="57ee9-179">The **Impersonation insight** page that opens contains the following information:</span></span>

- <span data-ttu-id="57ee9-180">**发件人**：发送电子邮件的模拟发件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="57ee9-180">**Sender**: The email address of the impersonating sender that sent the email message.</span></span>
- <span data-ttu-id="57ee9-181">**邮件计数**：最近 7 天内来自模拟发件人的邮件数。</span><span class="sxs-lookup"><span data-stu-id="57ee9-181">**Message count**: The number of messages from the impersonating sender over the last 7 days.</span></span>
- <span data-ttu-id="57ee9-182">**模拟类型**：此值为 **User in 显示名称。**</span><span class="sxs-lookup"><span data-stu-id="57ee9-182">**Impersonation type**: This value is **User in display name**.</span></span>
- <span data-ttu-id="57ee9-183">**模拟 (** 用户) ：模拟发件人的电子邮件地址，该地址应该与在反网络钓鱼策略中配置为进行模拟保护的用户非常类似。</span><span class="sxs-lookup"><span data-stu-id="57ee9-183">**Impersonated user(s)**: The email address of the impersonated sender, which should closely resemble the user that's configured for impersonation protection in the anti-phishing policy.</span></span>
- <span data-ttu-id="57ee9-184">**用户类型**：此值显示应用保护 (例如，受保护的用户或邮箱 **智能) 。** </span><span class="sxs-lookup"><span data-stu-id="57ee9-184">**User type**: This value shows the type of protection applied (for example, **Protected user** or **Mailbox Intelligence**).</span></span>
- <span data-ttu-id="57ee9-185">**策略**：检测到模拟发件人的防钓鱼策略。</span><span class="sxs-lookup"><span data-stu-id="57ee9-185">**Policy**: The anti-phishing policy that detected the impersonated sender.</span></span>
- <span data-ttu-id="57ee9-186">**允许模拟**：下列值之一：</span><span class="sxs-lookup"><span data-stu-id="57ee9-186">**Allowed to impersonate**: One of the following values:</span></span>
  - <span data-ttu-id="57ee9-187">**是**：发件人配置为受信任用户 (反垃圾邮件策略中) 的模拟保护例外。</span><span class="sxs-lookup"><span data-stu-id="57ee9-187">**Yes**: The sender was configured as trusted user (an exception for impersonation protection) in the anti-spam policy.</span></span> <span data-ttu-id="57ee9-188">检测到来自模拟发件人的邮件，但允许这些邮件。</span><span class="sxs-lookup"><span data-stu-id="57ee9-188">Messages from the impersonated sender were detected, but allowed.</span></span>
  - <span data-ttu-id="57ee9-189">**否**：发件人配置为在反垃圾邮件策略中提供模拟保护。</span><span class="sxs-lookup"><span data-stu-id="57ee9-189">**No**: The sender was configured for impersonation protection in the anti-spam policy.</span></span> <span data-ttu-id="57ee9-190">根据反垃圾邮件策略中模拟用户的操作，检测并操作来自模拟发件人的邮件。</span><span class="sxs-lookup"><span data-stu-id="57ee9-190">Messages from the impersonated sender were detected and acted upon based on the action for impersonated users in the anti-spam policy.</span></span>

<span data-ttu-id="57ee9-191">您可以单击所选列标题对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="57ee9-191">You can click selected column headings to sort the results.</span></span>

<span data-ttu-id="57ee9-192">若要筛选结果，可以使用"筛选发件人"框输入以逗号分隔的值列表以筛选结果。</span><span class="sxs-lookup"><span data-stu-id="57ee9-192">To filter the results, you can use the **Filter sender** box to enter a comma-separated list of values to filter the results.</span></span>

### <a name="view-details-about-messages-from-impersonated-senders"></a><span data-ttu-id="57ee9-193">查看有关来自模拟发件人的邮件的详细信息</span><span class="sxs-lookup"><span data-stu-id="57ee9-193">View details about messages from impersonated senders</span></span>

<span data-ttu-id="57ee9-194">在" **模拟见解** "页上，选择一个可用行。</span><span class="sxs-lookup"><span data-stu-id="57ee9-194">On the **Impersonation insight** page, select one of the available rows.</span></span> <span data-ttu-id="57ee9-195">显示的详细信息飞出包含以下信息和功能：</span><span class="sxs-lookup"><span data-stu-id="57ee9-195">The details flyout that appears contains the following information and features:</span></span>

- <span data-ttu-id="57ee9-196">**要修改的选择模拟策略**：选择要修改的受影响的防钓鱼策略。</span><span class="sxs-lookup"><span data-stu-id="57ee9-196">**Selection impersonation policy to modify**: Select the affected anti-phishing policy that you want to modify.</span></span> <span data-ttu-id="57ee9-197">只有策略中定义了模拟发件人的策略才可用。</span><span class="sxs-lookup"><span data-stu-id="57ee9-197">Only polices where the impersonated sender is defined in the policy are available.</span></span> <span data-ttu-id="57ee9-198">参考上一页，查看哪个策略实际负责根据收件人 (以及策略的优先级来检测) 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-198">Refer to the previous page to see which policy was actually responsible for detecting the impersonated sender (likely based on the recipient and the priority of the policy).</span></span>

- <span data-ttu-id="57ee9-199">添加到允许 **的** 模拟列表：使用此开关添加或删除所选防钓鱼策略的"受信任的发件人和域 **(** 模拟) 例外"中的发件人：</span><span class="sxs-lookup"><span data-stu-id="57ee9-199">**Add to the allowed to impersonation list**: Use this toggle to add or remove the sender from the **Trusted senders and domains** (impersonation exceptions) for the anti-phishing policy that you selected:</span></span>
  - <span data-ttu-id="57ee9-200">如果 **此条目的"允许模拟** "值为 **"否**"，则开关处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="57ee9-200">If the **Allowed to impersonate** value for this entry was **No**, the toggle is off.</span></span> <span data-ttu-id="57ee9-201">若要通过模拟保护使发件人免于评估，将开关滑动到"打开"： ![ 切换为" 打开 ](../../media/scc-toggle-on.png) "。</span><span class="sxs-lookup"><span data-stu-id="57ee9-201">To exempt the sender from evaluation by impersonation protection, slide the toggle to on: ![Toggle on](../../media/scc-toggle-on.png).</span></span> <span data-ttu-id="57ee9-202">发件人将添加到反 **网络钓鱼** 策略的模拟保护设置中的"受信任的用户"列表中。</span><span class="sxs-lookup"><span data-stu-id="57ee9-202">The sender is added to the **Trusted users** list in the impersonation protection settings of the anti-phishing policy.</span></span>
  - <span data-ttu-id="57ee9-203">如果 **此条目的"允许模拟** "值为 **"是**"，则切换处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="57ee9-203">If the **Allowed to impersonate** value for this entry was **Yes**, the toggle is on.</span></span> <span data-ttu-id="57ee9-204">若要通过模拟保护将发件人返回到评估，将切换开关切换为关闭： ![ 切换关闭 ](../../media/scc-toggle-off.png) 。</span><span class="sxs-lookup"><span data-stu-id="57ee9-204">To return the sender to evaluation by impersonation protection, slide the toggle to off: ![Toggle off](../../media/scc-toggle-off.png).</span></span> <span data-ttu-id="57ee9-205">发件人将从反网络钓鱼策略的模拟保护设置中的"受信任的用户"列表中删除。</span><span class="sxs-lookup"><span data-stu-id="57ee9-205">The sender is removed from the **Trusted users** list in the impersonation protection settings of the anti-phishing policy.</span></span>

- <span data-ttu-id="57ee9-206">我们为什么捕获到此。</span><span class="sxs-lookup"><span data-stu-id="57ee9-206">Why we caught this.</span></span>
- <span data-ttu-id="57ee9-207">需要执行哪些工作。</span><span class="sxs-lookup"><span data-stu-id="57ee9-207">What you need to do.</span></span>
- <span data-ttu-id="57ee9-208">列出模拟发件人的发件人摘要。</span><span class="sxs-lookup"><span data-stu-id="57ee9-208">A sender summary that list the impersonated sender.</span></span>
- <span data-ttu-id="57ee9-209">WhoIs 有关发件人的数据。</span><span class="sxs-lookup"><span data-stu-id="57ee9-209">WhoIs data about the sender.</span></span>
- <span data-ttu-id="57ee9-210">打开威胁资源管理器 [以查看有关](threat-explorer.md) 发件人的其他详细信息的链接。</span><span class="sxs-lookup"><span data-stu-id="57ee9-210">A link to open [Threat Explorer](threat-explorer.md) to see additional details about the sender.</span></span>
- <span data-ttu-id="57ee9-211">来自已传递到组织的同一发件人的类似邮件。</span><span class="sxs-lookup"><span data-stu-id="57ee9-211">Similar messages from the same sender that were delivered to your organization.</span></span>