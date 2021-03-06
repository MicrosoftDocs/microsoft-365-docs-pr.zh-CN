---
title: 最终用户垃圾邮件通知Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 管理员可以了解 EOP 邮箱中隔离邮件的最终用户Exchange Online Protection () 。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 71f2a33ad83f94895c396f92c18753bfca7f2905
ms.sourcegitcommit: ac3e9ccb7b43a42e600af8f44e6f30019533faeb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "52933163"
---
# <a name="use-user-spam-notifications-to-release-and-report-quarantined-messages"></a>使用用户垃圾邮件通知释放并报告隔离邮件

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**适用对象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 计划 1 和计划 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

无论是在有 Exchange Online 邮箱的 Microsoft 365 组织中，还是在没有 Exchange Online 邮箱的独立 Exchange Online Protection (EOP) 组织中，隔离功能都会隔离具有潜在危险或不需要的邮件。 有关详细信息，请参阅 [EOP 中的隔离邮件](quarantine-email-messages.md)。

默认情况下，最终用户垃圾邮件通知在反垃圾邮件策略中处于禁用状态。 当管理员启用[](configure-your-spam-filter-policies.md#configure-end-user-spam-notifications)最终用户垃圾邮件通知时，收件人 (包括启用了自动映射的共享邮箱) 将收到自 202) 0 年 4 月开始被隔离为垃圾邮件、批量电子邮件或 (网络钓鱼邮件的定期通知。

对于共享邮箱，只有被授予共享邮箱的 FullAccess 权限的用户才支持最终用户垃圾邮件通知。 有关详细信息，请参阅使用 [EAC 编辑共享邮箱委派](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation)。

组不支持最终用户垃圾邮件通知。

> [!NOTE]
> 被隔离为高可信度网络钓鱼、恶意软件或邮件流规则 (也称为传输规则) 仅对管理员可用。 有关详细信息，请参阅[在 EOP 中以管理员身份管理已隔离邮件](manage-quarantined-messages-and-files.md)。

最终用户垃圾邮件通知包含每个隔离邮件的以下信息：

- **发件人**：已隔离邮件的发送名称和电子邮件地址。
- **主题**：隔离邮件的主题行文本。
- **日期**：隔离邮件 (日期和时间) UTC 格式。
- **阻止发件人**：单击此链接将发件人添加到邮箱上的阻止发件人列表中。 有关详细信息，请参阅 [阻止邮件发件人](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4)。
- **释放**：对于 (网络钓鱼) 邮件，你可以在此处释放邮件，而无需进入隔离 Microsoft 365 Defender 门户。 
- 查看：单击此链接可转到Microsoft 365 Defender 门户中的"隔离"，你可以在那里 (查看、释放、删除或报告隔离邮件) 隔离邮件的原因。 有关详细信息，请参阅在 [EOP](find-and-release-quarantined-messages-as-a-user.md)中以用户模式查找并释放隔离邮件。

![示例最终用户垃圾邮件通知](../../media/end-user-spam-notification.png)

> [!NOTE]
> 阻止的发件人仍可向您发送邮件。 来自此发件人的任何发送到您的邮箱的邮件将立即移动到"垃圾邮件"文件夹。 来自此发件人的未来邮件将转到您的"垃圾邮件"文件夹或最终用户隔离邮箱。 如果要在到达时删除这些邮件，而不是隔离它们，请使用邮件流规则 [ (也称为](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) 传输规则) 到达时删除邮件。
