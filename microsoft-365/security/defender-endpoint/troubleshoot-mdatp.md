---
title: Microsoft Defender 终结点服务问题疑难解答
description: 查找已知问题（如尝试访问服务时的服务器错误）的解决方案和解决方法。
keywords: microsoft defender for endpoint 疑难解答， Windows ATP 疑难解答， 服务器错误， 访问被拒绝， 凭据无效， 无数据， 仪表板门户， 允许， 事件查看器
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 112f682836da37ddfb51c103282518ff74563727
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186013"
---
# <a name="troubleshoot-service-issues"></a><span data-ttu-id="e58e6-104">解决服务问题</span><span class="sxs-lookup"><span data-stu-id="e58e6-104">Troubleshoot service issues</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="e58e6-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="e58e6-105">**Applies to:**</span></span>
- [<span data-ttu-id="e58e6-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="e58e6-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [<span data-ttu-id="e58e6-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="e58e6-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="e58e6-108">想要体验适用于终结点的 Defender？</span><span class="sxs-lookup"><span data-stu-id="e58e6-108">Want to experience Defender for Endpoint?</span></span> [<span data-ttu-id="e58e6-109">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="e58e6-109">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


<span data-ttu-id="e58e6-110">本部分解决使用 Microsoft Defender 高级威胁服务时可能出现的问题。</span><span class="sxs-lookup"><span data-stu-id="e58e6-110">This section addresses issues that might arise as you use the Microsoft Defender Advanced Threat service.</span></span>

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a><span data-ttu-id="e58e6-111">服务器错误 - 由于凭据无效，访问被拒绝</span><span class="sxs-lookup"><span data-stu-id="e58e6-111">Server error - Access is denied due to invalid credentials</span></span>
<span data-ttu-id="e58e6-112">如果在尝试访问服务时遇到服务器错误，则需要更改浏览器 Cookie 设置。</span><span class="sxs-lookup"><span data-stu-id="e58e6-112">If you encounter a server error when trying to access the service, you’ll need to change your browser cookie settings.</span></span>
<span data-ttu-id="e58e6-113">配置浏览器以允许 Cookie。</span><span class="sxs-lookup"><span data-stu-id="e58e6-113">Configure your browser to allow cookies.</span></span>

## <a name="elements-or-data-missing-on-the-portal"></a><span data-ttu-id="e58e6-114">门户上缺少的元素或数据</span><span class="sxs-lookup"><span data-stu-id="e58e6-114">Elements or data missing on the portal</span></span>
<span data-ttu-id="e58e6-115">如果 Microsoft Defender 安全中心中缺少某些元素或数据，则代理设置可能会阻止它。</span><span class="sxs-lookup"><span data-stu-id="e58e6-115">If some elements or data is missing on Microsoft Defender Security Center it’s possible that proxy settings are blocking it.</span></span>

<span data-ttu-id="e58e6-116">确保包括 `*.securitycenter.windows.com` 代理允许列表。</span><span class="sxs-lookup"><span data-stu-id="e58e6-116">Make sure that `*.securitycenter.windows.com` is included the proxy allowlist.</span></span>


> [!NOTE]
> <span data-ttu-id="e58e6-117">添加以下终结点时，必须使用 HTTPS 协议。</span><span class="sxs-lookup"><span data-stu-id="e58e6-117">You must use the HTTPS protocol when adding the following endpoints.</span></span>

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a><span data-ttu-id="e58e6-118">Microsoft Defender for Endpoint 服务在事件查看器中显示事件或错误日志</span><span class="sxs-lookup"><span data-stu-id="e58e6-118">Microsoft Defender for Endpoint service shows event or error logs in the Event Viewer</span></span>

<span data-ttu-id="e58e6-119">有关 Microsoft Defender [for](event-error-codes.md) Endpoint 服务报告的事件 ID 列表，请参阅使用事件查看器查看事件和错误。</span><span class="sxs-lookup"><span data-stu-id="e58e6-119">See [Review events and errors using Event Viewer](event-error-codes.md) for a list of event IDs that are reported by the Microsoft Defender for Endpoint service.</span></span> <span data-ttu-id="e58e6-120">本文还包含事件错误的疑难解答步骤。</span><span class="sxs-lookup"><span data-stu-id="e58e6-120">The article also contains troubleshooting steps for event errors.</span></span>

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a><span data-ttu-id="e58e6-121">Microsoft Defender for Endpoint 服务在重启后无法启动，并且显示错误 577</span><span class="sxs-lookup"><span data-stu-id="e58e6-121">Microsoft Defender for Endpoint service fails to start after a reboot and shows error 577</span></span>

<span data-ttu-id="e58e6-122">如果载入设备成功完成，但 Microsoft Defender for Endpoint 在重启后未启动，并且显示错误 577，请检查Windows Defender策略是否禁用了该设置。</span><span class="sxs-lookup"><span data-stu-id="e58e6-122">If onboarding devices successfully completes but Microsoft Defender for Endpoint does not start after a reboot and shows error 577, check that Windows Defender is not disabled by a policy.</span></span>

<span data-ttu-id="e58e6-123">有关详细信息，请参阅 [确保策略](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)未禁用 Microsoft Defender 防病毒。</span><span class="sxs-lookup"><span data-stu-id="e58e6-123">For more information, see [Ensure that Microsoft Defender Antivirus is not disabled by policy](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).</span></span>

## <a name="known-issues-with-regional-formats"></a><span data-ttu-id="e58e6-124">区域格式的已知问题</span><span class="sxs-lookup"><span data-stu-id="e58e6-124">Known issues with regional formats</span></span>

<span data-ttu-id="e58e6-125">**日期和时间格式**</span><span class="sxs-lookup"><span data-stu-id="e58e6-125">**Date and time formats**</span></span><br>
<span data-ttu-id="e58e6-126">时间和日期格式存在一些已知问题。</span><span class="sxs-lookup"><span data-stu-id="e58e6-126">There are some known issues with the time and date formats.</span></span> 

<span data-ttu-id="e58e6-127">支持以下日期格式：</span><span class="sxs-lookup"><span data-stu-id="e58e6-127">The following date formats are supported:</span></span>
- <span data-ttu-id="e58e6-128">MM/dd/yyyy</span><span class="sxs-lookup"><span data-stu-id="e58e6-128">MM/dd/yyyy</span></span>
- <span data-ttu-id="e58e6-129">dd/MM/yyyy</span><span class="sxs-lookup"><span data-stu-id="e58e6-129">dd/MM/yyyy</span></span>

<span data-ttu-id="e58e6-130">目前不支持以下日期和时间格式：</span><span class="sxs-lookup"><span data-stu-id="e58e6-130">The following date and time formats are currently not supported:</span></span>
- <span data-ttu-id="e58e6-131">日期格式 yyyy/MM/dd</span><span class="sxs-lookup"><span data-stu-id="e58e6-131">Date format yyyy/MM/dd</span></span>
- <span data-ttu-id="e58e6-132">日期格式 dd/MM/yy</span><span class="sxs-lookup"><span data-stu-id="e58e6-132">Date format dd/MM/yy</span></span>
- <span data-ttu-id="e58e6-133">yy 的日期格式。</span><span class="sxs-lookup"><span data-stu-id="e58e6-133">Date format with yy.</span></span> <span data-ttu-id="e58e6-134">将只显示 yyyy。</span><span class="sxs-lookup"><span data-stu-id="e58e6-134">Will only show yyyy.</span></span>
- <span data-ttu-id="e58e6-135">时间格式 HH：mm：ss 不受支持， (12 小时 AM/PM 格式不受支持) 。</span><span class="sxs-lookup"><span data-stu-id="e58e6-135">Time format HH:mm:ss is not supported (the 12 hour AM/PM format is not supported).</span></span> <span data-ttu-id="e58e6-136">仅支持 24 小时制格式。</span><span class="sxs-lookup"><span data-stu-id="e58e6-136">Only the 24-hour format is supported.</span></span>

<span data-ttu-id="e58e6-137">**使用逗号指示千位**</span><span class="sxs-lookup"><span data-stu-id="e58e6-137">**Use of comma to indicate thousand**</span></span><br>
<span data-ttu-id="e58e6-138">不支持将逗号用作数字中的分隔符。</span><span class="sxs-lookup"><span data-stu-id="e58e6-138">Support of use of comma as a separator in numbers are not supported.</span></span> <span data-ttu-id="e58e6-139">用逗号分隔数字以指示千位的区域将只看到使用点作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="e58e6-139">Regions where a number is separated with a comma to indicate a thousand, will only see the use of a dot as a separator.</span></span> <span data-ttu-id="e58e6-140">例如，15，5K 显示为 15.5K。</span><span class="sxs-lookup"><span data-stu-id="e58e6-140">For example, 15,5K is displayed as 15.5K.</span></span>

><span data-ttu-id="e58e6-141">想要体验 Microsoft Defender for Endpoint？</span><span class="sxs-lookup"><span data-stu-id="e58e6-141">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="e58e6-142">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="e58e6-142">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a><span data-ttu-id="e58e6-143">Microsoft Defender for Endpoint 租户在欧洲自动创建</span><span class="sxs-lookup"><span data-stu-id="e58e6-143">Microsoft Defender for Endpoint tenant was automatically created in Europe</span></span>
<span data-ttu-id="e58e6-144">使用 Azure 安全中心监视服务器时，会自动创建 Microsoft Defender 终结点租户。</span><span class="sxs-lookup"><span data-stu-id="e58e6-144">When you use Azure Security Center to monitor servers, a Microsoft Defender for Endpoint tenant is automatically created.</span></span> <span data-ttu-id="e58e6-145">默认情况下，Microsoft Defender for Endpoint 数据存储在欧洲。</span><span class="sxs-lookup"><span data-stu-id="e58e6-145">The Microsoft Defender for Endpoint data is stored in Europe by default.</span></span>





## <a name="related-topics"></a><span data-ttu-id="e58e6-146">相关主题</span><span class="sxs-lookup"><span data-stu-id="e58e6-146">Related topics</span></span>
- [<span data-ttu-id="e58e6-147">Microsoft Defender 终结点载入问题疑难解答</span><span class="sxs-lookup"><span data-stu-id="e58e6-147">Troubleshoot Microsoft Defender for Endpoint onboarding issues</span></span>](troubleshoot-onboarding.md)
- [<span data-ttu-id="e58e6-148">使用事件查看器查看事件和错误</span><span class="sxs-lookup"><span data-stu-id="e58e6-148">Review events and errors using Event Viewer</span></span>](event-error-codes.md)
