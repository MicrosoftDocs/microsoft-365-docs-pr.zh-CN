---
title: Azure 与 Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: 如果需要Microsoft 365同步密码或单一登录，请与 Azure AD 集成。
ms.openlocfilehash: f977969634401d59d7598136f9323cb0e37f9ece
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905328"
---
# <a name="azure-integration-with-microsoft-365"></a>Azure 与 Microsoft 365

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

Microsoft 365使用 Azure Active Directory (Azure AD) 在后台管理用户标识。 你的 Microsoft 365 订阅包括免费的 Azure AD 订阅，以便你可以集成本地 Active Directory 域服务 (AD DS) 以同步用户帐户和密码或设置单一登录。 还可以购买高级功能，以更好地管理帐户。
  
Azure AD 还提供了其他功能，如管理集成应用，可用于扩展和自定义Microsoft 365订阅。
  
可以使用 Azure AD 部署顾问，在 Microsoft 365 管理中心获取指导性安装和配置 (必须登录到 Microsoft 365) ：

 - [Azure AD 连接顾问](https://aka.ms/aadconnectpwsync)
 - [AD FS 部署顾问](https://aka.ms/adfsguidance)
 - [Azure AD 设置指南](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Azure AD 版本和Microsoft 365身份管理

如果你有付费订阅，Microsoft 365 Azure AD 订阅。 可以使用 Azure AD 创建和管理用户和组帐户。 若要激活此订阅，必须完成一次注册。 之后，你可以从你的管理中心Microsoft 365 Azure AD。 

有关注册免费 Azure AD 订阅的说明，请参阅 [使用免费的 Azure AD 订阅](../compliance/use-your-free-azure-ad-subscription-in-office-365.md)。 不要直接转到 azure.microsoft.com 进行注册，否则你最终会获得 Microsoft Azure 的试用版或付费订阅，该订阅与使用 Microsoft 365 的免费 Azure AD 订阅Microsoft 365。 
  
借助免费订阅，你可以与本地目录同步、设置单一登录，以及将许多软件作为服务应用程序（如 Salesforce、DropBox 等）进行同步。
  
如果需要增强的 AD DS 功能、双向同步和其他管理功能，可以将免费订阅升级到付费付费订阅。 有关详细信息，请参阅Azure Active Directory[版本](https://azure.microsoft.com/pricing/details/active-directory/)。
  
有关 Azure AD Microsoft 365，请参阅Microsoft 365[标识模型。](about-microsoft-365-identity.md)
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>扩展租户Microsoft 365功能

|**功能**|**说明**|
|:-----|:-----|
|集成应用  <br/> |你可以向单个应用授予Microsoft 365数据的访问权限，如邮件、日历、联系人、用户、组、文件和文件夹。 还可以在全局管理员级别授权这些应用，并可在 Azure AD 中注册应用，使其可供整个公司使用。 有关详细信息，请参阅集成[应用和 Azure AD Microsoft 365管理员](integrated-apps-and-azure-ads.md)。  <br/> 另请参阅 [单一登录](/azure/active-directory/manage-apps/what-is-single-sign-on)。  <br/> |
|PowerApps  <br/> | Power 应用是适用于移动设备的聚焦应用，可连接到现有数据源，SharePoint列表和其他数据应用。 有关详细信息[，请参阅](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)在 SharePoint Online 和[PowerApps 页面中为列表创建 PowerApp。](https://powerapps.microsoft.com/)  <br/> |
   
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](microsoft-365-overview.md)