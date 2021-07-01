---
title: 使用 DAP 合作伙伴的 Windows PowerShell将域添加到客户端租赁
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 摘要：使用 PowerShell for Microsoft 365向现有客户租户添加备用域名。
ms.openlocfilehash: 3bcdb40e2c72e5aac8103b0b55ff6fccfe6a9fcc
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "53229079"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="fa8d8-103">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁</span><span class="sxs-lookup"><span data-stu-id="fa8d8-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

<span data-ttu-id="fa8d8-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="fa8d8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="fa8d8-105">您可以使用 PowerShell 创建新域并将其与客户租赁关联，Microsoft 365比使用 Microsoft 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-105">You can create and associate new domains with your customer's tenancy with PowerShell for Microsoft 365 faster than using the Microsoft 365 admin center.</span></span>

<span data-ttu-id="fa8d8-106">委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="fa8d8-107">他们通常是面向其他公司的网络或电信提供商。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="fa8d8-108">他们Microsoft 365订阅捆绑到他们的服务产品/服务中。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="fa8d8-109">当他们销售 Microsoft 365 订阅时，将自动被授予代表 (AOBO) 管理客户租赁的权限，以便他们可以管理和报告客户租赁。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="fa8d8-110">开始前，有必要了解什么？</span><span class="sxs-lookup"><span data-stu-id="fa8d8-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="fa8d8-111">本主题中的过程需要您连接到 连接[Microsoft 365 PowerShell 进行连接](connect-to-microsoft-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-111">The procedures in this topic require you to connect to [Connect to Microsoft 365 with PowerShell](connect-to-microsoft-365-powershell.md).</span></span>

<span data-ttu-id="fa8d8-112">您也需要您的合作伙伴租户管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-112">You also need your partner tenant administrator credentials.</span></span>

<span data-ttu-id="fa8d8-113">您也需要以下信息：</span><span class="sxs-lookup"><span data-stu-id="fa8d8-113">You also need the following information:</span></span>

- <span data-ttu-id="fa8d8-114">您需要客户所需的完全限定的域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-114">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>

- <span data-ttu-id="fa8d8-115">您需要客户的 **TenantId** 。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-115">You need the customer's **TenantId**.</span></span>

- <span data-ttu-id="fa8d8-p102">FQDN 必须在 Internet 域名服务 (DNS) 注册机构（如 GoDaddy）中注册。有关如何公开注册域名的详细信息，请参阅[如何购买域名](../admin/get-help-with-domains/buy-a-domain-name.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](../admin/get-help-with-domains/buy-a-domain-name.md).</span></span>

- <span data-ttu-id="fa8d8-118">您需要了解如何为您的 DNS 注册机构的注册 DNS 区域添加 TXT 记录。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-118">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar.</span></span> <span data-ttu-id="fa8d8-119">若要详细了解如何添加 TXT 记录，请参阅添加 [DNS 记录以连接域](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-119">For more information on how to add a TXT record, see [Add DNS records to connect your domain](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).</span></span> <span data-ttu-id="fa8d8-120">如果这些步骤对您不适用，您需要查找适用于您的 DNS 注册机构的过程。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-120">If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>

## <a name="create-domains"></a><span data-ttu-id="fa8d8-121">创建域</span><span class="sxs-lookup"><span data-stu-id="fa8d8-121">Create domains</span></span>

 <span data-ttu-id="fa8d8-p104">您的客户可能会要求您创建与其租赁关联的其他域，因为他们不想让默认的<domain>.onmicrosoft.com域成为向全世界展示其公司标识的主要域。此步骤将引导您创建与您的客户租赁相关联的新域。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>

> [!NOTE]
> <span data-ttu-id="fa8d8-124">若要执行其中某些操作，对于"向支持的公司分配管理访问权限"设置，登录时使用的合作伙伴管理员帐户必须设置为"完全管理"，此设置位于 Microsoft 365 管理中心 中管理员帐户的详细信息中。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-124">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="fa8d8-125">有关管理合作伙伴管理员角色详细信息，请参阅 [合作伙伴：提供委派管理](https://go.microsoft.com/fwlink/p/?LinkId=532435)。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-125">For more information on managing partner administrator roles, see [Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span>

### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="fa8d8-126">在 Azure Active Directory 中创建域</span><span class="sxs-lookup"><span data-stu-id="fa8d8-126">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="fa8d8-127">此命令在 Azure Active Directory 中创建域，但不会将其与公开注册的域相关联。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-127">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="fa8d8-128">当你向适用于企业的 Microsoft 企业认证证明你拥有公开注册的域Microsoft 365这一点。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-128">That comes when you prove that you own the publicly registered domain to Microsoft Microsoft 365 for enterprises.</span></span>

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> <span data-ttu-id="fa8d8-129">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fa8d8-130">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="fa8d8-131">获取 DNS TXT 验证记录的数据</span><span class="sxs-lookup"><span data-stu-id="fa8d8-131">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="fa8d8-132">Microsoft 365将生成需要放入 DNS TXT 验证记录中的特定数据。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-132">Microsoft 365 will generate the specific data that you need to place into the DNS TXT verification record.</span></span> <span data-ttu-id="fa8d8-133">要获取数据，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-133">To get the data, run this command.</span></span>

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="fa8d8-134">你将获得如下所示的输出：</span><span class="sxs-lookup"><span data-stu-id="fa8d8-134">This will give you output like:</span></span>

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> <span data-ttu-id="fa8d8-135">你将需要此文本以在公开注册的 DNS 区域中创建 TXT 记录。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-135">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="fa8d8-136">请确保将其复制并保存。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-136">Be sure to copy and save it.</span></span>

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="fa8d8-137">在公开注册的 DNS 区域中添加 TXT 记录</span><span class="sxs-lookup"><span data-stu-id="fa8d8-137">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="fa8d8-138">在Microsoft 365接受定向到公开注册域名的流量之前，您必须证明您拥有该域并拥有该域的管理员权限。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-138">Before Microsoft 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="fa8d8-139">您可通过在域中创建 TXT 记录来证明您拥有该域。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-139">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="fa8d8-140">TXT 记录不会在您的域中执行任何操作，并且可以在建立您对域的所有权后删除。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-140">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="fa8d8-141">若要创建 TXT 记录，请按照添加 [DNS 记录中的过程连接域](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-141">To create the TXT records, follow the procedures at [Add DNS records to connect your domain](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).</span></span> <span data-ttu-id="fa8d8-142">如果这些步骤对您不适用，您需要查找适用于您的 DNS 注册机构的过程。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-142">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>

<span data-ttu-id="fa8d8-p111">通过 nslookup 确认已成功创建 TXT 记录。遵循下面的语法。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-p111">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>

```console
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="fa8d8-145">您将获得如下所示的输出：</span><span class="sxs-lookup"><span data-stu-id="fa8d8-145">This will give you output like:</span></span>

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a><span data-ttu-id="fa8d8-146">验证域中的域Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="fa8d8-146">Validate domain ownership in Microsoft 365</span></span>

<span data-ttu-id="fa8d8-147">最后一步，验证Microsoft 365注册的域是否拥有。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-147">In this last step, you validate to Microsoft 365 that you own the publically registered domain.</span></span> <span data-ttu-id="fa8d8-148">执行此步骤后，Microsoft 365将开始接受路由到新域名的流量。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-148">After this step, Microsoft 365 will begin accepting traffic routed to the new domain name.</span></span> <span data-ttu-id="fa8d8-149">若要完成域创建和注册过程，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-149">To complete the domain creation and registration process, run this command.</span></span>

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="fa8d8-150">此命令不会返回任何输出，因此要确认其有效，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="fa8d8-150">This command won't return any output, so to confirm that this worked, run this command.</span></span>

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="fa8d8-151">这将返回如下所示的内容</span><span class="sxs-lookup"><span data-stu-id="fa8d8-151">This will return something like this</span></span>

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```


## <a name="see-also"></a><span data-ttu-id="fa8d8-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa8d8-152">See also</span></span>

####

[<span data-ttu-id="fa8d8-153">适用于合作伙伴的帮助</span><span class="sxs-lookup"><span data-stu-id="fa8d8-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)