---
title: Microsoft 365 中的数据保留、删除和销毁
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Microsoft 365 有关数据保留、删除和销毁的 Microsoft 策略概述。
ms.openlocfilehash: c522c1a1a4de46a4fc36bd87a031be8b47c5523d
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687776"
---
# <a name="data-retention-deletion-and-destruction-in-microsoft-365"></a>Microsoft 365 中的数据保留、删除和销毁

Microsoft 有一个用于 Microsoft 365 的数据处理标准策略，用于指定在删除后保留客户数据的时间。 在以下两种情况下，将删除客户数据：

- **主动删除**：租户具有活动的订阅，用户或管理员删除数据，或管理员删除了用户。
- **被动删除**：租户订阅结束。

## <a name="data-retention"></a>数据保留

对于每个删除方案，下表显示了数据类别和分类的最大数据保留期：

| 数据类别 | 数据分类 | 说明 | 示例 | 保留期 |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| 客户数据 | 客户内容| 由管理员和用户直接提供/创建的内容 <br><br> 在 microsoft 数据中心中使用 Microsoft 365 中的服务时，包括所有文本、声音、视频、图像文件以及软件的创建和存储。 | 最常使用的 Microsoft 365 应用程序的示例，这些应用程序允许用户创作数据包括 Word、Excel、PowerPoint、Outlook 和 OneNote <br><br> 客户内容还包括由客户拥有的/提供的机密 (密码、证书、加密密钥、存储密钥)  | **主动删除方案：** 最多30天 <br><br> **被动删除方案：** 最多180天 |
| 客户数据 | 最终用户可识别信息 (EUII)  | 标识或可用于标识 Microsoft 服务用户的数据。 EUII 不包含客户内容 | 用户名或显示名称 (域 \ 用户名)  <br><br> 用户主体名称 (name@domain)  <br><br>  特定于用户的 IP 地址 | **主动删除方案：** 最多180天 (仅租户管理员操作)  <br><br> **被动删除方案：** 最多180天 |
| 个人数据 <br> 客户数据中不包含 (数据)  | 最终用户匿名标识符 (EUPI)  | Microsoft 创建的与 Microsoft 服务用户关联的标识符。 与其他信息（如 mapping 表）结合使用时，EUPI 标识最终用户 <br><br> EUPI 不包含由客户上传或创建的信息 | 用户 Guid、PUIDs 或 Sid <br><br> 会话 Id | **主动删除方案：** 最多30天 <br><br> **被动删除方案：** 最多180天 |

## <a name="subscription-retention"></a>订阅保留

在活动订阅的期限内，订阅者可以访问、提取或删除存储在 Microsoft 365 中的客户数据。 如果付费订阅结束或终止，Microsoft 会将 Microsoft 365 中存储的客户数据保留在90天的受限制的帐户中，以使订阅者能够提取数据。 在90天的保留期结束后，Microsoft 将禁用该帐户并删除客户数据。 在过期或终止对 Microsoft 365 的订阅后，不超过180天，Microsoft 将禁用该帐户并删除帐户中的所有客户数据。 一旦所有数据的最大保留期已过，数据将以商业方式呈现，从而无法恢复。

对于免费试用版，你的帐户在大多数国家和地区中的30天内将转入宽限期状态。 在此宽限期内，你可以购买 Microsoft 365。 如果决定不购买 Microsoft 365，可取消试用或等待宽限期到期，届时系统将会删除你的试用帐户信息和数据。

## <a name="expedited-deletion"></a>加速删除

对于任何订阅，订阅者都可以与 Microsoft 支持人员联系，并请求加速订阅的取消设置。 在此过程中，管理员输入 Microsoft 提供的锁定代码后，将在三天内删除所有用户数据。 这包括 SharePoint Online 中的数据和 Exchange Online 中的 "保留" 或 "存储在非活动邮箱中"。

有关加速取消设置的详细信息，请参阅 [取消订阅](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/cancel-your-subscription)。

## <a name="related-links"></a>相关链接

- [数据销毁](microsoft-365-data-destruction.md)
- [Office 365 中的永久性](microsoft-365-data-immutability.md)
- [Exchange Online 数据删除](microsoft-365-exchange-online-data-deletion.md)
- [SharePoint Online 数据删除](microsoft-365-sharepoint-online-data-deletion.md)
- [Skype for Business 数据删除](microsoft-365-skype-data-deletion.md)
