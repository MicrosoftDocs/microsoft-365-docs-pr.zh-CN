---
title: Microsoft Defender for Endpoint 服务疑难解答
description: 查找已知问题（如尝试访问服务时的服务器错误）的解决方案和解决方法。
keywords: Microsoft Defender for Endpoint 疑难解答， 服务器错误， 访问被拒绝， 凭据无效， 无数据， 仪表板门户， 允许， 事件查看器
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
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 8aaea65c617300a16f99a9a3e3a62d94b7983198
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "52538347"
---
# <a name="troubleshoot-service-issues"></a>服务疑难解答

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


本部分解决使用 Microsoft Defender for Endpoint 服务时可能出现的问题。

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>服务器错误 - 由于凭据无效，访问被拒绝
如果在尝试访问服务时遇到服务器错误，则需要更改浏览器 Cookie 设置。
配置浏览器以允许 Cookie。

## <a name="elements-or-data-missing-on-the-portal"></a>门户上缺少的元素或数据
如果客户端上缺少某些元素或Microsoft Defender 安全中心代理设置可能会阻止它。

确保包括 `*.securitycenter.windows.com` 代理允许列表。


> [!NOTE]
> 添加以下终结点时，必须使用 HTTPS 协议。

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Microsoft Defender for Endpoint 服务在事件查看器中显示事件或错误日志

有关 Microsoft Defender [for](event-error-codes.md) Endpoint 服务报告的事件 ID 列表，请参阅使用事件查看器查看事件和错误。 本文还包含事件错误的疑难解答步骤。

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Microsoft Defender for Endpoint 服务在重启后无法启动，并且显示错误 577

如果载入设备成功完成，但 Microsoft Defender for Endpoint 在重启后未启动，并且显示错误 577，请检查Windows Defender策略是否禁用了该设置。

有关详细信息，请参阅[确保策略Microsoft Defender 防病毒禁用策略](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)。

## <a name="known-issues-with-regional-formats"></a>区域格式的已知问题

**日期和时间格式**<br>
时间和日期格式存在一些已知问题。 

支持以下日期格式：
- MM/dd/yyyy
- dd/MM/yyyy

目前不支持以下日期和时间格式：
- 日期格式 yyyy/MM/dd
- 日期格式 dd/MM/yy
- yy 的日期格式。 将只显示 yyyy。
- 时间格式 HH：mm：ss 不受支持， (12 小时 AM/PM 格式不受支持) 。 仅支持 24 小时制格式。

**使用逗号指示千位**<br>
不支持将逗号用作数字中的分隔符。 用逗号分隔数字以指示千位的区域将只看到使用点作为分隔符。 例如，15，5K 显示为 15.5K。

>想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Microsoft Defender for Endpoint 租户在欧洲自动创建
使用 Azure Defender 监视服务器时，会自动创建适用于终结点的 Microsoft Defender 租户。 默认情况下，Microsoft Defender for Endpoint 数据存储在欧洲。





## <a name="related-topics"></a>相关主题
- [Microsoft Defender 终结点载入问题疑难解答](troubleshoot-onboarding.md)
- [使用事件查看器查看事件和错误](event-error-codes.md)
