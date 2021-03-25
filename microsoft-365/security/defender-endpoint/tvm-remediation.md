---
title: 通过威胁和漏洞管理修正漏洞
description: 修正通过安全建议发现的安全漏洞，并根据需要在威胁和漏洞管理中创建例外。
keywords: microsoft defender atp tvm remediation， mdatp tvm， threat and vulnerability management， threat & vulnerability management， threat & vulnerability management remediation， tvm remediation intune， tvm remediation sccm
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0a0f70d81c3060f14f917cac49851af2e9dae210
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056564"
---
# <a name="remediate-vulnerabilities-with-threat-and-vulnerability-management"></a>通过威胁和漏洞管理修正漏洞

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [威胁和漏洞管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="request-remediation"></a>请求修正

Microsoft Defender for Endpoint 中的威胁和漏洞管理功能通过修正请求工作流填补了安全和 IT 管理员之间的空白。 安全管理员（如你可以请求 IT 管理员将漏洞从安全建议页面修正到Intune）

### <a name="enable-microsoft-intune-connection"></a>启用 Microsoft Intune 连接

若要使用此功能，请启用 Microsoft Intune 连接。 在 Microsoft Defender 安全中心中，**导航到"** 设置""  >  **常规**  >  **高级功能"。** 向下滚动并查找 **Microsoft Intune 连接**。 默认情况下，切换处于关闭状态。 打开 **Microsoft Intune 连接****切换开关。**

**注意**：如果启用了 Intune 连接，则创建修正请求时可以选择创建 Intune 安全任务。 如果未设置连接，则不显示此选项。

有关详细信息 [，请参阅使用 Intune 修正由 Microsoft Defender for Endpoint](https://docs.microsoft.com/intune/atp-manage-vulnerabilities) 标识的漏洞。

### <a name="remediation-request-steps"></a>修正请求步骤

1. 转到 Microsoft Defender 安全中心中的"威胁和漏洞管理"导航菜单，然后选择"[**安全建议"。**](tvm-security-recommendation.md)

2. 选择要请求修正的安全建议，然后选择"修正 **选项"。**

3. 填写表单，包括请求修正内容、适用的设备组、优先级、截止日期和可选注释。
    1. 如果选择"注意必需"修正选项，则选择截止日期将不可用，因为没有任何特定操作。

4. 选择 **"提交请求"。** 提交修正请求将在威胁和漏洞管理内创建修正活动项，可用于监视此建议中的修正进度。 这不会触发修正或对设备应用任何更改。

5. 将新请求通知 IT 管理员，让他们登录到 Intune 以批准或拒绝请求并启动程序包部署。

6. 转到" [**修正"**](tvm-remediation.md) 页以查看修正请求的状态。

如果你想要检查票证在 Intune 中的显示方式，请参阅使用 [Intune](https://docs.microsoft.com/intune/atp-manage-vulnerabilities) 修正由 Microsoft Defender for Endpoint 标识的漏洞，了解详细信息。

>[!NOTE]
>如果你的请求涉及修正超过 10，000 台设备，我们只能发送 10，000 台设备以修正 Intune。

确定组织的网络安全弱点并将其映射到可操作的安全建议后，开始创建安全任务。 [](tvm-security-recommendation.md) 通过与 Microsoft Intune 集成（其中创建了修正票证）可以创建任务。

通过修正安全建议，降低组织对漏洞的暴露程度，并增加安全配置。

## <a name="view-your-remediation-activities"></a>查看修正活动

当你从"安全建议"页提交修正请求时，它会启动修正活动。 将创建一个可在威胁和漏洞管理修正页中跟踪的安全任务，并且将在 Microsoft Intune 中创建修正票证。

如果选择"注意需要"修正选项，则没有进度栏、票证状态或截止日期，因为我们可以监视任何实际操作。

进入"修正"页后，选择要查看的修正活动。 你可以按照修正步骤、跟踪进度、查看相关建议、导出到 CSV 或标记为完成。
![包含所选修正活动的"修正"页的示例，以及该活动的列出说明、IT 服务和设备管理工具以及设备修正进度的飞出图。](images/remediation_flyouteolsw.png)

>[!NOTE]
> 已完成的修正活动保留期为 180 天。 若要使"修正"页以最佳方式执行，修正活动将在完成后 6 个月后删除。

### <a name="completed-by-column"></a>按列完成

使用"修正"页上的"完成者"列跟踪哪些人关闭了修正活动。

- **电子邮件地址**：手动完成任务的人的电子邮件
- **系统确认**：在已修正 (自动完成任务) 
- **N/A：** 信息不可用，因为我们不知道此旧任务的完成情况

![由具有两行的列创建和完成。 "完成者"的一行包含电子邮件示例，另一行显示系统确认。](images/tvm-completed-by.png)

### <a name="top-remediation-activities-in-the-dashboard"></a>仪表板中的热门修正活动

查看 **威胁和** 漏洞 [管理仪表板中的热门修正活动](tvm-dashboard-insights.md)。 选择任意条目以转到"修正 **"** 页。 可以在 IT 管理员团队修正任务后将修正活动标记为已完成。

![Top 修正活动卡片的示例，该表列出了根据安全建议生成的顶部活动。](images/tvm-remediation-activities-card.png)

## <a name="related-articles"></a>相关文章

- [威胁和漏洞管理概述](next-gen-threat-and-vuln-mgt.md)
- [仪表板](tvm-dashboard-insights.md)
- [安全性建议](tvm-security-recommendation.md)