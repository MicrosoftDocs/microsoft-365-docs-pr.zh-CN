---
title: 将 Microsoft Defender for Endpoint 与其他 Microsoft 解决方案集成
description: 了解 Microsoft Defender for Endpoint 如何与其他 Microsoft 解决方案集成，包括 Microsoft Defender for Identity 和 Azure 安全中心。
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender， 条件访问， office， 高级威胁防护， microsoft defender for identity， microsoft defender for office， azure 安全中心， Microsoft 云应用安全， azure sentinel
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 287ad9adeccd527b756bdd5304d3c89fc1b2d789
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056506"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender for Endpoint 和其他 Microsoft 解决方案

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>与其他 Microsoft 解决方案集成

Microsoft Defender for Endpoint 直接与各种 Microsoft 解决方案集成。

### <a name="azure-security-center"></a>Azure 安全中心
Microsoft Defender for Endpoint 提供了全面的服务器保护解决方案，包括终结点检测和响应 (Windows Server 上的 EDR) 功能。

### <a name="azure-sentinel"></a>Azure Sentinel
Microsoft Defender for Endpoint 连接器允许你将来自 Microsoft Defender for Endpoint 的警报流式传输至 Azure Sentinel。 这将使您能够更全面分析整个组织的安全事件，并生成有效且即时响应的手册。

### <a name="azure-information-protection"></a>Azure 信息保护
确保敏感数据安全，同时通过数据发现和数据保护在工作场所中提高工作效率。

### <a name="conditional-access"></a>条件访问
Microsoft Defender for Endpoint 的动态设备风险评分已集成到条件访问评估中，确保只有安全设备有权访问资源。 

### <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security
Microsoft Cloud App Security 利用 Microsoft Defender for Endpoint 终结点信号，直接查看云应用程序使用情况，包括从所有 Microsoft Defender for Endpoint 受监视设备使用不受支持的云服务 (卷影 IT) 。

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity
可疑活动是用户上下文中运行的进程。 Microsoft Defender for Endpoint 和 Azure ATP 之间的集成提供了跨活动和标识进行网络安全调查的灵活性。

### <a name="microsoft-defender-for-office"></a>Microsoft Defender for Office
[Defender for Office 365](https://docs.microsoft.com/office365/securitycompliance/office-365-atp) 通过 ATP 安全链接、ATP 安全附件、高级防钓鱼和欺骗智能功能帮助保护你的组织免受电子邮件或文件中恶意软件的攻击。 Office 365 ATP 和 Microsoft Defender for Endpoint 之间的集成使安全分析师能够前往上游调查攻击的入口点。 通过威胁情报共享，可以包含和阻止攻击。 

>[!NOTE]
> 针对过去 30 天内的事件显示 Defender for Office 365 数据。 对于警报，将基于第一次活动时间显示 Defender for Office 365 数据。 此后，数据在 Defender for Office 365 中不再可用。

### <a name="skype-for-business"></a>Skype for Business
Skype for Business 集成为分析员提供了一种通过门户中的简单按钮与可能受到威胁的用户或设备所有者进行通信的方法。

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender
借助 Microsoft 365 Defender，Microsoft Defender for Endpoint 和各种 Microsoft 安全解决方案形成统一的攻破前和入侵后企业防御套件，可跨终结点、标识、电子邮件和应用程序进行本机集成，以检测、预防、调查和自动响应复杂的攻击。 
 
[详细了解 Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)


## <a name="related-topics"></a>相关主题
- [配置集成和其他高级功能](advanced-features.md)
- [Microsoft 365 Defender 概述](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)
- [打开 Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/mtp-enable)
- [使用条件访问保护用户、数据和设备](conditional-access.md)