---
title: 设置连接器以在 Microsoft 365 中存档 Reuters Eikon Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: 管理员可以设置连接器，以从 Microsoft 365 中导入和存档来自Microsoft 365。 通过此连接器，您可以在 Microsoft 365 中存档来自第三方数据源Microsoft 365。 在存档此数据后，可以使用合规性功能（如合法保留、内容搜索和保留策略）管理第三方数据。
ms.openlocfilehash: f3e0c9d542f54a46703b4acd0c1f154d3ab84cb8
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2021
ms.locfileid: "51164093"
---
# <a name="set-up-a-connector-to-archive-reuters-eikon-data"></a>设置连接器以存档 Reuters Eikon 数据

使用 Microsoft 365 合规中心中的一个 Microsoft 365 连接器，将数据从 Reuters Eikon 平台导入并存档到组织Microsoft 365邮箱。 该连接器配置为定期[](https://globanet.com/eikon/)捕获第三方数据源 (中的项目，) 将这些项目导入Microsoft 365。 连接器将用户的 Reuters Eikon 帐户的内容（如人对人消息、群聊、附件和免责声明）转换为电子邮件格式，然后将这些项目导入 Microsoft 365 中的用户邮箱。

在将 Reuters Eikon 数据存储在用户邮箱中后，可以应用 Microsoft 365 合规性功能，如诉讼保留、电子数据展示、保留策略和保留标签以及通信合规性。 使用 Reuters Eikon 连接器在 Microsoft 365 导入和存档数据可帮助组织遵守政府及法规策略。

## <a name="overview-of-archiving-reuters-eikon-data"></a>Archiving Reuters Eikon 数据概述

以下概述说明了使用连接器在数据记录中存档 Reuters Eikon 数据Microsoft 365。

![用于 Reuters Eikon 数据的存档工作流](../media/ReutersEikonConnectorWorkflow.png)

1. 贵组织与 Reuters Eikon 合作，以设置和配置一个 Reuters Eikon 网站。

2. 每隔 24 小时一次，将 Reuters Eikon 项目复制到该"改进 24 小时"网站。 连接器还会将 Reuters Eikon 项目转换为电子邮件格式。

3. 在 Microsoft 365 合规中心创建的 Reuters Eikon 连接器每天连接到一个位于 Microsoft 云中的安全 Azure 存储 位置。

4. 连接器使用自动用户映射的 *Email* 属性值将项目导入特定用户的邮箱，如步骤 [3 中所述](#step-3-map-users-and-complete-the-connector-setup)。 "收件箱"文件夹中名为 **"Reuters Eikon"** 的子文件夹是在用户邮箱中创建的，并且项目会导入到该文件夹中。 连接器使用 Email 属性的值确定将项目导入到哪个 *邮箱* 。 每个 Reuters Eikon 项目都包含此属性，该属性用该项目每个参与者的电子邮件地址填充。

## <a name="before-you-begin"></a>开始之前

- 为 Microsoft 连接器创建一个 Microsoft Merge1 帐户。 若要创建帐户，请联系["用户支持人员"。](https://globanet.com/ms-connectors-contact) 在步骤 1 中创建连接器时，将登录到此帐户。

- 必须在步骤 1 (步骤 3) 创建一个 Reuters Eikon 连接器并将其完成的用户分配给 Exchange Online 中的邮箱导入导出角色。 若要在合规性中心的"数据连接器"页上添加 **连接器，Microsoft 365** 此角色。 默认情况下，此角色不会分配给角色组Exchange Online。 可以将"邮箱导入导出"角色添加到组织中"组织管理"角色Exchange Online。 也可以创建角色组，分配邮箱导入导出角色，然后将相应的用户添加为成员。 有关详细信息，请参阅"在角色[](/Exchange/permissions-exo/role-groups#create-role-groups)组中管理角色组[](/Exchange/permissions-exo/role-groups#modify-role-groups)"一文的"创建角色组"或"修改角色Exchange Online"。

## <a name="step-1-set-up-the-reuters-eikon-connector"></a>步骤 1：设置 Reuters Eikon 连接器

第一步是访问 Microsoft 365 合规中心的"数据连接器"页，并创建一个 Connector for Reuters Eikon 数据。

1. 转到 ， [https://compliance.microsoft.com](https://compliance.microsoft.com/) 然后单击 Data **connectors**  >  **Reuters Eikon**。

2. 在 **"Reuters Eikon** 产品说明"页上，单击"**添加连接器"。**

3. 在"**服务条款"页上**，单击"接受 **"。**

4. 输入标识连接器的唯一名称，然后单击下一 **步**。

5. 登录到 Merge1 帐户以配置连接器。

## <a name="step-2-configure-the-reuters-eikon-connector-on-the-veritas-merge1-site"></a>步骤 2：在"都斯合并 1"网站上配置 Reuters Eikon 连接器

第二步是在 Merge1 网站上配置 Reuters Eikon 连接器。 若要了解如何在"一线合并"网站上配置 Reuters Eikon 连接器，请参阅 [Merge1 第](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20Eikon%20User%20Guide%20.pdf)三方连接器用户指南。

单击"保存&**完成**"后，将显示合规性中心内连接器Microsoft 365中的"用户映射"页。

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>步骤 3：映射用户并完成连接器设置

若要映射用户并完成 Microsoft 365设置，请按照以下步骤操作：

1. 在"**将外部用户映射到 Microsoft 365"页上**，启用自动用户映射。 Reuters Eikon 项目包含一个称为 *Email* 的属性，其中包含您组织中用户的电子邮件地址。 如果连接器可以将此地址与Microsoft 365关联，则项目将导入该用户的邮箱。

2. 单击 **"下** 一步"，查看设置，然后转到"数据连接器"页以查看新连接器的导入过程的进度。

## <a name="step-4-monitor-the-reuters-eikon-connector"></a>步骤 4：监视 Reuters Eikon 连接器

创建 Reuters Eikon 连接器后，可以在合规性中心内查看Microsoft 365状态。

1. 转到左侧 [https://compliance.microsoft.com](https://compliance.microsoft.com) 导航 **导航中的"数据** 连接器"，然后单击" 数据连接器"。

2. 单击" **连接器"** 选项卡，然后选择 **"Reuters Eikon"** 连接器以显示飞出页。 此页面包含有关连接器的属性和信息。

3. 在 **"源的连接器状态"** 下， **单击"下载** 日志"链接 (或) 连接器的状态日志。 此日志包含有关已导入到 Microsoft 云的数据的信息。

## <a name="known-issues"></a>已知问题

- 目前，我们不支持导入大于 10 MB 的附件或项目。 稍后将提供对较大项目的支持。