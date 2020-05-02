---
title: 在文档中与来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
ms.custom:
- M365solutions
localization_priority: Normal
f1.keywords: NOCSH
description: 了解如何通过 SharePoint 和 OneDrive 中的文档与来宾进行协作。
ms.openlocfilehash: 33d9300343b23702d5024ac0b489930ac815be7e
ms.sourcegitcommit: 101084f9c81616342d78493232d8f13f5ffa4ddf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "44002261"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="20480-103">在文档中与来宾协作</span><span class="sxs-lookup"><span data-stu-id="20480-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="20480-104">如果需要与组织外部的人员协作处理 SharePoint 或 OneDrive 中的文档，则可以向其发送指向文档的共享链接。</span><span class="sxs-lookup"><span data-stu-id="20480-104">If you need to collaborate with people outside your organization on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="20480-105">在本文中，我们将完成必要的 Microsoft 365 配置步骤，以设置 SharePoint 和 OneDrive 的共享链接，以满足组织的需求。</span><span class="sxs-lookup"><span data-stu-id="20480-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive for the needs of your organization.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="20480-106">视频演示</span><span class="sxs-lookup"><span data-stu-id="20480-106">Video demonstration</span></span>

<span data-ttu-id="20480-107">该视频显示了本文档中描述的配置步骤。</span><span class="sxs-lookup"><span data-stu-id="20480-107">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="20480-108">Azure 组织关系设置</span><span class="sxs-lookup"><span data-stu-id="20480-108">Azure Organizational relationships settings</span></span>

<span data-ttu-id="20480-109">Microsoft 365 中的共享受 Azure Active Directory 中的组织关系设置的最高级别的管辖。</span><span class="sxs-lookup"><span data-stu-id="20480-109">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="20480-110">如果在 Azure AD 中禁用或限制来宾共享，这将替代您在 Microsoft 365 中配置的任何共享设置。</span><span class="sxs-lookup"><span data-stu-id="20480-110">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="20480-111">检查组织关系设置以确保不会阻止与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="20480-111">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory 组织关系设置页面的屏幕截图](../media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="20480-113">设置组织关系设置</span><span class="sxs-lookup"><span data-stu-id="20480-113">To set organizational relationship settings</span></span>

1. <span data-ttu-id="20480-114">登录到 Microsoft Azure [https://portal.azure.com](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="20480-114">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="20480-115">在左侧导航中，单击 " **Azure Active Directory**"。</span><span class="sxs-lookup"><span data-stu-id="20480-115">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="20480-116">在 "**概述**" 窗格中，单击 "**组织关系**"。</span><span class="sxs-lookup"><span data-stu-id="20480-116">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="20480-117">在 "**组织关系**" 窗格中，单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="20480-117">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="20480-118">确保**来宾邀请者角色中的管理员和用户可以邀请**和**成员**都可以邀请都设置为 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="20480-118">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="20480-119">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="20480-119">If you made changes, click **Save**.</span></span>

<span data-ttu-id="20480-120">请注意 "**协作限制**" 部分中的设置。</span><span class="sxs-lookup"><span data-stu-id="20480-120">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="20480-121">确保不会阻止您要与之进行协作的来宾域。</span><span class="sxs-lookup"><span data-stu-id="20480-121">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="20480-122">SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="20480-122">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="20480-123">为使组织外部的人员能够访问 SharePoint 或 OneDrive 中的文档，SharePoint 和 OneDrive 组织级共享设置必须允许与组织外部的人员共享。</span><span class="sxs-lookup"><span data-stu-id="20480-123">In order for people outside your organization to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with people outside your organization.</span></span>

<span data-ttu-id="20480-124">SharePoint 的组织级设置决定了各个 SharePoint 网站可用的设置。</span><span class="sxs-lookup"><span data-stu-id="20480-124">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="20480-125">网站设置不能比组织级别设置更具有更好的许可。</span><span class="sxs-lookup"><span data-stu-id="20480-125">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="20480-126">OneDrive 的组织级别设置决定了用户的 OneDrive 库中可用的共享级别。</span><span class="sxs-lookup"><span data-stu-id="20480-126">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="20480-127">对于 SharePoint 和 OneDrive，如果要允许未经身份验证的文件和文件夹共享，请选择 "**任何人**"。</span><span class="sxs-lookup"><span data-stu-id="20480-127">For SharePoint and OneDrive, if you want to allow unauthenticated file and folder sharing, choose **Anyone**.</span></span> <span data-ttu-id="20480-128">如果您想要确保组织外部的人员必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。</span><span class="sxs-lookup"><span data-stu-id="20480-128">If you want to ensure that people outside your organization have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="20480-129">*任何*链接都是最简单的共享方式：组织外部的人员可以在不进行身份验证的情况下打开链接，并且可以自由地将其传递给其他人。</span><span class="sxs-lookup"><span data-stu-id="20480-129">*Anyone* links are the easiest way to share: people outside your organization can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="20480-130">对于 SharePoint，选择组织中的任何网站将需要的 "最高" 设置。</span><span class="sxs-lookup"><span data-stu-id="20480-130">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 组织级别共享设置的屏幕截图](../media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="20480-132">设置 SharePoint 组织级别的共享设置</span><span class="sxs-lookup"><span data-stu-id="20480-132">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="20480-133">在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="20480-133">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="20480-134">在 SharePoint 管理中心的左侧导航栏中，单击 **“共享”**。</span><span class="sxs-lookup"><span data-stu-id="20480-134">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="20480-135">确保将 SharePoint 或 OneDrive 的外部共享设置为 "**任何人**" 或**新的和现有的来宾**。</span><span class="sxs-lookup"><span data-stu-id="20480-135">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="20480-136">（请注意，OneDrive 设置不能比 SharePoint 设置更具许可。）</span><span class="sxs-lookup"><span data-stu-id="20480-136">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="20480-137">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="20480-137">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="20480-138">SharePoint 组织级别的默认链接设置</span><span class="sxs-lookup"><span data-stu-id="20480-138">SharePoint organization level default link settings</span></span>

<span data-ttu-id="20480-139">默认的文件和文件夹链接设置确定在用户共享文件或文件夹时，默认情况下向用户显示的链接选项。</span><span class="sxs-lookup"><span data-stu-id="20480-139">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="20480-140">如果需要，用户可以在共享之前将链接类型更改为其他选项之一。</span><span class="sxs-lookup"><span data-stu-id="20480-140">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="20480-141">请注意，此设置会影响组织中的 SharePoint 网站以及 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="20480-141">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="20480-142">选择当用户共享文件和文件夹时默认选择的链接类型：</span><span class="sxs-lookup"><span data-stu-id="20480-142">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="20480-143">**任何具有链接的人**-如果您想要执行大量未经身份验证的文件和文件夹共享，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="20480-143">**Anyone with the link** - Choose this option if you expect to do a lot of unauthenticated file and folder sharing.</span></span> <span data-ttu-id="20480-144">如果要允许*任何人*链接，但担心意外的共享，请考虑其他选项之一作为默认选项。</span><span class="sxs-lookup"><span data-stu-id="20480-144">If you want to allow *Anyone* links but are concerned about accidental unauthenticated sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="20480-145">仅当您已启用**任何**共享时，此链接类型才可用。</span><span class="sxs-lookup"><span data-stu-id="20480-145">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="20480-146">**仅限组织中的人员**-如果您希望大多数文件和文件夹共享与组织内部的人员共享，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="20480-146">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="20480-147">**特定人员**-如果您希望对来宾执行大量文件和文件夹共享，请考虑此选项。</span><span class="sxs-lookup"><span data-stu-id="20480-147">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="20480-148">此类型的链接可与来宾配合使用，并要求用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="20480-148">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint 组织级别文件和文件夹共享设置的屏幕截图](../media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="20480-150">设置 SharePoint 和 OneDrive 组织级别默认链接设置</span><span class="sxs-lookup"><span data-stu-id="20480-150">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="20480-151">导航到 SharePoint 管理中心中的 "共享" 页面。</span><span class="sxs-lookup"><span data-stu-id="20480-151">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="20480-152">在 "**文件和文件夹链接**" 下，选择要使用的默认共享链接。</span><span class="sxs-lookup"><span data-stu-id="20480-152">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="20480-153">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="20480-153">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="20480-154">SharePoint 网站级别共享设置</span><span class="sxs-lookup"><span data-stu-id="20480-154">SharePoint site level sharing settings</span></span>

<span data-ttu-id="20480-155">如果要共享 SharePoint 网站中的文件和 fodlers，则还需要检查该网站的网站级共享设置。</span><span class="sxs-lookup"><span data-stu-id="20480-155">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![SharePoint 网站外部共享设置的屏幕截图](../media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="20480-157">设置网站级共享设置</span><span class="sxs-lookup"><span data-stu-id="20480-157">To set site-level sharing settings</span></span>
1. <span data-ttu-id="20480-158">在 SharePoint 管理中心的左侧导航栏中，展开 **“站点”**，然后单击 **“活动站点”**。</span><span class="sxs-lookup"><span data-stu-id="20480-158">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="20480-159">选择您刚刚创建的网站。</span><span class="sxs-lookup"><span data-stu-id="20480-159">Select the site that you just created.</span></span>
3. <span data-ttu-id="20480-160">在功能区中，单击 **“共享”**。</span><span class="sxs-lookup"><span data-stu-id="20480-160">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="20480-161">确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。</span><span class="sxs-lookup"><span data-stu-id="20480-161">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="20480-162">如果进行了任何更改，请单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="20480-162">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="20480-163">邀请用户</span><span class="sxs-lookup"><span data-stu-id="20480-163">Invite users</span></span>

<span data-ttu-id="20480-164">现在已配置来宾共享设置，因此用户现在可以与组织外部的人员共享文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="20480-164">Guest sharing settings are now configured, so users can now share files and folders with people outside your organization.</span></span> <span data-ttu-id="20480-165">有关详细信息，请参阅[共享 OneDrive 文件和文件夹](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)以及[共享 SharePoint 文件或文件夹](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)。</span><span class="sxs-lookup"><span data-stu-id="20480-165">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="20480-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20480-166">See Also</span></span>

[<span data-ttu-id="20480-167">有关与未经认证用户共享文件和文件夹的最佳做法</span><span class="sxs-lookup"><span data-stu-id="20480-167">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="20480-168">与来宾共享时限制文件意外曝光</span><span class="sxs-lookup"><span data-stu-id="20480-168">Limit accidental exposure to files when sharing with guests</span></span>](share-limit-accidental-exposure.md)