---
title: SharePoint Online 经典发布网站的图像优化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: 了解如何使用格式副本和子画面提高 SharePoint Online 经典发布网站上的图像性能。
ms.openlocfilehash: 47d0f085c13c192417842fcef88c695fe875124c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687827"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a><span data-ttu-id="4186a-103">SharePoint Online 经典发布网站的图像优化</span><span class="sxs-lookup"><span data-stu-id="4186a-103">Image optimization for SharePoint Online classic publishing sites</span></span>

<span data-ttu-id="4186a-104">网页的加载速度取决于呈现页面所需的所有组件的总大小，包括图像、HTML、JavaScript 和 CSS。</span><span class="sxs-lookup"><span data-stu-id="4186a-104">The loading speed of a webpage depends on the combined size of all the components required to render the page including images, HTML, JavaScript, and CSS.</span></span> <span data-ttu-id="4186a-105">图像是使网站更具吸引力的一种极好的方式，但其大小可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="4186a-105">Images are a great way to make your site more appealing, but their size can affect performance.</span></span> <span data-ttu-id="4186a-106">通过使用压缩和调整大小以及使用子画面优化图像，可以偏移超大型图像的效果。</span><span class="sxs-lookup"><span data-stu-id="4186a-106">By optimizing your images with compression and resizing, and using sprites, you can offset the effects of very large images.</span></span> <span data-ttu-id="4186a-107">使用 SharePoint 图像呈现形式，可以上传一个大图像，并显示图像的各个部分，以允许重用而不是重新加载图像。</span><span class="sxs-lookup"><span data-stu-id="4186a-107">Using SharePoint image renditions, you can upload a single large image, and display sections of the image allowing it to be reused rather than reloaded.</span></span>

>[!NOTE]
><span data-ttu-id="4186a-108">本主题适用于 SharePoint Online 经典发布网站，而不是新式门户网站。</span><span class="sxs-lookup"><span data-stu-id="4186a-108">This topic applies to SharePoint Online classic publishing sites, not modern portal sites.</span></span> <span data-ttu-id="4186a-109">有关 SharePoint Online 新式门户网站中的图像优化的信息，请参阅 [在 Sharepoint online 新式门户页面中优化图像](modern-image-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="4186a-109">For information about image optimization in SharePoint Online modern portal sites, see [Optimize images in SharePoint Online modern portal pages](modern-image-optimization.md).</span></span>
  
## <a name="using-sprites-to-speed-up-image-loading"></a><span data-ttu-id="4186a-110">使用子画面加快图像加载速度</span><span class="sxs-lookup"><span data-stu-id="4186a-110">Using sprites to speed up image loading</span></span>

|||
|:-----|:-----|
| <span data-ttu-id="4186a-111">图像子画面包含许多较小的图像。</span><span class="sxs-lookup"><span data-stu-id="4186a-111">An image sprite contains many smaller images.</span></span> <span data-ttu-id="4186a-112">使用 CSS 选择复合图像的一部分，以在页面的特定部分显示绝对定位。</span><span class="sxs-lookup"><span data-stu-id="4186a-112">Using CSS you select a part of the composite image to display on a particular part of the page with absolute positioning.</span></span> <span data-ttu-id="4186a-113">通常情况下，您可以在页面上移动单个图像，而不是加载多个图像，并使该图像的一小部分在显示给最终用户的 sprite 图像所需部分的小窗口中可见。</span><span class="sxs-lookup"><span data-stu-id="4186a-113">Basically, you move a single image around the page instead of loading multiple images, and make a small part of that image visible through a small window where the required part of the sprite image is shown to the end user.</span></span> <span data-ttu-id="4186a-114">SharePoint Online 使用子画面在 sprite spcommon.png 中显示其各种图标。</span><span class="sxs-lookup"><span data-stu-id="4186a-114">SharePoint Online uses sprites to display its various icons in the sprite spcommon.png.</span></span>  <br/>  <span data-ttu-id="4186a-115">这里讲述的内容：</span><span class="sxs-lookup"><span data-stu-id="4186a-115">What's covered here:</span></span>  <br/>  <span data-ttu-id="4186a-116">图像压缩</span><span class="sxs-lookup"><span data-stu-id="4186a-116">Image compression</span></span>  <br/>  <span data-ttu-id="4186a-117">图像优化</span><span class="sxs-lookup"><span data-stu-id="4186a-117">Image optimization</span></span>  <br/>  <span data-ttu-id="4186a-118">SharePoint 图像呈现形式</span><span class="sxs-lookup"><span data-stu-id="4186a-118">SharePoint image renditions</span></span>  <br/> |![Spcommon 的屏幕截图](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
<span data-ttu-id="4186a-120">这样可以提高性能，因为只需下载一幅图像而不是多个图像，然后再缓存并重新使用该图像。</span><span class="sxs-lookup"><span data-stu-id="4186a-120">This can increase performance because you download only one image instead of several and then cache and reuse that image.</span></span> <span data-ttu-id="4186a-121">即使图像未保持缓存，通过使用单个图像（而不是多个图像），此方法也可减少对服务器的 HTTP 请求总数，从而减少页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="4186a-121">Even if the image does not remain cached, by having a single image instead of multiple images, this method reduces the total number of HTTP requests to the server which will reduce page loading times.</span></span> <span data-ttu-id="4186a-122">这实际上是一种图像绑定形式。</span><span class="sxs-lookup"><span data-stu-id="4186a-122">This is really a form of image bundling.</span></span> <span data-ttu-id="4186a-123">如果图像不经常更改（如上面提供的 SharePoint 示例中所示），这是一项非常有用的技术。</span><span class="sxs-lookup"><span data-stu-id="4186a-123">This is a very useful technique if the images are not changing very often, for example, icons, as shown in the SharePoint example provided above.</span></span> <span data-ttu-id="4186a-124">您可以使用 [Web Essentials](https://vswebessentials.com/)（一种基于第三方的开放源代码的基于社区的项目）在 Microsoft Visual Studio 中轻松实现此目的。</span><span class="sxs-lookup"><span data-stu-id="4186a-124">You can how to use [Web Essentials](https://vswebessentials.com/), a third-party, open-source, community-based project to achieve this easily in Microsoft Visual Studio.</span></span> <span data-ttu-id="4186a-125">有关详细信息，请参阅 [SharePoint Online 中的缩小和捆绑](https://go.microsoft.com/fwlink/?LinkId=708698)。</span><span class="sxs-lookup"><span data-stu-id="4186a-125">For more information, see [Minification and bundling in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).</span></span>
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a><span data-ttu-id="4186a-126">使用图像压缩和优化以加快页面加载速度</span><span class="sxs-lookup"><span data-stu-id="4186a-126">Using image compression and optimization to speed up page loading</span></span>

<span data-ttu-id="4186a-127">图像压缩和优化是为了减小在您的网站上使用的图像的文件大小。</span><span class="sxs-lookup"><span data-stu-id="4186a-127">Image compression and optimization is about reducing the file size of the images you use on your site.</span></span> <span data-ttu-id="4186a-128">通常情况下，减小图像大小的最佳方法是将图像大小调整为在网站上查看的最大尺寸。</span><span class="sxs-lookup"><span data-stu-id="4186a-128">Often, the best technique to reduce the size of an image is to resize the image to the maximum dimensions that it will be viewed on the site.</span></span> <span data-ttu-id="4186a-129">如果图像大于查看的大小，则没有意义。</span><span class="sxs-lookup"><span data-stu-id="4186a-129">There is no sense in having an image larger than it will ever be viewed.</span></span> <span data-ttu-id="4186a-130">使用图像编辑器确保图像的尺寸是正确的，这是一种减小页面大小的快速而简单的方法。</span><span class="sxs-lookup"><span data-stu-id="4186a-130">Making sure images are of the correct dimensions using an image editor is a quick and easy way to reduce the size of your page.</span></span>
  
<span data-ttu-id="4186a-131">图像大小正确后，下一步是优化这些图像的压缩。</span><span class="sxs-lookup"><span data-stu-id="4186a-131">Once images are the right size, the next step is to optimize the compression of these images.</span></span> <span data-ttu-id="4186a-132">有多种工具可用于压缩和优化，包括照片库和第三方工具。</span><span class="sxs-lookup"><span data-stu-id="4186a-132">There are various tools available to use for compression and optimization, including Photo Gallery and third-party tools.</span></span> <span data-ttu-id="4186a-133">要进行压缩的关键是，尽量减小文件大小，而不会丢失最终用户的任何可辨识的质量。</span><span class="sxs-lookup"><span data-stu-id="4186a-133">The key to compression is to reduce the file size as much as possible without losing any discernible quality for end users.</span></span> <span data-ttu-id="4186a-134">请确保在高清晰度显示中测试压缩文件，以确保它们仍显示良好。</span><span class="sxs-lookup"><span data-stu-id="4186a-134">Make sure you test your compressed files on a high-definition display to ensure they will still look good.</span></span>
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a><span data-ttu-id="4186a-135">使用 SharePoint 图像呈现方式加快页面下载速度</span><span class="sxs-lookup"><span data-stu-id="4186a-135">Speed up page downloads by using SharePoint image renditions</span></span>

<span data-ttu-id="4186a-136">图像呈现形式是 SharePoint Online 中的一项功能，允许您根据预定义的图像尺寸提供不同版本的图像。</span><span class="sxs-lookup"><span data-stu-id="4186a-136">Image renditions are a feature in SharePoint Online that allows you to serve up different versions of images based on pre-defined image dimensions.</span></span> <span data-ttu-id="4186a-137">当网站上的 CSS 修复了用户生成的图像内容或图像尺寸（如宽度和高度）时，这一点尤其重要。</span><span class="sxs-lookup"><span data-stu-id="4186a-137">This is especially important when there is user-generated image content or the image dimensions such as width and height are fixed by the CSS on the site.</span></span> <span data-ttu-id="4186a-138">即使图像是通过 CSS 修复的，仍会加载完整的分辨率图像。</span><span class="sxs-lookup"><span data-stu-id="4186a-138">Even if an image is fixed by CSS, the full resolution image is still loaded.</span></span> <span data-ttu-id="4186a-139">在这种情况下，可以使用图像呈现形式来减少文件大小。</span><span class="sxs-lookup"><span data-stu-id="4186a-139">In this case the file size can be reduced by using image renditions.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4186a-140">仅当启用发布时，才可使用 SharePoint 的呈现形式。</span><span class="sxs-lookup"><span data-stu-id="4186a-140">Renditions are only available for SharePoint when publishing is enabled.</span></span> <span data-ttu-id="4186a-141">你可以在 "设置" 网站设置下启用发布 " \> \> 管理网站功能" \> SharePoint Server 发布。</span><span class="sxs-lookup"><span data-stu-id="4186a-141">You can enable publishing under Settings \> Site Settings \> Manage site features \> SharePoint Server Publishing.</span></span> <span data-ttu-id="4186a-142">否则，此选项将不会显示。</span><span class="sxs-lookup"><span data-stu-id="4186a-142">The option will not appear otherwise.</span></span>
  
<span data-ttu-id="4186a-143">通过获取定义的最小尺寸（宽度或高度），然后调整图像大小，以便根据锁定纵横比自动调整其他尺寸的大小，从而使图像呈现形式的大小调整正常。</span><span class="sxs-lookup"><span data-stu-id="4186a-143">The image rendition resizing works by taking the smallest dimension you define, either width or height, and then resizing the image so that the other dimension is automatically resized based on the locked aspect ratio.</span></span> <span data-ttu-id="4186a-144">默认情况下，它会将图像从中心裁剪到剩余的尺寸。</span><span class="sxs-lookup"><span data-stu-id="4186a-144">By default, it will crop the image from the center by the remaining dimensions.</span></span> <span data-ttu-id="4186a-145">例如，如果您定义100px 宽和50px 的格式副本，并且原始图像为1000px 宽且800px 高，则将调整其大小，以便800px 维度现在为50px，而1000px 维度 (现在从图像中心裁剪的 62.5 px) 。</span><span class="sxs-lookup"><span data-stu-id="4186a-145">For example, if you define a rendition of 100px wide and 50px high and your original image is 1000px wide and 800px high, it will be resized so that the 800px dimension is now 50px and the 1000px dimension (now 62.5px) is cropped from the center of the image.</span></span>
  
<span data-ttu-id="4186a-146">这些步骤相对简单，但要使用呈现形式的图像，在添加图像之前，必须在 SharePoint 网站上的呈现形式。</span><span class="sxs-lookup"><span data-stu-id="4186a-146">The steps are relatively simple but for images to use the renditions, the renditions need to be on the SharePoint site before you add the images.</span></span> <span data-ttu-id="4186a-147">此外，还需要启用 SharePoint Server 发布基础结构 (网站集级别) 和 SharePoint Server 发布 (网站级别) 功能。</span><span class="sxs-lookup"><span data-stu-id="4186a-147">In addition, you also need to have the SharePoint Server Publishing Infrastructure (Site Collection Level) and SharePoint Server Publishing (Site Level) features turned on.</span></span>
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a><span data-ttu-id="4186a-148">添加图像呈现形式以加快页面加载速度</span><span class="sxs-lookup"><span data-stu-id="4186a-148">Add an image rendition to speed up page loading</span></span>
  
1. <span data-ttu-id="4186a-149">确认执行此过程的用户帐户至少具有对网站集的首要网站的 "设计" 权限，并且该网站发布到网页。</span><span class="sxs-lookup"><span data-stu-id="4186a-149">Verify that the user account that is performing this procedure has, at minimum, Design permissions to the top-level site of the site collection, and that the site is being published to a webpage.</span></span>

2. <span data-ttu-id="4186a-150">在 web 浏览器中，转到发布网站集的首要网站。</span><span class="sxs-lookup"><span data-stu-id="4186a-150">In a web browser, go to the top-level site of the publishing site collection.</span></span>

3. <span data-ttu-id="4186a-151">选择"设置"图标。</span><span class="sxs-lookup"><span data-stu-id="4186a-151">Choose the **Settings** icon.</span></span>

4. <span data-ttu-id="4186a-152">在 " **网站设置** " 页上的 " **外观** " 部分中，您将看到内置的图像呈现形式。</span><span class="sxs-lookup"><span data-stu-id="4186a-152">On the **Site Settings** page, in the **Look and Feel** section, you will see the built-in image renditions.</span></span>

    <span data-ttu-id="4186a-153">您可以使用 "现成" 格式副本或选择 " **图像呈现形式** " 来创建一个新的。</span><span class="sxs-lookup"><span data-stu-id="4186a-153">You can use the out of the box renditions or choose **Image Renditions** to create a new one.</span></span>

    ![图像呈现形式的屏幕截图](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. <span data-ttu-id="4186a-155">在“图像呈现形式”\*\*\*\* 页上，选择“添加新项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4186a-155">On the **Image Renditions** page, choose **Add new item**.</span></span>

    ![添加新项目的屏幕截图](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. <span data-ttu-id="4186a-157">在"新建图像呈现形式"页上的"名称"框中，为呈现形式输入名称。</span><span class="sxs-lookup"><span data-stu-id="4186a-157">On the **New Image Rendition** page, in the **Name** box, enter a name for the rendition.</span></span>

7. <span data-ttu-id="4186a-158">在"宽度"和"高度"文本框中，输入呈现形式的宽度和高度（以像素为单位），然后选择"保存"。</span><span class="sxs-lookup"><span data-stu-id="4186a-158">In the **Width** and **Height** text boxes, enter the width and height, in pixels, of the rendition, and then choose **Save**.</span></span>

    ![图像再现名称的屏幕截图](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a><span data-ttu-id="4186a-160">使用图像呈现形式的自定义裁剪</span><span class="sxs-lookup"><span data-stu-id="4186a-160">Custom cropping with image renditions</span></span>

<span data-ttu-id="4186a-161">默认情况下，图像呈现形式在图像中心生成。</span><span class="sxs-lookup"><span data-stu-id="4186a-161">By default, an image rendition is generated from the center of the image.</span></span> <span data-ttu-id="4186a-162">您可以调整单个图像的图像呈现形式，具体方法是裁剪要使用的图像部分。</span><span class="sxs-lookup"><span data-stu-id="4186a-162">You can adjust the image rendition for individual images by cropping the portion of the image that you want to use.</span></span> <span data-ttu-id="4186a-163">您可以按每个节目逐个对图像进行裁剪。</span><span class="sxs-lookup"><span data-stu-id="4186a-163">You can crop the images on an individual basis, per rendition.</span></span> <span data-ttu-id="4186a-164">裁剪图像可通过使用 SharePoint 的 blob 缓存为每个节目创建一个版本的图像，从而加快页面加载速度。</span><span class="sxs-lookup"><span data-stu-id="4186a-164">Cropping the images speeds up page loading by using SharePoint's blob cache to create a version of the image for each rendition.</span></span> <span data-ttu-id="4186a-165">通过这种方式，服务器负载会降低，因为仅调整了图像大小一次，然后准备将其提供给最终用户多次。</span><span class="sxs-lookup"><span data-stu-id="4186a-165">This way the server load is reduced because the image is only resized once and is then ready to serve to end users multiple times.</span></span> <span data-ttu-id="4186a-166">有关如何裁剪图像呈现形式的详细信息，请参阅 [裁剪图像呈现形式](https://go.microsoft.com/fwlink/p/?LinkId=525626)。</span><span class="sxs-lookup"><span data-stu-id="4186a-166">For more information on how to crop an image rendition, see [Crop an image rendition](https://go.microsoft.com/fwlink/p/?LinkId=525626).</span></span>
  

