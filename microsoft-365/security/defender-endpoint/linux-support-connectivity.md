---
title: 解决 Microsoft Defender ATP for Linux 的云连接问题
ms.reviewer: ''
description: 解决 Microsoft Defender ATP for Linux 的云连接问题
keywords: microsoft， defender， atp， linux， 云， 连接， 通信
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: af4f0b00cc4470e855c7c9cb780703d65992c55e
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51055821"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-for-linux"></a><span data-ttu-id="6f21a-104">解决 Microsoft Defender for Endpoint for Linux 的云连接问题</span><span class="sxs-lookup"><span data-stu-id="6f21a-104">Troubleshoot cloud connectivity issues for Microsoft Defender for Endpoint for Linux</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="6f21a-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="6f21a-105">**Applies to:**</span></span>
- [<span data-ttu-id="6f21a-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="6f21a-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [<span data-ttu-id="6f21a-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="6f21a-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="6f21a-108">想要体验适用于终结点的 Defender？</span><span class="sxs-lookup"><span data-stu-id="6f21a-108">Want to experience Defender for Endpoint?</span></span> [<span data-ttu-id="6f21a-109">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="6f21a-109">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="run-the-connectivity-test"></a><span data-ttu-id="6f21a-110">运行连接测试</span><span class="sxs-lookup"><span data-stu-id="6f21a-110">Run the connectivity test</span></span>

<span data-ttu-id="6f21a-111">若要测试适用于 Linux 的 Defender for Endpoint 能否通过当前网络设置与云通信，请从命令行运行连接测试：</span><span class="sxs-lookup"><span data-stu-id="6f21a-111">To test if Defender for Endpoint for Linux can communicate to the cloud with the current network settings, run a connectivity test from the command line:</span></span>

```bash
mdatp connectivity test
```

<span data-ttu-id="6f21a-112">预期输出：</span><span class="sxs-lookup"><span data-stu-id="6f21a-112">expected output:</span></span>

```output
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

<span data-ttu-id="6f21a-113">如果连接测试失败，请检查设备是否具有 Internet 访问权限，以及[](microsoft-defender-endpoint-linux.md#network-connections)代理或防火墙是否阻止了产品所需的任何终结点。</span><span class="sxs-lookup"><span data-stu-id="6f21a-113">If the connectivity test fails, check if the device has Internet access and if [any of the endpoints required by the product](microsoft-defender-endpoint-linux.md#network-connections) are blocked by a proxy or firewall.</span></span>

<span data-ttu-id="6f21a-114">错误 35 或 60 的失败表示证书固定被拒绝。</span><span class="sxs-lookup"><span data-stu-id="6f21a-114">Failures with curl error 35 or 60, indicate certificate pinning rejection.</span></span> <span data-ttu-id="6f21a-115">请检查连接是否位于 SSL 或 HTTPS 检查下。</span><span class="sxs-lookup"><span data-stu-id="6f21a-115">Please check if the connection is under SSL or HTTPS inspection.</span></span> <span data-ttu-id="6f21a-116">如果是这样，将 Microsoft Defender for Endpoint 添加到允许列表。</span><span class="sxs-lookup"><span data-stu-id="6f21a-116">If so, add Microsoft Defender for Endpoint to the allow list.</span></span>

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-transparent-proxy"></a><span data-ttu-id="6f21a-117">无代理或具有透明代理的环境疑难解答步骤</span><span class="sxs-lookup"><span data-stu-id="6f21a-117">Troubleshooting steps for environments without proxy or with transparent proxy</span></span>

<span data-ttu-id="6f21a-118">若要测试在没有代理或具有透明代理的环境中连接是否被阻止，在终端中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6f21a-118">To test that a connection is not blocked in an environment without a proxy or with a transparent proxy, run the following command in the terminal:</span></span>

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

<span data-ttu-id="6f21a-119">此命令的输出应类似于：</span><span class="sxs-lookup"><span data-stu-id="6f21a-119">The output from this command should be similar to:</span></span>

```Output
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```

## <a name="troubleshooting-steps-for-environments-with-static-proxy"></a><span data-ttu-id="6f21a-120">使用静态代理的环境疑难解答步骤</span><span class="sxs-lookup"><span data-stu-id="6f21a-120">Troubleshooting steps for environments with static proxy</span></span>

> [!WARNING]
> <span data-ttu-id="6f21a-121">不支持 PAC、WPAD 和经过身份验证的代理。</span><span class="sxs-lookup"><span data-stu-id="6f21a-121">PAC, WPAD, and authenticated proxies are not supported.</span></span> <span data-ttu-id="6f21a-122">确保仅使用静态代理或透明代理。</span><span class="sxs-lookup"><span data-stu-id="6f21a-122">Ensure that only a static proxy or transparent proxy is being used.</span></span>
>
> <span data-ttu-id="6f21a-123">出于安全考虑，也不支持 SSL 检查和截获代理。</span><span class="sxs-lookup"><span data-stu-id="6f21a-123">SSL inspection and intercepting proxies are also not supported for security reasons.</span></span> <span data-ttu-id="6f21a-124">为 SSL 检查和代理服务器配置例外，以直接将数据从 Defender for Endpoint for Linux 传递到相关 URL，而不会拦截。</span><span class="sxs-lookup"><span data-stu-id="6f21a-124">Configure an exception for SSL inspection and your proxy server to directly pass through data from Defender for Endpoint for Linux to the relevant URLs without interception.</span></span> <span data-ttu-id="6f21a-125">将拦截证书添加到全局存储将不允许拦截。</span><span class="sxs-lookup"><span data-stu-id="6f21a-125">Adding your interception certificate to the global store will not allow for interception.</span></span>

<span data-ttu-id="6f21a-126">如果需要静态代理，则向上述命令添加代理参数，其中 `proxy_address:port` 对应于代理地址和端口：</span><span class="sxs-lookup"><span data-stu-id="6f21a-126">If a static proxy is required, add a proxy parameter to the above command, where `proxy_address:port` correspond to the proxy address and port:</span></span>

```bash
curl -x http://proxy_address:port -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

<span data-ttu-id="6f21a-127">确保使用与文件中配置相同的代理地址和 `/lib/system/system/mdatp.service` 端口。</span><span class="sxs-lookup"><span data-stu-id="6f21a-127">Ensure that you use the same proxy address and port as configured in the `/lib/system/system/mdatp.service` file.</span></span> <span data-ttu-id="6f21a-128">如果上述命令出错，请检查代理配置。</span><span class="sxs-lookup"><span data-stu-id="6f21a-128">Check your proxy configuration if there are errors from the above commands.</span></span>

> [!WARNING]
> <span data-ttu-id="6f21a-129">无法通过系统范围环境变量配置静态 `HTTPS_PROXY` 代理。</span><span class="sxs-lookup"><span data-stu-id="6f21a-129">The static proxy cannot be configured through a system-wide `HTTPS_PROXY` environment variable.</span></span> <span data-ttu-id="6f21a-130">相反，请确保 `HTTPS_PROXY` 在 文件中正确 `/lib/system/system/mdatp.service` 设置。</span><span class="sxs-lookup"><span data-stu-id="6f21a-130">Instead, ensure that `HTTPS_PROXY` is properly set in the `/lib/system/system/mdatp.service` file.</span></span>

<span data-ttu-id="6f21a-131">若要使用静态代理， `mdatp.service` 必须修改文件。</span><span class="sxs-lookup"><span data-stu-id="6f21a-131">To use a static proxy, the `mdatp.service` file must be modified.</span></span> <span data-ttu-id="6f21a-132">确保将前 `#` 导代码从 中删除为取消以下行的注释 `/lib/systemd/system/mdatp.service` ：</span><span class="sxs-lookup"><span data-stu-id="6f21a-132">Ensure the leading `#` is removed to uncomment the following line from `/lib/systemd/system/mdatp.service`:</span></span>

```bash
#Environment="HTTPS_PROXY=http://address:port"
```

<span data-ttu-id="6f21a-133">还要确保填充正确的静态代理地址以替换 `address:port` 。</span><span class="sxs-lookup"><span data-stu-id="6f21a-133">Also ensure that the correct static proxy address is filled in to replace `address:port`.</span></span>

<span data-ttu-id="6f21a-134">如果此文件正确，请尝试在终端中运行以下命令以重新加载适用于 Linux 的 Defender for Endpoint 并传播设置：</span><span class="sxs-lookup"><span data-stu-id="6f21a-134">If this file is correct, try running the following command in the terminal to reload Defender for Endpoint for Linux and propagate the setting:</span></span>

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```

<span data-ttu-id="6f21a-135">成功后，尝试从命令行进行另一个连接测试：</span><span class="sxs-lookup"><span data-stu-id="6f21a-135">Upon success, attempt another connectivity test from the command line:</span></span>

```bash
mdatp connectivity test
```

<span data-ttu-id="6f21a-136">如果问题仍然存在，请联系客户支持部门。</span><span class="sxs-lookup"><span data-stu-id="6f21a-136">If the problem persists, contact customer support.</span></span>

## <a name="resources"></a><span data-ttu-id="6f21a-137">资源</span><span class="sxs-lookup"><span data-stu-id="6f21a-137">Resources</span></span>

- <span data-ttu-id="6f21a-138">若要详细了解如何将产品配置为使用静态代理，请参阅为静态代理发现配置[Microsoft Defender for Endpoint。](linux-static-proxy-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="6f21a-138">For more information about how to configure the product to use a static proxy, see [Configure Microsoft Defender for Endpoint for static proxy discovery](linux-static-proxy-configuration.md).</span></span>
