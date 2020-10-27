---
title: Microsoft 365 的会话超时
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: 了解如何使用会话超时在 Microsoft 365 客户端应用程序中平衡安全性和轻松访问。
ms.openlocfilehash: 2c0a7c2633715ac23942a22858b41e83a091c46a
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769288"
---
# <a name="session-timeouts-for-microsoft-365"></a>Microsoft 365 的会话超时

会话生存期是 Microsoft 365 的身份验证的重要部分，并且是平衡安全性的重要组成部分以及用户提示其凭据的提示次数。

## <a name="session-times-for-microsoft-365-services"></a>Microsoft 365 服务的会话时间

当用户在任何 Microsoft 365 web 应用或移动应用程序中进行身份验证时，将建立一个会话。 在会话期间，用户不需要重新进行身份验证。 当用户处于非活动状态、关闭浏览器或选项卡时，或者当用户的身份验证令牌过期时，例如在重置其密码时，会话可能会过期。 Microsoft 365 服务具有不同的会话超时，以与每个服务的典型用途相对应。

下表列出了 Microsoft 365 服务的会话生存期：

| Microsoft 365 服务 | 会话超时 |
|:-----|:-----|
|Microsoft 365 管理中心  <br/> |系统将要求你为管理中心每隔8小时提供凭据。  <br/> |
|SharePoint Online  <br/> |只要用户选择 " **让我进入登录** 状态"，5天的非活动状态。 如果用户在24小时或更长时间后再次访问 SharePoint Online，则超时值将重置为5天。  <br/> |
|Outlook Web App  <br/> |6小时。  <br/> 您可以使用 [set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet 中的 _ActivityBasedAuthenticationTimeoutInterval_ 参数更改此值。  <br/> |
|Azure Active Directory  <br/> 在启用新式验证的 Windows 客户端中，Office 和 Microsoft 365 应用程序使用的 ()   <br/> | 新式验证使用访问令牌和刷新令牌向用户授予使用 Azure Active Directory 的 Microsoft 365 资源的访问权限。 访问令牌是在成功进行身份验证后提供的 JSON Web 令牌，有效期为1小时。 此外，还提供刷新令牌的生存期较长。 当访问令牌过期时，Office 客户端将使用有效的刷新令牌获取新的访问令牌。 如果用户的初始身份验证仍然有效，则 exchange 将成功。  <br/>  刷新令牌有效期为90天，且持续使用，它们在被吊销前可有效。  <br/>  刷新令牌可能会因以下几个事件而无效：  <br/>  用户的密码自发出刷新令牌后已更改。  <br/>  管理员可以应用条件访问策略，以限制对用户试图访问的资源的访问。  <br/> |
|适用于 Android、iOS 和 Windows 10 的 SharePoint 和 OneDrive 移动应用  <br/> |访问令牌的默认生存时间为1小时。 刷新令牌的默认最大非活动时间为90天。  <br/> [了解有关令牌和如何配置令牌生存期的详细信息](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 若要撤销刷新令牌，可以重置用户的 Microsoft 365 密码  <br/> |
|Yammer 与 Microsoft 365 Sign-In  <br/> |浏览器的生存期。 如果用户关闭浏览器并在新浏览器中访问 Yammer，Yammer 将使用 Microsoft 365 重新对其进行身份验证。 如果用户使用的是缓存 cookie 的第三方浏览器，则在重新打开浏览器时，可能不需要重新进行身份验证。  <br/> > [!NOTE]> 仅对使用适用于 Yammer 的 Microsoft 365 Sign-In 的网络有效。           |

