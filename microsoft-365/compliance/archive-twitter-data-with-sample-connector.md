---
title: 设置连接器以存档 Twitter 数据
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
description: 了解管理员如何设置和使用本机连接器将 Twitter 数据导入 Microsoft 365。
ms.openlocfilehash: b4eadc58393df651505287f9238f43a1db0563a8
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620258"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a><span data-ttu-id="81fab-103">设置连接器以存档 Twitter 数据 (预览) </span><span class="sxs-lookup"><span data-stu-id="81fab-103">Set up a connector to archive Twitter data (preview)</span></span>

<span data-ttu-id="81fab-104">使用 Microsoft 365 合规中心中的连接器将数据从 Twitter 导入和存档到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="81fab-104">Use a connector in the Microsoft 365 compliance center to import and archive data from Twitter to Microsoft 365.</span></span> <span data-ttu-id="81fab-105">设置和配置连接器后，它将按计划连接到组织的 Twitter 帐户 () ，将项目内容转换为电子邮件格式，然后将这些项目导入 Microsoft 365 中的邮箱。</span><span class="sxs-lookup"><span data-stu-id="81fab-105">After you set up and configure the connector, it connects to your organization's Twitter account (on a scheduled basis), converts the content of an item to an email message format, and then imports those items to a mailbox in Microsoft 365.</span></span>

<span data-ttu-id="81fab-106">导入 Twitter 数据后，可以将 Microsoft 365 合规性功能（如诉讼保留、内容搜索、In-Place 存档、审核和 Microsoft 365 保留策略）应用于 Twitter 数据。</span><span class="sxs-lookup"><span data-stu-id="81fab-106">After the Twitter data is imported, you can apply Microsoft 365 compliance features such as Litigation Hold, Content Search, In-Place Archiving, Auditing, and Microsoft 365 retention policies to the Twitter data.</span></span> <span data-ttu-id="81fab-107">例如，当邮箱置于诉讼保留或分配给保留策略时，将保留 Twitter 数据。</span><span class="sxs-lookup"><span data-stu-id="81fab-107">For example, when a mailbox is placed on Litigation Hold or assigned to a retention policy, the Twitter data is preserved.</span></span> <span data-ttu-id="81fab-108">您可以使用内容搜索搜索第三方数据，或将存储 Twitter 数据的邮箱与高级电子数据展示案例中的保管人关联。</span><span class="sxs-lookup"><span data-stu-id="81fab-108">You can search third-party data using Content Search or associate the mailbox where the Twitter data is stored with a custodian in an Advanced eDiscovery case.</span></span> <span data-ttu-id="81fab-109">使用连接器在 Microsoft 365 中导入和存档 Twitter 数据可帮助你的组织遵守政府政策和法规策略。</span><span class="sxs-lookup"><span data-stu-id="81fab-109">Using a connector to import and archive Twitter data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

<span data-ttu-id="81fab-110">导入 Twitter 数据后，可以将 Microsoft 365 合规性功能（如诉讼保留、内容搜索、In-Place 存档、审核、通信合规性和 Microsoft 365 保留策略）应用于邮箱中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="81fab-110">After Twitter data is imported, you can apply Microsoft 365 compliance features such as Litigation Hold, Content Search, In-Place Archiving, Auditing, Communication compliance, and Microsoft 365 retention policies to the data stored in the mailbox.</span></span> <span data-ttu-id="81fab-111">例如，您可以使用内容搜索搜索 Twitter 数据，或将数据存储到高级电子数据展示案例中的保管人相关联的邮箱。</span><span class="sxs-lookup"><span data-stu-id="81fab-111">For example, you can search Twitter data using Content Search or associate the mailbox where the data is stored with a custodian in an Advanced eDiscovery case.</span></span> <span data-ttu-id="81fab-112">使用连接器在 Microsoft 365 中导入和存档 Twitter 数据可帮助你的组织遵守政府政策和法规策略。</span><span class="sxs-lookup"><span data-stu-id="81fab-112">Using a connector to import and archive Twitter data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

## <a name="prerequisites-for-setting-up-a-connector-for-twitter"></a><span data-ttu-id="81fab-113">为 Twitter 设置连接器的先决条件</span><span class="sxs-lookup"><span data-stu-id="81fab-113">Prerequisites for setting up a connector for Twitter</span></span>

<span data-ttu-id="81fab-114">完成以下先决条件，然后才能在 Microsoft 365 合规中心中设置和配置连接器，以从组织的 Twitter 帐户导入和存档数据。</span><span class="sxs-lookup"><span data-stu-id="81fab-114">Complete the following prerequisites before you can set up and configure a connector in the Microsoft 365 compliance center to import and archive data from your organization's Twitter account.</span></span>

- <span data-ttu-id="81fab-115">你需要为组织使用 Twitter 帐户;设置连接器时需要登录到此帐户。</span><span class="sxs-lookup"><span data-stu-id="81fab-115">You need a Twitter account for your organization; you need to sign in to this account when setting up the connector.</span></span>

- <span data-ttu-id="81fab-116">你的组织必须具有有效的 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="81fab-116">Your organization must have a valid Azure subscription.</span></span> <span data-ttu-id="81fab-117">如果你没有现有的 Azure 订阅，你可以注册以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="81fab-117">If you don't have an existing Azure subscription, you can sign up for one of these options:</span></span>

    - [<span data-ttu-id="81fab-118">注册一年免费的 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="81fab-118">Sign up for a free one year Azure subscription</span></span>](https://azure.microsoft.com/free) 

    - [<span data-ttu-id="81fab-119">注册 Azure 付费订阅</span><span class="sxs-lookup"><span data-stu-id="81fab-119">Sign up for a Pay-As-You-Go Azure subscription</span></span>](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > <span data-ttu-id="81fab-120">Microsoft 365 订阅中包含的免费 [Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) 订阅不支持安全与合规&连接器。</span><span class="sxs-lookup"><span data-stu-id="81fab-120">The [free Azure Active Directory subscription](use-your-free-azure-ad-subscription-in-office-365.md) that's included with your Microsoft 365 subscription doesn't support the connectors in the Security & Compliance Center.</span></span>

- <span data-ttu-id="81fab-121">在步骤 5 (Microsoft 365 合规中心中设置 Twitter 连接器) 必须在 Exchange Online 中分配邮箱导入导出角色。</span><span class="sxs-lookup"><span data-stu-id="81fab-121">The user who sets up the Twitter connector in the Microsoft 365 compliance center (in Step 5) must be assigned the Mailbox Import Export role in Exchange Online.</span></span> <span data-ttu-id="81fab-122">默认情况下，不会向 Exchange Online 中任何角色组分配此角色。</span><span class="sxs-lookup"><span data-stu-id="81fab-122">By default, this role isn't assigned to any role group in Exchange Online.</span></span> <span data-ttu-id="81fab-123">可以将邮箱导入导出角色添加到 Exchange Online 中的组织管理角色组。</span><span class="sxs-lookup"><span data-stu-id="81fab-123">You can add the Mailbox Import Export role to the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="81fab-124">也可以创建一个角色组，分配邮箱导入导出角色，然后将相应的用户添加为成员。</span><span class="sxs-lookup"><span data-stu-id="81fab-124">Or you can create a role group, assign the Mailbox Import Export role, and then add the appropriate users as members.</span></span> <span data-ttu-id="81fab-125">有关详细信息，请参阅"在[](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups)Exchange Online[](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups)中管理角色组"一文的"创建角色组或修改角色组"部分。</span><span class="sxs-lookup"><span data-stu-id="81fab-125">For more information, see the  [Create role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) or [Modify role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) sections in the article "Manage role groups in Exchange Online".</span></span>

## <a name="step-1-create-an-app-in-azure-active-directory"></a><span data-ttu-id="81fab-126">步骤 1：在 Azure Active Directory 中创建应用</span><span class="sxs-lookup"><span data-stu-id="81fab-126">Step 1: Create an app in Azure Active Directory</span></span>

<span data-ttu-id="81fab-127">第一步是在 Azure Active Directory (AAD) 。</span><span class="sxs-lookup"><span data-stu-id="81fab-127">The first step is to register a new app in Azure Active Directory (AAD).</span></span> <span data-ttu-id="81fab-128">此应用程序对应于你在步骤 2 中为 Twitter 连接器实现的 Web 应用资源。</span><span class="sxs-lookup"><span data-stu-id="81fab-128">This app corresponds to the web app resource that you implement in Step 2 for the Twitter connector.</span></span>

<span data-ttu-id="81fab-129">有关分步说明，请参阅在 [Azure Active Directory 中创建应用](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory)。</span><span class="sxs-lookup"><span data-stu-id="81fab-129">For step-by-step instructions, see [Create an app in Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).</span></span>

<span data-ttu-id="81fab-130">完成此步骤 (按照下面的分步说明) ，将以下信息保存到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="81fab-130">During the completion of this step (by following the step-by-step instructions), you'll save the following information to a text file.</span></span> <span data-ttu-id="81fab-131">这些值将在部署过程的稍后步骤中使用。</span><span class="sxs-lookup"><span data-stu-id="81fab-131">These values will be used in later steps in the deployment process.</span></span>

- <span data-ttu-id="81fab-132">AAD 应用程序 ID</span><span class="sxs-lookup"><span data-stu-id="81fab-132">AAD application ID</span></span>

- <span data-ttu-id="81fab-133">AAD 应用程序密码</span><span class="sxs-lookup"><span data-stu-id="81fab-133">AAD application secret</span></span>

- <span data-ttu-id="81fab-134">租户 ID</span><span class="sxs-lookup"><span data-stu-id="81fab-134">Tenant Id</span></span>

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a><span data-ttu-id="81fab-135">步骤 2：将连接器 Web 服务从 GitHub 存储库部署到 Azure 帐户</span><span class="sxs-lookup"><span data-stu-id="81fab-135">Step 2: Deploy connector web service from GitHub repository to your Azure account</span></span>

<span data-ttu-id="81fab-136">下一步是部署 Twitter 连接器应用的源代码，该应用将使用 Twitter API 连接到你的 Twitter 帐户并提取数据，以便你可以将其导入到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="81fab-136">The next step is to deploy the source code for the Twitter connector app that will use Twitter API to connect to your Twitter account and extract data so you can import it to Microsoft 365.</span></span> <span data-ttu-id="81fab-137">为组织部署的 Twitter 连接器将项目从组织的 Twitter 帐户上载到此步骤中创建的 Azure 存储位置。</span><span class="sxs-lookup"><span data-stu-id="81fab-137">The Twitter connector that you deploy for your organization will upload the items from your organization's Twitter account to the Azure Storage location that is created in this step.</span></span> <span data-ttu-id="81fab-138">在步骤 5) 中的 Microsoft 365 合规中心 (创建 Twitter 连接器后，Microsoft 365 导入服务将 Twitter 数据从 Azure 存储位置复制到 Microsoft 365 中的邮箱。</span><span class="sxs-lookup"><span data-stu-id="81fab-138">After you create a Twitter connector in the Microsoft 365 compliance center (in Step 5), the Microsoft 365 Import service will copy the Twitter data from the Azure Storage location to a mailbox in Microsoft 365.</span></span> <span data-ttu-id="81fab-139">如前面" [先决条件"部分](#prerequisites-for-setting-up-a-connector-for-twitter) 所述，你必须具有有效的 Azure 订阅，以创建 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="81fab-139">As previous explained in the [Prerequisites](#prerequisites-for-setting-up-a-connector-for-twitter) section, you must have a valid Azure subscription to create an Azure Storage account.</span></span>

<span data-ttu-id="81fab-140">若要部署 Twitter 连接器应用的源代码：</span><span class="sxs-lookup"><span data-stu-id="81fab-140">To deploy the source code for the Twitter connector app:</span></span>

1. <span data-ttu-id="81fab-141">转到 [此 GitHub 网站](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet)。</span><span class="sxs-lookup"><span data-stu-id="81fab-141">Go to [this GitHub site](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).</span></span>

2. <span data-ttu-id="81fab-142">单击 **"部署到 Azure"。**</span><span class="sxs-lookup"><span data-stu-id="81fab-142">Click **Deploy to Azure**.</span></span>

<span data-ttu-id="81fab-143">有关分步说明，请参阅将连接器 [Web 服务从 GitHub 部署到 Azure 帐户](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account)。</span><span class="sxs-lookup"><span data-stu-id="81fab-143">For step-by-step instructions, see [Deploy the connector web service from GitHub to your Azure account](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).</span></span>

<span data-ttu-id="81fab-144">在按照分步说明完成此步骤时，您提供了以下信息</span><span class="sxs-lookup"><span data-stu-id="81fab-144">While you follow the step-by-step instructions to complete this step, you provide the following information</span></span>

- <span data-ttu-id="81fab-145">APISecretKey：在此步骤完成期间创建此密码。</span><span class="sxs-lookup"><span data-stu-id="81fab-145">APISecretKey: You create this secret during the completion of this step.</span></span> <span data-ttu-id="81fab-146">它在步骤 5 中使用。</span><span class="sxs-lookup"><span data-stu-id="81fab-146">It's used in Step 5.</span></span>

- <span data-ttu-id="81fab-147">tenantId：你在步骤 1 中的 Azure Active Directory 中创建 Twitter 应用后复制的 Microsoft 365 组织的租户 ID。</span><span class="sxs-lookup"><span data-stu-id="81fab-147">tenantId: The tenant ID of your Microsoft 365 organization that you copied after creating the Twitter app in Azure Active Directory in Step 1.</span></span>

<span data-ttu-id="81fab-148">完成此步骤后，请确保复制应用程序服务 URL (例如 `https://twitterconnector.azurewebsites.net` ，) 。</span><span class="sxs-lookup"><span data-stu-id="81fab-148">After completing this step, be sure to copy the app Service URL (for example, `https://twitterconnector.azurewebsites.net`).</span></span> <span data-ttu-id="81fab-149">您需要使用此 URL 完成步骤 3、步骤 4 和步骤 5) 。</span><span class="sxs-lookup"><span data-stu-id="81fab-149">You need to use this URL to complete Step 3, Step 4, and Step 5).</span></span>

## <a name="step-3-create-developer-app-on-twitter"></a><span data-ttu-id="81fab-150">步骤 3：在 Twitter 上创建开发人员应用</span><span class="sxs-lookup"><span data-stu-id="81fab-150">Step 3: Create developer app on Twitter</span></span>

<span data-ttu-id="81fab-151">下一步是在 Twitter 上创建和配置开发人员应用。</span><span class="sxs-lookup"><span data-stu-id="81fab-151">The next step is to create and configure a developer app on Twitter.</span></span> <span data-ttu-id="81fab-152">在步骤 7 中创建的自定义连接器使用 Twitter 应用与 Twitter API 交互，以从组织的 Twitter 帐户获取数据。</span><span class="sxs-lookup"><span data-stu-id="81fab-152">The custom connector that you create in Step 7 uses the Twitter app to interact with the Twitter API to obtain data from your organization's Twitter account.</span></span>

<span data-ttu-id="81fab-153">有关分步说明，请参阅"创建[Twitter 应用"。](deploy-twitter-connector.md#step-3-create-the-twitter-app)</span><span class="sxs-lookup"><span data-stu-id="81fab-153">For step-by-step instructions, see [Create the Twitter app](deploy-twitter-connector.md#step-3-create-the-twitter-app).</span></span>

<span data-ttu-id="81fab-154">完成此步骤 (按照下面的分步说明) ，将以下信息保存到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="81fab-154">During the completion of this step (by following the step-by-step instructions), you save the following information to a text file.</span></span> <span data-ttu-id="81fab-155">这些值将用于在步骤 4 中配置 Twitter 连接器应用。</span><span class="sxs-lookup"><span data-stu-id="81fab-155">These values will be used to configure the Twitter connector app in Step 4.</span></span>

- <span data-ttu-id="81fab-156">Twitter API 密钥</span><span class="sxs-lookup"><span data-stu-id="81fab-156">Twitter API Key</span></span>

- <span data-ttu-id="81fab-157">Twitter API 密钥</span><span class="sxs-lookup"><span data-stu-id="81fab-157">Twitter API Secret Key</span></span>

- <span data-ttu-id="81fab-158">Twitter 访问令牌</span><span class="sxs-lookup"><span data-stu-id="81fab-158">Twitter Access Token</span></span>

- <span data-ttu-id="81fab-159">Twitter 访问令牌密码</span><span class="sxs-lookup"><span data-stu-id="81fab-159">Twitter Access Token Secret</span></span>

## <a name="step-4-configure-the-twitter-connector-app"></a><span data-ttu-id="81fab-160">步骤 4：配置 Twitter 连接器应用</span><span class="sxs-lookup"><span data-stu-id="81fab-160">Step 4: Configure the Twitter connector app</span></span>

<span data-ttu-id="81fab-161">下一步是将配置设置添加到你在步骤 2 中部署的 Twitter 连接器应用。</span><span class="sxs-lookup"><span data-stu-id="81fab-161">The next step is to add configurations settings to the Twitter connector app that you deployed in Step 2.</span></span> <span data-ttu-id="81fab-162">为此，请进入连接器应用的主页并配置它。</span><span class="sxs-lookup"><span data-stu-id="81fab-162">You do this by going to the home page of your connector app and configuring it.</span></span>

<span data-ttu-id="81fab-163">有关分步说明，请参阅"[配置连接器 Web 应用"。](deploy-twitter-connector.md#step-4-configure-the-connector-web-app)</span><span class="sxs-lookup"><span data-stu-id="81fab-163">For step-by-step instructions, see [Configure the connector web app](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).</span></span>

<span data-ttu-id="81fab-164">完成此步骤 (按照) 中的分步说明进行操作， (在完成上述步骤后复制到文本文件中的以下信息) ：</span><span class="sxs-lookup"><span data-stu-id="81fab-164">During the completion of this step (by following the step-by-step instructions), you'll provide the following information (that you've copied to a text file after completing the previous steps):</span></span>

- <span data-ttu-id="81fab-165">在步骤 3 (获取的 Twitter API 密钥) </span><span class="sxs-lookup"><span data-stu-id="81fab-165">Twitter API Key (obtained in Step 3)</span></span>

- <span data-ttu-id="81fab-166">在步骤 3 (获取的 Twitter API 密钥) </span><span class="sxs-lookup"><span data-stu-id="81fab-166">Twitter API Secret Key (obtained in Step 3)</span></span>

- <span data-ttu-id="81fab-167">在步骤 3 (获取的 Twitter 访问) </span><span class="sxs-lookup"><span data-stu-id="81fab-167">Twitter Access Token (obtained in Step 3)</span></span>

- <span data-ttu-id="81fab-168">在步骤 3 (获取的 Twitter 访问令牌密码) </span><span class="sxs-lookup"><span data-stu-id="81fab-168">Twitter Access Token Secret (obtained in Step 3)</span></span>

- <span data-ttu-id="81fab-169">步骤 1 (获取的 AAD 应用程序 ID 中的 Azure Active Directory 应用程序 ID) </span><span class="sxs-lookup"><span data-stu-id="81fab-169">Azure Active Directory application ID (the AAD application ID obtained in Step 1)</span></span>

- <span data-ttu-id="81fab-170">在步骤 1 (获取的 AAD 应用程序密码的 Azure Active Directory 应用程序) </span><span class="sxs-lookup"><span data-stu-id="81fab-170">Azure Active Directory application secret (the AAD application secret obtained in Step 1)</span></span>

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a><span data-ttu-id="81fab-171">步骤 5：在 Microsoft 365 合规中心中设置 Twitter 连接器</span><span class="sxs-lookup"><span data-stu-id="81fab-171">Step 5: Set up a Twitter connector in the Microsoft 365 compliance center</span></span>

<span data-ttu-id="81fab-172">最后一步是在 Microsoft 365 合规中心中设置 Twitter 连接器，以将数据从组织的 Twitter 帐户导入到 Microsoft 365 中的指定邮箱。</span><span class="sxs-lookup"><span data-stu-id="81fab-172">The final step is to set up the Twitter connector in the Microsoft 365 compliance center that will import data from your organization's Twitter account to a specified mailbox in Microsoft 365.</span></span> <span data-ttu-id="81fab-173">完成此步骤后，Microsoft 365 导入服务将开始将数据从组织的 Twitter 帐户导入到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="81fab-173">After you complete this step, the Microsoft 365 Import service will start importing data from your organization's Twitter account to Microsoft 365.</span></span>

<span data-ttu-id="81fab-174">有关分步说明，请参阅 [在 Microsoft 365 合规](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center)中心中设置 Twitter 连接器。</span><span class="sxs-lookup"><span data-stu-id="81fab-174">For step-by-step instructions, see [Set up a Twitter connector in the Microsoft 365 compliance center](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center).</span></span> 

<span data-ttu-id="81fab-175">完成此步骤 (按照) 中的分步说明进行操作， (在完成步骤) 后复制到文本文件的以下信息。</span><span class="sxs-lookup"><span data-stu-id="81fab-175">During the completion of this step (by following the step-by-step instructions), you'll provide the following information (that you've copied to a text file after completing the steps).</span></span>

- <span data-ttu-id="81fab-176">在步骤 2 (获取的 Azure 应用服务 URL;例如 `https://twitterconnector.azurewebsites.net` ，) </span><span class="sxs-lookup"><span data-stu-id="81fab-176">Azure app service URL (obtained in Step 2; for example, `https://twitterconnector.azurewebsites.net`)</span></span>

- <span data-ttu-id="81fab-177">在步骤 2 (中创建的 APISecretKey) </span><span class="sxs-lookup"><span data-stu-id="81fab-177">APISecretKey (that you created in Step 2)</span></span>
