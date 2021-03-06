---
title: 调查事件Microsoft 365 Defender
description: 调查与设备、用户和邮箱相关的事件。
keywords: 事件， 事件， 分析， 响应， 计算机， 设备， 用户， 标识， 邮件， 电子邮件， 邮箱， 调查， 图形， 证据
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: fdfc065aea3549e99de72c968c0fa19412f9e246
ms.sourcegitcommit: ccbdf2638fc6646bfb89450169953f4c3ce4b9b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "53105352"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>调查事件Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**适用于：**

- Microsoft 365 Defender

Microsoft 365 Defender将来自设备、用户和邮箱的所有用户的相关警报、资产、调查和证据聚合到事件中，以便全面了解整个攻击范围。

在事件内，分析影响网络的警报，了解它们的含义，并整理证据，以便制定有效的修正计划。

## <a name="initial-investigation"></a>初始调查

在深入讨论详细信息之前，请看一下事件的属性和摘要。

你可以从选中标记列中选择事件开始。 下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="从选中标记列中选择事件的示例":::

当你这样做时，将打开一个摘要窗格，其中包含有关事件的关键信息，如严重性、分配到该事件的人以及事件的[MITRE ATT &trade; ](https://attack.mitre.org/)&CK 类别。 下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="事件的摘要窗格示例":::

从此处，可以选择"打开 **事件页面"。** 这将打开事件的主页，你将在此找到警报、设备、用户、调查和证据的更多摘要信息和选项卡。

您还可以通过从事件队列中选择事件名称来打开事件的主页。

## <a name="summary"></a>摘要

通过 **"摘要** "页面，您可以快速查看有关事件的顶部注意事项。

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="安全中心内事件的&quot;摘要&quot;Microsoft 365示例":::

攻击类别可直观和数字地了解攻击对击杀链的进度。 与其他 Microsoft 安全产品一样，Microsoft 365 Defender[与 MITRE &trade; ATT](https://attack.mitre.org/)&CK 框架一致。

“范围” 部分提供了属于此事件的最受影响的资产列表。 如果存在有关此资产的具体信息（例如风险级别、调查优先级以及资产上的任何标记），也将在本节中显示。

警报时间线可快速了解警报发生的时间顺序，以及这些警报链接到此事件的原因。

最后 ， 证据部分提供事件中包含的不同项目及其修正状态的摘要，以便你可以立即确定你是否需要任何操作。

本概述可通过深入了解应了解的事件主要特征，帮助对事件进行初始会审。

## <a name="alerts"></a>警报

在 **"警报** "选项卡上，您可以查看警报队列，了解与事件相关的警报及其其他信息，例如：

- 严重性。
- 警报中涉及的实体。
- Microsoft Defender for Identity、Microsoft Defender for Endpoint (Microsoft Defender for Office 365) 警报的来源。
- 链接在一起的原因。

下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="事件的警报页面示例":::

默认情况下，警报按时间顺序排序，以便查看事件如何随着时间的推移而播放。 在事件内选择警报时，Microsoft 365 Defender显示特定于整体事件上下文的警报信息。 

你可以查看警报的事件，其他触发的警报导致了当前警报，以及攻击中涉及的所有受影响的实体和活动，包括文件、用户和邮箱。

下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="事件内的警报详细信息页面示例":::

此事件警报页面包含以下部分：

- 警报情景，其中包括所发生事情的摘要
- 相关事件和警报
- 摘要详细信息

了解如何在调查警报中使用警报队列 [和警报页面](investigate-alerts.md)。

## <a name="devices"></a>设备

" **设备** "选项卡列出了与事件相关的所有设备。 下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="事件的设备页面示例":::

可以选择设备的选中标记以查看设备、目录数据、活动警报和登录用户的详细信息。 选择设备名称以查看 Microsoft Defender for Endpoints 设备清单中的设备详细信息。

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="适用于终结点的 Microsoft Defender 的设备页面示例":::

从设备页面，你可以收集有关设备的其他信息，例如其所有警报、时间线和安全建议。 例如，从"时间线"选项卡中，你可以滚动浏览计算机时间线，并按时间顺序查看计算机上观测到的所有事件和行为，与所发出警报的交错。

> [!TIP]
> 可以在设备页面上执行按需扫描。 In the Microsoft 365 security center， choose **Endpoints > Device inventory**. 选择具有警报的设备，然后运行防病毒扫描。 防病毒扫描等操作会进行跟踪，并且显示在"设备清单 **"页上。** 若要了解更多信息，请参阅在[Microsoft Defender 防病毒运行扫描](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices)。

## <a name="users"></a>用户

" **用户** "选项卡列出了标识为事件的一部分或与事件相关的所有用户。 下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="事件的用户页面示例":::

可以选择用户的选中标记以查看用户帐户威胁、曝光和联系人信息的详细信息。 选择用户名以查看其他用户帐户详细信息。

了解如何查看其他用户信息，以及如何在调查用户中管理 [事件的用户](investigate-users.md)。


## <a name="mailboxes"></a>邮箱

" **邮箱** "选项卡列出了标识为事件的一部分或与事件相关的所有邮箱。 下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="事件的&quot;邮箱&quot;页面示例":::

您可以选择邮箱的选中标记以查看活动警报列表。 选择邮箱名称以查看 Microsoft Defender for Office 365 资源管理器页面上的其他邮箱Office 365。

## <a name="investigations"></a>调查

"**调查**"选项卡列出了此事件中的 [](m365d-autoir.md)警报触发的所有自动调查。 调查将执行修正操作或等待分析员批准操作，具体取决于如何将自动调查配置为在 Microsoft Defender for Endpoint 和 Defender for Office 365 中运行。

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="事件的调查页面示例":::

选择调查以导航到其详细信息页，了解有关调查和修正状态的完整信息。 如果有作为调查的一部分等待审批的任何操作，它们将显示在"挂起的操作 **历史记录"** 选项卡中。采取操作作为事件修正的一部分。

还有一个 **"调查图形"** 选项卡，显示：

- 警报与组织中受影响资产的连接。
- 哪些实体与哪些警报相关，以及它们如何成为攻击的一部分。
- 事件的警报。

调查图通过将属于攻击的不同可疑实体连接到其相关资产（如用户、设备和邮箱）来帮助您快速了解攻击的完整范围。 

有关详细信息，请参阅自动[调查和响应Microsoft 365 Defender。](m365d-autoir.md)

## <a name="evidence-and-response"></a>证据和响应

" **证据和响应** "选项卡显示事件警报中所有受支持的事件和可疑实体。 下面是一个示例。

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="事件的证据和响应页面示例":::

Microsoft 365 Defender自动调查警报中所有事件支持的事件和可疑实体，并提供有关重要电子邮件、文件、进程、服务、IP 地址等的信息。 这可以帮助您快速检测和阻止事件中的潜在威胁。

每个被分析的实体都标记为"恶意 (可疑、) 清理"和修正状态。 这可以帮助您了解整个事件的修正状态以及可以采取哪些下一步操作。

## <a name="next-steps"></a>后续步骤

根据需要：

- [调查事件警报](investigate-alerts.md)
- [调查事件的用户](investigate-users.md)

## <a name="see-also"></a>另请参阅

- [事件概述](incidents-overview.md)
- [确定事件优先级](incident-queue.md)
- [管理事件](manage-incidents.md)

