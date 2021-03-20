---
title: 向应用启动器添加自定义磁贴
f1.keywords:
- CSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: '通过将自定义磁贴添加到应用启动器，创建指向电子邮件、文档、应用程序、SharePoint 网站、外部网站和其他资源的快速链接。 '
ms.openlocfilehash: cc4edbfadc5c9555e04d04de8f7368dd86aa9974
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50915430"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a><span data-ttu-id="a965f-103">向应用启动器添加自定义磁贴</span><span class="sxs-lookup"><span data-stu-id="a965f-103">Add custom tiles to the app launcher</span></span>

::: moniker range="o365-21vianet"

> [!NOTE]
> <span data-ttu-id="a965f-104">管理中心正在发生改变。</span><span class="sxs-lookup"><span data-stu-id="a965f-104">The admin center is changing.</span></span> <span data-ttu-id="a965f-105">如果你的体验与此处提供的详细信息不匹配，请参阅[有关新版 Microsoft 365 管理中心](../microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet)。</span><span class="sxs-lookup"><span data-stu-id="a965f-105">If your experience doesn't match the details presented here, see [About the new Microsoft 365 admin center](../microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet).</span></span>

::: moniker-end

<span data-ttu-id="a965f-106">在 Microsoft 365 中，可以使用应用启动器快速轻松地访问电子邮件、日历、文档和应用， ([了解) 。](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)</span><span class="sxs-lookup"><span data-stu-id="a965f-106">In Microsoft 365, you can quickly and easily get to your email, calendars, documents, and apps using the App launcher ([learn more](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)).</span></span> <span data-ttu-id="a965f-107">这些是使用 Microsoft 365 获取的应用，以及从 [SharePoint 商店](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) 或 [Azure AD](/previous-versions/office/office-365-api/)添加的自定义应用。</span><span class="sxs-lookup"><span data-stu-id="a965f-107">These are apps you get with Microsoft 365 as well as custom apps that you add from the [SharePoint Store](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) or [Azure AD](/previous-versions/office/office-365-api/).</span></span>
  
<span data-ttu-id="a965f-p103">可将自己的自定义磁贴添加到应用启动器，这些磁贴指向 SharePoint 网站、外部网站、旧版应用等。自定义磁贴显示在应用启动器的" **全部**"应用下，可将其固定到" **主页**"应用，并指示用户执行相同操作。这样做便于查找相关网站、应用和资源来完成工作。 在以下示例中，名为"Contoso 门户"的自定义磁贴用于访问组织的主要 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="a965f-p103">You can add your own custom tiles to the app launcher that point to SharePoint sites, external sites, legacy apps, and more. The custom tile appears under the app launcher's **All** apps, but you can pin it to the **Home** apps and instruct your users to do the same. This makes it easy to find the relevant sites, apps, and resources to do your job. In the below example, a custom tile called "Contoso Portal" is used to access an organization's SharePoint intranet site.</span></span> 
  
![应用启动器](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a><span data-ttu-id="a965f-113">向应用启动器添加自定义磁贴</span><span class="sxs-lookup"><span data-stu-id="a965f-113">Add a custom tile to the app launcher</span></span>

1. <span data-ttu-id="a965f-114">以全局管理员模式登录管理中心，转到"设置  >  **""组织设置**"，然后选择"**组织配置文件"** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a965f-114">Sign in to the admin center as a Global Administrator, go to **Settings** > **Org Settings**, and choose the **Organization profile** tab.</span></span>
    
2. <span data-ttu-id="a965f-115">在"**组织配置文件"** 选项卡上，选择 **"自定义应用启动器磁贴"。**</span><span class="sxs-lookup"><span data-stu-id="a965f-115">On the **Organization profile** tab, choose **Custom app launcher tiles**.</span></span>
  
3. <span data-ttu-id="a965f-116">选择 **"添加自定义磁贴"。**</span><span class="sxs-lookup"><span data-stu-id="a965f-116">Select **Add a custom tile**.</span></span> 
  
4. <span data-ttu-id="a965f-117">为新磁贴输入" **磁贴名称**"。</span><span class="sxs-lookup"><span data-stu-id="a965f-117">Enter a **Tile name** for the new tile.</span></span> <span data-ttu-id="a965f-118">该名称将显示在磁贴中。</span><span class="sxs-lookup"><span data-stu-id="a965f-118">The name will appear in the tile.</span></span> 
    
5. <span data-ttu-id="a965f-119">输入 **磁贴的网站** URL。</span><span class="sxs-lookup"><span data-stu-id="a965f-119">Enter a **URL of website** for the tile.</span></span> <span data-ttu-id="a965f-120">这是你想要用户在应用启动器上选择磁贴时转到的位置。</span><span class="sxs-lookup"><span data-stu-id="a965f-120">This is the location where you want your users to go when they select the tile on the app launcher.</span></span> <span data-ttu-id="a965f-121">在 URL 中使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a965f-121">Use HTTPS in the URL.</span></span><br/><span data-ttu-id="a965f-122">提示：若要为 SharePoint 网站创建磁贴，请导航到该网站，复制 URL，然后将其粘贴到此处。</span><span class="sxs-lookup"><span data-stu-id="a965f-122">TIP: If you're creating a tile for a SharePoint site, navigate to that site, copy the URL, and paste it here.</span></span> <span data-ttu-id="a965f-123">默认团队网站的 URL 如下所示： `https://<company_name>.sharepoint.com`</span><span class="sxs-lookup"><span data-stu-id="a965f-123">The URL of your default team site looks like this: `https://<company_name>.sharepoint.com`</span></span> 
  
6. <span data-ttu-id="a965f-124">输入 **磁贴的图像 URL。**</span><span class="sxs-lookup"><span data-stu-id="a965f-124">Enter an **URL of the image** for the tile.</span></span> <span data-ttu-id="a965f-125">此图像显示在"我的应用"页面上和应用启动器中。</span><span class="sxs-lookup"><span data-stu-id="a965f-125">The image appears on the My apps page and app launcher.</span></span><br/><span data-ttu-id="a965f-126">提示：图像应为 60x60 像素，无需身份验证即可供组织所有人使用。</span><span class="sxs-lookup"><span data-stu-id="a965f-126">TIP: The image should be 60x60 pixels and be available to everyone in your organization without requiring authentication.</span></span>

7. <span data-ttu-id="a965f-127">为磁贴输入" **说明**"。</span><span class="sxs-lookup"><span data-stu-id="a965f-127">Enter a **Description** for the tile.</span></span> <span data-ttu-id="a965f-128">当你在"我的应用"页面上选择磁贴并选择"应用详细信息"时， **你将看到此内容**。</span><span class="sxs-lookup"><span data-stu-id="a965f-128">You see this when you select the tile on the My apps page and select **App details**.</span></span> 
  
8. <span data-ttu-id="a965f-129">选择 **"保存更改** "以创建自定义磁贴。</span><span class="sxs-lookup"><span data-stu-id="a965f-129">Select **Save changes** to create the custom tile.</span></span> 
    
<span data-ttu-id="a965f-130">自定义磁贴现显示在应用启动器中的" **全部**"选项卡上。</span><span class="sxs-lookup"><span data-stu-id="a965f-130">Your custom tile now appears in the app launcher on the **All** tab for you and your users.</span></span> 
  
## <a name="edit-or-delete-a-custom-tile"></a><span data-ttu-id="a965f-131">Edit or delete a custom tile</span><span class="sxs-lookup"><span data-stu-id="a965f-131">Edit or delete a custom tile</span></span>

1. <span data-ttu-id="a965f-132">在管理中心，转到 **"设置**  >  **""组织设置**  >  **""组织配置文件"** </a> 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a965f-132">In the admin center, go to the **Settings** > **Org Settings** > **Organization profile**</a> tab.</span></span>
    
2. <span data-ttu-id="a965f-133">在"**组织配置文件"** 页上的"为组织添加 **自定义磁贴"旁边，** 选择"编辑 **"。**</span><span class="sxs-lookup"><span data-stu-id="a965f-133">On the **Organization profile** page, next to   **Add custom tiles for your organization**, select **Edit**.</span></span>

3. <span data-ttu-id="a965f-134">更新自定义磁贴的" **磁贴名称**"、" **URL**"、" **说明**"或" **图像 URL**"（请参阅 [向应用启动器添加自定义磁贴](#add-a-custom-tile-to-the-app-launcher)）。</span><span class="sxs-lookup"><span data-stu-id="a965f-134">Update the **Tile name**, **URL**, **Description**, or **Image URL** for the custom tile (see [Add a custom tile to the app launcher](#add-a-custom-tile-to-the-app-launcher)).</span></span>
    
4. <span data-ttu-id="a965f-135">选择 **"更新** \> **关闭"。**</span><span class="sxs-lookup"><span data-stu-id="a965f-135">Select **Update** \> **Close**.</span></span> 
    
<span data-ttu-id="a965f-136">若要删除自定义磁贴，请在"自定义磁贴"窗口中，选择该磁贴，选择"**删除磁贴""**  >  **删除"。**</span><span class="sxs-lookup"><span data-stu-id="a965f-136">To delete a custom tile, from the **Custom tiles** window, select the tile, select **Remove tile** > **Delete**.</span></span> 
  
## <a name="whats-next"></a><span data-ttu-id="a965f-137">下一步做什么？</span><span class="sxs-lookup"><span data-stu-id="a965f-137">What's next?</span></span>

<span data-ttu-id="a965f-138">除了向应用启动器添加磁贴外，还可以将应用启动器磁贴添加到导航 ([了解) 。](https://support.microsoft.com/office/eb34a21b-52fa-4fbf-a8d5-146132242985)</span><span class="sxs-lookup"><span data-stu-id="a965f-138">In addition to adding tiles to the app launcher, you can add app launcher tiles to the navigation bar ([learn more](https://support.microsoft.com/office/eb34a21b-52fa-4fbf-a8d5-146132242985)).</span></span> <span data-ttu-id="a965f-139">若要自定义 Microsoft 365 的外观以匹配组织的品牌，请参阅自定义 Microsoft [365 主题](../setup/customize-your-organization-theme.md)。</span><span class="sxs-lookup"><span data-stu-id="a965f-139">To customize the look and feel of Microsoft 365 to match your organization's brand, see [Customize the Microsoft 365 theme](../setup/customize-your-organization-theme.md).</span></span>
