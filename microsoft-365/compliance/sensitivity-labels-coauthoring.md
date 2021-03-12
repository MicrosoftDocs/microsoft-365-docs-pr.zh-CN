---
title: 为 Microsoft 365 中敏感度标签加密的文档启用共同创作
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
ms.topic: article
description: 打开对 SharePoint 和 OneDrive 中标记和加密的文档启用共同创作和自动保存的设置。
ms.openlocfilehash: d26696530ed86e6608b6473fead0775fb07a060b
ms.sourcegitcommit: 375168ee66be862cf3b00f2733c7be02e63408cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2021
ms.locfileid: "50454633"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a><span data-ttu-id="7f11c-103">为使用敏感度标签加密的文件启用共同创作</span><span class="sxs-lookup"><span data-stu-id="7f11c-103">Enable co-authoring for files encrypted with sensitivity labels</span></span>

><span data-ttu-id="7f11c-104">*[Microsoft 365 安全性与合规性许可指南](https://aka.ms/ComplianceSD)。*</span><span class="sxs-lookup"><span data-stu-id="7f11c-104">*[Microsoft 365 licensing guidance for security & compliance](https://aka.ms/ComplianceSD).*</span></span>

> [!NOTE]
> <span data-ttu-id="7f11c-105">此功能暂处于预览阶段，可能会发生变更。</span><span class="sxs-lookup"><span data-stu-id="7f11c-105">This feature is in preview and subject to change.</span></span> 
>
> <span data-ttu-id="7f11c-106">在测试租户中（而不是生产租户）中启用此功能，原因：</span><span class="sxs-lookup"><span data-stu-id="7f11c-106">Enable this feature in a test tenant rather than a production tenant because:</span></span>
> - <span data-ttu-id="7f11c-107">此功能将更改标记元数据，并非所有平台上的所有应用当前都支持此更改</span><span class="sxs-lookup"><span data-stu-id="7f11c-107">This feature makes changes to labeling metadata and not all apps on all platforms currently support this change</span></span>
> - <span data-ttu-id="7f11c-108">启用此功能后，无法自己禁用此功能</span><span class="sxs-lookup"><span data-stu-id="7f11c-108">You cannot disable this feature yourself after it is enabled</span></span>

<span data-ttu-id="7f11c-109">启用此设置以支持 Office 桌面应用的 [共同创作](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) ，以便当通过 [敏感度标签](sensitivity-labels.md)标记和加密文档时，多个用户可以同时编辑这些文档。</span><span class="sxs-lookup"><span data-stu-id="7f11c-109">Enable the setting to support [co-authoring](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) for Office desktop apps so that when documents are labeled and encrypted by [sensitivity labels](sensitivity-labels.md), multiple users can edit these documents at the same time.</span></span>

<span data-ttu-id="7f11c-110">如果不为租户启用此设置，用户必须在使用 Office 桌面应用时签出存储在 SharePoint 或 OneDrive 中的加密文档。</span><span class="sxs-lookup"><span data-stu-id="7f11c-110">Without this setting enabled for your tenant, users must check out an encrypted document stored in SharePoint or OneDrive when they use Office desktop apps.</span></span> <span data-ttu-id="7f11c-111">因此，他们无法实时协作。</span><span class="sxs-lookup"><span data-stu-id="7f11c-111">As a result, they can't collaborate in real time.</span></span> <span data-ttu-id="7f11c-112">或者，当为 SharePoint 和 OneDrive 中的 Office [启用敏感度标签时，必须使用 Office 网页](sensitivity-labels-sharepoint-onedrive-files.md)。</span><span class="sxs-lookup"><span data-stu-id="7f11c-112">Or, they must use Office on the web when [sensitivity labels are enabled for Office files in SharePoint and OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).</span></span>

<span data-ttu-id="7f11c-113">此外，启用此功能可实现 [和](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) 的文件都支持自动保存和自动保存功能。</span><span class="sxs-lookup"><span data-stu-id="7f11c-113">In addition, enabling this functionality results in the [AutoSave](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) functionality being supported for these labeled and encrypted files.</span></span>

<span data-ttu-id="7f11c-114">若要阅读发布公告，请参阅文章《宣布 [Microsoft 信息保护加密文档共同创作》并标记](https://techcommunity.microsoft.com/t5/microsoft-security-and/announcing-co-authoring-on-microsoft-information-protection/ba-p/2164162)。</span><span class="sxs-lookup"><span data-stu-id="7f11c-114">To read the release announcement, see the blog post [Announcing co-authoring on Microsoft Information Protection-encrypted documents and labeling updates](https://techcommunity.microsoft.com/t5/microsoft-security-and/announcing-co-authoring-on-microsoft-information-protection/ba-p/2164162).</span></span>

## <a name="metadata-changes-for-sensitivity-labels"></a><span data-ttu-id="7f11c-115">敏感度标签的元数据更改</span><span class="sxs-lookup"><span data-stu-id="7f11c-115">Metadata changes for sensitivity labels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f11c-116">启用共同创作的设置后，未加密文件的标签信息不再保存在自定义属性中。</span><span class="sxs-lookup"><span data-stu-id="7f11c-116">After you enable the setting for co-authoring, labeling information for unencrypted files is no longer saved in custom properties.</span></span>
> 
> <span data-ttu-id="7f11c-117">如果组织中具有用于将标签元数据读或写到旧位置的任何应用、服务、脚本或工具，请不要启用此设置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-117">Do not enable this setting if you use any apps, services, scripts, or tools that reads or writes labeling metadata to the old location.</span></span>

<span data-ttu-id="7f11c-118">启用此设置以支持 Office 桌面应用共同创作之前，了解此操作对保存到 Office 文件并读取的标签元数据的更改非常重要。</span><span class="sxs-lookup"><span data-stu-id="7f11c-118">Before you enable the setting to support co-authoring for Office desktop apps, it's important to understand that this action makes changes to the labeling metadata that is saved to and read from Office files.</span></span>

<span data-ttu-id="7f11c-119">标签元数据包含标识租户和应用敏感度标签的信息。</span><span class="sxs-lookup"><span data-stu-id="7f11c-119">The labeling metadata includes information that identifies your tenant and applied sensitivity label.</span></span> <span data-ttu-id="7f11c-120">此设置更改为 Word、Excel 和 PowerPoint 未加密文件的元数据格式和位置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-120">The change that this setting makes is the metadata format and location for unencrypted files for Word, Excel, and PowerPoint.</span></span> <span data-ttu-id="7f11c-121">加密文件或电子邮件没有标记元数据的更改。</span><span class="sxs-lookup"><span data-stu-id="7f11c-121">There are no labeling metadata changes for encrypted files or emails.</span></span>

<span data-ttu-id="7f11c-122">此更改将影响新标签的文件和已标记的文件。</span><span class="sxs-lookup"><span data-stu-id="7f11c-122">This change affects both files that are newly labeled and files that are already labeled.</span></span> <span data-ttu-id="7f11c-123">使用支持共同创作设置的应用和服务时：</span><span class="sxs-lookup"><span data-stu-id="7f11c-123">When you use apps and services that support the co-authoring setting:</span></span>
- <span data-ttu-id="7f11c-124">对于新标记的文件，仅将新格式和位置用于标签元数据。</span><span class="sxs-lookup"><span data-stu-id="7f11c-124">For files that are newly labeled, only the new format and location is used for the labeling metadata.</span></span>
- <span data-ttu-id="7f11c-125">对于已标记的文件，如果文件具有旧格式和位置的元数据，则下次打开和保存该文件时，该格式将复制到新格式和位置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-125">For files that are already labeled, the next time the file is opened and saved, if the file has metadata in the old format and location, it is copied to the new format and location.</span></span>

<span data-ttu-id="7f11c-126">可以从以下资源中阅读有关此元数据更改更多内容：</span><span class="sxs-lookup"><span data-stu-id="7f11c-126">You can read more about this metadata change from the following resources:</span></span>

- <span data-ttu-id="7f11c-127">博客文章： [即将推出的 Microsoft 信息保护元数据存储更改](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)</span><span class="sxs-lookup"><span data-stu-id="7f11c-127">Blog post: [Upcoming Changes to Microsoft Information Protection Metadata Storage](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)</span></span>

- <span data-ttu-id="7f11c-128">打开规范： [2.6.3 LabelInfo 与自定义文档属性对比](https://docs.microsoft.com/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)</span><span class="sxs-lookup"><span data-stu-id="7f11c-128">Open Specifications: [2.6.3 LabelInfo versus Custom Document Properties](https://docs.microsoft.com/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)</span></span>

<span data-ttu-id="7f11c-129">由于这些更改，如果你的组织具有将标签元数据读或写到旧位置的任何应用、服务、脚本或工具，则不要启用此设置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-129">Because of these changes, do not enable this setting if you have any apps, services, scripts, or tools in your organization that reads or writes labeling metadata to the old location.</span></span> <span data-ttu-id="7f11c-130">如果这样做，某些示例会产生什么影响：</span><span class="sxs-lookup"><span data-stu-id="7f11c-130">If you do, some example consequences:</span></span>

- <span data-ttu-id="7f11c-131">标记的文档将出现在用户未标记</span><span class="sxs-lookup"><span data-stu-id="7f11c-131">A document that is labeled appears to users to be unlabeled</span></span>

- <span data-ttu-id="7f11c-132">向用户显示过期标签的文档</span><span class="sxs-lookup"><span data-stu-id="7f11c-132">A document displays an out-of-date label to users</span></span>

- <span data-ttu-id="7f11c-133">如果其他用户在不支持新标签元数据的 Office 桌面应用中打开标签文档，则共同创作和自动保存将不起作用</span><span class="sxs-lookup"><span data-stu-id="7f11c-133">Co-authoring and AutoSave won't work for a labeled and encrypted document if another user has it open in an Office desktop app that doesn't support the new labeling metadata</span></span>

- <span data-ttu-id="7f11c-134">将标签标识为 Office 附件中的自定义 [Exchange Online 邮件流规则](https://docs.microsoft.com/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) 无法加密电子邮件和附件，或错误地加密它们</span><span class="sxs-lookup"><span data-stu-id="7f11c-134">An Exchange Online mail flow rule that [identifies labels as custom properties in Office attachments](https://docs.microsoft.com/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) fails to encrypt the email and attachment, or incorrectly encrypts them</span></span>

<span data-ttu-id="7f11c-135">查看下一部分，查看支持此设置以及标签元数据的更改的应用和服务列表。</span><span class="sxs-lookup"><span data-stu-id="7f11c-135">Check the following section for a list of apps and services that support this setting and the changes to the labeling metadata.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f11c-136">先决条件</span><span class="sxs-lookup"><span data-stu-id="7f11c-136">Prerequisites</span></span>

<span data-ttu-id="7f11c-137">启用此功能前，请确保了解以下先决条件。</span><span class="sxs-lookup"><span data-stu-id="7f11c-137">Make sure you understand the following prerequisites before you turn on this feature.</span></span>

- <span data-ttu-id="7f11c-138">必须为此预览使用测试租户。</span><span class="sxs-lookup"><span data-stu-id="7f11c-138">You must use a test tenant for this preview.</span></span>

- <span data-ttu-id="7f11c-139">只有全局管理员才能启用此功能。</span><span class="sxs-lookup"><span data-stu-id="7f11c-139">You must be a global admin to turn on this feature.</span></span>

- <span data-ttu-id="7f11c-140">必须为租户启用 [SharePoint 和 OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) 敏感度标签。</span><span class="sxs-lookup"><span data-stu-id="7f11c-140">Sensitivity labels must be [enabled for Office files in SharePoint and OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) for the tenant.</span></span> <span data-ttu-id="7f11c-141">如果尚未启用此功能，则当选择为具有敏感度标签的文件启用共同创作的设置时，将自动启用此功能。</span><span class="sxs-lookup"><span data-stu-id="7f11c-141">If this feature isn't already enabled, it will be automatically enabled when you select the setting to turn on co-authoring for files with sensitivity labels.</span></span>

- <span data-ttu-id="7f11c-142">适用于企业的 Microsoft 365 应用：</span><span class="sxs-lookup"><span data-stu-id="7f11c-142">Microsoft 365 Apps for enterprise:</span></span>
    - <span data-ttu-id="7f11c-143">**Windows**[：拥有最低内部版本 16.0.13801.20182 或 [Beta 频道](https://office.com/insider) 最低版本 16.0.13819.20006 的](https://office.com/insider) 当前频道（预览版）</span><span class="sxs-lookup"><span data-stu-id="7f11c-143">**Windows**: [Current Channel (Preview)](https://office.com/insider) with minimum build 16.0.13801.20182, or [Beta Channel](https://office.com/insider) with minimum build 16.0.13819.20006</span></span>
    - <span data-ttu-id="7f11c-144">**macOS**： [Beta](https://office.com/insider) 16.47.218.0 最低内部版本</span><span class="sxs-lookup"><span data-stu-id="7f11c-144">**macOS**: [Beta Channel](https://office.com/insider) with minimal build 16.47.218.0</span></span>
    - <span data-ttu-id="7f11c-145">**iOS**：尚不支持</span><span class="sxs-lookup"><span data-stu-id="7f11c-145">**iOS**: Not yet supported</span></span>
    - <span data-ttu-id="7f11c-146">**Android**：尚不支持</span><span class="sxs-lookup"><span data-stu-id="7f11c-146">**Android**: Not yet supported</span></span>

- <span data-ttu-id="7f11c-147">租户中所有应用、服务和操作工具必须支持用于标记元数据 [的新](#metadata-changes-for-sensitivity-labels)。</span><span class="sxs-lookup"><span data-stu-id="7f11c-147">All apps, services, and operational tools in your tenant must support the new [labeling metadata](#metadata-changes-for-sensitivity-labels).</span></span> <span data-ttu-id="7f11c-148">如果你使用以下任一方法，请检查所需的最低版本：</span><span class="sxs-lookup"><span data-stu-id="7f11c-148">If you use any of the following, check the minimum versions required:</span></span>
    
    - <span data-ttu-id="7f11c-149">**Azure 信息保护统一标签客户端和扫描仪：**</span><span class="sxs-lookup"><span data-stu-id="7f11c-149">**Azure Information Protection unified labeling client and scanner:**</span></span>
        - <span data-ttu-id="7f11c-150">可从 [Microsoft 下载中心安装的公共预览版本（AzInfoProtection_2.10.46_CoAuthoring_PublicPreview.exe）](https://www.microsoft.com/en-us/download/details.aspx?id=53018)</span><span class="sxs-lookup"><span data-stu-id="7f11c-150">A public preview version (installation name of AzInfoProtection_2.10.46_CoAuthoring_PublicPreview.exe) that you can install from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)</span></span>
    
    - <span data-ttu-id="7f11c-151">**适用于 Windows 或 macOS 的 OneDrive 同步应用：**</span><span class="sxs-lookup"><span data-stu-id="7f11c-151">**OneDrive sync app for Windows or macOS:**</span></span>
        - <span data-ttu-id="7f11c-152">最低版本 19.002.0121.0008</span><span class="sxs-lookup"><span data-stu-id="7f11c-152">Minimum version of 19.002.0121.0008</span></span>
    
    - <span data-ttu-id="7f11c-153">**终结点数据丢失防护 （Endpoint DLP）：**</span><span class="sxs-lookup"><span data-stu-id="7f11c-153">**Endpoint data loss prevention (Endpoint DLP):**</span></span>
        - <span data-ttu-id="7f11c-154">Windows 10 1809 KB 4601383</span><span class="sxs-lookup"><span data-stu-id="7f11c-154">Windows 10 1809 with KB 4601383</span></span>
        - <span data-ttu-id="7f11c-155">Windows 10 1903 和 1909，KB 4601380</span><span class="sxs-lookup"><span data-stu-id="7f11c-155">Windows 10 1903 and 1909 with KB 4601380</span></span>
        - <span data-ttu-id="7f11c-156">Windows 10 2004 KB 4601382</span><span class="sxs-lookup"><span data-stu-id="7f11c-156">Windows 10 2004 with KB 4601382</span></span>
    
    - <span data-ttu-id="7f11c-157">**使用 Microsoft 信息保护 SDK 的应用和服务：**</span><span class="sxs-lookup"><span data-stu-id="7f11c-157">**Apps and services that use the Microsoft Information Protection SDK:**</span></span> 
        - <span data-ttu-id="7f11c-158">最低版本 1.7</span><span class="sxs-lookup"><span data-stu-id="7f11c-158">Minimum version of 1.7</span></span> 

<span data-ttu-id="7f11c-159">启用此功能时，Microsoft 365 服务自动支持新的标签元数据。</span><span class="sxs-lookup"><span data-stu-id="7f11c-159">Microsoft 365 services automatically support the new labeling metadata when you turn on this feature.</span></span> <span data-ttu-id="7f11c-160">例如：</span><span class="sxs-lookup"><span data-stu-id="7f11c-160">For example:</span></span>

- [<span data-ttu-id="7f11c-161">自动标记策略</span><span class="sxs-lookup"><span data-stu-id="7f11c-161">Auto-labeling policies</span></span>](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [<span data-ttu-id="7f11c-162">使用敏感度标签作为条件的 DLP 策略</span><span class="sxs-lookup"><span data-stu-id="7f11c-162">DLP policies that use sensitivity labels as conditions</span></span>](dlp-sensitivity-label-as-condition.md)
- [<span data-ttu-id="7f11c-163">Microsoft 云应用安全性已配置为应用敏感度标签</span><span class="sxs-lookup"><span data-stu-id="7f11c-163">Microsoft Cloud App Security configured to apply sensitivity labels</span></span>](https://docs.microsoft.com/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

## <a name="limitations"></a><span data-ttu-id="7f11c-164">限制</span><span class="sxs-lookup"><span data-stu-id="7f11c-164">Limitations</span></span>

<span data-ttu-id="7f11c-165">为使用敏感度标签加密的文件启用租户设置进行共同创作之前，请确保了解此功能的下列限制。</span><span class="sxs-lookup"><span data-stu-id="7f11c-165">Before you enable the tenant setting for co-authoring for files encrypted with sensitivity labels, make sure you understand the following limitations of this feature.</span></span>

- <span data-ttu-id="7f11c-166">由于标签 [元数据的更改](#metadata-changes-for-sensitivity-labels)，租户中的所有应用、服务和操作工具必须支持新的标签元数据，确保标签体验一致且可靠。</span><span class="sxs-lookup"><span data-stu-id="7f11c-166">Because of the [labeling metadata changes](#metadata-changes-for-sensitivity-labels), all apps, services, and operational tools in your tenant must support the new labeling metadata for a consistent and reliable labeling experience.</span></span>
    
    <span data-ttu-id="7f11c-167">特定于 Excel：如果某人使用不支持敏感度标签的元数据更改的 Excel 版本编辑并保存该文件，则不应用加密的敏感度标签的元数据可删除。</span><span class="sxs-lookup"><span data-stu-id="7f11c-167">Specific to Excel: Metadata for a sensitivity label that doesn't apply encryption can be deleted from a file if somebody edits and saves that file by using a version of Excel that doesn't support the metadata changes for sensitivity labels.</span></span>

- <span data-ttu-id="7f11c-168">不支持共同创作和自动保存，并且不支持标签和加密的 Office 文档，这些文档使用下列任何 [配置加密](encryption-sensitivity-labels.md#configure-encryption-settings)：</span><span class="sxs-lookup"><span data-stu-id="7f11c-168">Co-authoring and AutoSave aren't supported and don't work for labeled and encrypted Office documents that use any of the following [configurations for encryption](encryption-sensitivity-labels.md#configure-encryption-settings):</span></span>
    - <span data-ttu-id="7f11c-169">**允许用户在应用标签权限** Word、PowerPoint 和 Excel **复选框时分配权限，提示用户** 权限。</span><span class="sxs-lookup"><span data-stu-id="7f11c-169">**Let users assign permissions when they apply the label** and the checkbox **In Word, PowerPoint, and Excel, prompt users to specify permissions** is selected.</span></span> <span data-ttu-id="7f11c-170">此配置有时称为"用户定义的权限"。</span><span class="sxs-lookup"><span data-stu-id="7f11c-170">This configuration is sometimes referred to as "user-defined permissions".</span></span>
    - <span data-ttu-id="7f11c-171">**将内容的访问权限设置为** 一个值，则对内容 **从不**。</span><span class="sxs-lookup"><span data-stu-id="7f11c-171">**User access to content expires** is set to a value other than **Never**.</span></span>
    - <span data-ttu-id="7f11c-172">**选择了双** 加密技术。</span><span class="sxs-lookup"><span data-stu-id="7f11c-172">**Double Key Encryption** is selected.</span></span>
    
    <span data-ttu-id="7f11c-173">对于采用以上任何加密配置的标签，标签会显示在 Office 应用中。</span><span class="sxs-lookup"><span data-stu-id="7f11c-173">For labels with any of these encryption configurations, the labels display in Office apps.</span></span> <span data-ttu-id="7f11c-174">但是，当用户选择这些标签，而其他人正在编辑文档时，你会警告他们共同创作且自动保存将不可用。</span><span class="sxs-lookup"><span data-stu-id="7f11c-174">However, when users select these labels and nobody else is editing the document, they are warned that co-authoring and AutoSave won't be available.</span></span> <span data-ttu-id="7f11c-175">如果其他人正在编辑文档，用户会看到一条消息，指出标签无法应用。</span><span class="sxs-lookup"><span data-stu-id="7f11c-175">If somebody else is editing the document, users see a message that the labels can't be applied.</span></span>

- <span data-ttu-id="7f11c-176">如果使用 Azure 信息保护统一标签客户端：查看此标签客户端的文档， [要求或限制](https://docs.microsoft.com/azure/information-protection/known-issues#known-issues-for-co-authoring-public-preview)。</span><span class="sxs-lookup"><span data-stu-id="7f11c-176">If you use the Azure Information Protection unified labeling client: Check the documentation for this labeling client for [more requirements or limitations](https://docs.microsoft.com/azure/information-protection/known-issues#known-issues-for-co-authoring-public-preview).</span></span>

## <a name="known-issues-for-this-preview"></a><span data-ttu-id="7f11c-177">此预览的已知问题</span><span class="sxs-lookup"><span data-stu-id="7f11c-177">Known issues for this preview</span></span>

<span data-ttu-id="7f11c-178">对于使用敏感度标签加密的文件，此预览版共同创作具有下列已知问题：</span><span class="sxs-lookup"><span data-stu-id="7f11c-178">This preview version of co-authoring for files encrypted with sensitivity labels has the following known issues:</span></span>

- <span data-ttu-id="7f11c-179">用户对于大于 300 MB 的 Word、Excel 和 PowerPoint 文件，不能对 Office 网页版应用任何标签。</span><span class="sxs-lookup"><span data-stu-id="7f11c-179">Users won't be able to apply any labels in Office for the web for Word, Excel, and PowerPoint files that are bigger than 300 MB.</span></span> <span data-ttu-id="7f11c-180">对于这些文件，可以使用 Office 桌面应用应用标签，但只有你才能打开文件。</span><span class="sxs-lookup"><span data-stu-id="7f11c-180">For these files, you can use the Office desktop apps to apply a label but you must be the only person who has the file open.</span></span>

- <span data-ttu-id="7f11c-181">当你使用 [敏感标签作为条件](dlp-sensitivity-label-as-condition.md)DLP 策略时，不支持电子邮件的未加密附件。</span><span class="sxs-lookup"><span data-stu-id="7f11c-181">When you use [DLP policies that use sensitivity labels as conditions](dlp-sensitivity-label-as-condition.md), unencrypted attachments for emails are not supported.</span></span>

- <span data-ttu-id="7f11c-182">不支持适用于 iOS 和 Android 的 Office 应用。</span><span class="sxs-lookup"><span data-stu-id="7f11c-182">Office apps for iOS and Android are not supported.</span></span>

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a><span data-ttu-id="7f11c-183">如何为具有敏感度标签的文件启用共同创作</span><span class="sxs-lookup"><span data-stu-id="7f11c-183">How to enable co-authoring for files with sensitivity labels</span></span>

> [!CAUTION]
> <span data-ttu-id="7f11c-184">打开此设置是一种单向操作。</span><span class="sxs-lookup"><span data-stu-id="7f11c-184">Turning on this setting is a one-way action.</span></span> <span data-ttu-id="7f11c-185">此功能在预览版中，仅在非生产环境中进行测试，且仅在阅读和理解该页上记录的任何元数据更改、先决条件、限制和任何已知问题后才能进行测试。</span><span class="sxs-lookup"><span data-stu-id="7f11c-185">While the feature is in preview, test it only in a non-production environment and only after you have read and understood the metadata changes, prerequisites, limitations, and any known issues documented on this page.</span></span>

<span data-ttu-id="7f11c-186">在预览期间，必须使用特定 URL 访问 Microsoft 365 合规中心中的此设置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-186">During the preview, you must use a specific URL to access this setting in the Microsoft 365 compliance center.</span></span>

1. <span data-ttu-id="7f11c-187">使用以下链接，以测试租户的全局管理员角色登录 Microsoft 365 合规中心：</span><span class="sxs-lookup"><span data-stu-id="7f11c-187">Sign in to the Microsoft 365 compliance center as a global admin for your test tenant, using the following link:</span></span>
    
    ```http
    https://compliance.microsoft.com/co-authoring_for_files_with_sensitivity_labels
    ```
    <span data-ttu-id="7f11c-188">此链接将直接进入租户设置，为具有敏感度标签 **创建共同**。</span><span class="sxs-lookup"><span data-stu-id="7f11c-188">This link takes you directly to the tenant setting, **Co-authoring for files with sensitivity labels**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7f11c-189">在继续之前，请检查是否登录到了对用户没有影响的测试租户：</span><span class="sxs-lookup"><span data-stu-id="7f11c-189">Before you continue, check you're signed in to a test tenant that won't affect your users:</span></span> 
    >
    > <span data-ttu-id="7f11c-190">在合规中心右上方选择带帐户缩写的圆圈，然后确认租户名称是否显示预期测试租户。</span><span class="sxs-lookup"><span data-stu-id="7f11c-190">Select the circle with your account initials in the top right of the compliance center, and confirm that the tenant name does display your intended test tenant.</span></span>
    
2. <span data-ttu-id="7f11c-191">阅读摘要说明、先决条件、预期内容以及打开此设置后无法关闭此设置的警告。</span><span class="sxs-lookup"><span data-stu-id="7f11c-191">Read the summary description, prerequisites, what to expect, and the warning that you can't turn off this setting after you've turned it on.</span></span> <span data-ttu-id="7f11c-192">然后选择 **针对具有敏感度标签的文件启用共同创作**， **应用**：</span><span class="sxs-lookup"><span data-stu-id="7f11c-192">Then select **Turn on co-authoring for files with sensitivity labels**, and **Apply**:</span></span>
    
    ![为具有敏感度标签的文件启用共同创作的选项](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. <span data-ttu-id="7f11c-194">请等待 24 小时，让此设置复制整个环境，然后再测试此新功能进行共同创作。</span><span class="sxs-lookup"><span data-stu-id="7f11c-194">Wait 24 hours for this setting to replicate across your environment before you test this new feature for co-authoring.</span></span>

## <a name="contact-support-if-you-need-to-disable-this-feature"></a><span data-ttu-id="7f11c-195">如果需要禁用此功能，请联系支持人员</span><span class="sxs-lookup"><span data-stu-id="7f11c-195">Contact Support if you need to disable this feature</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f11c-196">如果需要禁用此功能，请注意标签信息可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="7f11c-196">If you do need to disable this feature, be aware that labeling information can be lost.</span></span>

<span data-ttu-id="7f11c-197">为具有租户的敏感度标签的文件启用共同创作后，无法自己禁用此设置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-197">After you've enabled co-authoring for files with sensitivity labels for your tenant, you can't disable this setting yourself.</span></span> <span data-ttu-id="7f11c-198">因此，在启用此设置之前，必须检查并了解先决条件、结果和限制，这一点至关重要。</span><span class="sxs-lookup"><span data-stu-id="7f11c-198">That's why it's so important that you check and understand the prerequisites, consequences, and limitations before you enable this setting.</span></span> <span data-ttu-id="7f11c-199">这也是建议使用测试租户（而不是生产租户）测试此功能的原因。</span><span class="sxs-lookup"><span data-stu-id="7f11c-199">It's also why we recommend that you test this feature with a test tenant rather than a production tenant.</span></span>

![显示针对敏感度标签开启共同创作的选项](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

<span data-ttu-id="7f11c-201">如在打开此设置时从屏幕截图中看到的，可联系 Microsoft [支持人员](https://docs.microsoft.com/office365/admin/contact-support-for-business-products) 请求关闭此设置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-201">As you see from the screenshot when this setting has been turned on, you can contact [Microsoft Support](https://docs.microsoft.com/office365/admin/contact-support-for-business-products) and request to turn off this setting.</span></span> <span data-ttu-id="7f11c-202">此请求可能需要几天时间，并且你需要证明你是租户的全局管理员。</span><span class="sxs-lookup"><span data-stu-id="7f11c-202">This request might take several days and you will need to prove that you are a global administrator for your tenant.</span></span> <span data-ttu-id="7f11c-203">通常需要支付支持费用。</span><span class="sxs-lookup"><span data-stu-id="7f11c-203">Expect usual support charges to apply.</span></span> 

<span data-ttu-id="7f11c-204">如果支持工程师为租户禁用此设置：</span><span class="sxs-lookup"><span data-stu-id="7f11c-204">If a support engineer disables this setting for your tenant:</span></span>

- <span data-ttu-id="7f11c-205">对于支持新的标签元数据的应用和服务，读取或保存标签时，它们现在将还原为原始元数据格式和位置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-205">For apps and services that support the new labeling metadata, they now revert to the original metadata format and location when labels are read or saved.</span></span>

- <span data-ttu-id="7f11c-206">启用设置时使用的 Office 文档的新元数据格式和位置不会复制到原始格式和位置。</span><span class="sxs-lookup"><span data-stu-id="7f11c-206">The new metadata format and location for Office documents that were used while the setting was enabled will not be copied to the original format and location.</span></span> <span data-ttu-id="7f11c-207">因此，此未加密 Word、Excel 和 PowerPoint 文件的标记信息将会丢失。</span><span class="sxs-lookup"><span data-stu-id="7f11c-207">As a result, this labeling information for unencrypted Word, Excel, and PowerPoint files will be lost.</span></span>

- <span data-ttu-id="7f11c-208">共同创作和自动保存在租户中不再有效。</span><span class="sxs-lookup"><span data-stu-id="7f11c-208">Co-authoring and AutoSave no longer work in your tenant.</span></span>

- <span data-ttu-id="7f11c-209">对 OneDrive 和 SharePoint 中的 Office 文件，敏感度标签保持启用状态。</span><span class="sxs-lookup"><span data-stu-id="7f11c-209">Sensitivity labels remain enabled for Office files in OneDrive and SharePoint.</span></span>