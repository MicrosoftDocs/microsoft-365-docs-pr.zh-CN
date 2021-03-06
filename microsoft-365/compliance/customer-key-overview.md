---
title: 使用客户密钥执行服务加密
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: seo-marvel-apr2020
description: 本文将介绍服务加密如何与 Microsoft 365 中的客户密钥一Microsoft 365。
ms.openlocfilehash: d12a5d2f80de11a69fc4a36146a511c5f9a306f8
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769445"
---
# <a name="service-encryption-with-customer-key"></a>使用客户密钥执行服务加密

Microsoft 365 DKM 密钥管理器和分布式密钥管理器BitLocker启用基线 (级别) 。 Microsoft 365内容添加了一层加密。 此内容包括来自 Exchange Online、Skype for Business、SharePoint Online、OneDrive for Business 和 Microsoft Teams。

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>服务加密、BitLocker和客户密钥如何协同工作

你的数据始终在 Microsoft 365 Service 中通过 BitLocker DKM 进行加密。 有关详细信息，请参阅如何Exchange Online[电子邮件密码](exchange-online-secures-email-secrets.md)。 客户密钥提供额外保护，防止未经授权的系统或人员查看数据，并补充BitLocker Microsoft 数据中心中的磁盘加密。 服务加密并不用于阻止 Microsoft 人员访问你的数据。 相反，客户密钥可帮助你履行控制根密钥的法规或合规性义务。 您明确授权 Microsoft 365服务使用您的加密密钥来提供增值云服务，如电子数据展示、反恶意软件、反垃圾邮件、搜索索引等。

客户密钥基于服务加密构建，可让你提供和控制加密密钥。 Microsoft 365然后使用这些密钥加密你的其余数据，如联机服务条款 ([OST) ](https://www.microsoft.com/licensing/product-licensing/products.aspx)中所述。 客户密钥可帮助您履行合规性义务，因为您可以控制用于加密Microsoft 365解密数据的加密密钥。
  
客户密钥增强了组织满足合规性要求的能力，这些要求指定了与云服务提供商的关键安排。 使用客户密钥，你可以为应用程序级别的静态Microsoft 365数据提供和控制根加密密钥。 因此，你可以对组织的密钥进行控制。

## <a name="customer-key-with-hybrid-deployments"></a>混合部署的客户密钥

客户密钥仅加密云中的其余数据。 客户密钥无法保护本地邮箱和文件。 可以使用其他方法加密本地数据，如BitLocker。

## <a name="about-data-encryption-policies"></a>关于数据加密策略

数据加密策略 (DEP) 定义加密层次结构。 该服务使用此层次结构，使用你管理的每个密钥和受 Microsoft 保护的可用性密钥加密数据。 使用 PowerShell cmdlet 创建 DEP，然后分配这些 DESP 以加密应用程序数据。 客户密钥支持三种类型的 MICROSOFT 365，每种策略类型使用不同的 cmdlet，并提供不同类型的数据的覆盖范围。 你可以定义的 DESP 包括：

**用于多个 Microsoft 365 工作负荷的 DEP** 这些 DEP 可跨租户内所有用户的多个 M365 工作负载加密数据。 这些工作负载包括：

- Teams一 (聊天、群聊、会议聊天和频道对话时显示聊天) 
- Teams媒体消息 (图像、代码段、视频消息、音频消息、wiki 图像) 
- Teams存储中存储的呼叫和Teams录制
- Teams聊天通知
- Teams Cortana 提供聊天建议
- Teams状态消息
- 用户和信号Exchange Online
- Exchange Online未通过邮箱 DEP 加密的邮箱
- Microsoft 信息保护：

  - EDM (数据) 精确匹配，包括数据文件架构、规则包和用于对敏感数据进行哈希运算的量。 对于 EDM Microsoft Teams，多工作负载 DEP 会从将 DEP 分配给租户时对新数据进行加密。 例如Exchange Online，客户密钥会加密所有现有和新数据。

  - 敏感度标签的标签配置

多工作负荷 DEP 不加密以下类型的数据。 相反，Microsoft 365使用其他类型的加密来保护此数据。

- SharePoint和OneDrive for Business数据。
- Microsoft Teams保存在 OneDrive for Business 和 SharePoint Online 中的Teams和一些呼叫和会议录像SharePoint联机 DEP 进行加密。
- 其他Microsoft 365客户密钥Yammer支持的其他工作负载，例如 Yammer 和 Planner。
- Teams实时事件和问答&实时事件中的 A。 例如Teams，此方案是唯一一个使用多工作负载 DEP 的客户密钥未加密的方案。

可以为每个租户创建多个 DEP，但一次只能分配一个 DEP。 分配 DEP 时，加密将自动开始，但需要一段时间才能完成，具体取决于租户的大小。

**用于邮箱Exchange Online的 DEP** 邮箱 DEP 可更精确地控制邮箱内Exchange Online。 使用邮箱 DEP 加密存储在不同类型的 EXO 邮箱（如 UserMailbox、MailUser、Group、PublicFolder 和 Shared 邮箱）中的数据。 每个租户最多可以有 50 个活动 DECP，并将这些 DESP 分配给各个邮箱。 可以将一个 DEP 分配给多个邮箱。

默认情况下，使用 Microsoft 管理的密钥对邮箱进行加密。 将客户密钥 DEP 分配给邮箱时：

- 如果邮箱是使用多工作负荷 DEP 加密的，则只要用户或系统操作访问邮箱数据，该服务就使用新邮箱 DEP 来重新包装邮箱。

- 如果邮箱已使用 Microsoft 托管的密钥加密，则只要用户或系统操作访问邮箱数据，该服务就使用新邮箱 DEP 重新包装邮箱。

- 如果邮箱尚未使用默认加密进行加密，则服务将邮箱标记为移动。 移动完成后，将进行加密。 邮箱移动根据针对所有邮箱设置的优先级Microsoft 365。 有关详细信息，请参阅移动服务中的Microsoft 365[请求](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-office-365-service)。 如果邮箱未在指定的时间内加密，请与 Microsoft 联系。

稍后，您可以刷新 DEP 或为邮箱分配不同的 DEP，如管理客户密钥[for Office 365](customer-key-manage.md)中所述。 每个邮箱必须具有适当的许可证，以分配 DEP。 有关许可详细信息，请参阅 [设置客户密钥之前](customer-key-set-up.md#before-you-set-up-customer-key)。

对于符合用户邮箱的许可要求的租户，MICROSOFT 365共享邮箱、公用文件夹邮箱和组邮箱分配 DEP。 对于非用户特定邮箱，不需要单独的许可证来分配客户密钥 DEP。

对于分配给单个邮箱的客户密钥 DEP，可以请求 Microsoft 在离开服务时清除特定 DEP。 有关数据清除过程和密钥吊销的信息，请参阅 [撤销密钥并开始数据清除路径过程](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process)。

在离开服务时撤销对密钥的访问权限时，可用性密钥将被删除，从而导致数据的加密删除。 加密删除可以减少数据重新管理的风险，这一点对于履行安全和合规义务非常重要。

**适用于 SharePoint Online 和 OneDrive for Business 的 DEP** 此 DEP 用于加密存储在 SPO 和 OneDrive for Business 中的内容，Microsoft Teams存储在 SPO 中的文件。 如果你使用的是多地理位置功能，你可以为组织为每个地理位置创建一个 DEP。 如果未使用多地理位置功能，则只能为每个租户创建一个 DEP。 请参阅设置客户 [密钥中的详细信息](customer-key-set-up.md)。

### <a name="encryption-ciphers-used-by-customer-key"></a>客户密钥使用的加密密码

客户密钥使用各种加密密码来加密密钥，如下图所示。

用于加密多个 Microsoft 365 工作负荷数据的 DEP 的关键层次结构与用于单个邮箱的 DEP 的Exchange Online层次结构。 唯一的区别是，邮箱密钥将替换为相应的Microsoft 365工作负荷密钥。

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>加密密码，用于加密Exchange Online和Skype for Business

![客户密钥Exchange Online加密密码](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>加密密码，用于加密 SharePoint Online、OneDrive for Business和Teams密钥

![SharePoint Online 客户密钥的加密密码](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>相关文章

- [设置客户密钥](customer-key-set-up.md)

- [管理客户密钥](customer-key-manage.md)

- [滚动或旋转客户密钥或可用性密钥](customer-key-availability-key-roll.md)

- [了解可用性密钥](customer-key-availability-key-understand.md)

- [客户密码箱](customer-lockbox-requests.md)

- [服务加密](office-365-service-encryption.md)