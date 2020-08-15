---
title: 'Microsoft 365 管理中心内的 microsoft 365 连接测试 (预览) '
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 'M365 管理中心中的 Microsoft 365 连接测试 (preview) '
ms.openlocfilehash: 421df459e2a8a1c1c62680b2d3658f5bdd297b25
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687870"
---
# <a name="microsoft-365-connectivity-test-in-the-microsoft-365-admin-center-preview"></a><span data-ttu-id="18ceb-103">Microsoft 365 管理中心中的 microsoft 365 连接测试 (预览版) </span><span class="sxs-lookup"><span data-stu-id="18ceb-103">Microsoft 365 connectivity test in the Microsoft 365 admin center (preview)</span></span>

<span data-ttu-id="18ceb-104">Microsoft 365 连接测试位于 <https://connectivity.office.com> 。</span><span class="sxs-lookup"><span data-stu-id="18ceb-104">The Microsoft 365 connectivity test is located at <https://connectivity.office.com>.</span></span> <span data-ttu-id="18ceb-105">它是一个辅助工具，可用于 **运行状况 | 的 Microsoft 365 管理中心内的网络洞察力和网络积分信息。网络性能** 菜单。</span><span class="sxs-lookup"><span data-stu-id="18ceb-105">It is an adjunct tool to the network insights and network score information available in the Microsoft 365 admin center under the **Health | Network Performance** menu.</span></span>

>[!NOTE]
><span data-ttu-id="18ceb-106">加入工具支持 WW 商业和 GCC 中的租户，但不支持 GCC 高、DoD、德国或中国的租户。</span><span class="sxs-lookup"><span data-stu-id="18ceb-106">The onboarding tool supports tenants in WW Commercial and GCC Moderate but not GCC High, DoD, Germany or China.</span></span>

<span data-ttu-id="18ceb-107">Microsoft 365 管理中心的网络洞察力基于 Microsoft 365 租户的产品度量。</span><span class="sxs-lookup"><span data-stu-id="18ceb-107">The network insights in the Microsoft 365 Admin Center are based on in-product measurements for your Microsoft 365 tenant.</span></span> <span data-ttu-id="18ceb-108">相比之下，Microsoft 365 连接测试中的网络洞察力在该工具中本地运行。</span><span class="sxs-lookup"><span data-stu-id="18ceb-108">In comparison, the network insights from the Microsoft 365 connectivity test are run locally in the tool.</span></span> <span data-ttu-id="18ceb-109">可以在产品中完成的测试是有限的，并且可以通过在用户的本地运行测试来收集更多数据，从而获得更深入的见解。</span><span class="sxs-lookup"><span data-stu-id="18ceb-109">Testing that can be done in-product is limited and by running tests local to the user more data can be gathered resulting in deeper insights.</span></span> <span data-ttu-id="18ceb-110">请考虑，Microsoft 365 管理中心中的网络见解将显示在特定办公地点使用 Microsoft 365 的网络问题。</span><span class="sxs-lookup"><span data-stu-id="18ceb-110">Consider then that the network insights in the Microsoft 365 Admin Center will show that there is a networking problem for use of Microsoft 365 at a specific office location.</span></span> <span data-ttu-id="18ceb-111">Microsoft 365 连接测试可帮助确定问题的根本原因，从而导致建议的网络性能改进操作。</span><span class="sxs-lookup"><span data-stu-id="18ceb-111">The Microsoft 365 connectivity test can help to identify the root cause of that problem leading to a recommended network performance improvement action.</span></span>

<span data-ttu-id="18ceb-112">我们建议将这些信息结合使用，以便在 Microsoft 365 管理中心中的每个办公室位置评估网络质量状态，并在部署基于 Microsoft 365 连接测试的测试之后找到更多的详细信息。</span><span class="sxs-lookup"><span data-stu-id="18ceb-112">We recommend that these be used together where networking quality status can be assessed for each office location in the Microsoft 365 Admin Center and more specifics can be found after deployment of testing based on the Microsoft 365 connectivity test.</span></span>

>[!IMPORTANT]
><span data-ttu-id="18ceb-113">网络洞察力、Microsoft 365 管理中心中的性能建议和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Microsoft 365 租户。</span><span class="sxs-lookup"><span data-stu-id="18ceb-113">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="the-advanced-tests-client-application"></a><span data-ttu-id="18ceb-114">高级测试客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="18ceb-114">The advanced tests client application</span></span>

<span data-ttu-id="18ceb-115">Microsoft 365 连接测试分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="18ceb-115">There are two parts to the Microsoft 365 connectivity test.</span></span> <span data-ttu-id="18ceb-116">网站有 <https://connectivity.office.com> 一个可下载的 Windows 客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="18ceb-116">There is the web site <https://connectivity.office.com> and there is a downloadable Windows client application.</span></span> <span data-ttu-id="18ceb-117">可下载的客户端运行高级网络连接测试，大多数测试都需要运行此测试。</span><span class="sxs-lookup"><span data-stu-id="18ceb-117">The downloadable client runs advanced network connectivity tests and most of the tests require this to be run.</span></span>

<span data-ttu-id="18ceb-118">您可以从网站运行高级客户端测试，它会在运行时将结果重新填充到网页中。</span><span class="sxs-lookup"><span data-stu-id="18ceb-118">You can run the advanced client test from the web site, and it will populate results back into the web page as it runs.</span></span>

![O365 网络载入工具示例测试结果](../media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a><span data-ttu-id="18ceb-120">用户办公室位置</span><span class="sxs-lookup"><span data-stu-id="18ceb-120">User office location</span></span>

<span data-ttu-id="18ceb-121">用户办公室的位置是从用户 web 浏览器中检测到的。</span><span class="sxs-lookup"><span data-stu-id="18ceb-121">The user office location is detected from the users web browser.</span></span> <span data-ttu-id="18ceb-122">它用于标识与企业网络周边的特定部分之间的网络距离。</span><span class="sxs-lookup"><span data-stu-id="18ceb-122">It is used to identify network distances to specific parts of the enterprise network perimeter.</span></span>

<span data-ttu-id="18ceb-123">用户办公室位置显示在地图视图中。</span><span class="sxs-lookup"><span data-stu-id="18ceb-123">The user office location is shown on the map view.</span></span>

## <a name="distance-to-the-network-egress-location"></a><span data-ttu-id="18ceb-124">到网络传出位置的距离</span><span class="sxs-lookup"><span data-stu-id="18ceb-124">Distance to the network egress location</span></span>

<span data-ttu-id="18ceb-125">我们在服务器端标识网络出口 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="18ceb-125">We identify the network egress IP Address on the server side.</span></span> <span data-ttu-id="18ceb-126">位置数据库用于查找网络出口的大概位置，并确定从该位置到办公室位置的距离。</span><span class="sxs-lookup"><span data-stu-id="18ceb-126">Location databases are used to look up the approximate location for the network egress and determine the distance from that location to the office location.</span></span> <span data-ttu-id="18ceb-127">如果距离大于500英里 (800 公里) ，这会显示为网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-127">This is shown as a network insight if the distance is greater than 500 miles (800 kilometers).</span></span>

<span data-ttu-id="18ceb-128">网络出局位置显示在地图视图中，并连接到用户办公室位置，以指示企业 WAN 中的网络 backhaul。</span><span class="sxs-lookup"><span data-stu-id="18ceb-128">The network egress location is shown on the map view and connected to the user office location indicating the network backhaul inside of the enterprise WAN.</span></span>

<span data-ttu-id="18ceb-129">从网络传出 IP 地址查找的位置可能不准确，这将导致此测试产生错误结果。</span><span class="sxs-lookup"><span data-stu-id="18ceb-129">The location looked up from the network egress IP Address may not be accurate and this would lead to a false result from this test.</span></span> <span data-ttu-id="18ceb-130">若要验证是否为特定 IP 地址出现此错误，可以使用可公开访问的网络 IP 地址位置网站。</span><span class="sxs-lookup"><span data-stu-id="18ceb-130">To validate if this error is occurring for a specific IP Address you can use publicly accessible network IP Address location web sites.</span></span>

<span data-ttu-id="18ceb-131">建议在 Microsoft 365 网络连接中，将本地和直接的网络出口从用户办公室位置实施到 Internet。</span><span class="sxs-lookup"><span data-stu-id="18ceb-131">Implementing local and direct network egress from user office locations to the Internet is recommended for Microsoft 365 network connectivity.</span></span> <span data-ttu-id="18ceb-132">对本地和直接出口的改进是解决此网络洞察力的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="18ceb-132">Improvements to local and direct egress are the best way to address this network insight.</span></span>

## <a name="exchange-online-service-front-door"></a><span data-ttu-id="18ceb-133">Exchange Online 服务前盖</span><span class="sxs-lookup"><span data-stu-id="18ceb-133">Exchange Online service front door</span></span>

<span data-ttu-id="18ceb-134">以 Outlook 执行此功能的相同方式标识了 "使用中的 Exchange Online 服务前向门"，并将网络 TCP 延迟从用户办公室位置测量到它。</span><span class="sxs-lookup"><span data-stu-id="18ceb-134">The in-use Exchange Online service front door is identified in the same way that Outlook does this and we measure the network TCP latency from the user office location to it.</span></span> <span data-ttu-id="18ceb-135">将显示这些说明，并将与当前位置的建议最佳服务前盖列表进行比较，以供使用的 Exchange Online 服务前向。</span><span class="sxs-lookup"><span data-stu-id="18ceb-135">These are both shown and the in-use Exchange Online service front door is compared to the list of recommended optimal service front doors for the current location.</span></span> <span data-ttu-id="18ceb-136">如果使用非最佳 Exchange Online 服务前向门，这会显示为网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-136">This is shown as a network insight if a non-optimal Exchange Online service front door is in use.</span></span>

<span data-ttu-id="18ceb-137">使用非最佳 Exchange Online 服务前盖可能是由于网络 backhaul 在公司网络出口前，在这种情况下，我们建议本地和直接网络出口。</span><span class="sxs-lookup"><span data-stu-id="18ceb-137">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="18ceb-138">也可能是由于使用远程 DNS 递归冲突解决服务器而导致的，在这种情况下，我们建议您将 DNS 递归解析器服务器与网络出口对齐。</span><span class="sxs-lookup"><span data-stu-id="18ceb-138">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="18ceb-139">我们计算对 Exchange Online 服务前向门的 TCP 延迟的潜在改进。</span><span class="sxs-lookup"><span data-stu-id="18ceb-139">We calculate a potential improvement in TCP latency to the Exchange Online service front door.</span></span> <span data-ttu-id="18ceb-140">为此，请查看测试的用户办公室位置网络延迟，并将网络延迟从当前位置减去当前位置，再减去 closets Exchange Online service 前门。</span><span class="sxs-lookup"><span data-stu-id="18ceb-140">This is done by looking at the tested user office location network latency and subtracting the network latency from the current location to the closets Exchange Online service front door.</span></span> <span data-ttu-id="18ceb-141">不同之处表示潜在的改进机会。</span><span class="sxs-lookup"><span data-stu-id="18ceb-141">The difference represents the potential opportunity for improvement.</span></span>

## <a name="comparison-of-performance-of-customers-in-the-area"></a><span data-ttu-id="18ceb-142">区域中客户的性能比较</span><span class="sxs-lookup"><span data-stu-id="18ceb-142">Comparison of performance of customers in the area</span></span>

<span data-ttu-id="18ceb-143">与同一地铁区域中的其他 Microsoft 365 客户相比，Exchange Online 服务前向的用户办公室位置的网络 TCP 延迟。</span><span class="sxs-lookup"><span data-stu-id="18ceb-143">The network TCP latency of the user office location to the Exchange Online service front door is compared to other Microsoft 365 customers in the same metro area.</span></span> <span data-ttu-id="18ceb-144">如果在同一地铁区域中10% 或更多的客户具有更好的性能，则显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-144">A network insight is shown if 10% or more of customers in the same metro area have better performance.</span></span>

<span data-ttu-id="18ceb-145">根据城市中的所有用户都可以访问相同的电信基础结构和与 Internet 电路和 Microsoft 网络的邻近性，生成网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-145">This network insight is generated on the basis that all users in a city have access to the same telecommunications infrastructure and the same proximity to Internet circuits and Microsoft's network.</span></span>

## <a name="in-use-default-gateway"></a><span data-ttu-id="18ceb-146">使用默认网关</span><span class="sxs-lookup"><span data-stu-id="18ceb-146">In use default gateway</span></span>

<span data-ttu-id="18ceb-147">"使用中的默认网关" 是测试客户端为路由 TCP/IP 网络连接而配置的路由器。</span><span class="sxs-lookup"><span data-stu-id="18ceb-147">The in-use default gateway is the router that the test client has configured for routing TCP/IP network connections.</span></span>

<span data-ttu-id="18ceb-148">提供此功能仅用于提供信息，并不会影响网络的洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-148">This is provided for information only and does not contribute to any network insight.</span></span>

## <a name="in-use-dns-servers"></a><span data-ttu-id="18ceb-149">在 "使用 DNS 服务器 (s) </span><span class="sxs-lookup"><span data-stu-id="18ceb-149">In use DNS server(s)</span></span>

<span data-ttu-id="18ceb-150">此示例显示在运行测试的客户端计算机上配置的 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="18ceb-150">This shows the DNS server configured on the client machine that ran the tests.</span></span> <span data-ttu-id="18ceb-151">它可能是 DNS 递归解析器服务器，但这并不常见。</span><span class="sxs-lookup"><span data-stu-id="18ceb-151">It might be a DNS Recursive Resolver server however this is uncommon.</span></span> <span data-ttu-id="18ceb-152">它更可能是缓存 DNS 结果并将任何未缓存的 DNS 请求转发到另一个 DNS 服务器的 DNS 转发器服务器。</span><span class="sxs-lookup"><span data-stu-id="18ceb-152">It is more likely to be a DNS forwarder server which caches DNS results and forwards any uncached DNS requests to another DNS server.</span></span>

<span data-ttu-id="18ceb-153">提供此功能仅用于提供信息，并不会影响网络的洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-153">This is provided for information only and does not contribute to any network insight.</span></span>

## <a name="identified-dns-recursive-resolver-server"></a><span data-ttu-id="18ceb-154">已标识 DNS 递归冲突解决服务器</span><span class="sxs-lookup"><span data-stu-id="18ceb-154">Identified DNS Recursive Resolver server</span></span>

<span data-ttu-id="18ceb-155">通过发出特定的 DNS 请求，然后向 DNS 名称服务器提供来自收到相同请求的 IP 地址，可以标识使用中的 DNS 递归冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="18ceb-155">The in-use DNS Recursive Resolver is identified by making a specific DNS request and then asking the DNS Name Server for the IP Address that it received the same request from.</span></span> <span data-ttu-id="18ceb-156">此 IP 地址是 DNS 递归解析程序，将在 IP 地址位置数据库中查找以找到该位置。</span><span class="sxs-lookup"><span data-stu-id="18ceb-156">This IP Address is the DNS Recursive Resolver and it will be looked up in IP Address location databases to find the location.</span></span> <span data-ttu-id="18ceb-157">然后计算从用户办公室位置到 DNS 递归解析服务器位置之间的距离。</span><span class="sxs-lookup"><span data-stu-id="18ceb-157">The distance from the user office location to the DNS Recursive Resolver server location is then calculated.</span></span> <span data-ttu-id="18ceb-158">如果距离大于500英里 (800 公里) ，这会显示为网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-158">This is shown as a network insight if the distance is greater than 500 miles (800 kilometers).</span></span>

<span data-ttu-id="18ceb-159">从网络传出 IP 地址查找的位置可能不准确，这将导致此测试产生错误结果。</span><span class="sxs-lookup"><span data-stu-id="18ceb-159">The location looked up from the network egress IP Address may not be accurate and this would lead to a false result from this test.</span></span> <span data-ttu-id="18ceb-160">若要验证是否为特定 IP 地址出现此错误，可以使用可公开访问的网络 IP 地址位置网站。</span><span class="sxs-lookup"><span data-stu-id="18ceb-160">To validate if this error is occurring for a specific IP Address you can use publicly accessible network IP Address location web sites.</span></span>

<span data-ttu-id="18ceb-161">此网络洞察力尤其会影响 Exchange Online 服务前盖的选择。</span><span class="sxs-lookup"><span data-stu-id="18ceb-161">This network insight will specifically impact the selection of the Exchange Online service front door.</span></span> <span data-ttu-id="18ceb-162">若要解决此深入了解，本地和直接网络出口应为先决条件，然后 DNS 递归解析器应位于该网络出口附近。</span><span class="sxs-lookup"><span data-stu-id="18ceb-162">To address this insight local and direct network egress should be a pre-requisite and then DNS Recursive Resolver should be located close to that network egress.</span></span>

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a><span data-ttu-id="18ceb-163">Exchange Online 前端服务器和 SharePoint Online 前端服务器的 DNS 查找</span><span class="sxs-lookup"><span data-stu-id="18ceb-163">DNS lookup of Exchange Online front end server and SharePoint Online front end server</span></span>

<span data-ttu-id="18ceb-164">这些将显示这两个 Microsoft 365 工作负载的服务前向门的 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="18ceb-164">These show the DNS record for the service front door for these two Microsoft 365 workloads.</span></span> <span data-ttu-id="18ceb-165">仅提供了这些信息，并且没有相关的网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-165">They are provided for information only and there is no associated network insight.</span></span>

## <a name="proxy-server-identification"></a><span data-ttu-id="18ceb-166">代理服务器标识</span><span class="sxs-lookup"><span data-stu-id="18ceb-166">Proxy server identification</span></span>

<span data-ttu-id="18ceb-167">我们) 在本地计算机上配置代理服务器 (s。</span><span class="sxs-lookup"><span data-stu-id="18ceb-167">We identify proxy server(s) configured on the local machine.</span></span> <span data-ttu-id="18ceb-168">我们确定是否在网络路径中配置了这些配置以优化类别 Microsoft 365 网络流量。</span><span class="sxs-lookup"><span data-stu-id="18ceb-168">We identify if any of these are configured in the network path for optimize category Microsoft 365 network traffic.</span></span> <span data-ttu-id="18ceb-169">我们确定从用户办公室位置到代理服务器的距离。</span><span class="sxs-lookup"><span data-stu-id="18ceb-169">We identify the distance from the user office location to the proxy servers.</span></span> <span data-ttu-id="18ceb-170">先通过 ICMP ping 测试距离，如果此操作失败，我们使用 TCP ping 进行测试，如果失败，则在 IP 地址位置数据库中查找代理服务器 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="18ceb-170">The distance is tested first by ICMP ping and if that fails we test with TCP ping and finally if that fails we look up the proxy server IP Address in an IP Address location database.</span></span> <span data-ttu-id="18ceb-171">如果代理服务器超过500英里 (800 公里) 远离用户办公室位置，我们将显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-171">We show a network insight if the proxy server is further than 500 miles (800 kilometers) away from the user office location.</span></span>

## <a name="media-quality-checks"></a><span data-ttu-id="18ceb-172">媒体质量检查</span><span class="sxs-lookup"><span data-stu-id="18ceb-172">Media quality checks</span></span>

<span data-ttu-id="18ceb-173">此测试将安装并运行 Skype for Business 网络评估工具并解释结果。</span><span class="sxs-lookup"><span data-stu-id="18ceb-173">This test installs and runs the Skype for Business network assessment tool and interprets the results.</span></span> <span data-ttu-id="18ceb-174">可以在中找到该工具 [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885) 。</span><span class="sxs-lookup"><span data-stu-id="18ceb-174">The tool can be found at [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885).</span></span>

<span data-ttu-id="18ceb-175">这些是由 Microsoft 团队音频和视频通话和会议功能使用的 UDP 协议测试。</span><span class="sxs-lookup"><span data-stu-id="18ceb-175">These are UDP protocol tests as is used by Microsoft Teams audio and video call and conferencing functionality.</span></span> <span data-ttu-id="18ceb-176">我们测试 UDP 数据包丢失、UDP 网络延迟、UDP 抖动和 UDP 数据包重新排序。</span><span class="sxs-lookup"><span data-stu-id="18ceb-176">We test for UDP packet loss, UDP network latency, UDP jitter, and UDP packet reorder.</span></span> <span data-ttu-id="18ceb-177">如果其中有任何超出允许的范围，则显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-177">A network insight is shown if any of these are over the allowable range.</span></span>

## <a name="tcp-connectivity-tests"></a><span data-ttu-id="18ceb-178">TCP 连接测试</span><span class="sxs-lookup"><span data-stu-id="18ceb-178">TCP Connectivity tests</span></span>

<span data-ttu-id="18ceb-179">我们测试从用户办公室位置到所有必需的 Microsoft 365 网络终结点的 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="18ceb-179">We test for HTTP connectivity from the user office location to all of the required Microsoft 365 network endpoints.</span></span> <span data-ttu-id="18ceb-180">这些内容是在中发布的 [https://aka.ms/o365ip](https://aka.ms/o365ip) 。</span><span class="sxs-lookup"><span data-stu-id="18ceb-180">These are published at [https://aka.ms/o365ip](https://aka.ms/o365ip).</span></span> <span data-ttu-id="18ceb-181">对于任何不能连接到的必需网络终结点，都会显示网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-181">A network insight is shown for any required network endpoints which cannot be connected to.</span></span>

<span data-ttu-id="18ceb-182">连接 ay 由企业网络外围上的代理服务器、防火墙或其他网络安全设备阻止，或作为云代理使用。</span><span class="sxs-lookup"><span data-stu-id="18ceb-182">Connectivity ay be blocked by a proxy server, a firewall, or another network security device on the enterprise network perimeter or in use as a cloud proxy.</span></span>

## <a name="ssl-interception-tests"></a><span data-ttu-id="18ceb-183">SSL 侦听测试</span><span class="sxs-lookup"><span data-stu-id="18ceb-183">SSL interception tests</span></span>

<span data-ttu-id="18ceb-184">我们会在所需的每个 Microsoft 365 网络终结点（在上定义了）中测试 SSL 证书 [https://aka.ms/o365ip](https://aka.ms/o365ip) 。</span><span class="sxs-lookup"><span data-stu-id="18ceb-184">We test the SSL certificate at each required Microsoft 365 network endpoint that is in the optimize or allow category as defined at [https://aka.ms/o365ip](https://aka.ms/o365ip).</span></span> <span data-ttu-id="18ceb-185">如果有任何测试未找到 Microsoft SSL 证书，则已连接的加密网络必须已被中间网络设备截取。</span><span class="sxs-lookup"><span data-stu-id="18ceb-185">If any tests do not find a Microsoft SSL certificate, then the encrypted network connected must have been intercepted by an intermediary network device.</span></span> <span data-ttu-id="18ceb-186">网络洞察力显示在任何截获的加密网络终结点上。</span><span class="sxs-lookup"><span data-stu-id="18ceb-186">A network insight is shown on any intercepted encrypted network endpoints.</span></span>

<span data-ttu-id="18ceb-187">在找不到 Microsoft 提供的 SSL 证书的情况下，我们会显示该测试的 FQDN 以及正在使用的 SSL 证书所有者。</span><span class="sxs-lookup"><span data-stu-id="18ceb-187">Where an SSL certificate is found that isn't provided by Microsoft, we show the FQDN for the test and the in-use SSL certificate owner.</span></span> <span data-ttu-id="18ceb-188">此 SSL 证书所有者可能是代理服务器供应商，也可能是企业自签名证书。</span><span class="sxs-lookup"><span data-stu-id="18ceb-188">This SSL certificate owner may be a proxy server vendor, or it may be an enterprise self-signed certificate.</span></span>

## <a name="network-path-diagnostics"></a><span data-ttu-id="18ceb-189">网络路径诊断</span><span class="sxs-lookup"><span data-stu-id="18ceb-189">Network path diagnostics</span></span>

<span data-ttu-id="18ceb-190">本节显示了 ICMP traceroute 对 Exchange Online 服务前向门、SharePoint Online service 前门和 Microsoft 团队服务前盖的结果。</span><span class="sxs-lookup"><span data-stu-id="18ceb-190">This section shows the results of an ICMP traceroute to the Exchange Online service front door, the SharePoint Online service front door, and the Microsoft Teams service front door.</span></span> <span data-ttu-id="18ceb-191">仅提供此信息，没有相关的网络洞察力。</span><span class="sxs-lookup"><span data-stu-id="18ceb-191">It is provided for information only and there is no associated network insight.</span></span>

## <a name="faq"></a><span data-ttu-id="18ceb-192">常见问题</span><span class="sxs-lookup"><span data-stu-id="18ceb-192">FAQ</span></span>

<span data-ttu-id="18ceb-193">以下是一些常见问题的解答。</span><span class="sxs-lookup"><span data-stu-id="18ceb-193">Here are answers to some of our frequently asked questions.</span></span>

### <a name="is-this-tool-released-and-supported-by-microsoft"></a><span data-ttu-id="18ceb-194">此工具是否已发布并受 Microsoft 支持？</span><span class="sxs-lookup"><span data-stu-id="18ceb-194">Is this tool released and supported by Microsoft?</span></span>

<span data-ttu-id="18ceb-195">目前它是概念证明，我们计划定期提供更新，直到我们能够从 Microsoft 获得支持的常规可用性发布状态。</span><span class="sxs-lookup"><span data-stu-id="18ceb-195">It is currently a proof of concept and we plan to provide updates regularly until we reach general availability release status with support from Microsoft.</span></span> <span data-ttu-id="18ceb-196">请提供反馈以帮助我们改进。</span><span class="sxs-lookup"><span data-stu-id="18ceb-196">Please provide feedback to help us improve.</span></span> <span data-ttu-id="18ceb-197">我们打算将更详细的 Office 365 网络加入指南作为此工具的一部分进行发布，此工具可通过其测试结果自定义为组织。</span><span class="sxs-lookup"><span data-stu-id="18ceb-197">We are planning to publish a more detailed Office 365 Network Onboarding guide as part of this tool which is customized for the organization by its test results.</span></span>

### <a name="what-is-microsoft-365-service-front-door"></a><span data-ttu-id="18ceb-198">什么是 Microsoft 365 服务的前门？</span><span class="sxs-lookup"><span data-stu-id="18ceb-198">What is Microsoft 365 service front door?</span></span>

<span data-ttu-id="18ceb-199">Microsoft 365 服务的前端是 Microsoft 全球网络的一个入口点，Office 客户端和服务终止其网络连接。</span><span class="sxs-lookup"><span data-stu-id="18ceb-199">The Microsoft 365 service front door is an entry point on Microsoft's global network where Office clients and services terminate their network connection.</span></span> <span data-ttu-id="18ceb-200">为实现到 Microsoft 365 的最佳网络连接，建议您的网络连接在城市或地铁的最近 Microsoft 365 前向外端终止。</span><span class="sxs-lookup"><span data-stu-id="18ceb-200">For an optimal network connection to Microsoft 365, it is recommended that your network connection is terminated into the closest Microsoft 365 front door in your city or metro.</span></span>

<span data-ttu-id="18ceb-201">注意： Microsoft 365 服务前向在 Azure marketplace 中提供了与 "Azure 前门服务" 产品的直接关系。</span><span class="sxs-lookup"><span data-stu-id="18ceb-201">Note: Microsoft 365 service front door has no direct relationship to the "Azure Front Door Service" product available in the Azure marketplace.</span></span>

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a><span data-ttu-id="18ceb-202">什么是最佳 Microsoft 365 服务前门？</span><span class="sxs-lookup"><span data-stu-id="18ceb-202">What is an optimal Microsoft 365 service front door?</span></span>

<span data-ttu-id="18ceb-203">最佳 Microsoft 365 服务前盖是最接近你的网络出口（通常在你所在的城市或大都市区域中）的一门。</span><span class="sxs-lookup"><span data-stu-id="18ceb-203">An optimal Microsoft 365 service front door is one that is closest to your network egress, generally in your city or metro area.</span></span> <span data-ttu-id="18ceb-204">使用 Microsoft 365 网络性能工具来确定正在使用的 Microsoft 365 服务的前盖和最佳服务前盖的位置。</span><span class="sxs-lookup"><span data-stu-id="18ceb-204">Use the Microsoft 365 network performance tool to determine location of your in-use Microsoft 365 service front door and optimal service front door.</span></span> <span data-ttu-id="18ceb-205">如果该工具确定你的使用中的前向门是最佳的，则表示你正在以最佳方式连接到 Microsoft 的全球网络。</span><span class="sxs-lookup"><span data-stu-id="18ceb-205">If the tool determines your in-use front door is optimal, then you are optimally connecting into Microsoft's global network.</span></span>

### <a name="what-is-an-internet-egress-location"></a><span data-ttu-id="18ceb-206">Internet 出口的位置是什么？</span><span class="sxs-lookup"><span data-stu-id="18ceb-206">What is an internet egress location?</span></span>

<span data-ttu-id="18ceb-207">Internet 出局位置是网络流量退出企业网络并连接到 Internet 的位置。</span><span class="sxs-lookup"><span data-stu-id="18ceb-207">The internet egress Location is the location where your network traffic exits your enterprise network and connects to the Internet.</span></span> <span data-ttu-id="18ceb-208">这也标识为您的网络地址转换 (NAT) 设备的位置，通常与 Internet 服务提供商 (ISP) 进行连接的位置相同。</span><span class="sxs-lookup"><span data-stu-id="18ceb-208">This is also identified as the location where you have a Network Address Translation (NAT) device and usually where you connect with an Internet Service Provider (ISP).</span></span> <span data-ttu-id="18ceb-209">如果你发现您的位置和 internet 出局位置之间的距离很长，则这可能会发现重要的 WAN backhaul。</span><span class="sxs-lookup"><span data-stu-id="18ceb-209">If you see a long distance between your location and your internet egress Location, then this may identify a significant WAN backhaul.</span></span>

## <a name="related-topics"></a><span data-ttu-id="18ceb-210">相关主题</span><span class="sxs-lookup"><span data-stu-id="18ceb-210">Related topics</span></span>

[<span data-ttu-id="18ceb-211">Microsoft 365 管理中心中的网络性能建议 (preview) </span><span class="sxs-lookup"><span data-stu-id="18ceb-211">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="18ceb-212">Microsoft 365 网络性能见解 (预览版) </span><span class="sxs-lookup"><span data-stu-id="18ceb-212">Microsoft 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="18ceb-213">Microsoft 365 网络评估 (预览版) </span><span class="sxs-lookup"><span data-stu-id="18ceb-213">Microsoft 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="18ceb-214">Microsoft 365 网络连接位置服务 (预览) </span><span class="sxs-lookup"><span data-stu-id="18ceb-214">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
