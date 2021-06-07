---
title: 导出每个设备的软件漏洞评估
description: API 响应针对每个设备，并且包含安装在公开设备上易受攻击的软件，以及这些软件产品中的任何已知漏洞。 此表还包括操作系统信息、CVE ID 和漏洞严重性信息。
keywords: api， api， 导出评估， 按设备评估， 漏洞评估报告， 设备漏洞评估， 设备漏洞报告， 安全配置评估， 安全配置报告， 软件漏洞评估， 软件漏洞报告， 计算机漏洞报告，
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 849d1ab2bbc3b8f6d883d6041adda5fe4577741d
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2021
ms.locfileid: "52789331"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a><span data-ttu-id="106d5-105">导出每个设备的软件漏洞评估</span><span class="sxs-lookup"><span data-stu-id="106d5-105">Export software vulnerabilities assessment per device</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="106d5-106">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="106d5-106">**Applies to:**</span></span>

- [<span data-ttu-id="106d5-107">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="106d5-107">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [<span data-ttu-id="106d5-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="106d5-108">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="106d5-109">想要体验 Microsoft Defender for Endpoint？</span><span class="sxs-lookup"><span data-stu-id="106d5-109">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="106d5-110">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="106d5-110">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
<span data-ttu-id="106d5-111">基于每个设备返回所有已知软件漏洞及其所有设备的详细信息。</span><span class="sxs-lookup"><span data-stu-id="106d5-111">Returns all known software vulnerabilities and their details for all devices, on a per-device basis.</span></span>

<span data-ttu-id="106d5-112">不同的 API 调用用于获取不同类型的数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-112">There are different API calls to get different types of data.</span></span> <span data-ttu-id="106d5-113">由于数据量可能很大，因此有两种方法可以检索数据：</span><span class="sxs-lookup"><span data-stu-id="106d5-113">Because the amount of data can be large, there are two ways it can be retrieved:</span></span>

- <span data-ttu-id="106d5-114">[导出软件漏洞评估 OData](#1-export-software-vulnerabilities-assessment-odata)  API 按照 OData 协议提取组织的所有数据作为 Json 响应。</span><span class="sxs-lookup"><span data-stu-id="106d5-114">[Export software vulnerabilities assessment OData](#1-export-software-vulnerabilities-assessment-odata)  The API pulls all data in your organization as Json responses, following the OData protocol.</span></span> <span data-ttu-id="106d5-115">此方法最适合设备 _数少于 100 K_ 的小组织。</span><span class="sxs-lookup"><span data-stu-id="106d5-115">This method is best for _small organizations with less than 100-K devices_.</span></span> <span data-ttu-id="106d5-116">响应会分页，因此您可以使用响应中的 \@ odata.nextLink 字段获取下一个结果。</span><span class="sxs-lookup"><span data-stu-id="106d5-116">The response is paginated, so you can use the \@odata.nextLink field from the response to fetch the next results.</span></span>

- <span data-ttu-id="106d5-117">[通过文件导出软件漏洞评估](#2-export-software-vulnerabilities-assessment-via-files) 此 API 解决方案允许更快、更可靠地提取大量数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-117">[Export software vulnerabilities assessment via files](#2-export-software-vulnerabilities-assessment-via-files) This API solution enables pulling larger amounts of data faster and more reliably.</span></span> <span data-ttu-id="106d5-118">因此，建议拥有 100 K 以上设备的大型组织使用。</span><span class="sxs-lookup"><span data-stu-id="106d5-118">Therefore, it is recommended for large organizations, with more than 100-K devices.</span></span> <span data-ttu-id="106d5-119">此 API 将组织的所有数据提取为下载文件。</span><span class="sxs-lookup"><span data-stu-id="106d5-119">This API pulls all data in your organization as download files.</span></span> <span data-ttu-id="106d5-120">该响应包含从网站下载所有数据的Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="106d5-120">The response contains URLs to download all the data from Azure Storage.</span></span> <span data-ttu-id="106d5-121">此 API 使你能够按如下方式从Azure 存储数据：</span><span class="sxs-lookup"><span data-stu-id="106d5-121">This API enables you to download all your data from Azure Storage as follows:</span></span>

  - <span data-ttu-id="106d5-122">调用 API 获取包含所有组织数据的下载 URL 列表。</span><span class="sxs-lookup"><span data-stu-id="106d5-122">Call the API to get a list of download URLs with all your organization data.</span></span>

  - <span data-ttu-id="106d5-123">使用下载 URL 下载所有文件并处理您喜欢的数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-123">Download all the files using the download URLs and process the data as you like.</span></span>

<span data-ttu-id="106d5-124">使用 _OData_ 或 (文件收集的数据) 当前状态的当前快照，不包含历史数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-124">Data that is collected (using either _OData_ or _via files_) is the current snapshot of the current state, and does not contain historic data.</span></span> <span data-ttu-id="106d5-125">为了收集历史数据，客户必须将数据保存在自己的数据存储中。</span><span class="sxs-lookup"><span data-stu-id="106d5-125">In order to collect historic data, customers must save the data in their own data storages.</span></span>

> [!Note]
>
> <span data-ttu-id="106d5-126">除非另有说明，否则列出的所有导出评估方法都是 \*\*\*\* 完全导出 (\*\*\*\* 也称作按设备 **_) 。_**</span><span class="sxs-lookup"><span data-stu-id="106d5-126">Unless indicated otherwise, all export assessment methods listed are **_full export_** and **_by device_** (also referred to as **_per device_**).</span></span>

## <a name="1-export-software-vulnerabilities-assessment-odata"></a><span data-ttu-id="106d5-127">1. 导出 OData (软件) </span><span class="sxs-lookup"><span data-stu-id="106d5-127">1. Export software vulnerabilities assessment (OData)</span></span>

### <a name="11-api-method-description"></a><span data-ttu-id="106d5-128">1.1 API 方法说明</span><span class="sxs-lookup"><span data-stu-id="106d5-128">1.1 API method description</span></span>

<span data-ttu-id="106d5-129">此 API 响应包含每个设备已安装软件的所有数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-129">This API response contains all the data of installed software per device.</span></span> <span data-ttu-id="106d5-130">返回一个包含 DeviceId、SoftwareVendor、SoftwareName、SoftwareVersion、CVEID 每个唯一组合的条目的表。</span><span class="sxs-lookup"><span data-stu-id="106d5-130">Returns a table with an entry for every unique combination of DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.</span></span>

#### <a name="limitations"></a><span data-ttu-id="106d5-131">限制</span><span class="sxs-lookup"><span data-stu-id="106d5-131">Limitations</span></span>

>- <span data-ttu-id="106d5-132">最大页面大小为 200，000。</span><span class="sxs-lookup"><span data-stu-id="106d5-132">Maximum page size is 200,000.</span></span>
>
>- <span data-ttu-id="106d5-133">此 API 的速率限制是每分钟 30 个调用和每小时 1000 个调用。</span><span class="sxs-lookup"><span data-stu-id="106d5-133">Rate limitations for this API are 30 calls per minute and 1000 calls per hour.</span></span>

### <a name="12-permissions"></a><span data-ttu-id="106d5-134">1.2 权限</span><span class="sxs-lookup"><span data-stu-id="106d5-134">1.2 Permissions</span></span>

<span data-ttu-id="106d5-135">若要调用此 API，需要以下权限之一。</span><span class="sxs-lookup"><span data-stu-id="106d5-135">One of the following permissions is required to call this API.</span></span> <span data-ttu-id="106d5-136">若要了解详细信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API 了解详细信息。](apis-intro.md)</span><span class="sxs-lookup"><span data-stu-id="106d5-136">To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs for details.](apis-intro.md)</span></span>

<span data-ttu-id="106d5-137">权限类型</span><span class="sxs-lookup"><span data-stu-id="106d5-137">Permission type</span></span> | <span data-ttu-id="106d5-138">权限</span><span class="sxs-lookup"><span data-stu-id="106d5-138">Permission</span></span> | <span data-ttu-id="106d5-139">权限显示名称</span><span class="sxs-lookup"><span data-stu-id="106d5-139">Permission display name</span></span>
---|---|---
<span data-ttu-id="106d5-140">应用程序</span><span class="sxs-lookup"><span data-stu-id="106d5-140">Application</span></span> | <span data-ttu-id="106d5-141">Vulnerability.Read.All</span><span class="sxs-lookup"><span data-stu-id="106d5-141">Vulnerability.Read.All</span></span> | <span data-ttu-id="106d5-142">\'阅读威胁和漏洞管理漏洞信息\'</span><span class="sxs-lookup"><span data-stu-id="106d5-142">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>
<span data-ttu-id="106d5-143">委派（工作或学校帐户）</span><span class="sxs-lookup"><span data-stu-id="106d5-143">Delegated (work or school account)</span></span> | <span data-ttu-id="106d5-144">Vulnerability.Read</span><span class="sxs-lookup"><span data-stu-id="106d5-144">Vulnerability.Read</span></span> | <span data-ttu-id="106d5-145">\'阅读威胁和漏洞管理漏洞信息\'</span><span class="sxs-lookup"><span data-stu-id="106d5-145">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>

### <a name="13-url"></a><span data-ttu-id="106d5-146">1.3 URL</span><span class="sxs-lookup"><span data-stu-id="106d5-146">1.3 URL</span></span>

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a><span data-ttu-id="106d5-147">1.4 参数</span><span class="sxs-lookup"><span data-stu-id="106d5-147">1.4 Parameters</span></span>

- <span data-ttu-id="106d5-148">pageSize (默认值 = 50，000) – 响应中的结果数</span><span class="sxs-lookup"><span data-stu-id="106d5-148">pageSize (default = 50,000) – number of results in response</span></span>
- <span data-ttu-id="106d5-149">$top – 要返回 (的结果数不会返回 @odata.nextLink，因此不会拉取所有) </span><span class="sxs-lookup"><span data-stu-id="106d5-149">$top – number of results to return (doesn’t return @odata.nextLink and therefore doesn’t pull all the data)</span></span>

### <a name="15-properties"></a><span data-ttu-id="106d5-150">1.5 属性</span><span class="sxs-lookup"><span data-stu-id="106d5-150">1.5 Properties</span></span>
>
>[!Note]
>
>- <span data-ttu-id="106d5-151">每条记录大约包含 1KB 的数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-151">Each record is approximately 1KB of data.</span></span> <span data-ttu-id="106d5-152">在选择正确的 pageSize 参数时，您应当考虑到这一点。</span><span class="sxs-lookup"><span data-stu-id="106d5-152">You should take this into account when choosing the correct pageSize parameter for you.</span></span>
>
>- <span data-ttu-id="106d5-153">响应中可能会返回其他一些列。</span><span class="sxs-lookup"><span data-stu-id="106d5-153">Some additional columns might be returned in the response.</span></span> <span data-ttu-id="106d5-154">这些列是临时的，可能会被删除，请仅使用记录列。</span><span class="sxs-lookup"><span data-stu-id="106d5-154">These columns are temporary and might be removed, please use only the documented columns.</span></span>
>
>- <span data-ttu-id="106d5-155">下表中定义的属性按字母顺序按属性 ID 列出。</span><span class="sxs-lookup"><span data-stu-id="106d5-155">The properties defined in the following table are listed alphabetically, by property ID.</span></span>  <span data-ttu-id="106d5-156">运行此 API 时，生成的输出不必按此表中列出的相同顺序返回。</span><span class="sxs-lookup"><span data-stu-id="106d5-156">When running this API, the resulting output will not necessarily be returned in the same order listed in this table.</span></span>
>

<span data-ttu-id="106d5-157">属性 (ID) </span><span class="sxs-lookup"><span data-stu-id="106d5-157">Property (ID)</span></span> | <span data-ttu-id="106d5-158">数据类型</span><span class="sxs-lookup"><span data-stu-id="106d5-158">Data type</span></span> | <span data-ttu-id="106d5-159">说明</span><span class="sxs-lookup"><span data-stu-id="106d5-159">Description</span></span> | <span data-ttu-id="106d5-160">返回值的示例</span><span class="sxs-lookup"><span data-stu-id="106d5-160">Example of a returned value</span></span>
:---|:---|:---|:---
<span data-ttu-id="106d5-161">CveId</span><span class="sxs-lookup"><span data-stu-id="106d5-161">CveId</span></span> | <span data-ttu-id="106d5-162">string</span><span class="sxs-lookup"><span data-stu-id="106d5-162">string</span></span> | <span data-ttu-id="106d5-163">分配给 CVE 安全机制中常见漏洞和 (漏洞) 标识符。</span><span class="sxs-lookup"><span data-stu-id="106d5-163">Unique identifier assigned to the security vulnerability under the Common Vulnerabilities and Exposures (CVE) system.</span></span> | <span data-ttu-id="106d5-164">CVE-2020-15992</span><span class="sxs-lookup"><span data-stu-id="106d5-164">CVE-2020-15992</span></span>
<span data-ttu-id="106d5-165">CvssScore</span><span class="sxs-lookup"><span data-stu-id="106d5-165">CvssScore</span></span> | <span data-ttu-id="106d5-166">string</span><span class="sxs-lookup"><span data-stu-id="106d5-166">string</span></span> | <span data-ttu-id="106d5-167">CVE 的 CVSS 分数。</span><span class="sxs-lookup"><span data-stu-id="106d5-167">The CVSS score of the CVE.</span></span> | <span data-ttu-id="106d5-168">6.2</span><span class="sxs-lookup"><span data-stu-id="106d5-168">6.2</span></span>
<span data-ttu-id="106d5-169">DeviceId</span><span class="sxs-lookup"><span data-stu-id="106d5-169">DeviceId</span></span> | <span data-ttu-id="106d5-170">string</span><span class="sxs-lookup"><span data-stu-id="106d5-170">string</span></span> | <span data-ttu-id="106d5-171">服务中设备的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="106d5-171">Unique identifier for the device in the service.</span></span> | <span data-ttu-id="106d5-172">9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1</span><span class="sxs-lookup"><span data-stu-id="106d5-172">9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1</span></span>
<span data-ttu-id="106d5-173">DeviceName</span><span class="sxs-lookup"><span data-stu-id="106d5-173">DeviceName</span></span> | <span data-ttu-id="106d5-174">string</span><span class="sxs-lookup"><span data-stu-id="106d5-174">string</span></span> | <span data-ttu-id="106d5-175">设备的完全限定 (FQDN) FQDN。</span><span class="sxs-lookup"><span data-stu-id="106d5-175">Fully qualified domain name (FQDN) of the device.</span></span> | <span data-ttu-id="106d5-176">johnlaptop.europe.contoso.com</span><span class="sxs-lookup"><span data-stu-id="106d5-176">johnlaptop.europe.contoso.com</span></span>
<span data-ttu-id="106d5-177">DiskPaths</span><span class="sxs-lookup"><span data-stu-id="106d5-177">DiskPaths</span></span>  | <span data-ttu-id="106d5-178">数组 \[ 字符串\]</span><span class="sxs-lookup"><span data-stu-id="106d5-178">Array\[string\]</span></span> | <span data-ttu-id="106d5-179">表明产品已安装在设备的磁盘证据。</span><span class="sxs-lookup"><span data-stu-id="106d5-179">Disk evidence that the product is installed on the device.</span></span> | <span data-ttu-id="106d5-180">[ "C：\Program Files (x86) \Microsoft\Silverlight\Application\silverlight.exe" ]</span><span class="sxs-lookup"><span data-stu-id="106d5-180">[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]</span></span>
<span data-ttu-id="106d5-181">ExploitabilityLevel</span><span class="sxs-lookup"><span data-stu-id="106d5-181">ExploitabilityLevel</span></span> | <span data-ttu-id="106d5-182">string</span><span class="sxs-lookup"><span data-stu-id="106d5-182">string</span></span> | <span data-ttu-id="106d5-183">此漏洞的利用级别 (NoExploit、ExploitIsPublic、ExploitIsVerified、ExploitIsInKit) </span><span class="sxs-lookup"><span data-stu-id="106d5-183">The exploitability level of this vulnerability (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)</span></span> | <span data-ttu-id="106d5-184">ExploitIsInKit</span><span class="sxs-lookup"><span data-stu-id="106d5-184">ExploitIsInKit</span></span>
<span data-ttu-id="106d5-185">FirstSeenTimestamp</span><span class="sxs-lookup"><span data-stu-id="106d5-185">FirstSeenTimestamp</span></span> | <span data-ttu-id="106d5-186">string</span><span class="sxs-lookup"><span data-stu-id="106d5-186">string</span></span> | <span data-ttu-id="106d5-187">首次在设备上看到此产品的 CVE 时。</span><span class="sxs-lookup"><span data-stu-id="106d5-187">First time the CVE of this product was seen on the device.</span></span> | <span data-ttu-id="106d5-188">2020-11-03 10:13:34.8476880</span><span class="sxs-lookup"><span data-stu-id="106d5-188">2020-11-03 10:13:34.8476880</span></span>
<span data-ttu-id="106d5-189">Id</span><span class="sxs-lookup"><span data-stu-id="106d5-189">Id</span></span> | <span data-ttu-id="106d5-190">string</span><span class="sxs-lookup"><span data-stu-id="106d5-190">string</span></span> | <span data-ttu-id="106d5-191">记录的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="106d5-191">Unique identifier for the record.</span></span> | <span data-ttu-id="106d5-192">123ABG55_573AG&mnp！</span><span class="sxs-lookup"><span data-stu-id="106d5-192">123ABG55_573AG&mnp!</span></span>
<span data-ttu-id="106d5-193">LastSeenTimestamp</span><span class="sxs-lookup"><span data-stu-id="106d5-193">LastSeenTimestamp</span></span> | <span data-ttu-id="106d5-194">string</span><span class="sxs-lookup"><span data-stu-id="106d5-194">string</span></span> | <span data-ttu-id="106d5-195">上次在设备上看到 CVE 的时间。</span><span class="sxs-lookup"><span data-stu-id="106d5-195">Last time the CVE was seen on the device.</span></span> | <span data-ttu-id="106d5-196">2020-11-03 10:13:34.8476880</span><span class="sxs-lookup"><span data-stu-id="106d5-196">2020-11-03 10:13:34.8476880</span></span>
<span data-ttu-id="106d5-197">OSPlatform</span><span class="sxs-lookup"><span data-stu-id="106d5-197">OSPlatform</span></span> | <span data-ttu-id="106d5-198">string</span><span class="sxs-lookup"><span data-stu-id="106d5-198">string</span></span> | <span data-ttu-id="106d5-199">在设备上运行的操作系统的平台。</span><span class="sxs-lookup"><span data-stu-id="106d5-199">Platform of the operating system running on the device.</span></span> <span data-ttu-id="106d5-200">这表示特定操作系统，包括同一系列中的变体，如 Windows 10 和 Windows 7。</span><span class="sxs-lookup"><span data-stu-id="106d5-200">This indicates specific operating systems, including variations within the same family, such as Windows 10 and Windows 7.</span></span> <span data-ttu-id="106d5-201">有关详细信息，请参阅 tvm 支持的操作系统和平台。</span><span class="sxs-lookup"><span data-stu-id="106d5-201">See tvm supported operating systems and platforms for details.</span></span> | <span data-ttu-id="106d5-202">Windows 10</span><span class="sxs-lookup"><span data-stu-id="106d5-202">Windows10</span></span>
<span data-ttu-id="106d5-203">RbacGroupName</span><span class="sxs-lookup"><span data-stu-id="106d5-203">RbacGroupName</span></span>  | <span data-ttu-id="106d5-204">string</span><span class="sxs-lookup"><span data-stu-id="106d5-204">string</span></span> | <span data-ttu-id="106d5-205">基于角色的访问控制 (RBAC) 组。</span><span class="sxs-lookup"><span data-stu-id="106d5-205">The role-based access control (RBAC) group.</span></span> <span data-ttu-id="106d5-206">如果此设备未分配给任何 RBAC 组，则值将为"Unassigned"。</span><span class="sxs-lookup"><span data-stu-id="106d5-206">If this device is not assigned to any RBAC group, the value will be “Unassigned.”</span></span> <span data-ttu-id="106d5-207">如果组织不包含任何 RBAC 组，则值为"None"。</span><span class="sxs-lookup"><span data-stu-id="106d5-207">If the organization doesn’t contain any RBAC groups, the value will be “None.”</span></span> | <span data-ttu-id="106d5-208">服务器</span><span class="sxs-lookup"><span data-stu-id="106d5-208">Servers</span></span>
<span data-ttu-id="106d5-209">RecommendationReference</span><span class="sxs-lookup"><span data-stu-id="106d5-209">RecommendationReference</span></span> | <span data-ttu-id="106d5-210">string</span><span class="sxs-lookup"><span data-stu-id="106d5-210">string</span></span> | <span data-ttu-id="106d5-211">对此软件相关建议 ID 的引用。</span><span class="sxs-lookup"><span data-stu-id="106d5-211">A reference to the recommendation ID related to this software.</span></span> | <span data-ttu-id="106d5-212">va-_-microsoft-_-silverlight</span><span class="sxs-lookup"><span data-stu-id="106d5-212">va-_-microsoft-_-silverlight</span></span>
<span data-ttu-id="106d5-213">RecommendedSecurityUpdate (可选) </span><span class="sxs-lookup"><span data-stu-id="106d5-213">RecommendedSecurityUpdate (optional)</span></span> | <span data-ttu-id="106d5-214">string</span><span class="sxs-lookup"><span data-stu-id="106d5-214">string</span></span> | <span data-ttu-id="106d5-215">软件供应商提供的用于解决漏洞的安全更新的名称或说明。</span><span class="sxs-lookup"><span data-stu-id="106d5-215">Name or description of the security update provided by the software vendor to address the vulnerability.</span></span> | <span data-ttu-id="106d5-216">2020 年 4 月安全更新</span><span class="sxs-lookup"><span data-stu-id="106d5-216">April 2020 Security Updates</span></span>
<span data-ttu-id="106d5-217">RecommendedSecurityUpdateId (可选) </span><span class="sxs-lookup"><span data-stu-id="106d5-217">RecommendedSecurityUpdateId (optional)</span></span> | <span data-ttu-id="106d5-218">string</span><span class="sxs-lookup"><span data-stu-id="106d5-218">string</span></span> | <span data-ttu-id="106d5-219">相应指南或知识库的适用安全更新或标识符的标识符 (KB) 文章</span><span class="sxs-lookup"><span data-stu-id="106d5-219">Identifier of the applicable security updates or identifier for the corresponding guidance or knowledge base (KB) articles</span></span> | <span data-ttu-id="106d5-220">4550961</span><span class="sxs-lookup"><span data-stu-id="106d5-220">4550961</span></span>
<span data-ttu-id="106d5-221">RegistryPaths</span><span class="sxs-lookup"><span data-stu-id="106d5-221">RegistryPaths</span></span>  | <span data-ttu-id="106d5-222">数组 \[ 字符串\]</span><span class="sxs-lookup"><span data-stu-id="106d5-222">Array\[string\]</span></span> | <span data-ttu-id="106d5-223">注册表证据，表明产品已安装在设备中。</span><span class="sxs-lookup"><span data-stu-id="106d5-223">Registry evidence that the product is installed in the device.</span></span> | <span data-ttu-id="106d5-224">[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]</span><span class="sxs-lookup"><span data-stu-id="106d5-224">[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]</span></span>
<span data-ttu-id="106d5-225">SoftwareName</span><span class="sxs-lookup"><span data-stu-id="106d5-225">SoftwareName</span></span> | <span data-ttu-id="106d5-226">string</span><span class="sxs-lookup"><span data-stu-id="106d5-226">string</span></span> | <span data-ttu-id="106d5-227">软件产品的名称。</span><span class="sxs-lookup"><span data-stu-id="106d5-227">Name of the software product.</span></span> | <span data-ttu-id="106d5-228">chrome</span><span class="sxs-lookup"><span data-stu-id="106d5-228">chrome</span></span>
<span data-ttu-id="106d5-229">SoftwareVendor</span><span class="sxs-lookup"><span data-stu-id="106d5-229">SoftwareVendor</span></span> | <span data-ttu-id="106d5-230">string</span><span class="sxs-lookup"><span data-stu-id="106d5-230">string</span></span> | <span data-ttu-id="106d5-231">软件供应商的名称。</span><span class="sxs-lookup"><span data-stu-id="106d5-231">Name of the software vendor.</span></span> | <span data-ttu-id="106d5-232">google</span><span class="sxs-lookup"><span data-stu-id="106d5-232">google</span></span>
<span data-ttu-id="106d5-233">SoftwareVersion</span><span class="sxs-lookup"><span data-stu-id="106d5-233">SoftwareVersion</span></span> | <span data-ttu-id="106d5-234">string</span><span class="sxs-lookup"><span data-stu-id="106d5-234">string</span></span> | <span data-ttu-id="106d5-235">软件产品的版本号。</span><span class="sxs-lookup"><span data-stu-id="106d5-235">Version number of the software product.</span></span> | <span data-ttu-id="106d5-236">81.0.4044.138</span><span class="sxs-lookup"><span data-stu-id="106d5-236">81.0.4044.138</span></span>
<span data-ttu-id="106d5-237">VulnerabilitySeverityLevel</span><span class="sxs-lookup"><span data-stu-id="106d5-237">VulnerabilitySeverityLevel</span></span>  | <span data-ttu-id="106d5-238">string</span><span class="sxs-lookup"><span data-stu-id="106d5-238">string</span></span> | <span data-ttu-id="106d5-239">根据 CVSS 分数和受威胁环境影响的动态因素为安全漏洞分配的严重性级别。</span><span class="sxs-lookup"><span data-stu-id="106d5-239">Severity level assigned to the security vulnerability based on the CVSS score and dynamic factors influenced by the threat landscape.</span></span> | <span data-ttu-id="106d5-240">中</span><span class="sxs-lookup"><span data-stu-id="106d5-240">Medium</span></span>

### <a name="16-examples"></a><span data-ttu-id="106d5-241">1.6 示例</span><span class="sxs-lookup"><span data-stu-id="106d5-241">1.6 Examples</span></span>

#### <a name="161-request-example"></a><span data-ttu-id="106d5-242">1.6.1 请求示例</span><span class="sxs-lookup"><span data-stu-id="106d5-242">1.6.1 Request example</span></span>

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a><span data-ttu-id="106d5-243">1.6.2 响应示例</span><span class="sxs-lookup"><span data-stu-id="106d5-243">1.6.2 Response example</span></span>

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a><span data-ttu-id="106d5-244">2. 通过文件 (导出软件漏洞) </span><span class="sxs-lookup"><span data-stu-id="106d5-244">2. Export software vulnerabilities assessment (via files)</span></span>

### <a name="21-api-method-description"></a><span data-ttu-id="106d5-245">2.1 API 方法说明</span><span class="sxs-lookup"><span data-stu-id="106d5-245">2.1 API method description</span></span>

<span data-ttu-id="106d5-246">此 API 响应包含每个设备已安装软件的所有数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-246">This API response contains all the data of installed software per device.</span></span> <span data-ttu-id="106d5-247">返回一个包含 DeviceId、SoftwareVendor、SoftwareName、SoftwareVersion、CVEID 每个唯一组合的条目的表。</span><span class="sxs-lookup"><span data-stu-id="106d5-247">Returns a table with an entry for every unique combination of DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.</span></span>

#### <a name="212-limitations"></a><span data-ttu-id="106d5-248">2.1.2 限制</span><span class="sxs-lookup"><span data-stu-id="106d5-248">2.1.2 Limitations</span></span>

<span data-ttu-id="106d5-249">此 API 的速率限制是每分钟 5 个调用和每小时 20 个调用。</span><span class="sxs-lookup"><span data-stu-id="106d5-249">Rate limitations for this API are 5 calls per minute and 20 calls per hour.</span></span>

### <a name="22-permissions"></a><span data-ttu-id="106d5-250">2.2 权限</span><span class="sxs-lookup"><span data-stu-id="106d5-250">2.2 Permissions</span></span>

<span data-ttu-id="106d5-251">若要调用此 API，需要以下权限之一。</span><span class="sxs-lookup"><span data-stu-id="106d5-251">One of the following permissions is required to call this API.</span></span> <span data-ttu-id="106d5-252">若要了解详细信息，包括如何选择权限，请参阅使用 [Microsoft Defender for Endpoint API 了解详细信息](apis-intro.md)。</span><span class="sxs-lookup"><span data-stu-id="106d5-252">To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs for details](apis-intro.md).</span></span>

<span data-ttu-id="106d5-253">权限类型</span><span class="sxs-lookup"><span data-stu-id="106d5-253">Permission type</span></span> | <span data-ttu-id="106d5-254">权限</span><span class="sxs-lookup"><span data-stu-id="106d5-254">Permission</span></span> | <span data-ttu-id="106d5-255">权限显示名称</span><span class="sxs-lookup"><span data-stu-id="106d5-255">Permission display name</span></span>
---|---|---
<span data-ttu-id="106d5-256">应用程序</span><span class="sxs-lookup"><span data-stu-id="106d5-256">Application</span></span> | <span data-ttu-id="106d5-257">Vulnerability.Read.All</span><span class="sxs-lookup"><span data-stu-id="106d5-257">Vulnerability.Read.All</span></span> | <span data-ttu-id="106d5-258">\'阅读威胁和漏洞管理漏洞信息\'</span><span class="sxs-lookup"><span data-stu-id="106d5-258">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>
<span data-ttu-id="106d5-259">委派（工作或学校帐户）</span><span class="sxs-lookup"><span data-stu-id="106d5-259">Delegated (work or school account)</span></span> | <span data-ttu-id="106d5-260">Vulnerability.Read</span><span class="sxs-lookup"><span data-stu-id="106d5-260">Vulnerability.Read</span></span> | <span data-ttu-id="106d5-261">\'阅读威胁和漏洞管理漏洞信息\'</span><span class="sxs-lookup"><span data-stu-id="106d5-261">\'Read Threat and Vulnerability Management vulnerability information\'</span></span>

### <a name="23-url"></a><span data-ttu-id="106d5-262">2.3 URL</span><span class="sxs-lookup"><span data-stu-id="106d5-262">2.3 URL</span></span>

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a><span data-ttu-id="106d5-263">2.4 参数</span><span class="sxs-lookup"><span data-stu-id="106d5-263">2.4 Parameters</span></span>

- <span data-ttu-id="106d5-264">sasValidHours – 下载 URL 在最长 24 小时 (的有效小时数) </span><span class="sxs-lookup"><span data-stu-id="106d5-264">sasValidHours – The number of hours that the download URLs will be valid for (Maximum 24 hours)</span></span>

### <a name="25-properties"></a><span data-ttu-id="106d5-265">2.5 属性</span><span class="sxs-lookup"><span data-stu-id="106d5-265">2.5 Properties</span></span>

>[!Note]
>
>- <span data-ttu-id="106d5-266">文件是 gzip 压缩文件& Json 格式。</span><span class="sxs-lookup"><span data-stu-id="106d5-266">The files are gzip compressed & in multiline Json format.</span></span>
>
>- <span data-ttu-id="106d5-267">下载 URL 的有效期仅为 3 小时;否则，可以使用 参数。</span><span class="sxs-lookup"><span data-stu-id="106d5-267">The download URLs are only valid for 3 hours; otherwise you can use the parameter.</span></span>
>
>- <span data-ttu-id="106d5-268">为了最大限度提高数据的下载速度，你可以确保从数据所在的同一 Azure 区域进行下载。</span><span class="sxs-lookup"><span data-stu-id="106d5-268">For maximum download speed of your data, you can make sure you are downloading from the same Azure region that your data resides.</span></span>
>

>[!Note]
>
>- <span data-ttu-id="106d5-269">每条记录大约包含 1KB 的数据。</span><span class="sxs-lookup"><span data-stu-id="106d5-269">Each record is approximately 1KB of data.</span></span> <span data-ttu-id="106d5-270">在选择正确的 pageSize 参数时，您应当考虑到这一点。</span><span class="sxs-lookup"><span data-stu-id="106d5-270">You should take this into account when choosing the correct pageSize parameter for you.</span></span>
>
>- <span data-ttu-id="106d5-271">响应中可能会返回其他一些列。</span><span class="sxs-lookup"><span data-stu-id="106d5-271">Some additional columns might be returned in the response.</span></span> <span data-ttu-id="106d5-272">这些列是临时的，可能会被删除，请仅使用记录列。</span><span class="sxs-lookup"><span data-stu-id="106d5-272">These columns are temporary and might be removed, please use only the documented columns.</span></span>
>

<span data-ttu-id="106d5-273">属性 (ID) </span><span class="sxs-lookup"><span data-stu-id="106d5-273">Property (ID)</span></span> | <span data-ttu-id="106d5-274">数据类型</span><span class="sxs-lookup"><span data-stu-id="106d5-274">Data type</span></span> | <span data-ttu-id="106d5-275">说明</span><span class="sxs-lookup"><span data-stu-id="106d5-275">Description</span></span> | <span data-ttu-id="106d5-276">返回值的示例</span><span class="sxs-lookup"><span data-stu-id="106d5-276">Example of a returned value</span></span>
:---|:---|:---|:---
<span data-ttu-id="106d5-277">导出文件</span><span class="sxs-lookup"><span data-stu-id="106d5-277">Export files</span></span> | <span data-ttu-id="106d5-278">数组 \[ 字符串\]</span><span class="sxs-lookup"><span data-stu-id="106d5-278">array\[string\]</span></span>  | <span data-ttu-id="106d5-279">保存组织当前快照的文件的下载 URL 列表。</span><span class="sxs-lookup"><span data-stu-id="106d5-279">A list of download URLs for files holding the current snapshot of the organization.</span></span> | <span data-ttu-id="106d5-280">[  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]</span><span class="sxs-lookup"><span data-stu-id="106d5-280">[  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]</span></span>
<span data-ttu-id="106d5-281">GeneratedTime</span><span class="sxs-lookup"><span data-stu-id="106d5-281">GeneratedTime</span></span> | <span data-ttu-id="106d5-282">string</span><span class="sxs-lookup"><span data-stu-id="106d5-282">string</span></span> | <span data-ttu-id="106d5-283">导出的生成时间。</span><span class="sxs-lookup"><span data-stu-id="106d5-283">The time that the export was generated.</span></span> | <span data-ttu-id="106d5-284">2021-05-20T08：00：00Z</span><span class="sxs-lookup"><span data-stu-id="106d5-284">2021-05-20T08:00:00Z</span></span>

### <a name="26-examples"></a><span data-ttu-id="106d5-285">2.6 示例</span><span class="sxs-lookup"><span data-stu-id="106d5-285">2.6 Examples</span></span>

#### <a name="261-request-example"></a><span data-ttu-id="106d5-286">2.6.1 请求示例</span><span class="sxs-lookup"><span data-stu-id="106d5-286">2.6.1 Request example</span></span>

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a><span data-ttu-id="106d5-287">2.6.2 响应示例</span><span class="sxs-lookup"><span data-stu-id="106d5-287">2.6.2 Response example</span></span>

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a><span data-ttu-id="106d5-288">另请参阅</span><span class="sxs-lookup"><span data-stu-id="106d5-288">See also</span></span>

- [<span data-ttu-id="106d5-289">导出每个设备的评估方法和属性</span><span class="sxs-lookup"><span data-stu-id="106d5-289">Export assessment methods and properties per device</span></span>](get-assessment-methods-properties.md)

- [<span data-ttu-id="106d5-290">导出每个设备的安全配置评估</span><span class="sxs-lookup"><span data-stu-id="106d5-290">Export secure configuration assessment per device</span></span>](get-assessment-secure-config.md)

- [<span data-ttu-id="106d5-291">导出每个设备的软件清单评估</span><span class="sxs-lookup"><span data-stu-id="106d5-291">Export software inventory assessment per device</span></span>](get-assessment-software-inventory.md)

<span data-ttu-id="106d5-292">其他相关</span><span class="sxs-lookup"><span data-stu-id="106d5-292">Other related</span></span>

- [<span data-ttu-id="106d5-293">基于风险的威胁& 漏洞管理</span><span class="sxs-lookup"><span data-stu-id="106d5-293">Risk-based threat & vulnerability management</span></span>](next-gen-threat-and-vuln-mgt.md)

- [<span data-ttu-id="106d5-294">组织中漏洞</span><span class="sxs-lookup"><span data-stu-id="106d5-294">Vulnerabilities in your organization</span></span>](tvm-weaknesses.md)