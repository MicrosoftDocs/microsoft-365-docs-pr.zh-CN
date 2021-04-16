---
title: 使用域连接
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ec6f4bd8-5996-4505-ba68-afaf8a141fb9
description: 了解如何使用启用了域连接的注册机构，以及如何将域添加到 Microsoft 365。
ms.openlocfilehash: 5dec69f70273e6a9430ce5926ed07888e197adcd
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "51860651"
---
# <a name="using-domain-connect"></a><span data-ttu-id="f7011-103">使用域连接</span><span class="sxs-lookup"><span data-stu-id="f7011-103">Using Domain Connect</span></span>

 <span data-ttu-id="f7011-104">如果找不到要查找的内容，请 **[查看域常见问题解答](../setup/domains-faq.yml)**。</span><span class="sxs-lookup"><span data-stu-id="f7011-104">**[Check the Domains FAQ](../setup/domains-faq.yml)** if you don't find what you're looking for.</span></span>
  
<span data-ttu-id="f7011-105">[启用域连接的 ](https://www.domainconnect.org/) 注册机构让你在一个需要几分钟的三步过程中将域添加到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="f7011-105">[Domain Connect ](https://www.domainconnect.org/) enabled registrars let you add your domain to Microsoft 365 in a three-step process that takes minutes.</span></span> 
  
<span data-ttu-id="f7011-106">在向导中，我们将仅确认你拥有该域，然后自动设置域记录，因此电子邮件会发送到 Microsoft 365 和其他 Microsoft 365 服务（如 Teams）使用你的域。</span><span class="sxs-lookup"><span data-stu-id="f7011-106">In the wizard, we'll just confirm that you own the domain, and then automatically set up your domain's records, so email comes to Microsoft 365 and other Microsoft 365 services, like Teams, work with your domain.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f7011-107">在开始此设置向导前，请确保你已禁用浏览器中的任何弹出窗口阻止程序。</span><span class="sxs-lookup"><span data-stu-id="f7011-107">Make sure you disable any popup blockers in your browser before you start the setup wizard.</span></span>
  
## <a name="domain-connect-registrars-integrating-with-microsoft-365"></a><span data-ttu-id="f7011-108">与 Microsoft 365 集成域连接注册机构</span><span class="sxs-lookup"><span data-stu-id="f7011-108">Domain Connect registrars integrating with Microsoft 365</span></span>

- [<span data-ttu-id="f7011-109">1 &amp; 1 IONOS</span><span class="sxs-lookup"><span data-stu-id="f7011-109">1&amp;1 IONOS</span></span>](https://www.1and1.com/)
- [<span data-ttu-id="f7011-110">123Reg</span><span class="sxs-lookup"><span data-stu-id="f7011-110">123Reg</span></span>](https://www.123-reg.co.uk/)
- [<span data-ttu-id="f7011-111">GoDaddy</span><span class="sxs-lookup"><span data-stu-id="f7011-111">GoDaddy</span></span>](https://www.godaddy.com/)
- [<span data-ttu-id="f7011-112">WordPress</span><span class="sxs-lookup"><span data-stu-id="f7011-112">WordPress</span></span>](https://wordpress.com/)
- [<span data-ttu-id="f7011-113">Plesk</span><span class="sxs-lookup"><span data-stu-id="f7011-113">Plesk</span></span>](https://www.plesk.com/)
- [<span data-ttu-id="f7011-114">MediaTemple</span><span class="sxs-lookup"><span data-stu-id="f7011-114">MediaTemple</span></span>](https://mediatemple.net/)
- <span data-ttu-id="f7011-115">SecureServer 或 WildWestDomains (使用 SecureServer DNS 托管客户端的 GoDaddy) </span><span class="sxs-lookup"><span data-stu-id="f7011-115">SecureServer or WildWestDomains (GoDaddy resellers using SecureServer DNS hosting)</span></span>
    - [<span data-ttu-id="f7011-116">MadDog Web 托管</span><span class="sxs-lookup"><span data-stu-id="f7011-116">MadDog Web Hosting</span></span>](https://maddogwebhosting.com/domains/)
    - [<span data-ttu-id="f7011-117">CheapNames</span><span class="sxs-lookup"><span data-stu-id="f7011-117">CheapNames</span></span>](https://www.cheapnames.com)

## <a name="what-happens-to-my-email-and-website"></a><span data-ttu-id="f7011-118">我的电子邮件和网站会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="f7011-118">What happens to my email and website?</span></span>

<span data-ttu-id="f7011-119">完成设置后，你的域的 MX 记录将更新为指向 Microsoft 365，你的域的所有电子邮件都将开始发送到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="f7011-119">After you finish setup, the MX record for your domain is updated to point to Microsoft 365 and all email for your domain will start coming to Microsoft 365.</span></span> <span data-ttu-id="f7011-120">确保你已添加用户，并针对在你的域中收到电子邮件的每个人在 Microsoft 365 中设置邮箱！</span><span class="sxs-lookup"><span data-stu-id="f7011-120">Make sure you've added users and set up mailboxes in Microsoft 365 for everyone who gets email on your domain!</span></span>
  
<span data-ttu-id="f7011-121">如果你有一个用于你的企业的网站，它将在其所在的位置保持工作。</span><span class="sxs-lookup"><span data-stu-id="f7011-121">If you have a website that you use with your business, it will keep working where it is.</span></span> <span data-ttu-id="f7011-122">域连接设置步骤不会影响您的网站。</span><span class="sxs-lookup"><span data-stu-id="f7011-122">The Domain Connect setup steps don't affect your website.</span></span>
