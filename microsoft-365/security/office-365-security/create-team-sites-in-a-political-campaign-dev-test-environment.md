---
title: 创建团队网站 - 政治宣传活动开发/测试环境
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/21/2018
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
localization_priority: Priority
search.appverid:
- MET150
ms.custom: seo-marvel-apr2020
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 摘要：在政治宣传活动开发/测试环境中创建公共、专用、敏感和高度机密的 SharePoint Online 团队网站。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 80c975cd181f326fc2766c6ebfbd0d7f8a5164f2
ms.sourcegitcommit: ebb1c3b4d94058a58344317beb9475c8a2eae9a7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "53108147"
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>在政治宣传活动开发/测试环境中创建团队网站

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**适用对象**

- [适用于 Office 365 计划 2 的 Microsoft Defender](defender-for-office-365.md)

 **摘要：** 在政治宣传活动开发/测试环境中创建公共、专用、敏感和高度机密的 SharePoint Online 团队网站。

使用本文中的说明，这对 [Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解决方案，创建包含四个不同类型的 SharePoint Online 团队网站的开发/测试环境。在标题为 **SharePoint 和 OneDrive for Business** 的主题 10 详细介绍了这些网站。

## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>第 1 阶段：创建政治宣传活动开发/测试环境

首先，按照[为政治宣传运动开发/测试环境配置组和用户](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)中的说明，创建订阅、用户和组。

## <a name="phase-2-create-labels"></a>第 2 阶段：创建标签

此阶段将针对 SharePoint Online 团队网站文档文件夹的不同安全级别创建标签。

1. 如有需要，请使用试用订阅的全局管理员帐户凭据登录 Microsoft 365 管理中心（<https://admin.microsoft.com>）。如需帮助，请参阅[在何处登录 Microsoft 365](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)。

2. 在开始操作的 **主页** 页面中，单击“**全部显示**”。 在显示的 **管理中心** 部分中，单击“**合规性**”。

3. 在 Microsoft 365 合规中心的 **主页** 页面上，转到“**解决方案**”部分 \>“**信息保护**”。 要直接转到“**信息保护**”页面，请使用 <https://compliance.microsoft.com//informationprotection>。

4. 在“**信息保护**”页上，验证是否已选择“**标签**”标记，然后单击“![创建标签图标](../../media/m365-cc-sc-create-icon.png)”“**创建标签**”。

5. 将打开 **新敏感度标签** 向导。 在 **名称和说明** 步骤中，输入以下值：
   - **名称**：类型 **内部**。
   - **显示名称**
   - **面向用户的说明**

   完成后，单击“**下一步**”。

6. 在“标签设置”窗格中，单击“下一步”。

7. 在“查看设置”窗格中，单击“创建此标签”，然后单击“关闭”。

8. 对以下标签重复步骤 5-8：

   - Private
   - 敏感
   - 高度机密

9. 在“开始”>“标签”窗格中，单击“发布标签”。

10. 在“选择要发布的标签”窗格中，单击“选择要发布的标签”。

11. 在“选择标签”窗格中，单击“添加”并选择全部四个标签。

12. 单击“完成”。

13. 在“选择要发布的标签”窗格中，单击“下一步”。

14. 在“选择位置”窗格中，单击“下一步”。

15. 在“命名策略”窗格中，在“名称”中键入 **Campaign**，然后单击“下一步”。

16. 在“查看设置”窗格中，单击“发布标签”，然后单击“关闭”。

## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>第 3 阶段：创建 SharePoint Online 团队网站

在此阶段中，你可以为与四种类型的 SharePoint Online 团队网站相对应的政治宣传活动创建和配置 SharePoint Online 团队网站。

### <a name="campaign-wide-team-site"></a>宣传活动范围团队网站

要创建基线公共 SharePoint Online 团队网站，请执行以下操作：

1. 如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录管理中心 (<https://admin.microsoft.com>)。

2. 在磁贴列表中，单击“SharePoint”。

3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。

4. 在“创建网站”页中，单击“团队网站”。

5. 在“网站名称”中，键入 **Campaign wide**。

6. 在“团队网站描述”中，键入 **SharePoint site for the entire campaign**。

7. 在“隐私设置”中，选择“公用 - 组织中的任何人均可访问此网站”，然后单击“下一步”。

8. 在“希望添加哪些人员?”窗格中，单击“完成”。

接下来，针对内部标签配置宣传活动范围团队网站的文档文件夹。

1. 在浏览器的“宣传活动范围 - 主页”标签页中，单击“文档”。

2. 单击设置图标，然后单击“库设置”。

3. 在“权限和管理”下，单击“向此库中的项应用标签”。

4. 在“设置-应用标签”中，选择“内部”，然后单击“保存”。

### <a name="campaign-project-1-team-site"></a>宣传活动项目 1 团队网站

要为宣传活动内的项目创建基线专用 SharePoint Online 团队网站，请执行以下操作：

1. 如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录管理中心 (<https://admin.microsoft.com>)。

2. 在磁贴列表中，单击“SharePoint”。

3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。

4. 在“创建网站”页中，单击“团队网站”。

5. 在“网站名称”中，键入 **Campaign project 1**。

6. 在“团队网站描述”中，键入 **SharePoint site for Campaign project 1**。

7. 在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”。

8. 在“希望添加哪些人员?”窗格中，单击“完成”。

接下来，针对专用标签配置宣传活动项目 1 团队网站的文档文件夹。

1. 在浏览器的“宣传活动项目 1 - 主页”标签页中，单击“文档”。

2. 单击设置图标，然后单击“库设置”。

3. 在“权限和管理”下，单击“向此库中的项应用标签”。

4. 在“设置-应用标签”中，选择“专用”，然后单击“保存”。

### <a name="campaign-marketing-team-site"></a>宣传活动营销团队网站

要为宣传活动营销资源创建敏感级别的独立 SharePoint Online 团队网站，请执行以下操作：

1. 请使用本地计算机上的浏览器，并使用全局管理员帐户登录管理中心 (<https://admin.microsoft.com>)。

2. 在磁贴列表中，单击“SharePoint”。

3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。

4. 在“创建网站”页中，单击“团队网站”。

5. 在“团队网站名称”中，键入 **Campaign marketing**。

6. 在“团队网站描述”中，键入 **SharePoint site for campaign marketing (sensitive)**。

7. 在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”。

8. 在“希望添加哪些人员?”窗格中，单击“完成”。

9. 在浏览器上的新“宣传活动营销”标签页上，依次单击工具栏中的设置图标和“网站权限”。。

10. 在“网站权限”窗格中，单击“高级权限设置”。

11. 在浏览器的新“权限”标签页中，单击“访问请求设置”。

12. 在“**访问请求设置**”对话框中，清楚“**允许成员共享网站和单独的文件和文件夹**”和“**允许成员邀请他人到网站成员组**”复选框，请在“**发送所有访问请求**”中键入 **ITAdmin1@**\<your organization name\>**.onmicrosoft.com**，然后单击“**确定**”。

13. 单击列表中的“宣传活动营销成员”。

14. 在“人员和组”页中，单击“新建”。

15. 在“共享”对话框中，键入并选择 **Senior and strategic staff**，然后单击“共享”。

16. 为“分析人员”组和 Regular1 用户帐户重复步骤 14 和 15。

17. 单击浏览器上的后退按钮。

18. 单击列表中的“宣传活动营销所有者”。

19. 在“人员和组”页中，单击“新建”。

20. 在“共享”对话框中，键入并选择“IT staff”，然后单击“共享”。

21. 单击浏览器上的后退按钮。

22. 关闭浏览器上的“人员和组”标签页，单击浏览器上的“宣传活动营销-主页”标签页，然后关闭“网站权限”窗格。。

权限的配置结果如下所示：

- **宣传活动营销-成员** SharePoint 组仅包含“高级和策略人员”组（其中包含 Candidate、ChiefOfStaff 和 Strategic1 用户帐户）； **宣传活动营销** 组（其中包含全局管理员用户帐户）、**分析人员** 组（其中包含 DataScientist1 用户帐户）和 **Regular1** 用户帐户。

- **宣传活动营销-所有者** SharePoint 组仅包含“IT staff”组（其中仅包含 ITAdmin1 和 ITAdmin2 用户帐户）。

- **宣传活动营销-访问者** SharePoint 组不包含任何组或用户帐户。

- 成员不能修改网站级权限（此设置只能由“宣传活动营销-所有者”组的成员执行）。

- 其他用户帐户无法访问网站或其资源，但可以请求访问网站，将向 ITAdmin1 用户帐户邮箱发送电子邮件。

接下来，针对敏感标签配置宣传活动营销团队网站的文档文件夹。

1. 在浏览器的“宣传活动营销 - 主页”标签页中，单击“文档”。

2. 单击设置图标，然后单击“库设置”。

3. 在“权限和管理”下，单击“向此库中的项应用标签”。

4. 在“设置-应用标签”中，选择“敏感”，然后单击“保存”。

接下来，配置数据丢失防护 (DLP) 策略，以便用户在组织外共享关于含敏感标签的 SharePoint Online 团队网站的文档时进行通知。此 DLP 策略将应用于宣传活动营销网站中的资源。

1. 在浏览器的“Microsoft Office 主页”标签页中，单击“安全性与符合性”磁贴。

2. 在浏览器的新“安全性与符合性”标签页中，单击“数据丢失防护”>“策略”。

3. 在“数据丢失防护”窗格中，单击“+ 创建策略”。

4. 在“从模板开始或创建自定义策略”窗格中，单击“自定义”，然后单击“下一步”。

5. 在“命名策略”窗格中，在“名称”中键入 **Sensitive label SharePoint Online team sites**，然后单击“下一步”。

6. 在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”。

7. 在位置列表中，禁用“Exchange 电子邮件”和“OneDrive 帐户位置”，然后单击“下一步”。

8. 在“自定义要保护的敏感信息类型”窗格中，单击“编辑”。

9. 在“选择要保护的内容类型”窗格中，单击下拉框中的“添加”，然后单击“标签”。

10. 在“标签”窗格中，单击“+ 添加”，选择“敏感”标签，然后依次单击“添加”和“完成”。

11. 在“选择要保护的内容类型”窗格中，单击“保存”。

12. 在“自定义要保护的敏感信息类型”窗格中，单击“下一步”。

13. 在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”。

14. 在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”。

15. 在文本框中，键入或粘贴以下内容：

    - 要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。

16. 单击“确定”。

17. 在“如果检测到敏感信息，希望采取什么操作?”窗格中，取消勾选“阻止共享并将访问限于共享内容”复选框，然后单击“下一步”。

18. 在“是否希望立即启用策略或先进行测试?”窗格中，单击“是，立即启用”，然后单击“下一步”。

19. 在“查看设置”窗格中，单击“创建”，然后单击“关闭”。

### <a name="campaign-strategy-team-site"></a>宣传活动策略团队网站

若要针对宣传活动策略资源创建高度机密级别的独立 SharePoint Online 团队网站，请执行以下操作：

1. 如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录管理中心 (<https://admin.microsoft.com>)。

2. 在磁贴列表中，单击“SharePoint”。

3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。

4. 在“创建网站”页中，单击“团队网站”。

5. 在“团队网站名称”中，键入 **Campaign strategy**。

6. 在“团队网站描述”中，键入 **SharePoint site for campaign strategy (highly confidential)**。

7. 在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”。

8. 在“希望添加哪些人员?”窗格中，单击“完成”。

9. 在浏览器的新“宣传活动策略”标签页中，依次单击工具栏的设置图标和“网站权限”。

10. 在“网站权限”窗格中，单击“高级权限设置”。

11. 在浏览器的新“权限”标签页中，单击“访问请求设置”。

12. 在“访问请求设置”对话框中，清除“允许成员共享网站和单独的文件和文件夹”和“允许成员邀请他人到网站成员组”（这样三个复选框全被清除），然后单击“确定”。

13. 单击列表中的“宣传活动策略成员”。

14. 在“人员和组”页中，单击“新建”。

15. 在“共享”对话框中，键入并选择 **Senior and strategic staff**，然后单击“共享”。

16. 单击列表中的“宣传活动策略所有者”。

17. 在“人员和组”页中，单击“新建”。

18. 在“共享”对话框中，键入并选择“IT staff”，然后单击“共享”。

19. 单击浏览器上的后退按钮。

20. 关闭浏览器上的“人员和组”标签页，单击浏览器上的“宣传活动策略-主页”标签页，然后关闭“网站权限”窗格。

权限的配置结果如下所示：

- **宣传活动策略-成员** SharePoint 组仅包含“高级和策略人员”组（其中仅包含 Candidate、ChiefOfStaff 和 Strategic1 用户帐户）和 **宣传活动策略** 组（其中仅包含全局管理员用户帐户）。

- **宣传活动策略-所有者** SharePoint 组仅包含“IT staff”组（其中仅包含 ITAdmin1 和 ITAdmin2 用户帐户）。

- **宣传活动策略-访问者** SharePoint 组不包含任何组或用户帐户。

- 成员不能修改网站级别权限（仅“宣传活动策略-所有者”组的成员才可进行修改）。

- 其他用户帐户无法访问网站或其资源，也无法请求访问网站。网站的其他权限必须由全局管理员或“活动策略-所有者”组的成员履行。

接下来，针对高度机密标签配置宣传活动策略团队网站的文档文件夹。

1. 在浏览器的“宣传活动策略-主页”标签页中，单击“文档”。

2. 单击设置图标，然后单击“库设置”。

3. 在“权限和管理”下，单击“向此库中的项应用标签”。

4. 在“设置-应用标签”中，选择“高度机密”，然后单击“保存”。

接下来，配置 DLP 策略，以便阻止用户在组织外共享关于含高度机密标签的 SharePoint Online 团队网站的文档。此 DLP 策略将应用于宣传活动策略网站中的资源。

1. 如果需要，请使用本地计算机上的浏览器，以及使用具有安全管理员或公司管理员角色的帐户登录管理中心 (<https://admin.microsoft.com>)。

2. 在浏览器的“Microsoft Office 主页”标签页中，单击“安全性与符合性”磁贴。

3. 在浏览器的新“安全性与符合性”标签页中，单击“数据丢失防护”>“策略”。

4. 在“数据丢失防护”窗格中，单击“+ 创建策略”。

5. 在“从模板开始或创建自定义策略”窗格中，单击“自定义”，然后单击“下一步”。

6. 在“命名策略”窗格中，在“名称”中键入 **Highly Confidential label SharePoint Online team sites**，然后单击“下一步”。

7. 在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”。

8. 在位置列表中，禁用“Exchange 电子邮件”和“OneDrive 帐户位置”，然后单击“下一步”。

9. 在“自定义要保护的敏感信息类型”窗格中，单击“编辑”。

10. 在“选择要保护的内容类型”窗格中，单击下拉框中的“添加”，然后单击“标签”。

11. 在“标签”窗格中，单击“+ 添加”，选择“高度机密”标签，然后依次单击“添加”和“完成”。

12. 在“选择要保护的内容类型”窗格中，单击“保存”。

13. 在“自定义要保护的敏感信息类型”窗格中，单击“下一步”。

14. 在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”。

15. 在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”。

16. 在文本框中，键入或粘贴以下内容：

    - 要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。

17. 单击“确定”。

18. 在“如果检测到敏感信息，希望采取什么操作?”窗格中，选择“需要业务理由进行重写”，然后单击“下一步”。

19. 在“是否希望立即启用策略或先进行测试?”窗格中，单击“是，立即启用”，然后单击“下一步”。

20. 在“**查看设置**”窗格中，单击“**创建**”，然后单击“**关闭**”。

请按照[使用 Microsoft 365 管理中心激活 Azure RMS](/information-protection/deploy-use/activate-office365) 中的说明执行操作。

接下来，通过执行以下步骤，使用新作用域内策略以及保护和权限的子标签来配置 Azure 信息保护：

1. 使用具有安全管理员或公司管理员角色的帐户登录到管理中心。有关帮助信息，请参阅 [在何处登录 Office 365](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)。

2. 在浏览器的单独选项卡中，转到 Azure 门户 (<https://portal.azure.com>)。

3. 在搜索窗格中，键入“**信息**”，然后单击“**Azure 信息保护**”。

4. 单击“**标签**”。

5. 右键单击“高度机密”标签，然后单击“添加子标签”。

6. 在“名称”中键入“CampaignStrategy”，并在“描述”中键入“Label for documents in the Campaign strategy team site”。

7. 在“为包含此标签的文档和电子邮件设置权限”中，单击“保护”。

8. 在“保护”部分中，单击“Azure (云密钥)”。

9. 在“保护”边栏选项卡中，在“保护设置”下，单击“+ 添加权限”。

10. 在“添加权限”边栏选项卡的“指定用户和组”下，单击“+ 浏览目录”。

11. 在“AAD 用户和组”窗格中，选择“高级和策略人员”，然后单击“选择”。

12. 在“从预设或设置自定义中选择权限”下，单击“自定义”，然后依次单击“查看权限”、“编辑内容”、“保存”、“答复”和“全部答复”复选框。

13. 单击“**确定**”两次。

14. 在“**子标签**”边栏选项卡上，单击“**保存**”，然后单击“**确定**”。

15. 在“Azure 信息保护”边栏选项卡上，单击“策略”>“+ 添加新策略”。

16. 在“名称”中键入“CampaignStrategy”，并在“描述”中键入“Documents in the Campaign strategy team site”。

17. 单击“选择获取此策略的用户或组”>“用户/组”，然后选择“高层和策略人员”。

18. 单击“**选择”\>“确定**”。

19. 单击“添加或删除标签”。在“策略: 添加或删除标签”窗格中，单击“CampaignStrategy”，然后单击“确定”。

20. 单击“保存”，然后单击“确定”。

现在，可以在这四个网站中创建文档，并使用各种用户帐户进行访问测试。

若要使用 Azure 信息保护和新标签保护文档，必须在测试计算机上 [安装 Azure 信息保护客户端](/information-protection/rms-client/install-client-app)，从管理中心安装 Office，然后使用试用订阅的“**高级和策略人员**”组中的帐户从 Microsoft Word 登录。

## <a name="see-also"></a>另请参阅

[Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)

[为政治宣传活动开发/测试环境配置组和用户](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)

[云采用测试实验室指南 (TLG)](../../enterprise/cloud-adoption-test-lab-guides-tlgs.md)

[Microsoft 365 解决方案和体系结构中心](../../solutions/index.yml)
