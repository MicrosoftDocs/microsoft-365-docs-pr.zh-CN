---
title: Microsoft 365管理中心中的报告 - Microsoft 365组
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: 获取Microsoft 365组报告，了解组及其活动。
ms.openlocfilehash: a013e8fd7ff555cfb1700260cb26ce83f4d07339
ms.sourcegitcommit: 8c698d1a0c41baf5f35d07b0d765b4a5ead593d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2021
ms.locfileid: "53408944"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Microsoft 365管理中心中的报告 - Microsoft 365组

"Microsoft 365 **报表**"仪表板显示组织中各产品的活动概述。 它让你能够深入研究各产品级报表，以便更细致地了解每个产品内的活动。 请查看[报表概述主题](activity-reports.md)。 在Microsoft 365组中，可以深入了解组织中组的活动，并查看创建和使用的组数。
  
> [!NOTE]
> 您必须是 Microsoft 365 中的全局管理员、全局读者或报告读取者，或者 Exchange、SharePoint、Teams Service、Teams Communications 或 Skype for Business 管理员才能查看报告。  
  
## <a name="how-to-get-to-the-groups-report"></a>如何访问组报告

1. 在管理中心，转到“**报表**”\> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用情况</a>页面。

2. 在仪表板主页上，单击活动用户- Microsoft 365 应用版 或活动用户 - Microsoft 365 服务卡上的查看更多按钮，以访问 Office 365 报告页面。
  
## <a name="interpret-the-groups-report"></a>解释组报告

You can view the activations in the Office 365 by choosing the **Groups activity** tab.

:::image type="content" alt-text="Microsoft 365报表 - Microsoft Office 365组活动。" source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

选择 **"选择要在** 报表中添加或删除列的列"。

:::image type="content" alt-text="Office 365组活动报表 - 选择列" source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

您还可以通过选择"导出"链接将报告数据导出到Excel .csv文件。  此操作可导出所有用户的数据，使你能够对数据进行简单的排序和筛选，以进一步分析数据。 如果用户数量不足 2000，则可在报表中的表格内进行排序和筛选。 如果用户数超过 2000，则需要导出数据才能进行排序和筛选。 

|跃点数|定义|
|:-----|:-----|
|组名称 |组的名称。 |
|Deleted |已删除的组数。 如果该组被删除，但在报告时间段中有活动，它将显示在网格中，并显示设置为 true 的标记。 |
|组所有者 |组所有者的名称。 |
|上次活动日期 (UTC)  |组收到邮件的最近日期。 - 这是电子邮件对话、电子邮件或网站中Yammer发生的最新日期。 |
|类型 |组的类型。 可以是私有组，也可以是公用组。 |
|收到的电子邮件Exchange |组接收的邮件数。|
|电子邮件总数Exchange ()  |组邮箱中的项目总数。 |
|用于存储 EXCHANGE (MB)  |组邮箱使用的存储。 |
|SharePoint文件 (总数)  |组网站中存储SharePoint的数量。 |
|SharePoint活动 (文件)  |报告期间对 SharePoint 组网站中 (查看或修改、同步、在内部或外部共享) 文件数。 |
|用于存储的站点总SharePoint (MB)  |报告期间使用的存储量（以 MB 为单位）。 |
|邮件Yammer (中)  |报告期间在报告组中Yammer的邮件数。 |
|邮件Yammer (阅读)  |报告期间在报告Yammer组中读取的对话数。 |
|邮件Yammer (中)  |报告期间"组"Yammer的消息数。 |
|成员 |组中成员的数量。 |
|外部成员 |组中外部用户的数量。|


## <a name="related-content"></a>相关内容

[Microsoft 365管理中心中的报表 (](activity-reports.md)文章) \
[安全与合规中心&报告](../../compliance/reports-in-security-and-compliance.md) (文章) \
[Microsoft 365中心中的报表 - 活动](../../admin/activity-reports/active-users-ww.md)用户 (文章) 

