---
title: Microsoft Defender for Endpoint in Microsoft 365 Defender
description: 了解从 Microsoft Defender 安全中心 到 Microsoft 365 Defender 的更改
keywords: 开始使用 Microsoft 365 Defender， Microsoft Defender for Office 365， Microsoft Defender for Endpoint， MDO， MDE， 安全门户， Defender 安全门户
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
localization_priority: Normal
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.openlocfilehash: b43b7c99c6585e8610d34f3c4e5b372fb1c829a2
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842622"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft Defender for Endpoint in Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**适用于：**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>快速参考

图像和下表列出了 Defender 和 Microsoft Defender 安全中心 Microsoft 365 之间的导航更改。

> [!div class="mx-imgBorder"]
> ![移动到位置的图像](../../media/mde-m3d-security-center.png)

| Microsoft Defender 安全中心 | Microsoft 365 Defender |
|---------|---------|
| 仪表板 <ul><li>安全操作</li><li>威胁分析</li></ul>  |主页 <ul><li>威胁分析</li></ul>   |
| 事件 | 事件&警报 |
| 设备清单 | 设备清单 |
| 警报队列 | 事件&警报 |
| 自动调查 | 操作中心 |
| 高级搜寻 | 搜寻 |
| 报表 | 报表 |
| 合作伙伴& API | 合作伙伴& API |
| 威胁&漏洞管理 | 漏洞管理 |
| 评估和教程 | 评估&教程 |
| 配置管理 | 配置管理 |
| 设置 | 设置 | 

改进的[Microsoft 365 Defender](overview-security-center.md)结合了保护、检测、调查和响应电子邮件、协作、 [https://security.microsoft.com](https://security.microsoft.com) 标识和设备威胁的管理功能。 这汇集了现有 Microsoft 安全门户中的功能，包括 Microsoft Defender 安全中心 和 Office 365 安全&中心。

如果你熟悉本文Microsoft Defender 安全中心，本文可帮助描述 Microsoft 365 Defender 中的一些更改和改进。 但是，要注意一些新的和更新的元素。

过去[，Microsoft Defender 安全中心](/windows/security/threat-protection/microsoft-defender-atp/portal-overview)一直是 Microsoft Defender for Endpoint 的主页。 Enterprise安全团队已使用它监视和帮助响应潜在高级永久性威胁活动或数据泄露的警报。 为了帮助减少门户数量，Microsoft 365 Defender 将成为监视和管理 Microsoft 标识、数据、设备、应用和基础结构的安全性的主页。

Microsoft 365 Defender 中的 Microsoft Defender for Endpoint 支持向托管安全服务提供商[ (MSSP) ](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access)授予访问权限，方式与在 Microsoft Defender 安全中心授予访问权限[的方式相同](mssp-access.md)。

> [!IMPORTANT]
> 在 Defender 中Microsoft 365取决于你的当前订阅。 例如，如果你没有 Microsoft Defender for Office 365 许可证，将不会显示"电子邮件&协作"部分。

> [!Note]
> Microsoft 365Defender 不可用于：
>- 美国政府社区云 (GCC) 
>- 美国政府社区云高 (GCC高) 
>- 美国国防部
>- 所有拥有商业许可证的美国政府机构

请看一下Microsoft 365 [https://security.microsoft.com](https://security.microsoft.com) Defender：。

了解有关优势的更多信息[：Microsoft 365 Defender 概述](overview-security-center.md)

## <a name="whats-changed"></a>更改内容

此表快速引用了 Microsoft Defender 安全中心 和 Microsoft 365 Defender 之间的更改。

### <a name="alerts-and-actions"></a>警报和操作

| 领域 | 更改说明 |
|---------|---------|
| [事件&警报](incidents-overview.md)  | 在 Microsoft 365 Defender 中，你可以跨所有终结点、电子邮件和标识管理事件和警报。 我们已将体验融合在一起，帮助你更轻松地查找相关事件。 有关详细信息，请参阅 [事件概述](incidents-overview.md)。   |
| [搜寻](advanced-hunting-overview.md)  |  修改在 Microsoft Defender for Endpoint 中创建的自定义检测规则，以包含标识和电子邮件表会自动将它们Microsoft 365 Defender。 其相应的警报也会显示在 Microsoft 365 Defender 中。 有关这些更改的更多详细信息，请阅读迁移 [自定义检测规则](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules)。 <br><br>高级 `DeviceAlertEvents` 搜寻的表在 Microsoft 365 Defender 中不可用。 若要在 Microsoft 365 Defender 中查询特定于设备的警报信息，可以使用 和 表来容纳来自各种源 `AlertInfo` `AlertEvidence` 集的更多信息。 通过以下不含 [DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents)的 Write 查询制作下一个与设备相关的查询。|
|[操作中心](m365d-action-center.md)    | 列出在自动调查和修正操作之后采取的挂起和已完成的操作。 以前，"操作中心"Microsoft Defender 安全中心列出仅对设备上采取的修正操作挂起和已完成的操作，而自动调查列出了警报和状态。 在改进的 Microsoft 365 Defender 中，操作中心跨电子邮件、设备和用户将修正操作和调查汇集在一起，所有这些操作都位于一个位置。  |
| [威胁分析](threat-analytics.md) |  移动到导航栏顶部，以便更轻松地发现和使用。 现在包括终结点以及电子邮件和协作的威胁信息。    |

### <a name="endpoints"></a>终结点

| 领域 | 更改说明 |
|---------|---------|
|搜索   |  Microsoft Defender for Endpoint 搜索栏不是位于标题中，而是在"终结点"部分下移动。 你可以继续搜索设备、文件、用户、URL、IP、漏洞、软件和建议。  |
|[仪表板](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  这是安全操作仪表板。 请参阅触发的活动警报数、处于风险中的设备、处于风险中的用户以及警报、设备和用户的严重性级别。 还可以查看任何设备是否具有传感器问题、整体服务运行状况，以及如何检测到任何未解决的警报。 |
|设备清单 | 无更改。 |
|[漏洞管理](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    已缩短名称以适合导航窗格。 它与"页面"部分危险和漏洞管理相同，所有页面位于下方。     |
| 合作伙伴和 API | 无更改。 |
| 评估&教程    |     新的测试和学习功能。     |
| 配置管理   |  无更改。  |

> [!NOTE]
> **自动调查和修正** 现在是事件的一部分。 You can see Automated investigation and remediation events in the **Incident > Investigation** tab.

> [!TIP]
> 设备搜索从 Endpoints > Search 完成。

### <a name="access-and-reporting"></a>访问和报告

| 领域 | 更改说明 |
|---------|---------|
| 报表  | 请参阅终结点和电子邮件报告&协作，包括威胁防护、设备运行状况和合规性以及易受攻击的设备。 |
| 健康  |  当前链接到管理中心 中的"服务运行状况["Microsoft 365页面](https://admin.microsoft.com/)。 |
| 设置 |  管理 Defender、Microsoft 365、电子邮件&协作、标识和设备发现的设置。   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365安全导航和功能

左侧导航栏或快速启动栏将看起来熟悉。 但是，这个安全中心中有些新增和更新的元素。

### <a name="incidents-and-alerts"></a>事件和警报

将跨电子邮件、设备和标识的事件和警报管理结合起来。 警报页面通过组合攻击信号来构造详细的情景，为警报提供完整的上下文。 全新的统一体验现在汇集了跨工作负荷的一致警报视图。 您可以快速分案、调查，以及采取有效措施。

- [详细了解事件](incidents-overview.md)
- [深入了解如何管理警报](investigate-alerts.md)

![通知和操作快速启动栏](../../media/converge-1-alerts-and-actions.png)

### <a name="hunting"></a>搜寻

通过使用 [高级搜索查询来在终结点、Office 365 邮箱等位置主动搜索威胁、恶意软件和恶意](advanced-hunting-overview.md)。 这些强大的查询可用于查找和查看威胁指示器和实体，了解已知威胁和潜在威胁。

[自定义检测](custom-detection-rules.md) 规则可以从高级搜寻查询构建，以帮助你主动监视可能表示泄露活动和错误配置设备的事件。


### <a name="action-center"></a>操作中心

操作中心显示自动调查和响应功能创建调查。 Microsoft 365 Defender 中的自动自恢复功能可自动响应特定事件，帮助团队实现安全。

[详细了解操作中心](m365d-action-center.md)。

### <a name="threat-analytics"></a>威胁分析

从 Microsoft 安全研究人员获取威胁智能。 威胁分析可帮助安全团队在面对新兴威胁时更有效率。 威胁分析包括：

- Microsoft Defender for Office 365 的与电子邮件相关的检测和缓解措施。 除了从 Microsoft Defender for Endpoint 中可用的终结点数据外，还有一个终结点数据。
- 与威胁相关的事件视图。
- 增强的体验，可快速识别和使用报告中的可操作信息。

你可以从 Microsoft 365 Defender 中的左上角导航栏，或者从显示组织的主要威胁的专用仪表板卡访问威胁分析。

详细了解如何使用威胁 [分析跟踪和响应新出现的威胁](./threat-analytics.md)。

### <a name="endpoints-section"></a>终结点部分

查看和管理组织中终结点的安全性。 如果你已使用Microsoft Defender 安全中心，它看起来会很熟悉。

![终结点快速启动栏](../../media/converge-2-endpoints.png)

### <a name="access-and-reports"></a>访问和报告

查看报表、更改设置和修改用户角色。

!["访问和报告快速启动"栏](../../media/converge-4-access-and-reporting-new.png)

### <a name="siem-api-connections"></a>SIEM API 连接

如果你使用 [适用于终结点 SIEM API 的 Defender，](../defender-endpoint/enable-siem-integration.md)你可以继续这样做。 我们已在 API 负载上添加了指向安全门户中的警报页面或事件Microsoft 365链接。 新的 API 字段包括 LinkToMTP 和 IncidentLinkToMTP。 有关详细信息，请参阅将帐户从[Microsoft Defender for Endpoint 重定向到 Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md)。

### <a name="email-alerts"></a>电子邮件警报

你可以继续使用 Defender for Endpoint 的电子邮件警报。 我们已在电子邮件中添加指向 defender 中的警报页面或事件页面Microsoft 365链接。 有关详细信息，请参阅将帐户从[Microsoft Defender for Endpoint 重定向到 Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md)。

### <a name="managed-security-service-providers-mssp"></a>MSSP (托管安全服务) 

统一门户当前不支持在同一浏览会话中同时登录到多个租户。 可以通过还原到以前的 Microsoft Defender for [Endpoint](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal)门户来选择退出自动重定向，以维护此功能，直到问题得到解决为止。

## <a name="related-information"></a>相关信息

- [Microsoft 365 Defender](overview-security-center.md)
- [Microsoft Defender for Endpoint in Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [将帐户从 Microsoft Defender for Endpoint 重定向到 Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
