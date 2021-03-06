---
title: 在核心电子数据展示案例中搜索内容
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 搜索可能与核心电子数据展示案例相关的内容。
ms.openlocfilehash: 8d2e2a20135312a8f111a071abbe77b03b8e8363
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2021
ms.locfileid: "52311769"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>搜索核心电子数据展示案例中的内容

创建核心电子数据展示案例并保留该案例的关注人员后，可以创建并运行一个或多个搜索，以查找与案例相关的内容。 与核心电子数据展示案例关联的搜索不会在安全与合规中心的"内容搜索"Microsoft 365列出。 这些搜索将列在与 **搜索** 关联的核心电子数据展示案例的"搜索"页面上。 这也意味着与案例关联的搜索只能由案例成员访问。

创建核心电子数据展示搜索：
  
1. 转到 ，然后使用已分配有相应电子数据展示权限且是案例成员用户帐户的 <https://compliance.microsoft.com> 凭据登录。

2. 在合规性中心的左侧导航窗格中，Microsoft 365全部显示"，然后单击"电子数据展示>**核心"。**

3. 在"**核心电子数据展示**"页上，选择要创建关联搜索的案例，然后单击"打开 **案例"。**

4. 在案例 **的主页** 上，单击"搜索 **"** 选项卡，然后单击"新建 **搜索"。**

   ![单击"新建搜索"创建核心电子数据展示搜索](../media/CoreeDiscoverySearch1.png)

   > [!NOTE]
   > 通过 **"按 ID 搜索"** 列表选项，可以使用 ID 列表搜索特定电子邮件Exchange邮箱项目。 若要创建 ID 列表搜索，你可以提交一个用于标识要搜索的特定邮箱项的逗号分隔符值 (CSV) 文件。 有关说明，请参阅 [为 ID 列表搜索准备 CSV 文件](csv-file-for-an-id-list-content-search.md)。

5. 在 **"新建搜索** "向导中，键入搜索的名称和帮助标识搜索的可选说明。 搜索名称在组织中必须是唯一的。

6. 在 **"位置"** 页上，选择要搜索的内容位置。 可以搜索邮箱、网站和公用文件夹。

    ![选择将其置于保留状态的内容位置](../media/ContentSearchLocations.png)
  
   1. **Exchange邮箱**：将开关设置为 **"打开**"，然后单击"选择用户、组或团队"以指定要置于保留中的邮箱。 使用搜索框查找用户邮箱和通讯 (将要置于保留状态) 的组成员的邮箱置于保留状态。 您还可以搜索与 Microsoft Team (关联的邮箱，以查找) 组Office 365组Yammer邮件。 有关存储在邮箱中的应用程序数据详细信息，请参阅 [Ediscovery](what-is-stored-in-exo-mailbox.md)邮箱中存储的内容。

   2. **SharePoint网站**：将开关设置为 **"** 打开"，然后单击"选择网站"以指定SharePoint网站OneDrive保留的帐户。 键入要保留的每个网站的 URL。 还可以为 Microsoft 团队、SharePoint 组或组Office 365网站添加Yammer URL。
  
   3. **Exchange公用文件夹**：将开关设置为 **"打开**"，将组织Exchange Online文件夹置于保留状态。 你无法选择要置于保留状态的特定公用文件夹。 如果不想将公用文件夹置于保留状态，请关闭切换开关。
  
   4. 选中此复选框可搜索Teams本地用户的内容。 例如，如果搜索组织的所有 Exchange 邮箱并选中此复选框，则用于存储本地用户的 Teams 聊天数据的基于云的存储将包含在搜索范围内。 有关详细信息，请参阅 [搜索本地用户的 Teams 聊天数据](search-cloud-based-mailboxes-for-on-premises-users.md)。

7. 在" **定义搜索条件"** 页上，键入关键字查询，并在必要时向搜索查询添加条件。

   ![配置搜索查询](../media/ContentSearchQuery.png)

   1. 指定关键字、邮件属性（如发送日期和接收日期）或文档属性（如文件名或上次更改文档的日期）。 可以使用采用布尔运算符的更复杂查询，例如 **AND**、**OR**、**NOT** 和 **NEAR**。 如果将关键字框留空，则指定内容位置中的所有内容都将包括在搜索结果中。 有关详细信息，请参阅关键字 [查询和电子数据展示的搜索条件](keyword-queries-and-search-conditions.md)。

   2. 或者，可以单击“**显示关键字列表**”复选框，然后在每一行键入一个关键字。 如果执行此操作，则每行上的关键字将由逻辑运算符连接 (**c:s**)，类似于所创建的搜索创建中的 **OR** 运算符功能。

      为什么使用关键字列表？ 可以获取与每个关键字匹配的项数量的统计信息。 这可以帮助你快速标识哪些关键字最有效和最无效。 还可以在行中使用关键字短语（使用括号包围）。 有关关键字列表和搜索统计信息详细信息，请参阅获取 [搜索的关键字统计信息](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches)。

      > [!NOTE]
      > 为了帮助减少由大型关键字列表导致的问题，关键字列表中最多只能有 20 行。

   3. 您可以添加搜索条件来缩小搜索范围并返回更精确的结果集。 每个条件向开始搜索时创建和运行的搜索查询添加一个子句。 可通过使用功能类似于 **AND** 运算符的逻辑运算符 (**c:c**) 在逻辑上将条件连接至关键字查询（在关键字框中指定）。 这意味着，项必须满足关键字查询和要在结果中包括的一个或多个条件。 这就是条件如何帮助缩小结果范围的原理。 有关可在搜索查询中使用的条件的列表和说明，请参阅[搜索条件](keyword-queries-and-search-conditions.md#search-conditions)。

8. 查看搜索设置 (并在必要时编辑) ，然后提交搜索以启动它。

完成搜索后，您可以预览搜索结果。 如有必要，请单击 **"搜索"** 页上的"刷新"以显示您创建的搜索。

## <a name="more-information-about-searching-content-locations"></a>有关搜索内容位置详细信息

- 单击" **选择用户、组或** 团队"以指定要搜索的邮箱时，显示的邮箱选取器为空。 这种设计旨在增强性能。 To add recipients to this list， click **Choose users， groups， or teams**， type a name (a minimum of three characters) in the search box， select the check box next to the name， and then click **Choose**.

- 您可以将非活动邮箱、Microsoft Teams、Yammer 组、Office 365 组和通讯组添加到要搜索的邮箱列表中。 不支持动态通讯组。 如果添加Microsoft Teams组Yammer组或Office 365组，将搜索组或团队邮箱;不搜索其成员的邮箱。

- 若要将网站添加到搜索，请打开切换，然后单击选择 **网站**。 键入要搜索的每个网站的 URL。 还可以为 Microsoft 团队、SharePoint组或 Office 365 组添加 Yammer URL。
