---
title: 使用自动调查和响应的自定义报告解决方案
keywords: SIEM， API， AIR， autoIR， Microsoft Defender for Endpoint， 自动调查， 集成， 自定义报告
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: 了解如何将自动调查和响应与自定义或第三方报告解决方案集成。
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6ed752f9514f1d2c8cadeb7cbbd1d7b9311b1b5f
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "52275008"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365 的自定义或第三方报告解决方案

借助[Microsoft Defender for Office 365，](defender-for-office-365.md)[你可以获取有关自动调查的详细信息](air-view-investigation-results.md)。 但是，某些组织也使用自定义或第三方报告解决方案。 如果你的组织想要将有关自动调查的信息与[](office-365-air.md)此类解决方案集成，可以使用Office 365活动 API。

**适用对象**
- [适用于 Office 365 计划 2 的 Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

借助[Microsoft Defender for Office 365，](defender-for-office-365.md)[你可以获取有关自动调查的详细信息](air-view-investigation-results.md)。 但是，某些组织也使用自定义或第三方报告解决方案。 如果你的组织希望将有关自动调查的信息与此类解决方案集成，可以使用Office 365活动 API。

|资源|说明|
|:---|:---|
|[Office 365 管理 API 概述](/office/office-365-management-api/office-365-management-apis-overview)|管理Office 365 API 提供了有关用户、管理员、系统和策略操作以及活动日志中各种Microsoft 365 Azure Active Directory事件的信息。|
|[Office 365 管理 API 入门](/office/office-365-management-api/get-started-with-office-365-management-apis)|应用程序Office 365 API 使用 Azure AD 为应用程序提供身份验证服务，以访问Microsoft 365数据。 请按照本文中的步骤进行设置。|
|[Office 365 管理活动 API 参考](/office/office-365-management-api/office-365-management-activity-api-reference)|可以使用管理活动 API Office 365 Azure AD 活动日志中检索有关用户、管理员、系统和策略操作Microsoft 365事件的信息。 阅读本文可了解有关此工作原理的更多信息。|
|[Office 365 管理活动 API 架构](/office/office-365-management-api/office-365-management-activity-api-schema)|大致了解通用架构和[](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) [Defender for Office 365 威胁](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema)调查和响应架构，以了解通过 Office 365 管理活动 API 提供的特定数据类型。|
|

## <a name="see-also"></a>另请参阅

- [Microsoft Defender for Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender 中的自动调查和响应](/microsoft-365/security/defender/m365d-autoir)
