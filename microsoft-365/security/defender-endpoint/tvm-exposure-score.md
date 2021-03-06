---
title: 曝光分数（以危险和漏洞管理
description: 公开危险和漏洞管理分数反映了组织对网络安全威胁的易受攻击程度。
keywords: 曝光分数， 适用于终结点曝光分数的 Microsoft Defender， 适用于终结点电视曝光分数的 Microsoft Defender， 组织曝光分数， 电视组织曝光分数， 危险和漏洞管理， 适用于终结点的 Microsoft Defender
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
ms.openlocfilehash: fcea240fe1dc0ce97a2800391320b04c39c84336
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51934101"
---
# <a name="exposure-score---threat-and-vulnerability-management"></a>曝光分数 - 危险和漏洞管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [威胁和漏洞管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

你的曝光分数显示在威胁和漏洞管理[仪表板](tvm-dashboard-insights.md)中Microsoft Defender 安全中心。 它反映了你的组织对网络安全威胁的易受攻击程度。 低曝光分数意味着你的设备更容易被利用。

- 快速了解和识别有关组织中安全状态的高层次要点。
- 检测和响应需要调查或操作以改进当前状态的区域。
- 与对等方和管理人员就安全工作的影响进行沟通。

卡片可让你高级查看一段时间的曝光分数趋势。 图表中的任何峰值都直观地指示高网络安全威胁暴露，你可以进一步调查。

![曝光分数卡](images/tvm_exp_score.png)

## <a name="how-it-works"></a>运作方式

曝光分数分为以下级别：

- 0–29：低曝光分数
- 30–69：中等曝光分数
- 70–100：高曝光分数

你可以根据优先的安全建议修正问题 [，](tvm-security-recommendation.md) 以减少曝光评分。 每个软件都有一些缺陷，这些缺陷会转换为建议，并基于组织的风险确定优先级。

## <a name="reduce-your-threat-and-vulnerability-exposure"></a>减少威胁和漏洞暴露

通过修正安全建议降低威胁 [和漏洞暴露](tvm-security-recommendation.md)。 通过修正最高安全建议（可在仪表板中查看）来对曝光[危险和漏洞管理最大影响](tvm-dashboard-insights.md)。

## <a name="related-topics"></a>相关主题

- [威胁和漏洞管理概述](next-gen-threat-and-vuln-mgt.md)
- [设备的 Microsoft 安全功能分数](tvm-microsoft-secure-score-devices.md)
- [安全性建议](tvm-security-recommendation.md)
- [活动日程表](threat-and-vuln-mgt-event-timeline.md)
