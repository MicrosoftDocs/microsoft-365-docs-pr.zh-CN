---
title: 启用报告邮件或报告钓鱼外接程序
f1.keywords:
- NOCSH
ms.author: siosulli
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: 了解如何为单个用户或整个组织启用 Outlook 和 Outlook 网页版 报告邮件或报告网络钓鱼外接程序。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d5e336dcab9e3787d8c5245cdbe32855c59021f7
ms.sourcegitcommit: cd55fe6abe25b1e4f5fbe8295d3a99aebd97ce66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2021
ms.locfileid: "53082764"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a><span data-ttu-id="c60b3-103">启用报告邮件或报告钓鱼外接程序</span><span class="sxs-lookup"><span data-stu-id="c60b3-103">Enable the Report Message or the Report Phishing add-ins</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="c60b3-104">**适用对象**</span><span class="sxs-lookup"><span data-stu-id="c60b3-104">**Applies to**</span></span>
- [<span data-ttu-id="c60b3-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="c60b3-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="c60b3-106">Microsoft Defender for Office 365 计划 1 和计划 2</span><span class="sxs-lookup"><span data-stu-id="c60b3-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="c60b3-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="c60b3-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

> [!NOTE]
> <span data-ttu-id="c60b3-108">如果你是拥有邮箱的 Microsoft 365 组织的管理员Exchange Online，我们建议你使用 Microsoft 365 Defender 页面。 </span><span class="sxs-lookup"><span data-stu-id="c60b3-108">If you're an admin in a Microsoft 365 organization with Exchange Online mailboxes, we recommend that you use the **Submissions** page in the Microsoft 365 Defender portal.</span></span> <span data-ttu-id="c60b3-109">有关详细信息，请参阅使用[管理员提交将可疑的垃圾邮件、网络钓鱼、URL 和文件提交到 Microsoft。](admin-submission.md)</span><span class="sxs-lookup"><span data-stu-id="c60b3-109">For more information, see [Use Admin Submission to submit suspected spam, phish, URLs, and files to Microsoft](admin-submission.md).</span></span>

<span data-ttu-id="c60b3-110">Outlook 和 Outlook 网页版 (的"报告邮件"和"报告网络钓鱼"外接程序（以前称为 Outlook Web App) ）使用户能够轻松地将误报 (错误电子邮件报告为错误) 或漏报 (允许) 向 Microsoft 及其关联公司进行分析。</span><span class="sxs-lookup"><span data-stu-id="c60b3-110">The Report Message and Report Phishing add-ins for Outlook and Outlook on the web (formerly known as Outlook Web App) enable people to easily report false positives (good email marked as bad) or false negatives (bad email allowed) to Microsoft and its affiliates for analysis.</span></span>

<span data-ttu-id="c60b3-111">Microsoft 使用这些提交来提高电子邮件保护技术的有效性。</span><span class="sxs-lookup"><span data-stu-id="c60b3-111">Microsoft uses these submissions to improve the effectiveness of email protection technologies.</span></span> <span data-ttu-id="c60b3-112">例如，假设用户正在使用报告网络钓鱼外接程序报告许多邮件。</span><span class="sxs-lookup"><span data-stu-id="c60b3-112">For example, suppose that people are reporting many messages using the Report Phishing add-in.</span></span> <span data-ttu-id="c60b3-113">此信息在安全仪表板和其他报告中显示。</span><span class="sxs-lookup"><span data-stu-id="c60b3-113">This information surfaces in the Security Dashboard and other reports.</span></span> <span data-ttu-id="c60b3-114">组织的安全团队可以使用此信息指示可能需要更新反网络钓鱼策略。</span><span class="sxs-lookup"><span data-stu-id="c60b3-114">Your organization's security team can use this information as an indication that anti-phishing policies might need to be updated.</span></span>

<span data-ttu-id="c60b3-115">可以安装"报告邮件"或"报告钓鱼邮件"加载项。</span><span class="sxs-lookup"><span data-stu-id="c60b3-115">You can install either the Report Message or Report Phishing add-in.</span></span> <span data-ttu-id="c60b3-116">如果希望用户同时报告垃圾邮件和网络钓鱼邮件，请在你的组织中部署报告邮件外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-116">If you want your users to report both spam and phishing messages, deploy the Report Message add-in in your organization.</span></span> <span data-ttu-id="c60b3-117">有关详细信息，请参阅启用报告邮件外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-117">For more information, see Enable the Report Message add-in.</span></span>

<span data-ttu-id="c60b3-118">报告邮件外接程序提供报告垃圾邮件和网络钓鱼邮件的选项。</span><span class="sxs-lookup"><span data-stu-id="c60b3-118">The Report Message add-in provides the option to report both spam and phishing messages.</span></span> <span data-ttu-id="c60b3-119">管理员可以为组织启用"报告邮件"外接程序，并且各个用户可以自行安装它。</span><span class="sxs-lookup"><span data-stu-id="c60b3-119">Admins can enable the Report Message add-in for the organization, and individual users can install it for themselves.</span></span>

<span data-ttu-id="c60b3-120">报告网络钓鱼外接程序提供仅报告网络钓鱼邮件的选项。</span><span class="sxs-lookup"><span data-stu-id="c60b3-120">The Report Phishing add-in provides the option to report only phishing messages.</span></span> <span data-ttu-id="c60b3-121">管理员可以为组织启用报告网络钓鱼外接程序，并且单个用户可以自行安装它。</span><span class="sxs-lookup"><span data-stu-id="c60b3-121">Admins can enable the Report Phishing add-in for the organization, and individual users can install it for themselves.</span></span>

<span data-ttu-id="c60b3-122">如果您是单个用户，您可以为自己启用这两个外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-122">If you're an individual user, you can enable both the add-ins for yourself.</span></span>

<span data-ttu-id="c60b3-123">如果您是全局管理员或 Exchange Online 管理员，并且 Exchange 配置为使用 OAuth 身份验证，您可以为组织启用"报告邮件"外接程序和"报告网络钓鱼"外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-123">If you're a global administrator or an Exchange Online administrator, and Exchange is configured to use OAuth authentication, you can enable the Report Message add-in and the Report Phishing add-in for your organization.</span></span> <span data-ttu-id="c60b3-124">这两个加载项现在都可以通过集中 [部署获得](../../admin/manage/centralized-deployment-of-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="c60b3-124">Both add-ins are now available through [Centralized Deployment](../../admin/manage/centralized-deployment-of-add-ins.md).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c60b3-125">开始前，需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="c60b3-125">What do you need to know before you begin?</span></span>

- <span data-ttu-id="c60b3-126">报告邮件外接程序和报告网络钓鱼外接程序适用于大多数Microsoft 365订阅和以下产品：</span><span class="sxs-lookup"><span data-stu-id="c60b3-126">Both the Report Message add-in and the Report Phishing add-in works with most Microsoft 365 subscriptions and the following products:</span></span>
  - <span data-ttu-id="c60b3-127">Outlook 网页版</span><span class="sxs-lookup"><span data-stu-id="c60b3-127">Outlook on the web</span></span>
  - <span data-ttu-id="c60b3-128">Outlook 2013 SP1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="c60b3-128">Outlook 2013 SP1 or later</span></span>
  - <span data-ttu-id="c60b3-129">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="c60b3-129">Outlook 2016 for Mac</span></span>
  - <span data-ttu-id="c60b3-130">Outlook应用程序Microsoft 365中包含的Enterprise</span><span class="sxs-lookup"><span data-stu-id="c60b3-130">Outlook included with Microsoft 365 apps for Enterprise</span></span>
  - <span data-ttu-id="c60b3-131">Outlook iOS 和 Android 版应用</span><span class="sxs-lookup"><span data-stu-id="c60b3-131">Outlook app for iOS and Android</span></span>

- <span data-ttu-id="c60b3-132">这两个外接程序均不适用于共享邮箱或内部部署组织Exchange邮箱。</span><span class="sxs-lookup"><span data-stu-id="c60b3-132">Both add-ins are not available for shared mailboxes or mailboxes in on-premises Exchange organizations.</span></span>

- <span data-ttu-id="c60b3-133">现有的 Web 浏览器应同时使用报告邮件和报告钓鱼外接程序。但是，如果您注意到外接程序不可用或未正常工作，请尝试其他浏览器。</span><span class="sxs-lookup"><span data-stu-id="c60b3-133">Your existing web browser should work with both the Report Message and Report Phishing add-ins. But, if you notice the add-in is not available or not working as expected, try a different browser.</span></span>

- <span data-ttu-id="c60b3-134">对于组织安装，组织需要配置为使用 OAuth 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c60b3-134">For organizational installs, the organization needs to be configured to use OAuth authentication.</span></span> <span data-ttu-id="c60b3-135">有关详细信息，请参阅确定加载项的集中部署 [是否适用于你的组织](../../admin/manage/centralized-deployment-of-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="c60b3-135">For more information, see [Determine if Centralized Deployment of add-ins works for your organization](../../admin/manage/centralized-deployment-of-add-ins.md).</span></span>

- <span data-ttu-id="c60b3-136">管理员需为全局管理员角色组的成员。</span><span class="sxs-lookup"><span data-stu-id="c60b3-136">Admins need to be a member of the Global admins role group.</span></span> <span data-ttu-id="c60b3-137">有关详细信息，请参阅 [Microsoft 365 Defender 门户中的权限](permissions-microsoft-365-security-center.md)。</span><span class="sxs-lookup"><span data-stu-id="c60b3-137">For more information, see [Permissions in the Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).</span></span>

- <span data-ttu-id="c60b3-138">有关如何使用"报告邮件"功能报告邮件的信息，请参阅报告邮件中的误报和[Outlook。](report-false-positives-and-false-negatives.md)</span><span class="sxs-lookup"><span data-stu-id="c60b3-138">For more information on how to report a message using the Report Message feature, see [Report false positives and false negatives in Outlook](report-false-positives-and-false-negatives.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c60b3-139">我们不建议在应用内使用内置Outlook，因为它不使用用户[提交策略](./user-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="c60b3-139">We don't recommend the built-in reporting experience in Outlook because it can't use the [user submission policy](./user-submission.md).</span></span> <span data-ttu-id="c60b3-140">我们建议改为使用报告邮件外接程序或报告网络钓鱼外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-140">We recommend using the Report Message add-in or the Report Phishing add-in instead.</span></span>

## <a name="get-the-report-message-add-in"></a><span data-ttu-id="c60b3-141">获取报告邮件外接程序</span><span class="sxs-lookup"><span data-stu-id="c60b3-141">Get the Report Message add-in</span></span>

### <a name="get-the-report-message-add-in-for-yourself"></a><span data-ttu-id="c60b3-142">为自己获取报告邮件外接程序</span><span class="sxs-lookup"><span data-stu-id="c60b3-142">Get the Report Message add-in for yourself</span></span>

1. <span data-ttu-id="c60b3-143">转到 Microsoft AppSource ， <https://appsource.microsoft.com/marketplace/apps> 然后搜索"报告消息"加载项。</span><span class="sxs-lookup"><span data-stu-id="c60b3-143">Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Message add-in.</span></span> <span data-ttu-id="c60b3-144">若要直接转到"报告邮件"加载项，请转到 <https://appsource.microsoft.com/product/office/wa104381180> 。</span><span class="sxs-lookup"><span data-stu-id="c60b3-144">To go directly to the Report Message add-in, go to <https://appsource.microsoft.com/product/office/wa104381180>.</span></span>

2. <span data-ttu-id="c60b3-145">单击 **"立即获取"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-145">Click **GET IT NOW**.</span></span>

   ![报告邮件 - 现在获取](../../media/ReportMessageGETITNOW.png)

3. <span data-ttu-id="c60b3-147">在出现的对话框中，查看使用条款和隐私策略，然后单击"继续 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-147">In the dialog that appears, review the terms of use and privacy policy, and then click **Continue**.</span></span>

4. <span data-ttu-id="c60b3-148">使用工作或学校帐户登录 (商业用途) Microsoft 帐户 (供个人) 。</span><span class="sxs-lookup"><span data-stu-id="c60b3-148">Sign in using your work or school account (for business use) or your Microsoft account (for personal use).</span></span>

<span data-ttu-id="c60b3-149">安装并启用加载项后，你将看到以下图标：</span><span class="sxs-lookup"><span data-stu-id="c60b3-149">After the add-in is installed and enabled, you'll see the following icons:</span></span>

- <span data-ttu-id="c60b3-150">在Outlook中，图标如下所示：</span><span class="sxs-lookup"><span data-stu-id="c60b3-150">In Outlook, the icon looks like this:</span></span>

  > [!div class="mx-imgBorder"]
  > <span data-ttu-id="c60b3-151">![报告邮件外接程序图标的 Outlook](../../media/OutlookReportMessageIcon.png)</span><span class="sxs-lookup"><span data-stu-id="c60b3-151">![Report Message add-in icon for Outlook](../../media/OutlookReportMessageIcon.png)</span></span>

- <span data-ttu-id="c60b3-152">在Outlook 网页版中，图标如下所示：</span><span class="sxs-lookup"><span data-stu-id="c60b3-152">In Outlook on the web, the icon looks like this:</span></span>

  > [!div class="mx-imgBorder"]
  > <span data-ttu-id="c60b3-153">![Outlook 网页版"报告邮件"加载项图标](../../media/owa-report-message-icon.png)</span><span class="sxs-lookup"><span data-stu-id="c60b3-153">![Outlook on the web Report Message add-in icon](../../media/owa-report-message-icon.png)</span></span>

### <a name="get-the-report-message-add-in-for-your-organization"></a><span data-ttu-id="c60b3-154">获取组织的"报告邮件"加载项</span><span class="sxs-lookup"><span data-stu-id="c60b3-154">Get the Report Message add-in for your organization</span></span>

> [!NOTE]
> <span data-ttu-id="c60b3-155">外接程序可能需要 12 个小时才能显示在组织中。</span><span class="sxs-lookup"><span data-stu-id="c60b3-155">It could take up to 12 hours for the add-in to appear in your organization.</span></span>

1. <span data-ttu-id="c60b3-156">在Microsoft 365 管理中心中，转到设置 \> **外接程序"** 页 <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> 。</span><span class="sxs-lookup"><span data-stu-id="c60b3-156">In the Microsoft 365 admin center, go to the **Settings** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>.</span></span> <span data-ttu-id="c60b3-157">如果看不到"加载项"页面，请转到"**集成** 应用"设置顶部的"集成应用加载项 \>  \> **"** 链接。</span><span class="sxs-lookup"><span data-stu-id="c60b3-157">If you don't see the **Add-in** Page, go to the **Settings** \> **Integrated apps** \> **Add-ins** link on the top of the **Integrated apps** page.</span></span>

2. <span data-ttu-id="c60b3-158">选择 **页面顶部的"** 部署外接程序"，然后选择"下一步 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-158">Select **Deploy Add-in** at the top of the page, and then select **Next**.</span></span>

   ![外接程序页中的"服务和外接程序Microsoft 365 管理中心](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. <span data-ttu-id="c60b3-160">在出现的 **"部署新的外接程序"** 飞出中，查看信息，然后单击"下一步 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-160">In the **Deploy a new add-in** flyout that appears, review the information, and then click **Next**.</span></span>

4. <span data-ttu-id="c60b3-161">下一页上，单击 **从应用商店中选择**。</span><span class="sxs-lookup"><span data-stu-id="c60b3-161">On the next page, click **Choose from the Store**.</span></span>

   ![部署新的外接程序页面](../../media/NewAddInScreen2.png)

5. <span data-ttu-id="c60b3-163">在出现的 **"选择外接程序"** 页中，单击"搜索"框中，输入"**报告** 邮件"，然后单击"**搜索搜索"** ![ 图标 ](../../media/search-icon.png) 。</span><span class="sxs-lookup"><span data-stu-id="c60b3-163">In the **Select add-in** page that appears, click in the **Search** box, enter **Report Message**, and then click **Search** ![Search icon](../../media/search-icon.png).</span></span> <span data-ttu-id="c60b3-164">在结果列表中，找到"**报告邮件**"，然后单击"添加 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-164">In the list of results, find **Report Message** and then click **Add**.</span></span>

   ![选择外接程序搜索结果](../../media/NewAddInScreen3.png)

6. <span data-ttu-id="c60b3-166">在出现的对话框中，查看许可和隐私信息，然后单击"继续 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-166">In the dialog that appears, review the licensing and privacy information, and then click **Continue**.</span></span>

7. <span data-ttu-id="c60b3-167">在 **出现的"配置外接程序"** 页中，配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="c60b3-167">In the **Configure add-in** page that appears, configure the following settings:</span></span>

   - <span data-ttu-id="c60b3-168">**已分配用户**：选择下列值之一：</span><span class="sxs-lookup"><span data-stu-id="c60b3-168">**Assigned users**: Select one of the following values:</span></span>
     - <span data-ttu-id="c60b3-169">**每个人都** (默认) </span><span class="sxs-lookup"><span data-stu-id="c60b3-169">**Everyone** (default)</span></span>
     - <span data-ttu-id="c60b3-170">**特定用户/组**</span><span class="sxs-lookup"><span data-stu-id="c60b3-170">**Specific users / groups**</span></span>
     - <span data-ttu-id="c60b3-171">**就我自己**</span><span class="sxs-lookup"><span data-stu-id="c60b3-171">**Just me**</span></span>

   - <span data-ttu-id="c60b3-172">**部署方法**：选择下列值之一：</span><span class="sxs-lookup"><span data-stu-id="c60b3-172">**Deployment method**: Select one of the following values:</span></span>
     - <span data-ttu-id="c60b3-173">**修复 (默认) ：** 加载项会自动部署到指定用户，且无法删除。</span><span class="sxs-lookup"><span data-stu-id="c60b3-173">**Fixed (Default)**: The add-in is automatically deployed to the specified users and they can't remove it.</span></span>
     - <span data-ttu-id="c60b3-174">**可用**：用户可以在"主页""获取加载项 \> **""管理员管理**" \> **中安装加载项**。</span><span class="sxs-lookup"><span data-stu-id="c60b3-174">**Available**: Users can install the add-in at **Home** \> **Get add-ins** \> **Admin-managed**.</span></span>
     - <span data-ttu-id="c60b3-175">**可选**：外接程序将自动部署到指定用户，但他们可以选择将其删除。</span><span class="sxs-lookup"><span data-stu-id="c60b3-175">**Optional**: The add-in is automatically deployed to the specified users, but they can choose to remove it.</span></span>

   ![配置外接程序页面](../../media/configure-add-in.png)

   <span data-ttu-id="c60b3-177">完成后，单击"部署 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-177">When you're finished, click **Deploy**.</span></span>

8. <span data-ttu-id="c60b3-178">在 **出现的"** 部署报告消息"页中，你将看到一个进度报告，然后确认外接程序已部署。</span><span class="sxs-lookup"><span data-stu-id="c60b3-178">In the **Deploy Report Message** page that appears, you'll see a progress report followed by a confirmation that the add-in was deployed.</span></span> <span data-ttu-id="c60b3-179">阅读信息后，单击"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-179">After you read the information, click **Next**.</span></span>

   !["部署报告消息"页](../../media/deploy-report-message-page.png)

9. <span data-ttu-id="c60b3-181">在出现的 **"宣布外接程序"** 页上，查看信息，然后单击"关闭 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-181">On the **Announce add-in** page that appears, review the information, and then click **Close**.</span></span>

   !["宣布外接程序"页](../../media/announce-add-in-page.png)

## <a name="review-or-edit-settings-for-the-report-message-add-in"></a><span data-ttu-id="c60b3-183">查看或编辑报告邮件外接程序的设置</span><span class="sxs-lookup"><span data-stu-id="c60b3-183">Review or edit settings for the Report Message add-in</span></span>

1. <span data-ttu-id="c60b3-184">In the Microsoft 365 管理中心， go to the go to the **设置** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> .</span><span class="sxs-lookup"><span data-stu-id="c60b3-184">In the Microsoft 365 admin center, go to the go to the **Settings** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>.</span></span> <span data-ttu-id="c60b3-185">如果看不到"加载项"页面，请转到"**集成** 应用"设置顶部的"集成应用加载项 \>  \> **"** 链接。</span><span class="sxs-lookup"><span data-stu-id="c60b3-185">If you don't see the **Add-in** Page, go to the **Settings** \> **Integrated apps** \> **Add-ins** link on the top of the **Integrated apps** page.</span></span>

   ![新Add-Ins中心中的"服务和Microsoft 365 管理页面](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. <span data-ttu-id="c60b3-187">查找并选择 **"报告邮件** "外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-187">Find and select the **Report Message** add-in.</span></span>

3. <span data-ttu-id="c60b3-188">在出现的 **"编辑报告** 消息"飞出控件中，根据组织情况查看和编辑设置。</span><span class="sxs-lookup"><span data-stu-id="c60b3-188">In the **Edit Report Message** flyout that appears, review and edit settings as appropriate for your organization.</span></span> <span data-ttu-id="c60b3-189">完成后，单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="c60b3-189">When you're finished, click **Save**.</span></span>

   ![设置邮件外接程序的外接程序](../../media/EditReportMessageAddIn.png)

## <a name="get-the-report-phishing-add-in"></a><span data-ttu-id="c60b3-191">获取报告网络钓鱼外接程序</span><span class="sxs-lookup"><span data-stu-id="c60b3-191">Get the Report Phishing add-in</span></span>

### <a name="get-the-report-phishing-add-in-for-yourself"></a><span data-ttu-id="c60b3-192">为自己获取报告网络钓鱼外接程序</span><span class="sxs-lookup"><span data-stu-id="c60b3-192">Get the Report Phishing add-in for yourself</span></span>

1. <span data-ttu-id="c60b3-193">转到 Microsoft AppSource， <https://appsource.microsoft.com/marketplace/apps> 然后搜索"报告钓鱼"加载项。</span><span class="sxs-lookup"><span data-stu-id="c60b3-193">Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Phishing add-in.</span></span>

2. <span data-ttu-id="c60b3-194">单击 **"立即获取"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-194">Click **GET IT NOW**.</span></span>

3. <span data-ttu-id="c60b3-195">在出现的对话框中，查看使用条款和隐私策略，然后单击"继续 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-195">In the dialog that appears, review the terms of use and privacy policy, and then click **Continue**.</span></span>

4. <span data-ttu-id="c60b3-196">使用工作或学校帐户登录 (商业用途) Microsoft 帐户 (供个人) 。</span><span class="sxs-lookup"><span data-stu-id="c60b3-196">Sign in using your work or school account (for business use) or your Microsoft account (for personal use).</span></span>

<span data-ttu-id="c60b3-197">安装并启用加载项后，你将看到以下图标：</span><span class="sxs-lookup"><span data-stu-id="c60b3-197">After the add-in is installed and enabled, you'll see the following icons:</span></span>

- <span data-ttu-id="c60b3-198">在Outlook中，图标如下所示：</span><span class="sxs-lookup"><span data-stu-id="c60b3-198">In Outlook, the icon looks like this:</span></span>

  ![报告电子邮件的网络钓鱼外接程序Outlook](../../media/Outlook-ReportPhishing.png)

- <span data-ttu-id="c60b3-200">在Outlook 网页版中，图标如下所示：</span><span class="sxs-lookup"><span data-stu-id="c60b3-200">In Outlook on the web, the icon looks like this:</span></span>

  > [!div class="mx-imgBorder"]
  > <span data-ttu-id="c60b3-201">![Outlook 网页版报告网络钓鱼外接程序图标](../../media/OWA-ReportPhishing.png)</span><span class="sxs-lookup"><span data-stu-id="c60b3-201">![Outlook on the web Report Phishing add-in icon](../../media/OWA-ReportPhishing.png)</span></span>

### <a name="get-the-report-phishing-add-in-for-your-organization"></a><span data-ttu-id="c60b3-202">获取组织的"报告网络钓鱼"外接程序</span><span class="sxs-lookup"><span data-stu-id="c60b3-202">Get the Report Phishing add-in for your organization</span></span>

> [!NOTE]
> <span data-ttu-id="c60b3-203">外接程序可能需要 12 个小时才能显示在组织中。</span><span class="sxs-lookup"><span data-stu-id="c60b3-203">It could take up to 12 hours for the add-in to appear in your organization.</span></span>

1. <span data-ttu-id="c60b3-204">In the Microsoft 365 管理中心， go to the go to the **设置** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> .</span><span class="sxs-lookup"><span data-stu-id="c60b3-204">In the Microsoft 365 admin center, go to the go to the **Settings** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>.</span></span> <span data-ttu-id="c60b3-205">如果看不到"加载项"页面，请转到"**集成** 应用"设置顶部的"集成应用加载项 \>  \> **"** 链接。</span><span class="sxs-lookup"><span data-stu-id="c60b3-205">If you don't see the **Add-in** Page, go to the **Settings** \> **Integrated apps** \> **Add-ins** link on the top of the **Integrated apps** page.</span></span>

2. <span data-ttu-id="c60b3-206">选择 **页面顶部的"** 部署外接程序"，然后选择"下一步 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-206">Select **Deploy Add-in** at the top of the page, and then select **Next**.</span></span>

   ![外接程序页中的"服务和外接程序Microsoft 365 管理中心](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. <span data-ttu-id="c60b3-208">在出现的 **"部署新的外接程序"** 飞出中，查看信息，然后单击"下一步 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-208">In the **Deploy a new add-in** flyout that appears, review the information, and then click **Next**.</span></span>

4. <span data-ttu-id="c60b3-209">下一页上，单击 **从应用商店中选择**。</span><span class="sxs-lookup"><span data-stu-id="c60b3-209">On the next page, click **Choose from the Store**.</span></span>

   ![部署新的外接程序页面](../../media/NewAddInScreen2.png)

5. <span data-ttu-id="c60b3-211">在出现的 **"选择外接程序"** 页中，单击"搜索"框中，输入"**报告网络钓鱼"，** 然后单击"**搜索搜索"** ![ 图标 ](../../media/search-icon.png) 。</span><span class="sxs-lookup"><span data-stu-id="c60b3-211">In the **Select add-in** page that appears, click in the **Search** box, enter **Report Phishing**, and then click **Search** ![Search icon](../../media/search-icon.png).</span></span> <span data-ttu-id="c60b3-212">在结果列表中，找到"**报告网络钓鱼"，** 然后单击"添加 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-212">In the list of results, find **Report Phishing** and then click **Add**.</span></span>

6. <span data-ttu-id="c60b3-213">在出现的对话框中，查看许可和隐私信息，然后单击"继续 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-213">In the dialog that appears, review the licensing and privacy information, and then click **Continue**.</span></span>

7. <span data-ttu-id="c60b3-214">在 **出现的"配置外接程序"** 页中，配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="c60b3-214">In the **Configure add-in** page that appears, configure the following settings:</span></span>

   - <span data-ttu-id="c60b3-215">**已分配用户**：选择下列值之一：</span><span class="sxs-lookup"><span data-stu-id="c60b3-215">**Assigned users**: Select one of the following values:</span></span>
     - <span data-ttu-id="c60b3-216">**每个人都** (默认) </span><span class="sxs-lookup"><span data-stu-id="c60b3-216">**Everyone** (default)</span></span>
     - <span data-ttu-id="c60b3-217">**特定用户/组**</span><span class="sxs-lookup"><span data-stu-id="c60b3-217">**Specific users / groups**</span></span>
     - <span data-ttu-id="c60b3-218">**就我自己**</span><span class="sxs-lookup"><span data-stu-id="c60b3-218">**Just me**</span></span>

   - <span data-ttu-id="c60b3-219">**部署方法**：选择下列值之一：</span><span class="sxs-lookup"><span data-stu-id="c60b3-219">**Deployment method**: Select one of the following values:</span></span>
     - <span data-ttu-id="c60b3-220">**修复 (默认) ：** 加载项会自动部署到指定用户，且无法删除。</span><span class="sxs-lookup"><span data-stu-id="c60b3-220">**Fixed (Default)**: The add-in is automatically deployed to the specified users and they can't remove it.</span></span>
     - <span data-ttu-id="c60b3-221">**可用**：用户可以在"主页""获取加载项 \> **""管理员管理**" \> **中安装加载项**。</span><span class="sxs-lookup"><span data-stu-id="c60b3-221">**Available**: Users can install the add-in at **Home** \> **Get add-ins** \> **Admin-managed**.</span></span>
     - <span data-ttu-id="c60b3-222">**可选**：外接程序将自动部署到指定用户，但他们可以选择将其删除。</span><span class="sxs-lookup"><span data-stu-id="c60b3-222">**Optional**: The add-in is automatically deployed to the specified users, but they can choose to remove it.</span></span>

   <span data-ttu-id="c60b3-223">完成后，单击"部署 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-223">When you're finished, click **Deploy**.</span></span>

8. <span data-ttu-id="c60b3-224">在 **出现的"部署** 报告网络钓鱼"页中，你将看到一个进度报告，然后确认外接程序已部署。</span><span class="sxs-lookup"><span data-stu-id="c60b3-224">In the **Deploy Report Phishing** page that appears, you'll see a progress report followed by a confirmation that the add-in was deployed.</span></span> <span data-ttu-id="c60b3-225">阅读信息后，单击"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-225">After you read the information, click **Next**.</span></span>

9. <span data-ttu-id="c60b3-226">在出现的 **"宣布外接程序"** 页上，查看信息，然后单击"关闭 **"。**</span><span class="sxs-lookup"><span data-stu-id="c60b3-226">On the **Announce add-in** page that appears, review the information, and then click **Close**.</span></span>

## <a name="review-or-edit-settings-for-the-report-phishing-add-in"></a><span data-ttu-id="c60b3-227">查看或编辑报告网络钓鱼外接程序的设置</span><span class="sxs-lookup"><span data-stu-id="c60b3-227">Review or edit settings for the Report Phishing add-in</span></span>

1. <span data-ttu-id="c60b3-228">In the Microsoft 365 管理中心， go to the go to the **设置** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> .</span><span class="sxs-lookup"><span data-stu-id="c60b3-228">In the Microsoft 365 admin center, go to the go to the **Settings** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>.</span></span> <span data-ttu-id="c60b3-229">如果看不到"加载项"页面，请转到"**集成** 应用"设置顶部的"集成应用加载项 \>  \> **"** 链接。</span><span class="sxs-lookup"><span data-stu-id="c60b3-229">If you don't see the **Add-in** Page, go to the **Settings** \> **Integrated apps** \> **Add-ins** link on the top of the **Integrated apps** page.</span></span>

2. <span data-ttu-id="c60b3-230">查找并选择报告 **网络钓鱼** 外接程序。</span><span class="sxs-lookup"><span data-stu-id="c60b3-230">Find and select the **Report Phishing** add-in.</span></span>

3. <span data-ttu-id="c60b3-231">在出现的 **"编辑报告** 钓鱼"飞出控件中，查看和编辑适合你的组织的设置。</span><span class="sxs-lookup"><span data-stu-id="c60b3-231">In the **Edit Report Phishing** flyout that appears, review, and edit settings as appropriate for your organization.</span></span> <span data-ttu-id="c60b3-232">完成后，单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="c60b3-232">When you're finished, click **Save**.</span></span>
