---
title: Microsoft 365管理中心中的报告 - 电子邮件应用使用情况
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: 了解如何获取电子邮件应用使用情况报告，以了解连接到 Exchange Online 的电子邮件Outlook用户使用的版本。
ms.openlocfilehash: f2a7b79a00b47896dac4427c532f85dccb931c60
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921921"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365管理中心中的报告 - 电子邮件应用使用情况

"Microsoft 365 **报表**"仪表板显示组织中各产品的活动概述。 它让你能够深入研究各产品级报表，以便更细致地了解每个产品内的活动。 请查看[报表概述主题](activity-reports.md)。 在电子邮件应用使用情况报告中，你可以看到连接到电子邮件应用Exchange Online。 还可以查看用户当前使用的 Outlook 应用的版本信息，这样便可跟进使用不受支持的版本安装支持版本的 Outlook 的用户。
  
> [!NOTE]
> 您必须是 Microsoft 365 中的全局管理员、全局读者或报告读取者，或者 Exchange、SharePoint、Teams Service、Teams Communications 或 Skype for Business 管理员才能查看报告。  
 
## <a name="how-to-get-to-the-email-apps-report"></a>如何获取电子邮件应用报告

1. 在管理中心，转到“**报表**”\> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用情况</a>页面。
2. 选择 **"电子邮件活动"** 下的"**查看更多"。** 
3. From the **Email activity** drop-down list， select **Exchange** Email \> **apps usage**.
  
## <a name="interpret-the-email-apps-report"></a>解释电子邮件应用报告

可以通过查看"用户"和"客户端"图表了解电子邮件 **应用** 活动。  
  
![使用的电子邮件客户端](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|项目|说明|
|:-----|:-----|
|1.  <br/> |可查看 **电子邮件应用** 使用情况报告，了解过去 7 天、30 天、90 天或 180 天的趋势。 但是，如果您选择报告中的特定日期，则表 (7) 将显示自当前日期起最多 28 天的数据 (而不是报告生成日期) 。  <br/> |
|2.  <br/> |每个报告中的数据通常涵盖过去 24 至 48 小时的数据。  <br/> |
|3.  <br/> |" **用户**"视图显示使用任意电子邮件应用连接到 Exchange Online 的独特用户数。  <br/> |
|4.  <br/> |" **应用**"视图显示选定时间段内各应用的不同用户数。  <br/> |
|5.  <br/> |"**版本"** 视图显示当前版本中每个版本版本Outlook用户Windows。  <br/> |
|6.  <br/> | 在" **用户**"图表中，Y 轴表示在报告时段内的任意一天连接到应用的独特用户总数。  <br/>  在" **用户**"图表中，X 轴表示在报告时段内使用应用的独特用户数。  <br/>  在" **应用**"图表中，Y 轴表示在报告时段内使用特定应用的不同用户总数。  <br/>  在" **应用**"图表中，X 轴表示所在组织使用的应用列表。  <br/>  在" **版本**"图表中，Y 轴表示使用特定版本的 Outlook 桌面应用的独特用户总数。 如果报告无法解析该版本号Outlook，数量将显示为 **"不确定"。**  <br/>  在" **版本**"图表中，X 轴表示所在组织使用的应用列表。  <br/> |
|7.  <br/> |通过选择图例中的项目，可以筛选在图表上看到的系列。  <br/> |
|8.  <br/> | 添加所有项之后，才能在下表的列中看到这些项。<br/> **Username** 是电子邮件应用所有者的名称。  <br/> **上次活动** 日期是用户阅读或发送电子邮件的最近日期。  <br/> " **Mac 邮件**"、" **Mac Outlook**"、" **Outlook**"、" **Outlook 移动版**"、" **Outlook 网页版**"是所在组织可能使用的电子邮件应用示例。  <br/>  如果组织的策略阻止你查看显示了可识别用户信息的报表，可更改所有这些报表的隐私设置。 请查看管理中心的活动报告中的如何隐藏用户 **级别详细信息Microsoft 365**[部分](activity-reports.md)。  <br/> |
|9.  <br/> |选择 **"选择要在** 报表中添加或删除列的列"。  <br/> ![电子邮件应用使用情况报告 - 选择列](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |您还可以通过选择"导出"链接将报告数据导出到Excel .csv文件。  此操作可导出所有用户的数据，使你能够对数据进行简单的排序和筛选，以进一步分析数据。 如果用户数量不足 2000，则可在报表中的表格内进行排序和筛选。 如果用户数超过 2000，则需要导出数据才能进行排序和筛选。  <br/> |
|||
   
