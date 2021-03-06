---
title: Microsoft Defender for Endpoint 中的已连接应用程序
ms.reviewer: ''
description: 查看使用标准 OAuth 2.0 协议进行身份验证并提供用于 Microsoft Defender for Endpoint API 的令牌的已连接合作伙伴应用程序。
keywords: partners， applications， third-party， connections， sentinelone， lookout， bitdefender， corrata， morphisec， paloalto， ziften， better mobile
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4b212acdf4bdf8fa53ef00763463190e204fc1ed
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339162"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint 中的已连接应用程序

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

连接的应用程序使用 API 与 Defender for Endpoint 平台集成。 

应用程序使用标准 OAuth 2.0 协议进行身份验证并提供与 Microsoft Defender for Endpoint API 一同使用的令牌。  此外，Azure Active Directory (Azure AD) 应用程序允许租户管理员设置对哪些 API 可以使用相应应用访问的显式控制。
 
需要按照以下步骤 [操作，](/microsoft-365/security/defender-endpoint/apis-intro) 将 API 与已连接的应用程序一同使用。
 
## <a name="access-the-connected-application-page"></a>访问已连接的应用程序页
从左侧导航菜单中，**选择终结点**  >  **合作伙伴和 API**  >  **连接的应用程序**。

 
## <a name="view-connected-application-details"></a>查看连接的应用程序详细信息
"已连接应用程序"页提供有关连接到组织中 Microsoft Defender for Endpoint 的 Azure AD 应用程序的信息。 你可以查看已连接应用程序的使用情况：上次查看时间、过去 24 小时内的请求数以及最近 30 天内的请求趋势。

![已连接应用的图像](images/connected-apps.png)
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>编辑、重新配置或删除已连接的应用程序
" **打开应用程序设置"** 链接将在 Azure 门户中打开相应的 Azure AD 应用程序管理页面。 在 Azure 门户中，你可以管理权限、重新配置或删除已连接的应用程序。
