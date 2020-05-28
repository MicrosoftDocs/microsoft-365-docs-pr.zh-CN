---
title: 在 Dreamhost 处为 Microsoft 创建 DNS 记录
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9c0812e0-908b-4b41-a64b-77f0dbd3db7a
description: 了解如何验证您的域，并在 Dreamhost for Microsoft 中为电子邮件、Skype for Business Online 和其他服务设置 DNS 记录。
ms.openlocfilehash: 4b321138892cb4a7b5f67c37ed66f3baf0f6c45a
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "44400505"
---
# <a name="create-dns-records-at-dreamhost-for-microsoft"></a><span data-ttu-id="a38cb-103">在 Dreamhost 处为 Microsoft 创建 DNS 记录</span><span class="sxs-lookup"><span data-stu-id="a38cb-103">Create DNS records at Dreamhost for Microsoft</span></span>

 <span data-ttu-id="a38cb-104">如果找不到要查找的内容，请**[查看域常见问题解答](../setup/domains-faq.md)**。</span><span class="sxs-lookup"><span data-stu-id="a38cb-104">**[Check the Domains FAQ](../setup/domains-faq.md)** if you don't find what you're looking for.</span></span> 
  
<span data-ttu-id="a38cb-105">如果 DreamHost 是您的 DNS 托管提供商，请按照本文中的步骤验证您的域并为电子邮件、Lync 等设置 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-105">If DreamHost is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Lync, and so on.</span></span>
 
<span data-ttu-id="a38cb-106">在 DreamHost 中添加这些记录后，您的域将设置为与 Microsoft 服务一起使用。</span><span class="sxs-lookup"><span data-stu-id="a38cb-106">After you add these records at DreamHost, your domain will be set up to work with Microsoft services.</span></span>
  
  
> [!NOTE]
> <span data-ttu-id="a38cb-p101">DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a38cb-p101">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  
## <a name="add-a-txt-record-for-verification"></a><span data-ttu-id="a38cb-110">添加 TXT 记录进行验证</span><span class="sxs-lookup"><span data-stu-id="a38cb-110">Add a TXT record for verification</span></span>
<span data-ttu-id="a38cb-111"><a name="BKMK_verify"> </a></span><span class="sxs-lookup"><span data-stu-id="a38cb-111"><a name="BKMK_verify"> </a></span></span>

<span data-ttu-id="a38cb-p102">在将域用于 Microsoft 之前，必须确保你拥有该域。如果你能够在域注册机构处登录到你的帐户并创建 DNS 记录，便可向 Microsoft 证明你是域所有者。</span><span class="sxs-lookup"><span data-stu-id="a38cb-p102">Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a38cb-p103">此记录仅用于验证您是否拥有自己的域；它不会影响其他任何内容。 如果需要，您可以以后将其删除。</span><span class="sxs-lookup"><span data-stu-id="a38cb-p103">This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.</span></span> 
  
1. <span data-ttu-id="a38cb-116">若要开始，请使用[此链接](https://panel.dreamhost.com/)转到 DreamHost 上的 "域" 页面。</span><span class="sxs-lookup"><span data-stu-id="a38cb-116">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="a38cb-117">系统将提示您登录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-117">You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-配置-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="a38cb-119">在**仪表板**页面上，选择 "**域**"，然后**管理域**。</span><span class="sxs-lookup"><span data-stu-id="a38cb-119">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-配置-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="a38cb-121">在 "**管理域**" 页上的 "**域**" 部分，为要编辑的域选择 " **DNS** "。</span><span class="sxs-lookup"><span data-stu-id="a38cb-121">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-配置-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="a38cb-123">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table.</span><span class="sxs-lookup"><span data-stu-id="a38cb-123">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table.</span></span> 
    
    <span data-ttu-id="a38cb-124">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-124">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="a38cb-125">(Choose the **Type** value from the drop-down list.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-125">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="a38cb-126">**名称**</span><span class="sxs-lookup"><span data-stu-id="a38cb-126">**Name**</span></span>|<span data-ttu-id="a38cb-127">**Type**</span><span class="sxs-lookup"><span data-stu-id="a38cb-127">**Type**</span></span>|<span data-ttu-id="a38cb-128">**值**</span><span class="sxs-lookup"><span data-stu-id="a38cb-128">**Value**</span></span>|<span data-ttu-id="a38cb-129">**Comment**</span><span class="sxs-lookup"><span data-stu-id="a38cb-129">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="a38cb-130">(Leave this field empty.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-130">(Leave this field empty.)</span></span>  <br/> |<span data-ttu-id="a38cb-131">TXT</span><span class="sxs-lookup"><span data-stu-id="a38cb-131">TXT</span></span>  <br/> |<span data-ttu-id="a38cb-132">MS=ms *XXXXXXXX*</span><span class="sxs-lookup"><span data-stu-id="a38cb-132">MS=ms *XXXXXXXX*</span></span>  <br/> <span data-ttu-id="a38cb-133">**注意：** 这是一个示例。</span><span class="sxs-lookup"><span data-stu-id="a38cb-133">**Note:** This is an example.</span></span> <span data-ttu-id="a38cb-134">在这里使用表中的特定“**目标地址或指向的地址**”值。</span><span class="sxs-lookup"><span data-stu-id="a38cb-134">Use your specific **Destination or Points to Address** value here, from the table.</span></span>           [<span data-ttu-id="a38cb-135">如何查找此项？</span><span class="sxs-lookup"><span data-stu-id="a38cb-135">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |<span data-ttu-id="a38cb-136">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-136">(This field is optional.)</span></span>  <br/> |
   
   ![Dreamhost-验证-1-1](../../media/ed4a7d43-eeeb-4ec8-849c-37f81315dc69.png)
  
5. <span data-ttu-id="a38cb-138">立即选择 "**添加记录"！**</span><span class="sxs-lookup"><span data-stu-id="a38cb-138">Select **Add Record Now!**</span></span>
    
    ![Dreamhost-验证-1-2](../../media/5b89c89b-3a8e-4624-895a-86f3cc4638f6.png)
  
6. <span data-ttu-id="a38cb-140">请在继续之前等待数分钟，以便您刚刚创建的记录可以通过 Internet 完成更新。</span><span class="sxs-lookup"><span data-stu-id="a38cb-140">Wait a few minutes before you continue, so that the record you just created can update across the Internet.</span></span>
    
<span data-ttu-id="a38cb-141">在在域注册机构网站添加了记录后，你将返回到 Microsoft 并请求记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-141">Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record.</span></span>
  
<span data-ttu-id="a38cb-142">Microsof 找到正确的 TXT 记录表明域已通过验证。</span><span class="sxs-lookup"><span data-stu-id="a38cb-142">When Microsoft finds the correct TXT record, your domain is verified.</span></span>
  
1. <span data-ttu-id="a38cb-143">在 Microsoft 管理中心，转到“**设置**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">域</a>”页面。</span><span class="sxs-lookup"><span data-stu-id="a38cb-143">In the Microsoft admin center, go to the **Settings** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.</span></span>

    
2. <span data-ttu-id="a38cb-144">在“**域**”页面上，选择要验证的域。</span><span class="sxs-lookup"><span data-stu-id="a38cb-144">On the **Domains** page, select the domain that you are verifying.</span></span> 
    
    
  
3. <span data-ttu-id="a38cb-145">在“**设置**”页面上，选择“**开始设置**”。</span><span class="sxs-lookup"><span data-stu-id="a38cb-145">On the **Setup** page, select **Start setup**.</span></span>
    
    
  
4. <span data-ttu-id="a38cb-146">在“**验证域**”页面上，选择“**验证**”。</span><span class="sxs-lookup"><span data-stu-id="a38cb-146">On the **Verify domain** page, select **Verify**.</span></span>
    
    
  
> [!NOTE]
>  <span data-ttu-id="a38cb-p106">DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a38cb-p106">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="a38cb-150">添加一条 MX 记录，确保发往你的域的电子邮件将会发送到 Microsoft</span><span class="sxs-lookup"><span data-stu-id="a38cb-150">Add an MX record so email for your domain will come to Microsoft</span></span>
<span data-ttu-id="a38cb-151"><a name="BKMK_add_MX"> </a></span><span class="sxs-lookup"><span data-stu-id="a38cb-151"><a name="BKMK_add_MX"> </a></span></span>

<span data-ttu-id="a38cb-152">按照下面的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="a38cb-152">Follow the steps below.</span></span>
  
1. <span data-ttu-id="a38cb-153">若要开始，请使用[此链接](https://panel.dreamhost.com/)转到 DreamHost 上的 "域" 页面。</span><span class="sxs-lookup"><span data-stu-id="a38cb-153">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="a38cb-154">系统将提示您登录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-154">You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-配置-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="a38cb-156">在**仪表板**页面上，依次选择 "**邮件**" 和 "**自定义 MX**"。</span><span class="sxs-lookup"><span data-stu-id="a38cb-156">On the **Dashboard** page, select **Mail**, and then **Custom MX**.</span></span>
    
    ![Dreamhost-配置-2-1](../../media/58478679-4018-49cc-9d83-371dc5fa4a22.png)
  
3. <span data-ttu-id="a38cb-158">在 "**管理邮件传递**" 部分的 "**操作**" 列中，为要编辑的域选择 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="a38cb-158">In the **Manage Mail Delivery** section, in the **Actions** column, select **Edit** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-配置-2-2](../../media/6eed0be2-6477-4f49-9f90-39e190499a53.png)
  
4. <span data-ttu-id="a38cb-160">在 "**自定义 MX 记录**" 部分中，在新记录的框中，键入或复制并粘贴下表中的以下值。</span><span class="sxs-lookup"><span data-stu-id="a38cb-160">In the **Custom MX Record** section, in the boxes for the new record, type or copy and paste the following values from the following table.</span></span> 
    
    <span data-ttu-id="a38cb-161">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-161">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="a38cb-162">（如果存在任何其他现有 MX 记录，则将这些记录标记为 "删除"。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-162">(If there are any other existing MX records, mark those records to be deleted.)</span></span>
    
    |<span data-ttu-id="a38cb-163">**MX 记录（必需）**</span><span class="sxs-lookup"><span data-stu-id="a38cb-163">**MX Record (required)**</span></span>|
    |:-----|
    |<span data-ttu-id="a38cb-164">0 *\<domain-key\>* . mail.protection.outlook.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-164">0  *\<domain-key\>*  .mail.protection.outlook.com.</span></span>  <br/> <span data-ttu-id="a38cb-165">**This value MUST end with a period (.)**</span><span class="sxs-lookup"><span data-stu-id="a38cb-165">**This value MUST end with a period (.)**</span></span> <br/> <span data-ttu-id="a38cb-p108">0 是 MX 优先级值。 将其添加到 MX 值的开头，使用一个空格将其与其余部分隔开。  </span><span class="sxs-lookup"><span data-stu-id="a38cb-p108">The 0 is the MX priority value. Add it to the beginning of the MX value, separated from the remainder of the value by a space.  </span></span><br/> <span data-ttu-id="a38cb-168">\**注意：\*\*\*\<domain-key\>* 从你的 Microsoft 帐户获取你的。</span><span class="sxs-lookup"><span data-stu-id="a38cb-168">**Note:** Get your  *\<domain-key\>*  from your Microsoft account.</span></span>           [<span data-ttu-id="a38cb-169">如何查找此项？</span><span class="sxs-lookup"><span data-stu-id="a38cb-169">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Dreamhost-配置-2-3](../../media/90da1816-e186-4016-ab22-7962f8b86add.png)
  
5. <span data-ttu-id="a38cb-171">选择 "**立即将此域改为使用自定义 MX 记录！** "</span><span class="sxs-lookup"><span data-stu-id="a38cb-171">Select **Change this domain to use custom MX records now!**</span></span>
    
    ![Dreamhost-配置-2-4](../../media/3221c767-83d3-4f30-9d08-dc998772d2a3.png)
  
6. <span data-ttu-id="a38cb-173">如果存在任何其他现有 MX 记录，请通过选择相应的条目，然后按键盘上的**delete**键来删除每个记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-173">If there are any other existing MX records, delete each record by selecting the entry and then pressing the **Delete** key on your keyboard.</span></span> 
    
    ![Dreamhost-配置-2-5](../../media/1827733c-3609-4b0f-bba1-531ab090da91.png)
  
7. <span data-ttu-id="a38cb-175">如果已删除任何记录，请选择 "**立即更新自定义 MX 记录！** "</span><span class="sxs-lookup"><span data-stu-id="a38cb-175">If you have deleted any records, select **Update your custom MX records now!**</span></span>
    
    ![Dreamhost-配置-2-6](../../media/177462be-0686-47b7-a389-025dfc8d6526.png)

  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a><span data-ttu-id="a38cb-177">添加 Microsoft 所需的六条 CNAME 记录</span><span class="sxs-lookup"><span data-stu-id="a38cb-177">Add the six CNAME records that are required for Microsoft</span></span>
<span data-ttu-id="a38cb-178"><a name="BKMK_add_CNAME"> </a></span><span class="sxs-lookup"><span data-stu-id="a38cb-178"><a name="BKMK_add_CNAME"> </a></span></span>

<span data-ttu-id="a38cb-179">按照下面的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="a38cb-179">Follow the steps below.</span></span>
  
1. <span data-ttu-id="a38cb-180">若要开始，请使用[此链接](https://panel.dreamhost.com/)转到 DreamHost 上的 "域" 页面。</span><span class="sxs-lookup"><span data-stu-id="a38cb-180">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="a38cb-181">系统将提示您登录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-181">You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-配置-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="a38cb-183">在**仪表板**页面上，选择 "**域**"，然后**管理域**。</span><span class="sxs-lookup"><span data-stu-id="a38cb-183">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-配置-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="a38cb-185">在 "**管理域**" 页上的 "**域**" 部分，为要编辑的域选择 " **DNS** "。</span><span class="sxs-lookup"><span data-stu-id="a38cb-185">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-配置-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="a38cb-187">在 "**添加自定义 DNS 记录**" 部分中，在新记录的框中，键入或复制并粘贴下表中第一行的值。</span><span class="sxs-lookup"><span data-stu-id="a38cb-187">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="a38cb-188">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-188">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="a38cb-189">(Choose the **Type** value from the drop-down list.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-189">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="a38cb-190">**名称**</span><span class="sxs-lookup"><span data-stu-id="a38cb-190">**Name**</span></span>|<span data-ttu-id="a38cb-191">**Type**</span><span class="sxs-lookup"><span data-stu-id="a38cb-191">**Type**</span></span>|<span data-ttu-id="a38cb-192">**值**</span><span class="sxs-lookup"><span data-stu-id="a38cb-192">**Value**</span></span>|<span data-ttu-id="a38cb-193">**Comment**</span><span class="sxs-lookup"><span data-stu-id="a38cb-193">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="a38cb-194">autodiscover</span><span class="sxs-lookup"><span data-stu-id="a38cb-194">autodiscover</span></span>  <br/> |<span data-ttu-id="a38cb-195">CNAME</span><span class="sxs-lookup"><span data-stu-id="a38cb-195">CNAME</span></span>  <br/> |<span data-ttu-id="a38cb-196">autodiscover.outlook.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-196">autodiscover.outlook.com.</span></span>  <br/> <span data-ttu-id="a38cb-197">**This value MUST end with a period (.)**</span><span class="sxs-lookup"><span data-stu-id="a38cb-197">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-198">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-198">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="a38cb-199">sip</span><span class="sxs-lookup"><span data-stu-id="a38cb-199">sip</span></span>  <br/> |<span data-ttu-id="a38cb-200">CNAME</span><span class="sxs-lookup"><span data-stu-id="a38cb-200">CNAME</span></span>  <br/> |<span data-ttu-id="a38cb-201">sipdir.online.lync.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-201">sipdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="a38cb-202">**This value MUST end with a period (.)**</span><span class="sxs-lookup"><span data-stu-id="a38cb-202">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-203">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-203">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="a38cb-204">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="a38cb-204">lyncdiscover</span></span>  <br/> |<span data-ttu-id="a38cb-205">CNAME</span><span class="sxs-lookup"><span data-stu-id="a38cb-205">CNAME</span></span>  <br/> |<span data-ttu-id="a38cb-206">webdir.online.lync.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-206">webdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="a38cb-207">**This value MUST end with a period (.)**</span><span class="sxs-lookup"><span data-stu-id="a38cb-207">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-208">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-208">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="a38cb-209">enterpriseregistration</span><span class="sxs-lookup"><span data-stu-id="a38cb-209">enterpriseregistration</span></span>  <br/> |<span data-ttu-id="a38cb-210">CNAME</span><span class="sxs-lookup"><span data-stu-id="a38cb-210">CNAME</span></span>  <br/> |<span data-ttu-id="a38cb-211">enterpriseregistration.windows.net。</span><span class="sxs-lookup"><span data-stu-id="a38cb-211">enterpriseregistration.windows.net.</span></span>  <br/> <span data-ttu-id="a38cb-212">**This value MUST end with a period (.)**</span><span class="sxs-lookup"><span data-stu-id="a38cb-212">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-213">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-213">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="a38cb-214">enterpriseenrollment</span><span class="sxs-lookup"><span data-stu-id="a38cb-214">enterpriseenrollment</span></span>  <br/> |<span data-ttu-id="a38cb-215">CNAME</span><span class="sxs-lookup"><span data-stu-id="a38cb-215">CNAME</span></span>  <br/> |<span data-ttu-id="a38cb-216">enterpriseenrollment-s.manage.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-216">enterpriseenrollment-s.manage.microsoft.com.</span></span>  <br/> <span data-ttu-id="a38cb-217">**此值必须以句点 (.) 结尾。**</span><span class="sxs-lookup"><span data-stu-id="a38cb-217">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-218">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-218">(This field is optional.)</span></span>  <br/> |
   
    ![Dreamhost-配置-3-1](../../media/0c4cc587-ea24-47f2-8dc6-a35735b250e6.png)
  
5. <span data-ttu-id="a38cb-220">立即选择 "**添加记录"！**</span><span class="sxs-lookup"><span data-stu-id="a38cb-220">Select **Add Record Now!**</span></span>
    
    ![Dreamhost-配置-3-2](../../media/b5d4f939-de6d-4d1f-a20a-4eb5fe715281.png)
  
6. <span data-ttu-id="a38cb-222">使用前面的两个步骤和表中的其他五行中的值，添加其他五个 CNAME 记录中的每个。</span><span class="sxs-lookup"><span data-stu-id="a38cb-222">Using the preceding two steps and the values from the other five rows in the table, add each of the other five CNAME records.</span></span>

  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a><span data-ttu-id="a38cb-223">为 SPF 添加 TXT 记录以帮助防止垃圾邮件</span><span class="sxs-lookup"><span data-stu-id="a38cb-223">Add a TXT record for SPF to help prevent email spam</span></span>
<span data-ttu-id="a38cb-224"><a name="BKMK_add_TXT"> </a></span><span class="sxs-lookup"><span data-stu-id="a38cb-224"><a name="BKMK_add_TXT"> </a></span></span>

> [!IMPORTANT]
> <span data-ttu-id="a38cb-225">一个域所拥有的 SPF 的 TXT 记录不能超过一个。</span><span class="sxs-lookup"><span data-stu-id="a38cb-225">You cannot have more than one TXT record for SPF for a domain.</span></span> <span data-ttu-id="a38cb-226">如果域具有多个 SPF 记录，你将收到电子邮件错误，其中随附发送和垃圾邮件分类问题。</span><span class="sxs-lookup"><span data-stu-id="a38cb-226">If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues.</span></span> <span data-ttu-id="a38cb-227">如果你的域已有 SPF 记录，请不要为 Microsoft 创建新记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-227">If you already have an SPF record for your domain, don't create a new one for Microsoft.</span></span> <span data-ttu-id="a38cb-228">改为将所需的 Microsoft 值添加到当前记录，以便您具有包含两组值的*单个*SPF 记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-228">Instead, add the required Microsoft values to the current record so that you have a  *single*  SPF record that includes both sets of values.</span></span>
  
<span data-ttu-id="a38cb-229">按照下面的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="a38cb-229">Follow the steps below.</span></span>
  
1. <span data-ttu-id="a38cb-230">若要开始，请使用[此链接](https://panel.dreamhost.com/)转到 DreamHost 上的 "域" 页面。</span><span class="sxs-lookup"><span data-stu-id="a38cb-230">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="a38cb-231">系统将提示您登录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-231">You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-配置-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="a38cb-233">在**仪表板**页面上，选择 "**域**"，然后**管理域**。</span><span class="sxs-lookup"><span data-stu-id="a38cb-233">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-配置-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="a38cb-235">在 "**管理域**" 页上的 "**域**" 部分，为要编辑的域选择 " **DNS** "。</span><span class="sxs-lookup"><span data-stu-id="a38cb-235">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-配置-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="a38cb-237">在 "**添加自定义 DNS 记录**" 部分中，在新记录的框中，键入或复制并粘贴下表中第一行的值。</span><span class="sxs-lookup"><span data-stu-id="a38cb-237">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="a38cb-238">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-238">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="a38cb-239">(Choose the **Type** value from the drop-down list.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-239">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="a38cb-240">**名称**</span><span class="sxs-lookup"><span data-stu-id="a38cb-240">**Name**</span></span>|<span data-ttu-id="a38cb-241">**Type**</span><span class="sxs-lookup"><span data-stu-id="a38cb-241">**Type**</span></span>|<span data-ttu-id="a38cb-242">**值**</span><span class="sxs-lookup"><span data-stu-id="a38cb-242">**Value**</span></span>|<span data-ttu-id="a38cb-243">**Comment**</span><span class="sxs-lookup"><span data-stu-id="a38cb-243">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="a38cb-244">(Leave this field empty.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-244">(Leave this field empty.)</span></span>  <br/> |<span data-ttu-id="a38cb-245">TXT</span><span class="sxs-lookup"><span data-stu-id="a38cb-245">TXT</span></span>  <br/> |<span data-ttu-id="a38cb-246">v=spf1 include:spf.protection.outlook.com -all</span><span class="sxs-lookup"><span data-stu-id="a38cb-246">v=spf1 include:spf.protection.outlook.com -all</span></span>  <br/> <span data-ttu-id="a38cb-247">**注意：** 我们建议您复制并粘贴此条目，以保证正确保留所有空格。</span><span class="sxs-lookup"><span data-stu-id="a38cb-247">**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct.</span></span>           |<span data-ttu-id="a38cb-248">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-248">(This field is optional.)</span></span>  <br/> |
   
   ![Dreamhost-配置-4-1](../../media/cbc4bbca-bdbc-4dc9-b1b7-b55491eb1e53.png)
  
5. <span data-ttu-id="a38cb-250">立即选择 "**添加记录"！**</span><span class="sxs-lookup"><span data-stu-id="a38cb-250">Select **Add Record Now!**</span></span>
    
    ![Dreamhost-配置-4-2](../../media/2bd7cae8-1fbc-4407-8dfa-06ce37c586c0.png)
  
6. <span data-ttu-id="a38cb-252">使用前面的两个步骤和表中第二行的值，添加另一条 SRV 记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-252">Using the preceding two steps and the values from the second row in the table, add the other SRV record.</span></span>
    
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a><span data-ttu-id="a38cb-253">添加 Microsoft 所需的两条 SRV 记录</span><span class="sxs-lookup"><span data-stu-id="a38cb-253">Add the two SRV records that are required for Microsoft</span></span>
<span data-ttu-id="a38cb-254"><a name="BKMK_add_SRV"> </a></span><span class="sxs-lookup"><span data-stu-id="a38cb-254"><a name="BKMK_add_SRV"> </a></span></span>

<span data-ttu-id="a38cb-255">按照下面的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="a38cb-255">Follow the steps below.</span></span>
  
1. <span data-ttu-id="a38cb-256">若要开始，请使用[此链接](https://panel.dreamhost.com/)转到 DreamHost 上的 "域" 页面。</span><span class="sxs-lookup"><span data-stu-id="a38cb-256">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/).</span></span> <span data-ttu-id="a38cb-257">系统将提示您登录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-257">You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-配置-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="a38cb-259">在**仪表板**页面上，选择 "**域**"，然后**管理域**。</span><span class="sxs-lookup"><span data-stu-id="a38cb-259">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-配置-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="a38cb-261">在 "**管理域**" 页上的 "**域**" 部分，为要编辑的域选择 " **DNS** "。</span><span class="sxs-lookup"><span data-stu-id="a38cb-261">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-配置-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="a38cb-263">在 "**添加自定义 DNS 记录**" 部分中，在新记录的框中，键入或复制并粘贴下表中第一行的值。</span><span class="sxs-lookup"><span data-stu-id="a38cb-263">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="a38cb-264">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-264">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="a38cb-265">(Choose the **Type** value from the drop-down list.)</span><span class="sxs-lookup"><span data-stu-id="a38cb-265">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="a38cb-266">**名称**</span><span class="sxs-lookup"><span data-stu-id="a38cb-266">**Name**</span></span>|<span data-ttu-id="a38cb-267">**Type**</span><span class="sxs-lookup"><span data-stu-id="a38cb-267">**Type**</span></span>|<span data-ttu-id="a38cb-268">**值**</span><span class="sxs-lookup"><span data-stu-id="a38cb-268">**Value**</span></span>|<span data-ttu-id="a38cb-269">**Comment**</span><span class="sxs-lookup"><span data-stu-id="a38cb-269">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="a38cb-270">_sip _tls</span><span class="sxs-lookup"><span data-stu-id="a38cb-270">_sip._tls</span></span>  <br/> |<span data-ttu-id="a38cb-271">SRV</span><span class="sxs-lookup"><span data-stu-id="a38cb-271">SRV</span></span>  <br/> |<span data-ttu-id="a38cb-272">100 1 443</span><span class="sxs-lookup"><span data-stu-id="a38cb-272">100 1 443</span></span>  <br/> <span data-ttu-id="a38cb-273">sipdir.online.lync.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-273">sipdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="a38cb-274">**This value MUST end with a period (.)**</span><span class="sxs-lookup"><span data-stu-id="a38cb-274">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-275">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-275">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="a38cb-276">_sipfederationtls _tcp</span><span class="sxs-lookup"><span data-stu-id="a38cb-276">_sipfederationtls._tcp</span></span>  <br/> |<span data-ttu-id="a38cb-277">SRV</span><span class="sxs-lookup"><span data-stu-id="a38cb-277">SRV</span></span>  <br/> |<span data-ttu-id="a38cb-278">100 1 5061</span><span class="sxs-lookup"><span data-stu-id="a38cb-278">100 1 5061</span></span>  <br/> <span data-ttu-id="a38cb-279">sipfed.online.lync.com。</span><span class="sxs-lookup"><span data-stu-id="a38cb-279">sipfed.online.lync.com.</span></span>  <br/> <span data-ttu-id="a38cb-280">**此值必须以句点 (.) 结尾。**</span><span class="sxs-lookup"><span data-stu-id="a38cb-280">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="a38cb-281">（此字段是可选的。）</span><span class="sxs-lookup"><span data-stu-id="a38cb-281">(This field is optional.)</span></span>  <br/> |
   
    ![Dreamhost-配置-5-1](../../media/934eb79f-3617-4b72-802c-c42c7d165283.png)
  
5. <span data-ttu-id="a38cb-283">选择 "**立即添加记录"！**。</span><span class="sxs-lookup"><span data-stu-id="a38cb-283">Select **Add Record Now!**.</span></span>
    
    ![Dreamhost-配置-5-2](../../media/015bc73c-8f88-49ce-87f9-e5a6ea3e10a8.png)
  
6. <span data-ttu-id="a38cb-285">使用前面的两个步骤和表中第二行的值，添加另一条 SRV 记录。</span><span class="sxs-lookup"><span data-stu-id="a38cb-285">Using the preceding two steps and the values from the second row in the table, add the other SRV record.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="a38cb-p114">DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a38cb-p114">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 

  
