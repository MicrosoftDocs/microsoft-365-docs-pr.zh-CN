---
title: 将帐户从 Microsoft Defender for Endpoint 重定向到 Microsoft 365 安全中心
description: 如何将帐户和会话从 Defender for Endpoint 重定向到 Microsoft 365 安全中心。
keywords: Microsoft 365 安全中心，Microsoft 365 安全中心入门，安全中心重定向
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: bdad55a98dba868d45ecea383ba379108ee5305a
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50906754"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-the-microsoft-365-security-center"></a><span data-ttu-id="bdb81-104">将帐户从 Microsoft Defender for Endpoint 重定向到 Microsoft 365 安全中心</span><span class="sxs-lookup"><span data-stu-id="bdb81-104">Redirecting accounts from Microsoft Defender for Endpoint to the Microsoft 365 security center</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

<span data-ttu-id="bdb81-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="bdb81-105">**Applies to:**</span></span>
- <span data-ttu-id="bdb81-106">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="bdb81-106">Microsoft 365 Defender</span></span>
- <span data-ttu-id="bdb81-107">Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="bdb81-107">Defender for Endpoint</span></span>

<span data-ttu-id="bdb81-108">为了与 Microsoft 使用 SIEM 进行威胁防护的跨域方法以及扩展检测和响应 (XDR) 一致，我们将 Microsoft Defender 高级威胁防护重新品牌化为适用于终结点的 Microsoft Defender，并统一到单个集成门户 -Microsoft 365 安全中心。</span><span class="sxs-lookup"><span data-stu-id="bdb81-108">In alignment with Microsoft’s cross-domain approach to threat protection with SIEM and Extended detection and response (XDR), we’ve rebranded Microsoft Defender Advanced Threat Protection as Microsoft Defender for Endpoint and unified it into a single integrated portal - the Microsoft 365 security center.</span></span>

<span data-ttu-id="bdb81-109">本指南介绍如何通过启用从以前的 Microsoft Defender for Endpoint 门户 (securitycenter.windows.com 或 securitycenter.microsoft.com) 到 Microsoft 365 安全中心门户 (security.microsoft.com) 的自动重定向，将帐户路由到 Microsoft 365 安全中心。</span><span class="sxs-lookup"><span data-stu-id="bdb81-109">This guide explains how to route accounts to the Microsoft 365 security center by enabling automatic redirection from the former Microsoft Defender for Endpoint portal (securitycenter.windows.com or securitycenter.microsoft.com), to the Microsoft 365 security center portal (security.microsoft.com).</span></span>

> [!NOTE]
> <span data-ttu-id="bdb81-110">Microsoft 365 安全中心中的 Microsoft Defender for Endpoint 支持向托管安全服务提供商 [ (MSSP) ](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) 授予访问权限，方式与在 [Microsoft Defender](./mssp-access.md)安全中心授予访问权限的方式相同。</span><span class="sxs-lookup"><span data-stu-id="bdb81-110">Microsoft Defender for Endpoint in the Microsoft 365 security center supports [granting access to managed security service providers (MSSPs)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) in the same that way access is [granted in the Microsoft Defender security center](./mssp-access.md).</span></span>

## <a name="what-to-expect"></a><span data-ttu-id="bdb81-111">预期结果</span><span class="sxs-lookup"><span data-stu-id="bdb81-111">What to expect</span></span>
<span data-ttu-id="bdb81-112">启用自动重定向后，访问位于 securitycenter.windows.com 或 securitycenter.microsoft.com 的以前 Microsoft Defender 终结点门户的帐户将自动路由到位于 security.microsoft.com 的 Microsoft 365 安全中心门户。</span><span class="sxs-lookup"><span data-stu-id="bdb81-112">Once automatic redirection is enabled, accounts accessing the former Microsoft Defender for Endpoint portal at securitycenter.windows.com or securitycenter.microsoft.com, will be automatically routed to the Microsoft 365 security center portal at security.microsoft.com.</span></span>
 
<span data-ttu-id="bdb81-113">详细了解更改了哪些功能 [：Microsoft 365](microsoft-365-security-center-mde.md)安全中心中的 Microsoft Defender for Endpoint。</span><span class="sxs-lookup"><span data-stu-id="bdb81-113">Learn more about what’s changed: [Microsoft Defender for Endpoint in the Microsoft 365 security center](microsoft-365-security-center-mde.md).</span></span>

<span data-ttu-id="bdb81-114">这包括通过浏览器直接访问以前的门户的重定向，包括指向以前的 securitycenter.windows.com 门户的链接（如电子邮件通知中的链接，以及 SIEM API 调用返回的链接）。</span><span class="sxs-lookup"><span data-stu-id="bdb81-114">This includes redirection for direct access to the former portal via browser, including links pointing towards the former securitycenter.windows.com portal - such as links in email notifications, and links returned by SIEM API calls.</span></span>  

 <span data-ttu-id="bdb81-115">电子邮件通知或 SIEM API 中的外部链接当前包含指向这两个门户的链接。</span><span class="sxs-lookup"><span data-stu-id="bdb81-115">External links from email notifications or SIEM APIs currently contain links to both portals.</span></span> <span data-ttu-id="bdb81-116">启用重定向后，两个链接将指向 Microsoft 365 安全中心，直到最终删除旧链接。</span><span class="sxs-lookup"><span data-stu-id="bdb81-116">Once redirection is enabled, both links will point to the Microsoft 365 security center until the old link is eventually removed.</span></span> <span data-ttu-id="bdb81-117">我们鼓励你采用指向 Microsoft 365 安全中心的新链接。</span><span class="sxs-lookup"><span data-stu-id="bdb81-117">We encourage you to adopt the new link pointing to the Microsoft 365 security center.</span></span>

<span data-ttu-id="bdb81-118">有关链接和路由的详细信息，请参阅下表。</span><span class="sxs-lookup"><span data-stu-id="bdb81-118">Refer to the table below for more on links and routing.</span></span>
## <a name="siem-api-routing"></a><span data-ttu-id="bdb81-119">SIEM API 路由</span><span class="sxs-lookup"><span data-stu-id="bdb81-119">SIEM API routing</span></span>

|<span data-ttu-id="bdb81-120">**属性**</span><span class="sxs-lookup"><span data-stu-id="bdb81-120">**Property**</span></span>  |<span data-ttu-id="bdb81-121">**重定向关闭时的目标**</span><span class="sxs-lookup"><span data-stu-id="bdb81-121">**Destination when redirection is OFF**</span></span>  |<span data-ttu-id="bdb81-122">**重定向打开时的目标**</span><span class="sxs-lookup"><span data-stu-id="bdb81-122">**Destination when redirection is ON**</span></span> | 
|---------|---------|---------|
| <span data-ttu-id="bdb81-123">LinkToWDATP</span><span class="sxs-lookup"><span data-stu-id="bdb81-123">LinkToWDATP</span></span> | <span data-ttu-id="bdb81-124">警报页 securitycenter.windows.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-124">Alert page in securitycenter.windows.com</span></span> | <span data-ttu-id="bdb81-125">警报页 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-125">Alert page in security.microsoft.com</span></span>  |
| <span data-ttu-id="bdb81-126">IncidentLinkToWDATP</span><span class="sxs-lookup"><span data-stu-id="bdb81-126">IncidentLinkToWDATP</span></span> | <span data-ttu-id="bdb81-127">事件页面中 securitycenter.windows.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-127">Incident page in securitycenter.windows.com</span></span>  | <span data-ttu-id="bdb81-128">事件页面中 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-128">Incident page in security.microsoft.com</span></span>  |
| <span data-ttu-id="bdb81-129">LinkToMTP</span><span class="sxs-lookup"><span data-stu-id="bdb81-129">LinkToMTP</span></span> | <span data-ttu-id="bdb81-130">警报页 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-130">Alert page in security.microsoft.com</span></span> | <span data-ttu-id="bdb81-131">警报页 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-131">Alert page in security.microsoft.com</span></span>  |
| <span data-ttu-id="bdb81-132">IncidentLinkToMTP</span><span class="sxs-lookup"><span data-stu-id="bdb81-132">IncidentLinkToMTP</span></span> | <span data-ttu-id="bdb81-133">事件页面中 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-133">Incident page in security.microsoft.com</span></span>  | <span data-ttu-id="bdb81-134">事件页面中 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-134">Incident page in security.microsoft.com</span></span>  

## <a name="email-alert-notifications"></a><span data-ttu-id="bdb81-135">电子邮件通知</span><span class="sxs-lookup"><span data-stu-id="bdb81-135">Email alert notifications</span></span>

|<span data-ttu-id="bdb81-136">**属性**</span><span class="sxs-lookup"><span data-stu-id="bdb81-136">**Property**</span></span>  |<span data-ttu-id="bdb81-137">**重定向关闭时的目标**</span><span class="sxs-lookup"><span data-stu-id="bdb81-137">**Destination when redirection is OFF**</span></span>  |<span data-ttu-id="bdb81-138">**重定向打开时的目标**</span><span class="sxs-lookup"><span data-stu-id="bdb81-138">**Destination when redirection is ON**</span></span> |
|---------|---------|---------|
| <span data-ttu-id="bdb81-139">警报页面</span><span class="sxs-lookup"><span data-stu-id="bdb81-139">Alert page</span></span>  | <span data-ttu-id="bdb81-140">警报页 securitycenter.windows.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-140">Alert page in securitycenter.windows.com</span></span>  | <span data-ttu-id="bdb81-141">警报页 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-141">Alert page in security.microsoft.com</span></span>  |
| <span data-ttu-id="bdb81-142">事件页面</span><span class="sxs-lookup"><span data-stu-id="bdb81-142">Incident page</span></span>  |<span data-ttu-id="bdb81-143">事件页面中 securitycenter.windows.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-143">Incident page in securitycenter.windows.com</span></span>  | <span data-ttu-id="bdb81-144">事件页面中 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-144">Incident page in security.microsoft.com</span></span>  
| <span data-ttu-id="bdb81-145">安全中心门户中的警报页面</span><span class="sxs-lookup"><span data-stu-id="bdb81-145">Alert page in security center portal</span></span> | <span data-ttu-id="bdb81-146">警报页 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-146">Alert page in security.microsoft.com</span></span> | <span data-ttu-id="bdb81-147">警报页 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-147">Alert page in security.microsoft.com</span></span> | 
| <span data-ttu-id="bdb81-148">安全中心门户中的事件页面</span><span class="sxs-lookup"><span data-stu-id="bdb81-148">Incident page in security center portal</span></span> | <span data-ttu-id="bdb81-149">事件页面中 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-149">Incident page in security.microsoft.com</span></span>  | <span data-ttu-id="bdb81-150">事件页面中 security.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="bdb81-150">Incident page in security.microsoft.com</span></span>  |

## <a name="when-does-this-take-effect"></a><span data-ttu-id="bdb81-151">这何时生效？</span><span class="sxs-lookup"><span data-stu-id="bdb81-151">When does this take effect?</span></span> 
<span data-ttu-id="bdb81-152">启用后，此更新可能会立即对一些帐户生效。</span><span class="sxs-lookup"><span data-stu-id="bdb81-152">Once enabled, this update might take effect almost immediately for some accounts.</span></span> <span data-ttu-id="bdb81-153">但是，重定向可能需要更长时间才能传播到组织的每一个帐户。</span><span class="sxs-lookup"><span data-stu-id="bdb81-153">But the redirection might take longer to propagate to every account in your organization.</span></span> <span data-ttu-id="bdb81-154">应用此设置时的活动会话中的帐户不会从会话弹出，并且仅在结束当前会话并再次登录后路由到 Microsoft 365 安全中心。</span><span class="sxs-lookup"><span data-stu-id="bdb81-154">Accounts in active sessions while this setting is applied will not be ejected from their session and will only be routed to the Microsoft 365 security center after ending their current session and signing back in again.</span></span>  

### <a name="set-up-portal-redirection"></a><span data-ttu-id="bdb81-155">设置门户重定向</span><span class="sxs-lookup"><span data-stu-id="bdb81-155">Set up portal redirection</span></span>
<span data-ttu-id="bdb81-156">若要开始将帐户路由到 Microsoft 365 安全中心：</span><span class="sxs-lookup"><span data-stu-id="bdb81-156">To start routing accounts to the Microsoft 365 security center:</span></span>
1. <span data-ttu-id="bdb81-157">确保你是全局管理员或在 Azure Active directory 中具有安全管理员权限</span><span class="sxs-lookup"><span data-stu-id="bdb81-157">Make sure you’re a global administrator or have security administrator permissions in Azure Active directory</span></span> 

2. <span data-ttu-id="bdb81-158">[登录到](https://security.microsoft.com/) Microsoft 365 安全中心。</span><span class="sxs-lookup"><span data-stu-id="bdb81-158">[Sign in](https://security.microsoft.com/) to the Microsoft 365 security center.</span></span>

3. <span data-ttu-id="bdb81-159">导航到 **设置**  >  **终结点**  >  **常规**  >  **门户重定向或**[单击此处](https://security.microsoft.com/preferences2/portal_redirection)。</span><span class="sxs-lookup"><span data-stu-id="bdb81-159">Navigate to **Settings** > **Endpoints** > **General** > **Portal redirection** or [click here](https://security.microsoft.com/preferences2/portal_redirection).</span></span>  

4. <span data-ttu-id="bdb81-160">将"自动重定向"设置切换为 **"打开"。**</span><span class="sxs-lookup"><span data-stu-id="bdb81-160">Toggle the Automatic redirection setting to **On**.</span></span>

5. <span data-ttu-id="bdb81-161">单击 **"** 启用"以将自动重定向应用到 Microsoft 365 安全中心门户。</span><span class="sxs-lookup"><span data-stu-id="bdb81-161">Click **Enable** to apply automatic redirection to the Microsoft 365 security center portal.</span></span>

>[!IMPORTANT]
><span data-ttu-id="bdb81-162">启用此设置不会终止活动用户会话。</span><span class="sxs-lookup"><span data-stu-id="bdb81-162">Enabling this setting will not terminate active user sessions.</span></span> <span data-ttu-id="bdb81-163">应用此设置时，活动会话中的帐户只有在结束当前会话并再次登录后，才能定向到 Microsoft 365 安全中心。</span><span class="sxs-lookup"><span data-stu-id="bdb81-163">Accounts who are in an active session while this setting is applied will only be directed to the Microsoft 365 security center after ending their current session and signing in again.</span></span>

>[!NOTE]
><span data-ttu-id="bdb81-164">你必须是全局管理员或在 Azure Active Directory 中具有安全管理员权限才能启用或禁用此设置。</span><span class="sxs-lookup"><span data-stu-id="bdb81-164">You must be a global administrator or have security administrator permissions in Azure Active Directory to enable or disable this setting.</span></span>  

## <a name="can-i-go-back-to-using-the-former-portal"></a><span data-ttu-id="bdb81-165">我能否返回到使用以前的门户？</span><span class="sxs-lookup"><span data-stu-id="bdb81-165">Can I go back to using the former portal?</span></span>
<span data-ttu-id="bdb81-166">如果无法通过 Microsoft 365 安全中心门户完成某些操作或无法完成某些操作，我们希望听到有关它的信息。</span><span class="sxs-lookup"><span data-stu-id="bdb81-166">If something isn’t working for you or if there’s anything you’re unable to complete through the Microsoft 365 security center portal, we want to hear about it.</span></span> <span data-ttu-id="bdb81-167">如果遇到重定向问题，我们鼓励你使用"提供反馈提交"表单告知我们。</span><span class="sxs-lookup"><span data-stu-id="bdb81-167">If you’ve encountered any issues with redirection, we encourage you to let us know by using the Give feedback submission form.</span></span>

<span data-ttu-id="bdb81-168">若要还原到以前的 Microsoft Defender 终结点门户：</span><span class="sxs-lookup"><span data-stu-id="bdb81-168">To revert to the former Microsoft Defender for Endpoint portal:</span></span>

1. <span data-ttu-id="bdb81-169">[以全局](https://security.microsoft.com/) 管理员或 Azure Active Directory 中的安全管理员权限使用 和 帐户登录 Microsoft 365 安全中心。</span><span class="sxs-lookup"><span data-stu-id="bdb81-169">[Sign in](https://security.microsoft.com/) to the Microsoft 365 security center as a global administrator or using and account with security administrator permissions in Azure Active directory.</span></span>

2. <span data-ttu-id="bdb81-170">导航到 **设置**  >  **终结点**  >  **常规**  >  **门户重定向** 或 [在此处打开页面](https://security.microsoft.com/preferences2/portal_redirection)。</span><span class="sxs-lookup"><span data-stu-id="bdb81-170">Navigate to **Settings** > **Endpoints** > **General** > **Portal redirection** or [open the page here](https://security.microsoft.com/preferences2/portal_redirection).</span></span>  

3. <span data-ttu-id="bdb81-171">将"自动重定向"设置切换为 **"关"。**</span><span class="sxs-lookup"><span data-stu-id="bdb81-171">Toggle the Automatic redirection setting to **Off**.</span></span>

4. <span data-ttu-id="bdb81-172">当 **系统&** 时，单击"禁用共享反馈"。</span><span class="sxs-lookup"><span data-stu-id="bdb81-172">Click **Disable** & share feedback when prompted.</span></span>

<span data-ttu-id="bdb81-173">可以随时再次启用此设置。</span><span class="sxs-lookup"><span data-stu-id="bdb81-173">This setting can be enabled again at any time.</span></span> 

<span data-ttu-id="bdb81-174">禁用后，帐户将不再路由到 security.microsoft.com，并且你将再次有权访问以前的门户 -securitycenter.windows.com 或 securitycenter.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="bdb81-174">Once disabled, accounts will no longer be routed to security.microsoft.com, and you will once again have access to the former portal - securitycenter.windows.com or securitycenter.microsoft.com.</span></span> 

## <a name="related-information"></a><span data-ttu-id="bdb81-175">相关信息</span><span class="sxs-lookup"><span data-stu-id="bdb81-175">Related information</span></span>
- [<span data-ttu-id="bdb81-176">Microsoft 365 安全中心概述</span><span class="sxs-lookup"><span data-stu-id="bdb81-176">Microsoft 365 security center overview</span></span>](overview-security-center.md)
- [<span data-ttu-id="bdb81-177">Microsoft 365 安全中心中的 Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="bdb81-177">Microsoft Defender for Endpoint in the Microsoft 365 security center</span></span>](microsoft-365-security-center-mde.md)
- [<span data-ttu-id="bdb81-178">Microsoft 提供统一的 SIEM 和 XDR 以现代化安全操作</span><span class="sxs-lookup"><span data-stu-id="bdb81-178">Microsoft delivers unified SIEM and XDR to modernize security operations</span></span>](https://www.microsoft.com/security/blog/?p=91813) 
- [<span data-ttu-id="bdb81-179">XDR 与 SIEM 信息图</span><span class="sxs-lookup"><span data-stu-id="bdb81-179">XDR versus SIEM infographic</span></span>](https://afrait.com/blog/xdr-versus-siem/) 
- [<span data-ttu-id="bdb81-180">新 Defender</span><span class="sxs-lookup"><span data-stu-id="bdb81-180">The New Defender</span></span>](https://afrait.com/blog/the-new-defender/) 
- [<span data-ttu-id="bdb81-181">关于 Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="bdb81-181">About Microsoft 365 Defender</span></span>](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [<span data-ttu-id="bdb81-182">Microsoft 安全门户和管理中心</span><span class="sxs-lookup"><span data-stu-id="bdb81-182">Microsoft security portals and admin centers</span></span>](portals.md)