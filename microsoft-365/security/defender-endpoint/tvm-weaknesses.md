---
title: 我的组织中漏洞 - 危险和漏洞管理
description: 列出 CVE 的常见 () 在组织中运行的软件中发现漏洞的 ID。 由 Microsoft Defender for Endpoint 危险和漏洞管理发现。
keywords: Microsoft Defender for Endpoint threat & 漏洞管理， 危险和漏洞管理， Microsoft Defender for Endpoint tvm vulnerabilites page， finding vulnerabilites through tvm， tvm vulnerability list， vulnerability details in tvm
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
ms.openlocfilehash: a8039a06dc58c31158f90d39857ffbeba92138d5
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933069"
---
# <a name="vulnerabilities-in-my-organization---threat-and-vulnerability-management"></a>我的组织中漏洞 - 危险和漏洞管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [威胁和漏洞管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

威胁和漏洞管理使用 Defender for Endpoint 终结点保护中的相同信号扫描和检测漏洞。

" **漏洞** "页通过列出 CVE 中"常见漏洞和曝光" (CVE) 漏洞。 还可以查看严重性、常见漏洞评分系统 (CVSS) 分级、组织中的普遍程度、相应的漏洞、威胁见解等。

>[!NOTE]
>如果没有为漏洞分配正式的 CVE-ID，则此漏洞名称由 危险和漏洞管理。

>[!TIP]
>若要获取有关新漏洞事件的电子邮件，请参阅在 Microsoft [Defender for Endpoint](configure-vulnerability-email-notifications.md)中配置漏洞电子邮件通知

## <a name="navigate-to-the-weaknesses-page"></a>导航到"漏洞"页面

以几种不同方式访问"漏洞"页面：

- 从 **导航菜单中** 的危险和漏洞管理选择"漏洞 ["Microsoft Defender 安全中心](portal-overview.md)
- 全局搜索

### <a name="navigation-menu"></a>导航菜单

转到"危险和漏洞管理菜单并选择 **"漏洞**"以打开 CVEs 列表。

### <a name="vulnerabilities-in-global-search"></a>全局搜索中的漏洞

1. 转到全局搜索下拉菜单。
2. 选择 **要查找** 的常见漏洞和 (CVE) ID 中的漏洞和密钥，然后选择搜索图标。 " **漏洞"** 页面将打开，并包含要查找的 CVE 信息。
![已选择下拉列表选项"漏洞"的全局搜索框和示例 CVE。](images/tvm-vuln-globalsearch.png)
3. 选择 CVE 打开包含详细信息的飞出面板，包括漏洞描述、详细信息、威胁见解和公开的设备。

若要在"漏洞"页中查看其余的漏洞，请键入 CVE，然后选择"搜索"。

## <a name="weaknesses-overview"></a>漏洞概述

修正公开的设备中的漏洞，以降低对资产和组织的风险。 如果 **"公开的设备"** 列显示"0"，则意味着你没有风险。

![登录页面存在缺陷。](images/tvm-weaknesses-overview.png)

### <a name="breach-and-threat-insights"></a>泄露和威胁见解

当图标为红色时，在"威胁"列中查看任何相关的泄露和威胁见解。

 >[!NOTE]
 > 始终对与持续威胁相关的建议设置优先级。 这些建议使用威胁见解图标"简单 ![ 绘制红色 Bug"进行标记。](images/tvm_bug_icon.png) 和泄露见解图标 ![ 简单绘制一个指向目标的箭头 ](images/tvm_alert_icon.png) 。  

如果在组织中发现漏洞，则突出显示"泄露见解"图标。
![将鼠标悬停在图标上时可能会显示泄露见解文本的示例。 其中显示"可能的活动警报与此建议关联。"](images/tvm-breach-insights.png)

如果在组织中发现漏洞存在关联攻击，则突出显示威胁见解图标。 将鼠标悬停在图标上可显示威胁是攻击工具包的一部分，还是连接到特定高级永久市场活动或活动组。 如果可用，有一个指向威胁分析报告的链接，该报告包含零日攻击新闻、披露或相关安全公告。  

![将鼠标悬停在图标上时可能显示的威胁见解文本。 此文本具有多个项目符号点和链接文本。](images/tvm-threat-insights.png)

### <a name="gain-vulnerability-insights"></a>获取漏洞见解

如果选择 CVE，将打开一个飞出面板，该面板将包含详细信息，例如漏洞描述、详细信息、威胁见解和公开的设备。

- 相关方案中显示了"OS 功能"类别
- 你可以转到针对每个已公开设备的 CVE 的相关安全建议

 ![漏洞飞出示例。](images/tvm-weakness-flyout400.png)

### <a name="software-that-isnt-supported"></a>不支持的软件

当前不受威胁威胁支持的软件的 & 漏洞管理"漏洞"页中仍然存在。 由于软件不受支持，因此只有有限的数据可用。

使用不受支持的软件的 CES 不会提供公开的设备信息。 通过选择"公开设备"部分中的"不可用"选项，按不受支持的软件进行筛选。

 ![公开的设备筛选器。](images/tvm-exposed-devices-filter.png)

## <a name="view-common-vulnerabilities-and-exposures-cve-entries-in-other-places"></a>查看其他位置的 CVE (项) 漏洞和曝光

### <a name="top-vulnerable-software-in-the-dashboard"></a>仪表板中最易受攻击的软件

1. Go to the [危险和漏洞管理 dashboard](tvm-dashboard-insights.md) and scroll down to the Top **vulnerable software** widget. 你将看到每个软件中发现漏洞的数量，以及威胁信息和设备曝光的一段时间的高级别视图。

    ![具有四列的主要易受攻击的软件卡：软件、漏洞、威胁、公开的设备。](images/tvm-top-vulnerable-software500.png)

2. 选择要调查的软件以转到向下钻取页面。
3. 选择" **发现的漏洞"** 选项卡。
4. 选择要调查的漏洞，了解有关漏洞详细信息的详细信息

    ![WindowsServer 2019 向下钻取概述。](images/windows-server-drilldown.png)

### <a name="discover-vulnerabilities-in-the-device-page"></a>发现设备页面中的漏洞

在设备页面中查看相关漏洞信息。

1. 转到导航Microsoft Defender 安全中心栏，然后选择设备图标。 将 **打开"设备"** 列表页。
2. 在 **"设备"列表** 页中，选择要调查的设备名称。

    ![包含要调查的选定设备的设备列表。](images/tvm_machinetoinvestigate.png)

3. 设备页面将打开，并包含要调查的设备的详细信息和响应选项。
4. 选择 **"发现的漏洞"。**

    ![包含详细信息和响应选项的设备页面。](images/tvm-discovered-vulnerabilities.png)

5. 选择要调查的漏洞，以打开包含 CVE 详细信息的飞出面板，例如：漏洞描述、威胁见解和检测逻辑。

#### <a name="cve-detection-logic"></a>CVE 检测逻辑

与软件证据类似，我们现在显示了在设备上应用的检测逻辑，以表明该设备易受攻击。 新部分称为"检测逻辑" (发现的设备页中发现的任何漏洞) 显示检测逻辑和来源。

相关方案中也显示了"OS 功能"类别。 只有在启用了特定操作系统组件时，CVE 才会影响运行易受攻击的操作系统的设备。 假设 Windows Server 2019 在其 DNS 组件中具有漏洞。 借助此新功能，我们将仅将此 CVE 附加到 Windows Server 2019 设备，这些设备的 OS 中启用了 DNS 功能。

![检测逻辑示例，列出在设备和 KB 上检测到的软件。](images/tvm-cve-detection-logic.png)

## <a name="report-inaccuracy"></a>报告 inaccuracy

当你看到任何模糊、不准确或不完整的信息时报告误报。 还可以报告已修正的安全建议。

1. 打开"漏洞"页上的 CVE。
2. 选择 **"报告不准确"，** 将打开一个飞出窗格。
3. 从下拉菜单中选择不准确类别，并填写您的电子邮件地址和不准确的详细信息。
4. 选择“**提交**”。 你的反馈将立即发送给危险和漏洞管理专家。

## <a name="related-articles"></a>相关文章

- [威胁和漏洞管理概述](next-gen-threat-and-vuln-mgt.md)
- [安全性建议](tvm-security-recommendation.md)
- [软件库存](tvm-software-inventory.md)
- [仪表板见解](tvm-dashboard-insights.md)
- [查看和组织适用于终结点设备的 Microsoft Defender 列表](machines-view-overview.md)
