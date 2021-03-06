---
title: PerformancePoint Server 2007 停止提供支持路线图
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: PerformancePoint Server 2007、ProClarity 和 SharePoint Server 2007 已终止支持。 阅读本文有助于规划 BI 解决方案升级。
ms.openlocfilehash: aa6adae24d78b6be72f17fd56c272b1293e6fcdc
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927332"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>PerformancePoint Server 2007 停止提供支持路线图

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

Office 2007 服务器和应用程序已终止支持，包括可能用作 商业智能 (BI 解决方案一) 的服务器和应用程序。 下表列出了受影响的 BI 应用程序：
  
|**Microsoft BI 应用程序**|**结束日期支持**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 Service Pack 3  <br/> ProClarity Desktop Professional 6.3  <br/> ProClarity SharePoint Viewer 6.3  <br/> |2017 年 7 月 11 日  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |2017 年 10 月 10 日  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |2018 年 1 月 9 日  <br/> |
   
有关详细信息，请参阅帮助您从 [Office 2007 服务器和客户端升级的资源](upgrade-from-office-2007-servers-and-products.md)。
  
## <a name="what-does-end-of-support-mean"></a>停止 *提供支持意味着什么* ？

与大多数 Microsoft 产品一样，PerformancePoint Server 2007 SP3、ProClarity 软件和 SharePoint Server 2007 SP3 具有支持生命周期，在此期间 Microsoft 提供新功能、Bug 修复和安全更新。 产品的生命周期通常自产品初始发布起持续 10 年。 该生命周期的结束称为产品停止提供支持。 由于 ProClarity、PerformancePoint Server 和 SharePoint Server 2007 已终止支持，因此 Microsoft 不再提供：
  
- 针对可能会出现的问题的技术支持。
    
- 发现并可能会影响服务器稳定性和可用性的问题的错误修复。
    
- 已发现并且可能导致服务器或应用程序易受安全漏洞攻击的漏洞的安全修复。
    
- 时区更新。
    
ProClarity、SharePoint Server 2007 SP3 和 PerformancePoint Server 2007 SP3 的安装将继续运行，即使支持已终止。 但是，我们强烈建议您尽快从这些应用程序迁移。
  
## <a name="what-are-my-options"></a>我的选项是什么？

自 2007 以来，Microsoft BI 应用程序进行了大量更改，并且有几个选项需要考虑，如下表所示。
  
|**如果你使用的是此 ...**|**浏览这些选项...**|**请记住这一点...**|
|:-----|:-----|:-----|
| PerformancePoint Server 2007 监控 &amp; 分析功能，包括：<br/>- PerformancePoint Monitoring Server <br/>- PerformancePoint 仪表板设计器<br/>- 用于SharePoint Services (PerformancePoint 仪表板、记分卡和报表的仪表板查看器) <br/> |**Excel 在浏览器中与 Excel** (位于云或本地) 。 有关概述，请参阅 [Excel 和 Microsoft 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx)中的 BI 功能。<br/><br/> **Power BI** (云或本地部署) 。 有关概述，请参阅 [什么是 Power BI？](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (本地) 。 有关概述，请参阅 [SQL Server Reporting Services (SSRS) ：](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports)创建、部署和管理移动和分页报告。 <br/><br/> **PerformancePoint Services (** 本地) 。 有关概述，请参阅 [What's new for PerformancePoint Services (SharePoint Server 2010) ](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14))。 <br/> |Excel 作为基于云的 (或本地解决方案) 联机部署。 Excel 可以满足许多报告和仪表板需求。  <br/><br/> Power BI 作为联机或本地解决方案提供。 Power BI 不包含在 Microsoft 365 中。 但你可以开始使用 Power BI 免费。 稍后，根据数据使用情况和业务需求，可以使用 Microsoft 365 E5 升级到 Power BI Pro。<br/> <br/> Reporting Services 和 PerformancePoint Services 都是本地解决方案。 <br/><br/> PerformancePoint Services SharePoint Server 2010、SharePoint Server 2013 和 SharePoint Server 2016 中提供。 <br/> <br/> Excel、Power BI、Reporting Services 或 PerformancePoint Services 中提供 2007 年 2 月PerformancePoint Server功能和报表PerformancePoint Services。 查看可用功能以确定最适合业务需求的解决方案。 <br/> |
| ProClarity 软件，包括：<br/>- ProClarity Desktop Professional<br/> - ProClarity Analytics Server<br/>- ProClarity SharePoint Viewer<br/> |**与 Microsoft 合作伙伴合作** ，以确定最能满足你需求的解决方案。 请访问 [Microsoft 合作伙伴中心](https://go.microsoft.com/fwlink/?linkid=841249)。 <br/><br/> 还可以考虑在浏览器、Power BI、SQL Server Reporting Services 或 PerformancePoint Services 中将 Excel 与 Excel 一PerformancePoint Services。  <br/> |ProClarity 软件的几个（但不是全部）功能在其他 Microsoft 产品/服务中可用，包括 Excel、Power BI、Reporting Services 和 PerformancePoint Services。  <br/> |
|SharePoint Server 2007 KPI (也称为 MOSS KPI)   <br/> |**Excel Excel Services**。 有关概述，请参阅[Business intelligence in Excel and Excel Services (SharePoint Server 2013) 。 ](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |使用 SharePoint Server 2007 创建的 MOSS KPI 可用于 SharePoint Server 2010、SharePoint Server 2013 和 SharePoint Server 2016。 但无法创建新的 MOSS KPI。  <br/> |
|Excel 2007  <br/> |**Excel** (云或本地部署) 。 有关概述，请参阅 [Excel 和 Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx)中的 BI 功能。 <br/><br/> **Power BI** (云或本地部署) 。 有关概述，请参阅 [什么是 Power BI？](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Excel 和 Power BI 都为组织提供基于云的和本地解决方案，并支持各种数据源。  <br/> |
   
### <a name="help-selecting-a-solution"></a>帮助选择解决方案

由于可用的 BI 选项太多，确定哪个选项最好似乎难以确定。 我们提供了一个在线指南来提供帮助。 请参阅 [选择 Microsoft 商业智能 (BI) 工具进行分析和报告](/sql/reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting)。
  
### <a name="what-if-i-dont-upgrade-now"></a>如果现在不升级，该做什么？

可以选择不立即升级。 现有服务器和应用程序将继续运行。 但是，你将不会收到任何进一步的更新，包括安全更新，因为支持已结束。 如果服务器应用程序出现问题，你将无法从 Microsoft 技术支持获得帮助。
  
## <a name="how-do-i-plan-my-upgrade"></a>如何规划升级？

浏览升级选项后，下一步是准备升级计划。 以下各节包含信息和其他帮助资源。 你有四个主要选项，包括两个同时在云或本地工作的选项，以及两个仅本地选项：
  
|**选项**|**在云中还是本地？**|
|:-----|:-----|
|[Excel 与 SharePoint Server (本地) ](#excel-with-sharepoint-server-on-premises) <br/> |两者都有  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises)<br/> |两者都有  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |仅本地  <br/> |
|[PerformancePoint 服务](#use-performancepoint-services-on-premises) <br/> |仅本地  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>在 (或本地部署中使用 Excel) 

使用 Excel（在 SharePoint  Server 中也称为 Excel Services 应用程序）可以在浏览器窗口中查看和使用工作簿，即使计算机上未安装 Excel。 可以使用 Excel 创建报表、记分卡和仪表板。 然后，与其他人共享工作簿，无论他们是使用 SharePoint Online 作为 Microsoft 365 的一部分，还是本地 SharePoint Server，这些人员都可以在浏览器中使用 Excel。 可以使用本地或云中存储的数据，这使您能够使用各种数据源。
  
下表对将 Excel 与 Microsoft 365 与将 Excel 与 SharePoint Server 一同使用的主要优势进行比较。 详细信息如下所示。
  
|**Excel 与 Microsoft 365 (云解决方案)**|**Excel 与 SharePoint Server (本地)**|
|:-----|:-----|
|**获取最新、最出色的 Excel 版本**。 使用 Microsoft 365，可获取最新版本的 Excel，其中包括功能强大的新图表类型、快速而轻松地创建图表和表格的能力，以及支持更多数据源。 <br/> <br/> **安装程序要简单得多**。 Excel 包含在 Microsoft 365 商业版中，因此你无需繁重工作。 注册和登录，与升级本地服务器时一样，启动和运行速度更快且更高效。 <br/> <br/> **人们可以任何地方访问其工作簿**。 用户可以使用计算机、智能手机和平板电脑从他们身在何处安全地查看工作簿。 <br/> <br/> **更多功能！** 请参阅 [Excel 和 Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx)中的 BI 功能。 <br/> |**管理全局设置**。 作为 SharePoint 管理员，您可以指定全局设置，如安全性、负载平衡、会话管理、工作簿缓存和外部数据连接。 <br/> <br/> **可以将 Excel Services 与 PerformancePoint Services 一PerformancePoint Services。** 可以在 SharePoint Server Excel Services配置 PerformancePoint Services 和 Excel Services，并包括 PerformancePoint 仪表板中的报表。 <br/> <br/> **更多功能！** 请参阅[Excel 和 SharePoint Server 2013 Excel Services (中的商业) 。 ](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |
   
#### <a name="excel-with-microsoft-365-in-the-cloud"></a>云解决方案中的 Excel (Microsoft 365) 

如果你移动到 Microsoft 365，你将拥有最新的服务和应用程序，包括 Excel 2016。 PerformancePoint Services Microsoft 365 中不可用，因此将用 Excel 工作簿或其他报表替换 PerformancePoint 仪表板内容。 好消息是，Excel 2016 具有许多新的图表类型，在 Excel 中创建仪表板比以往更加简单。 并且会定期添加新功能。 若要了解更多信息， [请参阅 Excel 2016 for Windows 中的新增功能](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx)。
  
此外，如果你购买了 50 个席位或购买 50 个席位或购买更多 Microsoft 365，Microsoft FastTrack 团队可以帮助你进行设置。 若要了解更多信息，请访问 [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365)。
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel 与 SharePoint Server (本地) 

如果升级到较新版本的 SharePoint，可以将 Excel 与 Excel Services或浏览器一起使用，如下所示：
  
- SharePoint Server 2010 中的 Excel Services
    
- SharePoint Server 2013 中的 Excel Services
    
- Excel 是 Office Online Server 的一部分，与 SharePoint Server 2016 分开安装
    
您还可以在PerformancePoint Services SharePoint Server 中配置 sharePoint Server，并与 Excel 一起使用它。
  
若要了解有关 SharePoint 升级选项的详细信息，请参阅 [SharePoint Server 2007 停止提供支持路线图](sharepoint-2007-end-of-support.md)。
  
若要详细了解Excel Services，请参阅 Excel Services overview [ (SharePoint Server 2010) ](/previous-versions/office/sharepoint-server-2010/ee424405(v=office.14))。
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>在云 (本地部署中使用 Power BI) 

Power BI 是一套用于分析数据和共享见解的业务分析工具。 借助 Power BI，可以使用本地或联机数据源创建交互式报表和仪表板。 用户可以在计算机或移动设备上查看和使用报表和仪表板。
  
Power BI 不是 Microsoft 365 或 SharePoint Server 的一部分。 它是一个单独的产品/服务，包括 Power BI Desktop、Power BI 网关和 Power BI 服务。 Power BI 还与 SharePoint Online 集成。 你可以免费开始使用 Power BI。 根据数据使用情况和业务需求，稍后可以使用 Microsoft 365 E5 升级到 Power BI Pro。 若要了解更多信息，请参阅 [什么是 Power BI？](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>在本地部署 (Reporting Services) 

SQL Server Reporting Services 提供了一个可靠的报告解决方案。 可以在本机模式或 SharePoint 集成模式下配置 Reporting Services。 您可以使用几种不同的工具来创作报告，包括报表设计器、报表生成器Power View。 使用最新版本的 SQL Server，您还可以使用 SQL Server 移动报表发布服务器提供可缩放到任何屏幕大小的报表。 这允许查看者使用其移动设备上的报告。 若要了解更多信息，请参阅 [SQL Server Reporting Services (SSRS) ：](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports)创建、部署和管理移动和分页报告。
  
### <a name="use-performancepoint-services-on-premises"></a>使用PerformancePoint Services (本地) 

PerformancePoint Server 2007 与 SharePoint Server 2007 分开出售。 从 SharePoint Server 2010 开始，PerformancePoint Services SharePoint Server 中的服务应用程序。 因此，你不必购买单独的服务器许可证或硬件来使用PerformancePoint Services。
  
若要从 2007 PerformancePoint Server 2007 PerformancePoint Services，请移动到 SharePoint Server 的最新版本，并配置PerformancePoint Services。 您移至的 SharePoint Server 版本确定是否可以将现有仪表板内容从 PerformancePoint Server 2007 导入 PerformancePoint Services。
  
- 如果升级到 SharePoint Server 2010，可以在 SharePoint Server 2010 中将 PerformancePoint 仪表板内容从 PerformancePoint Server 2007 导入 PerformancePoint Services。 若要了解更多信息，请参阅 Import [Wizard： PerformancePoint Server 2007 content to SharePoint Server 2010。](/previous-versions/office/sharepoint-server-2010/ee681485(v=office.14))
    
- 如果您移动到 SharePoint Server 2013 或 SharePoint Server 2016，您很可能需要创建新的仪表板内容 (数据源、报表、记分卡和仪表板) 。
    
若要开始执行PerformancePoint Services升级计划，请参阅以下资源：
  
- [SharePoint Server 2007 停止提供支持路线图](sharepoint-2007-end-of-support.md)
    
- 当您知道要迁移到哪个版本的 SharePoint 时，请参阅适用于以下版本PerformancePoint Services：
    
  - [规划 PerformancePoint Services (SharePoint Server 2010) ](/previous-versions/office/sharepoint-server-2010/ee681486(v=office.14))
    
  - [PerformancePoint Services SharePoint Server 2013 概述](/sharepoint/administration/performancepoint-services-overview)
    
  - [SharePoint Server 2016 中的 PerformancePoint Services 概述](/sharepoint/administration/performancepoint-services-overview)
    
当您升级到 PerformancePoint Services时，您将获得一些新功能和增强功能。 PerformancePoint Services提供改进的记分卡;新的可视化效果，如分解树和 KPI 详细信息报表;更多图表类型;更好的时间智能筛选功能;改进了辅助功能合规性。 若要了解更多信息，请参阅[SharePoint Server 2010 PerformancePoint Services (的新增) 。 ](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14))
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>在哪里可以获取有关升级的帮助？

无论是在本地升级还是移动到 Microsoft 365，我们建议你与 Microsoft 合作伙伴合作。 合格的合作伙伴可以帮助你确定最能满足业务需求的解决方案，并帮助你进行部署。 访问 [Microsoft 合作伙伴中心](https://go.microsoft.com/fwlink/?linkid=841249)，并使用搜索筛选器查找解决方案提供商。
  
## <a name="related-topics"></a>相关主题

[帮助您从 Office 2007 服务器和客户端升级的资源](upgrade-from-office-2007-servers-and-products.md)