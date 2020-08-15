---
title: 适用于德国的 Office 365 端点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/08/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 在本文中，您将找到在德国使用 Office 365 的客户可以访问的终结点。
hideEdit: true
ms.openlocfilehash: 07badf1febec964ffdf6d6ef39c88f0e8bbca3f7
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46688152"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany 终结点

 *适用于： Office 365 管理员*

Office 365 要求连接到 Internet。 下面的终结点应仅供使用 **Office 365 德国** 计划的客户访问。
  
 **Office 365 终结点：**[全球（包括 GCC）](urls-and-ip-address-ranges.md)  | [由世纪互联运营的 Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 美国政府版 DoD](microsoft-365-u-s-government-dod-endpoints.md) | [Office 365 美国政府版 GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**上次更新时间：** 07/08/2020- ![ RSS ](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [更改日志订阅](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**下载：** 一个 [JSON 格式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)列表中的所有必需和可选目标。  <br/> |

从 [管理 Office 365 终结点](managing-office-365-endpoints.md) 开始，了解我们关于使用此数据管理网络连接的建议。 终结点数据在每月开始时更新，并在30天内发布新的 IP 地址和 Url，并在处于活动状态之前发布。 这样一来，在需要新的连接之前，尚不具有自动更新的客户即可完成其过程。 如果需要，还可以更新终结点，以解决支持升级、安全事件或其他立即运行的要求。 您始终可以引用 [更改日志订阅](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。

以下页面上显示的数据都是从基于 REST 的 web 服务生成的。 如果使用脚本或网络设备访问此数据，则应直接转到 [Web 服务](microsoft-365-ip-web-service.md) 。

下面的终结点数据列出了从用户计算机到 Office 365 的连接要求。 它不包括从 Microsoft 到客户网络的网络连接，有时也称为混合网络连接或入站网络连接。

终结点分为四个服务区域。可以独立选择前三个服务区域进行连接。第四个服务区域是一个常见的依赖项（称为 Microsoft 365 Common 和 Office），并且必须始终具有网络连接。

显示的数据列是：

- **ID**：行的 ID 号，也称为终结点集。此 ID 与终结点集的 Web 服务返回的 ID 相同。

- **类别**：显示终结点集是分类为“优化”、“允许”还是“默认”。可以在 [https://aka.ms/pnc](https://aka.ms/pnc) 上了解管理它们的这些类别和指南。此列还列出了哪些终结点集需要具有网络连接。对于不需要具有网络连接的终结点集，我们在此字段中提供备注，以指示在终结点集被阻止时将丢失哪些功能。如果要排除整个服务区域，则根据需要列出的终结点集不需要连接。

- **ER**：如果使用带有 Office 365 路由前缀的 Azure ExpressRoute 支持终结点集，则为**是**。包含所显示的路由前缀的 BGP 社区与列出的服务区域一致。当 ER 为**否**时，这意味着此终结点集不支持 ExpressRoute。但是，不应假设没有为 ER 为 **否**的终结点集播发路由。

- **地址**：列出终结点集的 FQDN 或通配符域名以及 IP 地址范围。请注意，IP 地址范围采用 CIDR 格式，并且可能包含指定网络中的许多单独 IP 地址。
 
- **端口**：列出与地址合并以形成网络终结点的 TCP 或 UDP 端口。你会注意到 IP 地址范围中存在一些重复，其中列出了不同的端口。

[!INCLUDE [Office 365 Germany endpoints](../includes/office-365-germany-endpoints.md)]

 

