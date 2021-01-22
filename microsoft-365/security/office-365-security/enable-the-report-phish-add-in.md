---
title: 启用报告钓鱼加载项
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: 了解如何为单个用户或整个组织启用 Outlook 和 Web 上的 Outlook 报告网络钓鱼外接程序。
ms.openlocfilehash: 2ea6a9bf9b00fc844aede6daeb9fc11f23c81e4a
ms.sourcegitcommit: cc354fd54400be0ff0401f60bbe68ed975b69cda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "49865257"
---
# <a name="enable-the-report-phishing-add-in"></a>启用报告网络钓鱼外接程序

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!NOTE]
> 如果你是具有 Exchange Online 邮箱的 Microsoft 365 组织的管理员，我们建议你使用安全与合规中心&门户。 有关详细信息，请参阅"使用管理员提交"将可疑的垃圾邮件、网络钓鱼[、URL 和文件提交到 Microsoft。](admin-submission.md)

Outlook 和 Web 上的 Outlook 的"报告邮件"和"报告钓鱼"外接程序 (以前称为 Outlook Web App) ，使用户能够轻松地将标记为错误) 或漏报的 (错误电子邮件报告给 Microsoft 及其关联公司 (允许) 进行分析。

Microsoft 使用这些提交来提高电子邮件保护技术的有效性。 例如，假设用户使用报告网络钓鱼外接程序报告许多邮件。 此信息在安全仪表板 [和其他](security-dashboard.md) 报告中显示。 组织的安全团队可以使用此信息来指示可能需要更新防钓鱼策略。

可以安装"报告邮件"或"报告钓鱼"加载项。 如果希望用户同时报告垃圾邮件和网络钓鱼邮件，请在你的组织中部署报告邮件外接程序。 有关详细信息，请参阅 ["启用报告邮件"加载项](enable-the-report-message-add-in.md)。

报告网络钓鱼外接程序提供仅报告网络钓鱼邮件的选项。 管理员可以为组织启用报告网络钓鱼外接程序，并且单个用户可以自行安装它。

如果您是单个用户，您可以为自己启用报告网络钓鱼 [外接程序](#get-the-report-phishing-add-in-for-yourself)。

如果您是全局管理员或 Exchange Online 管理员，并且 Exchange 配置为使用 OAuth 身份验证，您可以为组织启用报告网络钓鱼 [外接程序](#get-and-enable-the-report-phishing-add-in-for-your-organization)。 报告网络钓鱼Add-In现在可以通过集中 [部署获得](https://docs.microsoft.com/microsoft-365/admin/manage/centralized-deployment-of-add-ins)。

## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

- 报告网络钓鱼外接程序适用于大多数 Microsoft 365 订阅和以下产品：

  - Outlook 网页版
  - Outlook 2013 SP1 或更高版本
  - Outlook 2016 for Mac
  - Microsoft 365 企业应用版中包含的 Outlook

- 报告网络钓鱼外接程序对内部部署 Exchange 组织的邮箱不可用。

- 可以将报告的邮件配置为复制或重定向到指定的邮箱。 有关详细信息，请参阅用户 [提交策略](user-submission.md)。

- 现有的 Web 浏览器应该与报告网络钓鱼外接程序一起使用。 但是，如果发现加载项不可用或无法正常使用，请尝试其他浏览器。

- 对于组织安装，组织需要配置为使用 OAuth 身份验证。 有关详细信息，请参阅"确定加载项集中部署[是否适用于你的组织"。](../../admin/manage/centralized-deployment-of-add-ins.md)

- 管理员需是全局管理员角色组的成员。 有关详细信息，请参阅[安全与合规中心中的权限](permissions-in-the-security-and-compliance-center.md)。

## <a name="get-the-report-phishing-add-in-for-yourself"></a>为自己获取报告网络钓鱼外接程序

1. 转到 Microsoft AppSource， <https://appsource.microsoft.com/marketplace/apps> 然后搜索"报告钓鱼"加载项。

2. 单击 **"立即获取"。**

3. 在出现的对话框中，查看使用条款和隐私策略，然后单击"继续 **"。**

4. 使用工作或学校帐户登录 (商业) 或 Microsoft 帐户 (个人使用) 。

安装并启用加载项后，你将看到以下图标：

- 在 Outlook 中，图标如下所示：

  ![Outlook 的"报告钓鱼外接程序"图标](../../media/Outlook-ReportPhishing.png)

- 在 Outlook 网页 Outlook 中，图标如下所示：

  ![Outlook 网页报告网络钓鱼外接程序图标](../../media/OWA-ReportPhishing.png)

## <a name="get-and-enable-the-report-phishing-add-in-for-your-organization"></a>获取并启用组织的"报告钓鱼"加载项

> [!NOTE]
> 外接程序最多可能需要 12 小时才能显示在组织中。

1. 在 Microsoft 365 管理中心中，转到"设置"、"**集成&加载项**"页面，然后单击"部署 <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> **外接程序"。**

   ![Microsoft 365 管理中心中的"服务和加载项"页](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. 在 **出现的"部署新的外接程序"** 飞出中，查看信息，然后单击"下一 **步"。**

3. 下一页上，单击 **"从应用商店中选择"。**

   ![部署新外接程序页面](../../media/NewAddInScreen2.png)

4. 在 **出现的"选择外接程序"** 页中，在"搜索"框中单击，输入"报告钓鱼"，然后单击 **"搜索搜索"** ![ 图标 ](../../media/search-icon.png) 。 在结果列表中，找到 **"报告钓鱼"，** 然后单击"添加 **"。**

5. 在出现的对话框中，查看许可和隐私信息，然后单击"继续 **"。**

6. 在 **出现的"配置外接程序"** 页中，配置以下设置：

   - **已分配用户**：选择下列值之一：

     - **每个** (默认) 
     - **特定用户/组**
     - **就我自己**

   - **部署方法**：选择下列值之一：

     - **修复 (默认) ：** 外接程序会自动部署到指定用户，并且他们无法删除它。
     - **可用**：用户可以在家庭获取外接程序管理员管理的 \>  \> **安装外接程序**。
     - **可选**：加载项会自动部署到指定用户，但他们可以选择将其删除。

   完成后，单击"部署 **"。**

7. 在 **出现的"部署报告** 钓鱼"页中，你将看到一个进度报告，后跟加载项已部署的确认。 阅读信息后，单击"下一 **步"。**

8. 在出现的 **"宣布外接程序"** 页上，查看信息，然后单击"关闭 **"。**

## <a name="learn-how-to-use-the-report-phishing-add-in"></a>了解如何使用报告网络钓鱼外接程序

分配了外接程序的人将看到以下图标：

- 在 Outlook 中，图标如下所示：

  ![Outlook 的"报告钓鱼外接程序"图标](../../media/Outlook-ReportPhishing.png)

- 在 Outlook 网页 Outlook 中，图标如下所示：

  ![Outlook 网页报告钓鱼外接程序图标](../../media/OWA-ReportPhishing.png)

## <a name="review-or-edit-settings-for-the-report-phishing-add-in"></a>查看或编辑报告网络钓鱼外接程序的设置

1. 在 Microsoft 365 管理中心中，转到& **加载项** 页面 <https://admin.microsoft.com/AdminPortal/Home#/Settings/ServicesAndAddIns> 。

2. 查找并选择 **"报告钓鱼** "加载项。

3. 在 **"编辑报告钓鱼"** 飞出控件中，根据组织需要显示、查看和编辑设置。 完成后，单击“**保存**”。

## <a name="view-and-review-reported-messages"></a>查看和查看报告的邮件

若要查看用户向 Microsoft 报告的邮件，可以使用以下选项：

- 使用管理员提交门户。 有关详细信息，请参阅查看 [Microsoft 的用户提交](admin-submission.md#view-user-submissions-to-microsoft)。

- 创建邮件流规则 (传输规则) 报告的邮件副本。 有关说明， [请参阅"使用邮件流规则"查看用户向 Microsoft 报告哪些内容](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md)。