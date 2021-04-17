---
title: 设置连接器以在 Microsoft 365 中存档 PostgreSQL 数据上的 Cisco Jabber
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: 了解如何在 Microsoft 365 合规中心设置和使用连接器，以将数据从 PostgreSQL 上的 Cisco Jabber 导入和存档到 Microsoft 365。
ms.openlocfilehash: 47cd3c7e9d3717426fbcf43bf1b0df16bbe2cf80
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2021
ms.locfileid: "51767073"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data-preview"></a><span data-ttu-id="37c54-103">设置连接器以在 PostgreSQL 数据上存档 Cisco Jabber， (预览) </span><span class="sxs-lookup"><span data-stu-id="37c54-103">Set up a connector to archive Cisco Jabber on PostgreSQL data (preview)</span></span>

<span data-ttu-id="37c54-104">使用 Microsoft 365 合规中心中的一个 Microsoft 365 连接器，将数据从 Cisco Jabber 平台导入并存档到 Microsoft 365 组织的用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="37c54-104">Use a Veritas connector in the Microsoft 365 compliance center to import and archive data from the Cisco Jabber platform to user mailboxes in your Microsoft 365 organization.</span></span> <span data-ttu-id="37c54-105">Microsoft 在 [PostgreSQL](https://www.veritas.com/insights/merge1/jabber) 连接器上提供了 Cisco Jabber，配置为定期捕获第三方数据源 (中的项目) 将这些项目导入到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="37c54-105">Veritas provides a [Cisco Jabber on PostgreSQL](https://www.veritas.com/insights/merge1/jabber) connector that is configured to capture items from the third-party data source (on a regular basis) and import those items to Microsoft 365.</span></span> <span data-ttu-id="37c54-106">连接器将内容（如消息、聊天和共享内容）从 PostgreSQL 上的 Cisco Jabber 转换为电子邮件格式，然后将这些项目导入到 Microsoft 365 中的用户邮箱。</span><span class="sxs-lookup"><span data-stu-id="37c54-106">The connector converts the content such as messages, chats, and shared content from Cisco Jabber on PostgreSQL to an email message format and then imports those items to the user's mailbox in Microsoft 365.</span></span>

<span data-ttu-id="37c54-107">在 PostgreSQL 上的 Cisco Jabber 数据存储在用户邮箱中后，可以应用 Microsoft 365 合规性功能，如诉讼保留、电子数据展示、保留策略和保留标签。</span><span class="sxs-lookup"><span data-stu-id="37c54-107">After Cisco Jabber on PostgreSQL data is stored in user mailboxes, you can apply Microsoft 365 compliance features such as Litigation Hold, eDiscovery, retention policies and retention labels.</span></span> <span data-ttu-id="37c54-108">使用 PostgreSQL 连接器上的 Cisco Jabber 在 Microsoft 365 中导入和存档数据可帮助组织遵守政府法规策略。</span><span class="sxs-lookup"><span data-stu-id="37c54-108">Using a Cisco Jabber on PostgreSQL connector to import and archive data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a><span data-ttu-id="37c54-109">对 PostgreSQL 数据存档 Cisco Jabber 概述</span><span class="sxs-lookup"><span data-stu-id="37c54-109">Overview of archiving Cisco Jabber on PostgreSQL data</span></span>

<span data-ttu-id="37c54-110">以下概述介绍了使用连接器在 Microsoft 365 中存档 PostgreSQL 数据上的 Cisco Jabber 的过程。</span><span class="sxs-lookup"><span data-stu-id="37c54-110">The following overview explains the process of using a connector to archive the Cisco Jabber on PostgreSQL data in Microsoft 365.</span></span>

![针对 PostgreSQL 数据的 Cisco Jabber 存档工作流](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. <span data-ttu-id="37c54-112">贵组织与 PostgreSQL 上的 Cisco Jabber 合作，在 PostgreSQL 网站上设置和配置 Cisco Jabber。</span><span class="sxs-lookup"><span data-stu-id="37c54-112">Your organization works with Cisco Jabber on PostgreSQL to set up and configure a Cisco Jabber on PostgreSQL site.</span></span>

2. <span data-ttu-id="37c54-113">每 24 小时一次，PostgreSQL 项上的 Cisco Jabber 将复制到位于以下位置的 Cisco Merge1 网站：</span><span class="sxs-lookup"><span data-stu-id="37c54-113">Once every 24 hours, Cisco Jabber on PostgreSQL items are copied to the Veritas Merge1 site.</span></span> <span data-ttu-id="37c54-114">连接器还将 PostgreSQL 项上的 Cisco Jabber 转换为电子邮件格式。</span><span class="sxs-lookup"><span data-stu-id="37c54-114">The connector also converts Cisco Jabber on PostgreSQL items to an email message format.</span></span>

3. <span data-ttu-id="37c54-115">在 Microsoft 365 合规中心创建的 PostgreSQL 连接器上的 Cisco Jabber 每天连接到一个 Microsoft Merge1 网站，将 Jabber 内容传输至 Microsoft 云中的安全 Azure 存储位置。</span><span class="sxs-lookup"><span data-stu-id="37c54-115">The Cisco Jabber on PostgreSQL connector that you create in the Microsoft 365 compliance center, connects to the Veritas Merge1 site every day, and transfers the Jabber content to a secure Azure Storage location in the Microsoft cloud.</span></span>

4. <span data-ttu-id="37c54-116">连接器使用自动用户映射的 *Email* 属性值将转换的项目导入到特定用户的邮箱，如步骤 [3 中所述](#step-3-map-users-and-complete-the-connector-setup)。</span><span class="sxs-lookup"><span data-stu-id="37c54-116">The connector imports the converted items to the mailboxes of specific users using the value of the *Email* property of the automatic user mapping as described in [Step 3](#step-3-map-users-and-complete-the-connector-setup).</span></span> <span data-ttu-id="37c54-117">PostgreSQL 上名为 **Cisco Jabber** 的收件箱文件夹中的子文件夹是在用户邮箱中创建的，并且项目会导入到该文件夹中。</span><span class="sxs-lookup"><span data-stu-id="37c54-117">A subfolder in the Inbox folder named **Cisco Jabber on PostgreSQL** is created in the user mailboxes, and items are imported to that folder.</span></span> <span data-ttu-id="37c54-118">连接器使用 *Email* 属性的值实现此操作。</span><span class="sxs-lookup"><span data-stu-id="37c54-118">The connector does this by using the value of the *Email* property.</span></span> <span data-ttu-id="37c54-119">每个 Jabber 项目都包含此属性，该属性用项目每个参与者的电子邮件地址填充。</span><span class="sxs-lookup"><span data-stu-id="37c54-119">Every Jabber item contains this property, which is populated with the email address of every participant of the item.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="37c54-120">准备工作</span><span class="sxs-lookup"><span data-stu-id="37c54-120">Before you begin</span></span>

- <span data-ttu-id="37c54-121">为 Microsoft 连接器创建 Merge1 帐户。</span><span class="sxs-lookup"><span data-stu-id="37c54-121">Create a Merge1 account for Microsoft connectors.</span></span> <span data-ttu-id="37c54-122">若要进行此操作，请联系["用户支持人员"。](https://www.veritas.com/content/support/en_US)</span><span class="sxs-lookup"><span data-stu-id="37c54-122">To do this, contact [Veritas Customer Support](https://www.veritas.com/content/support/en_US).</span></span> <span data-ttu-id="37c54-123">在步骤 1 中创建连接器时，需要登录此帐户。</span><span class="sxs-lookup"><span data-stu-id="37c54-123">You need to sign into this account when you create the connector in Step 1.</span></span>

- <span data-ttu-id="37c54-124">必须将在步骤 1 (中的 PostgreSQL 连接器上创建 Cisco Jabber 并将其在步骤 3) 中完成的用户分配给 Exchange Online 中的邮箱导入导出角色。</span><span class="sxs-lookup"><span data-stu-id="37c54-124">The user who creates the Cisco Jabber on PostgreSQL connector in Step 1 (and completes it in Step 3) must be assigned to the Mailbox Import Export role in Exchange Online.</span></span> <span data-ttu-id="37c54-125">在 Microsoft 365 合规中心的"数据连接器"页面上添加连接器需要此角色。</span><span class="sxs-lookup"><span data-stu-id="37c54-125">This role is required to add connectors on the **Data connectors** page in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="37c54-126">默认情况下，此角色不会分配给 Exchange Online 中任何角色组。</span><span class="sxs-lookup"><span data-stu-id="37c54-126">By default, this role is not assigned to any role group in Exchange Online.</span></span> <span data-ttu-id="37c54-127">可以将"邮箱导入导出"角色添加到 Exchange Online 中的"组织管理"角色组。</span><span class="sxs-lookup"><span data-stu-id="37c54-127">You can add the Mailbox Import Export role to the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="37c54-128">也可以创建角色组，分配邮箱导入导出角色，然后将相应的用户添加为成员。</span><span class="sxs-lookup"><span data-stu-id="37c54-128">Or you can create a role group, assign the Mailbox Import Export role, and then add the appropriate users as members.</span></span> <span data-ttu-id="37c54-129">有关详细信息，请参阅"在[](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups)Exchange Online[](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups)中管理角色组"一文的创建角色组或修改角色组部分。</span><span class="sxs-lookup"><span data-stu-id="37c54-129">For more information, see the [Create role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) or [Modify role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) sections in the article "Manage role groups in Exchange Online".</span></span>

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a><span data-ttu-id="37c54-130">步骤 1：在 PostgreSQL 连接器上设置 Cisco Jabber</span><span class="sxs-lookup"><span data-stu-id="37c54-130">Step 1: Set up the Cisco Jabber on PostgreSQL connector</span></span>

<span data-ttu-id="37c54-131">第一步是访问 Microsoft 365 合规中心的"数据连接器"页面，并创建用于 Jabber 数据的连接器。 </span><span class="sxs-lookup"><span data-stu-id="37c54-131">The first step is to access to the **Data Connectors** page in the Microsoft 365 compliance center and create a connector for Jabber data.</span></span>

1. <span data-ttu-id="37c54-132">转到 <https://compliance.microsoft.com>  &gt; **PostgreSQL，然后单击"数据连接器""Cisco Jabber"。**</span><span class="sxs-lookup"><span data-stu-id="37c54-132">Go to <https://compliance.microsoft.com> and then click **Data connectors** &gt; **Cisco Jabber on PostgreSQL**.</span></span>

2. <span data-ttu-id="37c54-133">在 **PostgreSQL 产品说明页上的 Cisco Jabber 上**，单击"**添加连接器"。**</span><span class="sxs-lookup"><span data-stu-id="37c54-133">On the **Cisco Jabber on PostgreSQL** product description page, click **Add connector**.</span></span>

3. <span data-ttu-id="37c54-134">在"**服务条款"页上**，单击"接受 **"。**</span><span class="sxs-lookup"><span data-stu-id="37c54-134">On the **Terms of service** page, click **Accept**.</span></span>

4. <span data-ttu-id="37c54-135">输入标识连接器的唯一名称，然后单击下一 **步**。</span><span class="sxs-lookup"><span data-stu-id="37c54-135">Enter a unique name that identifies the connector, and then click **Next**.</span></span>

5. <span data-ttu-id="37c54-136">登录到 Merge1 帐户以配置连接器。</span><span class="sxs-lookup"><span data-stu-id="37c54-136">Sign in to your Merge1 account to configure the connector.</span></span>

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a><span data-ttu-id="37c54-137">步骤 2：在位于百度合并 1 网站的 PostgreSQL 上配置 Cisco Jabber</span><span class="sxs-lookup"><span data-stu-id="37c54-137">Step 2: Configure the Cisco Jabber on PostgreSQL on the Veritas Merge1 site</span></span>

<span data-ttu-id="37c54-138">第二步是配置位于以下位置的 Cisco Jabber：位于"一线"上的"Iss Merge1"站点上的 PostgreSQL 连接器。</span><span class="sxs-lookup"><span data-stu-id="37c54-138">The second step is to configure the Cisco Jabber on PostgreSQL connector on the Veritas Merge1 site.</span></span> <span data-ttu-id="37c54-139">若要了解如何在 PostgreSQL 连接器上配置 Cisco Jabber，请参阅 [Merge1 第三方连接器用户指南](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf)。</span><span class="sxs-lookup"><span data-stu-id="37c54-139">For information about how to configure the Cisco Jabber on PostgreSQL connector, see [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).</span></span>

<span data-ttu-id="37c54-140">单击 **"保存&** 完成"后，将显示 Microsoft  365 合规中心中的连接器向导中的"用户映射"页。</span><span class="sxs-lookup"><span data-stu-id="37c54-140">After you click **Save & Finish**, the **User mapping** page in the connector wizard in the Microsoft 365 compliance center is displayed.</span></span>

## <a name="step-3-map-users-and-complete-the-connector-setup"></a><span data-ttu-id="37c54-141">步骤 3：映射用户并完成连接器设置</span><span class="sxs-lookup"><span data-stu-id="37c54-141">Step 3: Map users and complete the connector setup</span></span>

<span data-ttu-id="37c54-142">若要映射用户并完成 Microsoft 365 合规中心中的连接器设置，请按照以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="37c54-142">To map users and complete the connector setup in the Microsoft 365 compliance center, follow these steps:</span></span>

1. <span data-ttu-id="37c54-143">在 **PostgreSQL 用户映射到 Microsoft 365 用户的"将 Cisco Jabber 映射到 Microsoft 365** 用户"页上，启用自动用户映射。</span><span class="sxs-lookup"><span data-stu-id="37c54-143">On the **Map Cisco Jabber on PostgreSQL users to Microsoft 365 users** page, enable automatic user mapping.</span></span> <span data-ttu-id="37c54-144">PostgreSQL 项上的 Cisco Jabber 包括名为 *Email* 的属性，该属性包含组织中用户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="37c54-144">The Cisco Jabber on PostgreSQL items include a property called *Email*, which contains email addresses for users in your organization.</span></span> <span data-ttu-id="37c54-145">如果连接器可以将此地址与 Microsoft 365 用户关联，则项目将导入该用户的邮箱。</span><span class="sxs-lookup"><span data-stu-id="37c54-145">If the connector can associate this address with a Microsoft 365 user, the items are imported to that user's mailbox.</span></span>

2. <span data-ttu-id="37c54-146">单击 **"下** 一步"，查看设置，然后转到"数据连接器"页以查看新连接器的导入过程的进度。</span><span class="sxs-lookup"><span data-stu-id="37c54-146">Click **Next**, review your settings, and then go to the **Data connectors** page to see the progress of the import process for the new connector.</span></span>

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a><span data-ttu-id="37c54-147">步骤 4：监视 PostgreSQL 连接器上的 Cisco Jabber</span><span class="sxs-lookup"><span data-stu-id="37c54-147">Step 4: Monitor the Cisco Jabber on PostgreSQL connector</span></span>

<span data-ttu-id="37c54-148">在 PostgreSQL 连接器上创建 Cisco Jabber 后，可以在 Microsoft 365 合规中心查看连接器状态。</span><span class="sxs-lookup"><span data-stu-id="37c54-148">After you create the Cisco Jabber on PostgreSQL connector, you can view the connector status in the Microsoft 365 compliance center.</span></span>

1. <span data-ttu-id="37c54-149">转到左侧 <https://compliance.microsoft.com/> 导航 **导航中的"数据** 连接器"，然后单击" 数据连接器"。</span><span class="sxs-lookup"><span data-stu-id="37c54-149">Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.</span></span>

2. <span data-ttu-id="37c54-150">单击" **连接器"** 选项卡，然后选择 **PostgreSQL** 连接器上的 Cisco Jabber 以显示包含连接器的属性和信息的飞出页。</span><span class="sxs-lookup"><span data-stu-id="37c54-150">Click the **Connectors** tab and then select the **Cisco Jabber on PostgreSQL** connector to display the flyout page, which contains the properties and information about the connector.</span></span>

3. <span data-ttu-id="37c54-151">在 **"源的连接器状态"** 下， **单击"下载** 日志"链接 (或) 连接器的状态日志。</span><span class="sxs-lookup"><span data-stu-id="37c54-151">Under **Connector status with source**, click the **Download log** link to open (or save) the status log for the connector.</span></span> <span data-ttu-id="37c54-152">此日志包含已导入到 Microsoft 云的数据。</span><span class="sxs-lookup"><span data-stu-id="37c54-152">This log contains data that has been imported to the Microsoft cloud.</span></span>

## <a name="known-issues"></a><span data-ttu-id="37c54-153">已知问题</span><span class="sxs-lookup"><span data-stu-id="37c54-153">Known issues</span></span>

- <span data-ttu-id="37c54-154">目前，我们不支持导入大于 10 MB 的附件或项目，但稍后会提供对较大项目的支持。</span><span class="sxs-lookup"><span data-stu-id="37c54-154">At this time, we don't support importing attachments or items larger than 10 MB but support for larger items will be available at a later date.</span></span>