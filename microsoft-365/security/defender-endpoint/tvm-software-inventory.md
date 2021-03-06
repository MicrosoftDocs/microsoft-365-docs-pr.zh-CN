---
title: 软件清单危险和漏洞管理
description: 适用于终结点的 Microsoft Defender 软件清单页危险和漏洞管理软件中检测到的漏洞和漏洞数量。
keywords: 危险和漏洞管理， Microsoft Defender for Endpoint， Microsoft Defender for Endpoint 软件清单， Microsoft Defender for Endpoint threat & 漏洞管理， Microsoft Defender for Endpoint threat & 漏洞管理 software inventory， Microsoft Defender for Endpoint tvm software inventory， tvm software inventory
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
ms.openlocfilehash: 0d270760cfed965c8190668afcdb1cc25223d2b1
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933717"
---
# <a name="software-inventory---threat-and-vulnerability-management"></a>软件清单 - 危险和漏洞管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [威胁和漏洞管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

危险和漏洞管理软件清单是组织中具有正式通用平台枚举的已知软件列表 ([CPE) 。 ](https://nvd.nist.gov/products/cpe) 没有正式 CPE 的软件产品没有发布漏洞。 它还包括供应商名称、漏洞数量、威胁和公开设备数量等详细信息。

## <a name="how-it-works"></a>运作方式

在发现领域，我们正在利用在 Microsoft Defender 中负责检测和漏洞评估的同一组信号，用于终结点检测和 [响应功能](overview-endpoint-detection-response.md)。

由于它是实时的，因此在几分钟内，您将在发现漏洞信息时看到它们。 该引擎自动从多个安全源获取信息。 事实上，你将看到特定软件是否连接到实时威胁活动。 它还提供指向威胁分析报告的链接（一旦可用）。

## <a name="navigate-to-the-software-inventory-page"></a>导航到"软件清单"页

通过在页面的导航 **菜单中从**"危险和漏洞管理"菜单中选择"软件清单"，访问"软件 [Microsoft Defender 安全中心"。](portal-overview.md)

在"设备"列表的"单个设备"页面中查看 [特定设备上的软件](machines-view-overview.md)。

>[!NOTE]
>如果使用 Microsoft Defender for Endpoint 全局搜索搜索软件，请确保使用下划线字符而不是空格。 例如，为了获得最佳搜索结果，您可以编写"windows_10"，而不是"Windows 10"。

## <a name="software-inventory-overview"></a>软件清单概述

" **软件清单** "页将打开，其中列出了网络中安装的软件，包括供应商名称、发现的缺点、与其关联的威胁、公开的设备、曝光评分的影响和标签。

你可以根据软件中发现的缺点、与其关联的威胁以及软件是否已达到支持终止等标记来筛选列表视图。

![软件清单的登陆页面示例。](images/tvm-software-inventory.png)

选择要调查的软件。 在打开一个飞出面板时，页面上的信息视图会更紧凑。 你可以深入调查并选择"打开软件页"，或者通过选择"报告不准确"来标记 **任何技术不一致情况**。

### <a name="software-that-isnt-supported"></a>不支持的软件

"软件清单"页中& 漏洞管理当前不受威胁威胁支持的软件。 由于它不受支持，因此只有有限的数据可用。 使用"漏洞"部分中的"不可用"选项按不受支持的软件进行筛选。

![不支持的软件筛选器。](images/tvm-unsupported-software-filter.png)

下面指示软件不受支持：

- "漏洞"字段显示"不可用"
- "公开的设备"字段显示短划线
- 在侧面板和软件页中添加的信息性文本
- 软件页面将没有安全建议、发现的漏洞或事件时间线部分

目前，没有 CPE 的产品不会显示在软件清单页中，而只显示在设备级别的软件清单中。

## <a name="software-inventory-on-devices"></a>设备上的软件清单

从Microsoft Defender 安全中心导航面板中，转到 **["设备"列表](machines-view-overview.md)**。 选择设备名称以打开设备页面 (如 Computer1) ，然后选择"软件清单"选项卡以查看设备上存在的所有已知软件的列表。 选择特定软件项以打开包含详细信息的飞出区。

软件可能在设备级别可见，即使软件当前不受设备危险和漏洞管理。 但是，只有有限的数据可用。 你将知道软件是否不受支持，因为它将在"漏洞"列中显示"不可用"。

没有 CPE 的软件也可以显示在此设备特定的软件清单下。

### <a name="software-evidence"></a>软件证据

查看我们在设备上从注册表和/或磁盘检测到特定软件的证据。可以在设备软件清单的任何设备上找到它。

选择一个软件名称以打开该飞出页面，并查找名为"软件证据"的部分。

![软件证据示例Windows 10列表，显示软件证据注册表路径。](images/tvm-software-evidence.png)

## <a name="software-pages"></a>软件页

可以通过几种不同的方式查看软件页面：

- "软件清单">在>"选择 **打开** 软件"页中选择软件名称
- ["安全建议">](tvm-security-recommendation.md) 在>选择 **"打开** 软件"页中的"选择建议"
- [事件时间线页面](threat-and-vuln-mgt-event-timeline.md)> 选择事件>在 ("相关组件"部分选择超链接软件名称 (如 Visual Studio 2017) 

 将显示一个完整的页面，其中包含特定软件的所有详细信息和以下信息：

- 包含供应商信息的侧面板、组织中软件的普遍程度 (包括其安装的设备数量，以及未修补) 的公开设备、是否可用和攻击，以及你的曝光评分。
- 显示漏洞和错误配置的数量和严重性的数据可视化。 此外，使用公开的设备数的图形。
- 显示以下信息的选项卡：
    - 针对所识别的漏洞的相应安全建议。
    - 发现的漏洞的命名 CVEs。
    - 安装了软件的设备 (设备名称、域、操作系统等) 。
    - 软件版本列表 (包括安装版本的设备数、发现的漏洞数以及安装的设备名称) 。

    ![2017 Visual Studio软件详细信息、漏洞、公开设备等的 2017 软件示例页面。](images/tvm-software-page-example.png)

## <a name="report-inaccuracy"></a>报告 inaccuracy

当你看到任何模糊、不准确或不完整的信息时报告误报。 还可以报告已修正的安全建议。

1. 在"软件清单"页上打开软件飞出。
2. 选择 **报告 inaccuracy**。
3. 从弹出窗格中，从下拉菜单中选择不准确类别，填写您的电子邮件地址和有关不准确的详细信息。
4. 选择“**提交**”。 你的反馈将立即发送给危险和漏洞管理专家。

## <a name="related-articles"></a>相关文章

- [威胁和漏洞管理概述](next-gen-threat-and-vuln-mgt.md)
- [安全性建议](tvm-security-recommendation.md)
- [活动日程表](threat-and-vuln-mgt-event-timeline.md)
- [查看和组织适用于终结点设备的 Microsoft Defender 列表](machines-view-overview.md)
