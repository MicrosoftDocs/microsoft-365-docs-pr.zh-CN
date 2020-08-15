---
title: 规划 Microsoft 365 的第三方 SSL 证书
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要：介绍了 Exchange 内部部署和混合部署、使用 AD FS 的 SSO、Exchange Online services 和 Exchange Web 服务所需的 SSL 证书。
ms.openlocfilehash: 1738e4c316772d928138adc654372bd0b9efae65
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687836"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>规划 Microsoft 365 的第三方 SSL 证书

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

若要对客户端和 Microsoft 365 环境之间的通信进行加密，必须在基础结构服务器上安装第三方安全套接字层 (SSL) 证书。

本文是 [Microsoft 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。
   
以下 Microsoft 365 组件需要证书：
  
- 本地 Exchange
    
- 针对 Active Directory 联合身份验证服务 (AD FS) 联合服务器和 AD FS 联合服务器代理的单一登录 (SSO)  () 
    
- Exchange Online 服务，例如自动发现、Outlook 无处不在和 Exchange Web 服务
    
- Exchange 混合服务器
    
## <a name="certificates-for-exchange-on-premises"></a>Exchange 本地的证书

有关如何使用数字证书在本地 Exchange 组织和 Exchange Online 之间进行通信的概述，请参阅 TechNet 文章 " [了解证书要求](https://go.microsoft.com/fwlink/p/?LinkID=243657)"。
  
## <a name="certificates-for-single-sign-on"></a>单一登录的证书

若要向您的用户提供简化的单一登录体验，其中包括强健的安全性，联合服务器或联合服务器代理需要下表中所示的证书。 下表重点介绍了 Active Directory 联合身份验证服务 (AD FS) ，我们还提供了有关 [使用第三方标识提供程序](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的详细信息。
  
| 证书类型 | 说明 | 在部署之前，您需要了解的内容 |
|:-----|:-----|:-----|
|**SSL 证书 (也称为服务器身份验证证书) ** <br/> |这是用于在联合服务器、客户端和联合服务器代理计算机之间进行通信的标准 SSL 证书。  <br/> |AD FS 需要 SSL 证书。 默认情况下，AD FS 使用在 Internet Information Services (IIS) 中为默认网站配置的 SSL 证书。  <br/> 此 SSL 证书的使用者名称用于确定要部署的每个 AD FS 实例的联合身份验证服务 (FS) 名称。 请考虑为任何新的证书颁发机构选择一个主题名称， (CA) 颁发的证书，这些证书最能代表 Microsoft 365 的公司或组织的名称。 此名称必须是可通过 Internet 路由的。  <br/>**警告：** AD FS 要求此 SSL 证书没有无点 (短名称) 主题名称。          <br/> **建议：** 由于 AD FS 的客户端必须信任此证书，因此我们建议使用由公共 (第三方) CA 颁发的 SSL 证书，或者使用受信任根颁发的 CA 颁发的 SSL 证书;例如，VeriSign 或 Thawte。  <br/> |
|**令牌签名证书** <br/> |这是标准的 x.509 证书，用于对联合服务器发出的和 Microsoft 365 接受和验证的所有令牌进行安全签名。  <br/> |令牌签名证书必须包含链接到 FS 中的受信任根的私钥。 默认情况下，AD FS 将创建自签名证书。 但是，根据组织的需要，可以使用 AD FS 管理单元将此证书更改为 CA 颁发的证书。  <br/>**警告：** 令牌签名证书对 FS 稳定性至关重要。 如果更改了证书，则必须通知 Microsoft 365 更改。 如果未提供通知，则用户将无法登录到其 Microsoft 365 服务产品。<br/>**建议：** 建议使用 AD FS 生成的自签名令牌签名证书。 这样一来，它将默认为您管理此证书。 例如，当此证书即将过期时，AD FS 将生成一个新的自签名证书。  <br/> |
   
联合服务器代理需要下表中所述的证书。
  
| 证书类型 | 说明 | 在部署之前，您需要了解的内容 |
|:-----|:-----|:-----|
|SSL 证书  <br/> |这是用于保护联合服务器、联合服务器代理和 Internet 客户端计算机之间的通信的标准 SSL 证书。  <br/> |必须先将此 SSL 证书绑定到 IIS 中的默认网站，然后才能成功运行 AD FS 联合服务器代理配置向导。  <br/> 此证书必须与企业网络中的联合服务器上配置的 SSL 证书具有相同的主题名称。  <br/> **建议：** 我们建议您使用与此联合服务器代理连接的联合服务器上配置的相同服务器身份验证证书。  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>用于自动发现、Outlook 无处不在和 Active Directory 同步的证书

面向外部的 Exchange 2013、Exchange 2010、Exchange 2007 和 Exchange 2003 客户端访问服务器 (CASs) 需要第三方 SSL 证书，以实现自动发现、Outlook 无处不在和 Active Directory 同步服务的安全连接。 您可能已在您的本地环境中安装了此证书。
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange 混合服务器的证书

面向外部的 Exchange 混合服务器需要第三方 SSL 证书，以实现与 Exchange Online 服务的安全连接。 您需要从第三方 SSL 提供商获取此证书。
  
## <a name="microsoft-365-certificate-chains"></a>Microsoft 365 证书链

本文介绍了您可能需要在基础结构上安装的证书。 有关安装在 Microsoft 365 服务器上的证书的详细信息，请参阅 [microsoft 365 证书链](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](microsoft-365-overview.md)
