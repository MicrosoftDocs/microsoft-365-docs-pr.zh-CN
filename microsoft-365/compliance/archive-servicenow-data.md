---
title: 设置连接器以在 Microsoft 365 中存档 ServiceNow 数据
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: 管理员可以设置连接器以将 ServiceNow 数据从 Globanet 导入和存档到 Microsoft 365。 此连接器允许你在 Microsoft 365 中存档来自第三方数据源的数据。 存档此数据后，可以使用合规性功能（如法定保留、内容搜索和保留策略）管理第三方数据。
ms.openlocfilehash: 99b1f64bdb1d977816d4881fa633d77acd60952c
ms.sourcegitcommit: 36d12e02f6fda199ae7f2fb72fe52d7e2b5b4efd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740329"
---
# <a name="set-up-a-connector-to-archive-servicenow-data"></a><span data-ttu-id="a2298-105">设置连接器以存档 ServiceNow 数据</span><span class="sxs-lookup"><span data-stu-id="a2298-105">Set up a connector to archive ServiceNow data</span></span>

<span data-ttu-id="a2298-106">使用 Microsoft 365 合规中心中的 Globanet 连接器，将数据从 ServiceNow 平台导入并存档到 Microsoft 365 组织的用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="a2298-106">Use a Globanet connector in the Microsoft 365 compliance center to import and archive data from the ServiceNow platform to user mailboxes in your Microsoft 365 organization.</span></span> <span data-ttu-id="a2298-107">Globanet 提供了 [一个 ServiceNow](https://globanet.com/servicenow/) 连接器，可捕获第三方数据源中的项目，并导入到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="a2298-107">Globanet provides a [ServiceNow](https://globanet.com/servicenow/) connector that captures items from the third-party data source and import those items to Microsoft 365.</span></span> <span data-ttu-id="a2298-108">连接器将实时邮件、附件和帖子等内容从 ServiceNow 转换为电子邮件格式，然后将这些项目导入 Microsoft 365 中的用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="a2298-108">The connector converts the content such as live messages, attachments, and posts from ServiceNow to an email message format and then imports those items to user mailboxes in Microsoft 365.</span></span>

<span data-ttu-id="a2298-109">将 ServiceNow 数据存储在用户邮箱中后，可以应用 Microsoft 365 合规性功能，如诉讼保留、电子数据展示、保留策略和保留标签。</span><span class="sxs-lookup"><span data-stu-id="a2298-109">After ServiceNow data is stored in user mailboxes, you can apply Microsoft 365 compliance features such as Litigation Hold, eDiscovery, retention policies, and retention labels.</span></span> <span data-ttu-id="a2298-110">使用 ServiceNow 连接器在 Microsoft 365 中导入和存档数据可帮助组织遵守政府法规策略。</span><span class="sxs-lookup"><span data-stu-id="a2298-110">Using a ServiceNow connector to import and archive data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

## <a name="overview-of-archiving-servicenow-data"></a><span data-ttu-id="a2298-111">存档 ServiceNow 数据概述</span><span class="sxs-lookup"><span data-stu-id="a2298-111">Overview of archiving ServiceNow data</span></span>

<span data-ttu-id="a2298-112">以下概述介绍了使用连接器在 Microsoft 365 中存档 ServiceNow 数据的过程。</span><span class="sxs-lookup"><span data-stu-id="a2298-112">The following overview explains the process of using a connector to archive the ServiceNow data in Microsoft 365.</span></span>

![ServiceNow 数据的存档工作流](../media/ServiceNowConnectorWorkflow.png)

1. <span data-ttu-id="a2298-114">您的组织与 ServiceNow 一起设置和配置 ServiceNow 网站。</span><span class="sxs-lookup"><span data-stu-id="a2298-114">Your organization works with ServiceNow to set up and configure a ServiceNow site.</span></span>

2. <span data-ttu-id="a2298-115">每 24 小时一次，ServiceNow 项目将复制到 Globanet Merge1 网站。</span><span class="sxs-lookup"><span data-stu-id="a2298-115">Once every 24 hours, ServiceNow items are copied to the Globanet Merge1 site.</span></span> <span data-ttu-id="a2298-116">连接器还会将 ServiceNow 项目转换为电子邮件格式。</span><span class="sxs-lookup"><span data-stu-id="a2298-116">The connector also converts ServiceNow items to an email message format.</span></span>

3. <span data-ttu-id="a2298-117">在 Microsoft 365 合规中心创建的 ServiceNow 连接器每天连接到 Globanet Merge1 网站，将 ServiceNow 内容转移到 Microsoft 云中安全的 Azure 存储位置。</span><span class="sxs-lookup"><span data-stu-id="a2298-117">The ServiceNow connector that you create in the Microsoft 365 compliance center connects to the Globanet Merge1 site every day and transfers the ServiceNow content to a secure Azure Storage location in the Microsoft cloud.</span></span>

4. <span data-ttu-id="a2298-118">连接器使用自动用户映射的 *Email* 属性值将转换的项目导入到特定用户的邮箱，如步骤 [3 中所述](#step-3-map-users-and-complete-the-connector-setup)。</span><span class="sxs-lookup"><span data-stu-id="a2298-118">The connector imports the converted items to the mailboxes of specific users using the value of the *Email* property of the automatic user mapping as described in [Step 3](#step-3-map-users-and-complete-the-connector-setup).</span></span> <span data-ttu-id="a2298-119">在用户邮箱中创建名为 **ServiceNow** 的收件箱文件夹中的子文件夹，项目将导入到该文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a2298-119">A subfolder in the Inbox folder named **ServiceNow** is created in the user mailboxes, and items are imported to that folder.</span></span> <span data-ttu-id="a2298-120">连接器使用 Email 属性的值确定将项目导入到哪个 *邮箱* 。</span><span class="sxs-lookup"><span data-stu-id="a2298-120">The connector determines which mailbox to import items to by using the value of the *Email* property.</span></span> <span data-ttu-id="a2298-121">每个 ServiceNow 项都包含此属性，该属性用项目每个参与者的电子邮件地址填充。</span><span class="sxs-lookup"><span data-stu-id="a2298-121">Every ServiceNow item contains this property, which is populated with the email address of every participant of the item.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="a2298-122">准备工作</span><span class="sxs-lookup"><span data-stu-id="a2298-122">Before you begin</span></span>

- <span data-ttu-id="a2298-123">为 Microsoft 连接器创建 Merge1 帐户。</span><span class="sxs-lookup"><span data-stu-id="a2298-123">Create a Merge1 account for Microsoft connectors.</span></span> <span data-ttu-id="a2298-124">若要创建帐户，请联系 [Globanet 客户支持部门](https://globanet.com/contact-us/)。</span><span class="sxs-lookup"><span data-stu-id="a2298-124">To create an account, contact [Globanet Customer Support](https://globanet.com/contact-us/).</span></span> <span data-ttu-id="a2298-125">在步骤 1 中创建连接器时，需要登录到此帐户。</span><span class="sxs-lookup"><span data-stu-id="a2298-125">You need to sign into this account when you create the connector in Step 1.</span></span>

- <span data-ttu-id="a2298-126">创建 ServiceNow 应用程序以从 ServiceNow 帐户提取数据。</span><span class="sxs-lookup"><span data-stu-id="a2298-126">Create a ServiceNow application to fetch data from your ServiceNow account.</span></span> <span data-ttu-id="a2298-127">有关创建应用程序的分步说明，请参阅 [Merge1 第三方连接器用户指南](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf)。</span><span class="sxs-lookup"><span data-stu-id="a2298-127">For step-by step instructions about creating the application, see [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).</span></span>

- <span data-ttu-id="a2298-128">在步骤 1 中创建 ServiceNow 连接器 (在步骤 3) 必须分配给 Exchange Online 中的邮箱导入导出角色。</span><span class="sxs-lookup"><span data-stu-id="a2298-128">The user who creates the ServiceNow connector in Step 1 (and completes it in Step 3) must be assigned to the Mailbox Import Export role in Exchange Online.</span></span> <span data-ttu-id="a2298-129">在 Microsoft 365 合规中心的"数据连接器"页上添加连接器需要此角色。</span><span class="sxs-lookup"><span data-stu-id="a2298-129">This role is required to add connectors on the **Data connectors** page in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="a2298-130">默认情况下，不会向 Exchange Online 中任何角色组分配此角色。</span><span class="sxs-lookup"><span data-stu-id="a2298-130">By default, this role isn't assigned to any role group in Exchange Online.</span></span> <span data-ttu-id="a2298-131">可以将邮箱导入导出角色添加到 Exchange Online 中的组织管理角色组。</span><span class="sxs-lookup"><span data-stu-id="a2298-131">You can add the Mailbox Import Export role to the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="a2298-132">也可以创建一个角色组，分配邮箱导入导出角色，然后将相应的用户添加为成员。</span><span class="sxs-lookup"><span data-stu-id="a2298-132">Or you can create a role group, assign the Mailbox Import Export role, and then add the appropriate users as members.</span></span> <span data-ttu-id="a2298-133">有关详细信息，请参阅"在[](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups)Exchange Online[](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups)中管理角色组"一文的"创建角色组或修改角色组"部分。</span><span class="sxs-lookup"><span data-stu-id="a2298-133">For more information, see the [Create role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) or [Modify role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) sections in the article "Manage role groups in Exchange Online".</span></span>

## <a name="step-1-set-up-the-servicenow-connector"></a><span data-ttu-id="a2298-134">步骤 1：设置 ServiceNow 连接器</span><span class="sxs-lookup"><span data-stu-id="a2298-134">Step 1: Set up the ServiceNow connector</span></span>

<span data-ttu-id="a2298-135">第一步是访问 Microsoft 365 合规中心中的"数据连接器"页，并创建 ServiceNow 数据的连接器。 </span><span class="sxs-lookup"><span data-stu-id="a2298-135">The first step is to access to the **Data Connectors** page in the Microsoft 365 compliance center and create a connector for ServiceNow data.</span></span>

1. <span data-ttu-id="a2298-136">转到 [https://compliance.microsoft.com](https://compliance.microsoft.com/) ，然后单击"**数据连接器**  >  **服务Now"。**</span><span class="sxs-lookup"><span data-stu-id="a2298-136">Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click **Data connectors** > **ServiceNow**.</span></span>

2. <span data-ttu-id="a2298-137">在 **ServiceNow** 产品说明页上，单击"**添加连接器"。**</span><span class="sxs-lookup"><span data-stu-id="a2298-137">On the **ServiceNow** product description page, click **Add connector**.</span></span>

3. <span data-ttu-id="a2298-138">在"**服务条款"页上**，单击"**接受"。**</span><span class="sxs-lookup"><span data-stu-id="a2298-138">On the **Terms of service** page, click **Accept**.</span></span>

4. <span data-ttu-id="a2298-139">输入标识连接器的唯一名称，然后单击"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="a2298-139">Enter a unique name that identifies the connector, and then click **Next**.</span></span>

5. <span data-ttu-id="a2298-140">登录到 Merge1 帐户以配置连接器。</span><span class="sxs-lookup"><span data-stu-id="a2298-140">Sign in to your Merge1 account to configure the connector.</span></span>

## <a name="step-2-configure-the-servicenow-on-the-globanet-merge1-site"></a><span data-ttu-id="a2298-141">步骤 2：在 Globanet Merge1 网站上配置 ServiceNow</span><span class="sxs-lookup"><span data-stu-id="a2298-141">Step 2: Configure the ServiceNow on the Globanet Merge1 site</span></span>

<span data-ttu-id="a2298-142">第二步是在 Globanet Merge1 网站上配置 ServiceNow 连接器。</span><span class="sxs-lookup"><span data-stu-id="a2298-142">The second step is to configure the ServiceNow connector on the Globanet Merge1 site.</span></span> <span data-ttu-id="a2298-143">若要了解如何配置 ServiceNow 连接器，请参阅 [Merge1 第三方连接器用户指南](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf)。</span><span class="sxs-lookup"><span data-stu-id="a2298-143">For information about how to configure the ServiceNow connector, see [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).</span></span>

<span data-ttu-id="a2298-144">单击 **"保存**&完成"后，将显示Microsoft 365 合规中心连接器向导中的"用户映射"页。</span><span class="sxs-lookup"><span data-stu-id="a2298-144">After you click **Save & Finish,** the **User mapping** page in the connector wizard in the Microsoft 365 compliance center is displayed.</span></span>

## <a name="step-3-map-users-and-complete-the-connector-setup"></a><span data-ttu-id="a2298-145">步骤 3：映射用户并完成连接器设置</span><span class="sxs-lookup"><span data-stu-id="a2298-145">Step 3: Map users and complete the connector setup</span></span>

<span data-ttu-id="a2298-146">若要映射用户并完成 Microsoft 365 合规中心中的连接器设置，请按照以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="a2298-146">To map users and complete the connector setup in the Microsoft 365 compliance center, follow these steps:</span></span>

1. <span data-ttu-id="a2298-147">在 **"将用户映射到 Microsoft 365 用户** "页上，启用自动用户映射。</span><span class="sxs-lookup"><span data-stu-id="a2298-147">On the **Map ServiceNow users to Microsoft 365 users** page, enable automatic user mapping.</span></span> <span data-ttu-id="a2298-148">ServiceNow 项目包括一个称为 *"电子邮件*"的属性，该属性包含组织中用户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="a2298-148">The ServiceNow items include a property called *Email*, which contains email addresses for users in your organization.</span></span> <span data-ttu-id="a2298-149">如果连接器可以将此地址与 Microsoft 365 用户关联，则项目将导入该用户的邮箱。</span><span class="sxs-lookup"><span data-stu-id="a2298-149">If the connector can associate this address with a Microsoft 365 user, the items are imported to that user's mailbox.</span></span>

2. <span data-ttu-id="a2298-150">单击 **"** 下一步"，查看设置，然后转到"数据连接器"页以查看新连接器的导入过程的进度。</span><span class="sxs-lookup"><span data-stu-id="a2298-150">Click **Next**, review your settings, and then go to the **Data connectors** page to see the progress of the import process for the new connector.</span></span>

## <a name="step-4-monitor-the-servicenow-connector"></a><span data-ttu-id="a2298-151">步骤 4：监视 ServiceNow 连接器</span><span class="sxs-lookup"><span data-stu-id="a2298-151">Step 4: Monitor the ServiceNow connector</span></span>

<span data-ttu-id="a2298-152">创建 ServiceNow 连接器后，可以在 Microsoft 365 合规中心查看连接器状态。</span><span class="sxs-lookup"><span data-stu-id="a2298-152">After you create the ServiceNow connector, you can view the connector status in the Microsoft 365 compliance center.</span></span>

1. <span data-ttu-id="a2298-153">转到 [https://compliance.microsoft.com](https://compliance.microsoft.com/) 左侧导航 **中的"数据连接器** "，然后单击"数据连接器"。</span><span class="sxs-lookup"><span data-stu-id="a2298-153">Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and click **Data connectors** in the left nav.</span></span>

2. <span data-ttu-id="a2298-154">单击 **"连接器"** 选项卡，然后选择 **ServiceNow** 连接器以显示包含连接器的属性和信息的飞出页。</span><span class="sxs-lookup"><span data-stu-id="a2298-154">Click the **Connectors** tab and then select the **ServiceNow** connector to display the flyout page, which contains the properties and information about the connector.</span></span>

3. <span data-ttu-id="a2298-155">在 **"源的** 连接器状态"下，单击"下载日志"链接 (或保存) 连接器的状态日志。</span><span class="sxs-lookup"><span data-stu-id="a2298-155">Under **Connector status with source**, click the **Download log** link to open (or save) the status log for the connector.</span></span> <span data-ttu-id="a2298-156">此日志包含已导入到 Microsoft 云的数据。</span><span class="sxs-lookup"><span data-stu-id="a2298-156">This log contains data that has been imported to the Microsoft cloud.</span></span>

## <a name="known-issues"></a><span data-ttu-id="a2298-157">已知问题</span><span class="sxs-lookup"><span data-stu-id="a2298-157">Known issues</span></span>

- <span data-ttu-id="a2298-158">目前，我们不支持导入大于 10 MB 的附件或项目。</span><span class="sxs-lookup"><span data-stu-id="a2298-158">At this time, we don't support importing attachments or items that are larger than 10 MB.</span></span> <span data-ttu-id="a2298-159">稍后将提供对较大项目的支持。</span><span class="sxs-lookup"><span data-stu-id="a2298-159">Support for larger items will be available at a later date.</span></span>