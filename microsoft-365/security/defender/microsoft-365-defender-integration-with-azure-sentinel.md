---
title: Microsoft 365 Defender 与 Azure Sentinel 的集成
description: 使用 Azure Sentinel 作为 SIEM，Microsoft 365 Defender事件和事件。
keywords: 事件， 警报， 调查， 分析， 响应， 关联， 攻击， 计算机， 设备， 用户， 标识， 标识， 邮箱， 电子邮件， 365， microsoft， m365
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
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: adb65c82713464da2df4d473d2fd7a055e0dbeb3
ms.sourcegitcommit: 4046c2c390851dffcdb430e1ba38c4df23fe2e69
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2021
ms.locfileid: "53415572"
---
# <a name="microsoft-365-defender-integration-with-azure-sentinel"></a>Microsoft 365 Defender 与 Azure Sentinel 的集成

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**适用于：**
- Microsoft 365 Defender

Azure Sentinel Microsoft 365 Defender 预览版 (连接器) 所有 Microsoft 365 Defender 事件和警报信息发送到 Azure Sentinel，并保持事件同步。 

添加连接器后，Microsoft 365 Defender 事件（包括从 Microsoft Defender for Endpoint、Microsoft Defender for Identity、Microsoft Defender for Office 365 和 Microsoft Cloud App Security 接收的所有关联警报、实体和相关信息）会作为安全信息和事件管理 (SIEM) 数据流式传输至 &mdash; Azure Sentinel，从而为您提供使用 Azure Sentinel 执行会审和事件响应的上下文。 &mdash; 

进入 Azure Sentinel 后，事件将与 Microsoft 365 Defender 保持双向同步，从而可以利用 azure 门户中的 Microsoft 365 Defender 门户和 Azure Sentinel 的优势，以便进行事件调查和响应。

观看此简短概述 Azure Sentinel 与 Microsoft 365 Defender (集成，) 。

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


下面是它的工作原理。

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="事件数据在 Microsoft 365 Defender 和 Azure Sentinel 之间的流和共享":::

## <a name="next-steps"></a>后续步骤

1. 深入了解与 Azure [Microsoft 365 Defender集成](/azure/sentinel/microsoft-365-defender-sentinel-integration)。
2. [连接数据从 Microsoft 365 Defender Azure Sentinel](/azure/sentinel/connect-microsoft-365-defender)。

## <a name="see-also"></a>另请参阅

- [事件概述Microsoft 365 Defender](incidents-overview.md)
- [使用 Azure Sentinel 调查事件](/azure/sentinel/tutorial-investigate-cases)
