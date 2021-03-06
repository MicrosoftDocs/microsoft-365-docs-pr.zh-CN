---
title: 排查问题并查找与 iOS 上的 Microsoft Defender for Endpoint 相关的常见问题解答
description: 疑难解答和常见问题解答 - 适用于 iOS 上的终结点的 Microsoft Defender
keywords: microsoft， defender， Microsoft Defender for Endpoint， ios， 疑难解答， 如何
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
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b82b6993ce9ed5a3f0f3e6e13e8a260a185c9730
ms.sourcegitcommit: 6749455c52b0f98a92f6fffbc2bb86caf3538bd8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2021
ms.locfileid: "53194969"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>排查问题并查找 iOS 上 Microsoft Defender for Endpoint 上的常见问题解答

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

本主题提供疑难解答信息，以帮助你解决在 iOS 上使用 Microsoft Defender for Endpoint 时可能出现的问题。



> [!NOTE]
> iOS 上的 Defender for Endpoint 将使用 VPN 来提供 Web 保护功能。 这不是常规 VPN，它是不接受设备外流量的本地/自循环 VPN。

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>打开 VPN 后，应用无法工作
某些应用在检测到活动 VPN 时停止运行。 可以在使用此类应用时禁用 VPN。 

默认情况下，iOS 上的 Defender for Endpoint 包括并启用 Web 保护功能。 [Web](web-protection-overview.md) 保护有助于保护设备免受 Web 威胁，并保护用户免受网络钓鱼攻击。 iOS 上的 Defender for Endpoint 使用 VPN 来提供此保护。 请注意，这是本地 VPN，与传统 VPN 不同，网络流量不会在设备外部发送。

虽然默认启用，但在某些情况下可能需要你禁用 VPN。 例如，你想要运行一些在配置 VPN 时不起作用的应用。 在这种情况下，你可以选择按照以下步骤在设备上禁用应用中的 VPN：

1. 在 iOS 设备上，打开 **"设置应用**"，单击 **或点击"** 常规"，然后单击 **"VPN"。**
1. 单击或点击 Microsoft Defender for Endpoint 的"i"按钮。
1. 关闭 **"连接按需"** 以禁用 VPN。

    > [!div class="mx-imgBorder"]
    > ![VPN 配置按需连接](images/ios-vpn-config.png)

> [!NOTE]
> 禁用 VPN 后，Web 保护将不可用。 若要重新启用 Web 保护，请在设备上打开 Microsoft Defender for Endpoint 应用，然后单击或点击"启动 **VPN"。**

## <a name="co-existence-with-multiple-vpn-profiles"></a>与多个 VPN 配置文件共存

Apple iOS 不支持多个 **设备范围的** VPN 同时处于活动状态。 虽然设备上可以存在多个 VPN 配置文件，但一次只能有一个 VPN 处于活动状态。

Microsoft Defender for Endpoint VPN 可以与配置为每应用或"个人"的其他 VPN *共存*。

## <a name="battery-consumption"></a>电池消耗

在设置应用中，iOS 仅显示特定持续时间内对用户可见的应用的电池使用情况。 屏幕上显示的应用的电池使用情况仅在该持续时间内，由 iOS 根据大量因素（包括 CPU 和网络使用情况）计算。 Microsoft Defender for Endpoint 在后台使用本地/环回 VPN 来检查任何恶意网站或连接的 Web 流量。 来自任何应用的网络数据包都经过此检查，这会导致 Microsoft Defender for Endpoint 的电池使用情况计算不准确。 Microsoft Defender for Endpoint 的实际电池消耗远小于设备上"电池设置页面上显示的内容。

平均而言，运行在后台的终结点的 Microsoft Defender 每天的电池使用量大约为当天消耗的总电池的 **8.81%。** Apple 根据最终用户设备上 Microsoft Defender for Endpoint 的实际使用情况报告此指标，并且由于上述原因，还可以将指标计算到具有网络活动的其他应用。

此外，使用的 VPN 是本地 VPN，与传统 VPN 不同，网络流量不会在设备外部发送。

## <a name="data-usage"></a>数据使用情况

Microsoft Defender for Endpoint 使用本地/环回 VPN 检查任何恶意网站或连接的 Web 流量。 由于此原因，Microsoft Defender 终结点数据使用情况可能不准确。 我们还观察到，如果设备仅在移动电话网络上，服务提供商报告的数据使用量将非常接近实际使用量，而在 设置 应用中，Apple 显示的实际使用量大约是实际使用量的 1.5 倍到 2 倍。

我们还与其他 VPN 服务有类似的观察结果，并且已经向 Apple 报告了这一点。

此外，使用后端服务更新 Microsoft Defender for Endpoint 以提供更好的保护至关重要。 但是，我们正在优化 Microsoft Defender for Endpoint 的数据使用情况。

## <a name="report-unsafe-site"></a>报告不安全网站

网络钓鱼网站会模拟可信赖的网站，以获取你的个人或财务信息。 访问 ["提供有关网络保护的反馈"页](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) ，以报告可能是网络钓鱼网站的网站。

## <a name="malicious-site-detected"></a>检测到恶意站点

Microsoft Defender for Endpoint 可保护你免受网络钓鱼或其他基于 Web 的攻击。 如果检测到恶意站点，连接将被阻止，并且会向组织的安全中心门户发送警报。 警报包括连接的域名、远程 IP 地址和设备详细信息。

此外，iOS 设备上还显示通知。 点击通知将打开以下屏幕，供用户查看详细信息。

> [!div class="mx-imgBorder"]
> ![报告为不安全通知的网站的图像](images/ios-phish-alert.png)

## <a name="data-and-privacy"></a>数据和隐私

有关收集的数据和隐私的详细信息，请参阅 [Privacy Information - Microsoft Defender for Endpoint on iOS](ios-privacy.md)。

