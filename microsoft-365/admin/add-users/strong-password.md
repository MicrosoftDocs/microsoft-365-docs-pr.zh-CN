---
title: 为用户关闭强密码要求
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: 了解如何使用 Windows PowerShell 为用户设置强密码Windows PowerShell。
ms.openlocfilehash: e2300e3c94de53cd04d0c1726538fdb8a86a1ccf
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50903532"
---
# <a name="turn-off-strong-password-requirements-for-users"></a><span data-ttu-id="ea146-103">为用户关闭强密码要求</span><span class="sxs-lookup"><span data-stu-id="ea146-103">Turn off strong password requirements for users</span></span>

<span data-ttu-id="ea146-104">本文介绍如何为用户关闭强密码要求。</span><span class="sxs-lookup"><span data-stu-id="ea146-104">This article explains how to turn off strong password requirements for your users.</span></span> <span data-ttu-id="ea146-105">Microsoft 365 商业版组织中默认启用强密码要求。</span><span class="sxs-lookup"><span data-stu-id="ea146-105">Strong password requirements are turned on by default in your Microsoft 365 for business organization.</span></span> <span data-ttu-id="ea146-106">您的组织可能要求禁用强密码。</span><span class="sxs-lookup"><span data-stu-id="ea146-106">Your organization might have requirements to disable strong passwords.</span></span> <span data-ttu-id="ea146-107">请按照以下步骤关闭强密码要求。</span><span class="sxs-lookup"><span data-stu-id="ea146-107">Follow the steps below to turn off strong password requirements.</span></span> <span data-ttu-id="ea146-108">您必须使用 PowerShell 完成这些步骤。</span><span class="sxs-lookup"><span data-stu-id="ea146-108">You have to complete these steps using PowerShell.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ea146-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="ea146-109">Before you begin</span></span>

<span data-ttu-id="ea146-110">本文适用于管理企业、学校或非营利组织的密码策略的用户。</span><span class="sxs-lookup"><span data-stu-id="ea146-110">This article is for people who manage password policy for a business, school, or nonprofit.</span></span> <span data-ttu-id="ea146-111">若要完成这些步骤，你需要使用 Microsoft 365 管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="ea146-111">To complete these steps, you need to sign in with your Microsoft 365 admin account.</span></span> [<span data-ttu-id="ea146-112">什么是管理员帐户？</span><span class="sxs-lookup"><span data-stu-id="ea146-112">What's an admin account?</span></span>](../admin-overview/admin-overview.md) <span data-ttu-id="ea146-113">您必须是全局 [管理员或密码管理员](about-admin-roles.md) 才能执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="ea146-113">You must be an [global admin or password administrator](about-admin-roles.md) to perform these steps.</span></span>

<span data-ttu-id="ea146-114">还必须使用 PowerShell 连接到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="ea146-114">You must also connect to Microsoft 365 with PowerShell.</span></span>

## <a name="set-strong-passwords"></a><span data-ttu-id="ea146-115">设置强密码</span><span class="sxs-lookup"><span data-stu-id="ea146-115">Set strong passwords</span></span>

1. <span data-ttu-id="ea146-116">[使用 PowerShell 连接到 Microsoft 365。](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)</span><span class="sxs-lookup"><span data-stu-id="ea146-116">[Connect to Microsoft 365 with PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

2. <span data-ttu-id="ea146-117">使用 PowerShell，可以使用以下命令关闭所有用户的强密码要求：</span><span class="sxs-lookup"><span data-stu-id="ea146-117">Using PowerShell, you can turn off strong password requirements for all users with the following command:</span></span>

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn of strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> <span data-ttu-id="ea146-118">userPrincipalName 必须采用 Internet 样式的登录格式，其中用户名后跟 at 符号 (@) 和域名。</span><span class="sxs-lookup"><span data-stu-id="ea146-118">The userPrincipalName must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name.</span></span> <span data-ttu-id="ea146-119">例如：user@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="ea146-119">For example: user@contoso.com.</span></span>

## <a name="related-content"></a><span data-ttu-id="ea146-120">相关内容</span><span class="sxs-lookup"><span data-stu-id="ea146-120">Related content</span></span>

[<span data-ttu-id="ea146-121">如何使用 PowerShell 连接到 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ea146-121">How to connect to Microsoft 365 with PowerShell</span></span>](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[<span data-ttu-id="ea146-122">有关 PowerShell MsolUser 命令详细信息</span><span class="sxs-lookup"><span data-stu-id="ea146-122">More information on PowerShell MsolUser commands</span></span>](/powershell/module/msonline/set-msoluser?view=azureadps-1.0)

[<span data-ttu-id="ea146-123">有关密码策略详细信息</span><span class="sxs-lookup"><span data-stu-id="ea146-123">More information on password policy</span></span>](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)