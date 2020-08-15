---
title: 升级自 SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: 查找要从 SharePoint 2010 和 Sharepoint Server 2010 升级的信息和资源，以支持在10月13日的2020上提供。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 57e44cf14a74f6a5a2098512e0a2339037d70655
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687579"
---
# <a name="upgrading-from-sharepoint-2010"></a>升级自 SharePoint 2010

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

Microsoft SharePoint 2010 和 SharePoint Server 2010 将在 **年4月 13 2021 日**到达支持的末尾。 本文详细介绍了可帮助您在 Microsoft 365 中将现有的 SharePoint Server 2010 数据迁移到 SharePoint Online 或升级本地 SharePoint Server 2010 环境的资源。
  
## <a name="what-is-end-of-support"></a>什么是支持结束？

当您的 SharePoint Server 2010 和 SharePoint Foundation 2010 软件达到其支持生命周期的结束时间时 (在 Microsoft 提供新功能、缺陷修补程序、安全修补程序等) 的情况下，这称为软件的 "支持终止"，有时也称为 "退休"。 当产品的支持终止 (或 EOS) 不正常时，实际上不会关机或停止工作，否则不会执行任何操作。但是，在软件支持结束时，Microsoft 不再提供：
  
- 可能出现的问题的技术支持;
    
- 针对已发现且可能影响服务器的稳定性和可用性的问题的 Bug 修补程序。
    
- 已发现的漏洞安全修补程序以及可能会使服务器易受安全威胁的安全修补程序。
    
- 时区更新。
    
这意味着将不会为产品提供任何进一步的更新、修补程序或修补程序 (包括安全修补程序/修复程序) ，Microsoft 支持也会将其支持工作完全转移到更新版本。 在支持 SharePoint Server 2010 方法之后，您应该利用机会在升级产品和/或迁移重要数据之前，对不再需要的数据进行修整。
  
> [!NOTE]
> 软件生命周期通常是从产品初始发布之日起10年的时间内持续。 您可以搜索 [microsoft 解决方案提供商](https://go.microsoft.com/fwlink/?linkid=841249) ，他们可以帮助升级到下一个版本的软件，或使用 microsoft 365 迁移 (或这两个) 。 一定要确保您了解关键基础技术的支持日期的结束日期，尤其是您在使用 SharePoint 时使用的 SQL Server 版本。 请参阅 [固定生命周期策略](https://support.microsoft.com/help/14085) 以详细了解产品生命周期。
  
## <a name="what-are-my-options"></a>我的选项是什么？

首先，检查 [产品生命周期网站](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010)上的支持结束的日期。 接下来，请务必通过了解此日期来规划升级或迁移时间。 请注意，你的产品不会在列出的日期  *停止工作*  ，并且你可以继续使用它，但是，因为在该日期之后安装将不再修补，所以你将需要一种策略来帮助你更顺利地转换到产品的下一版本。 
  
此矩阵有助于在迁移产品功能和用户数据时绘制课程：
  
| 支持产品的结束 | 较好 | 最好 |
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013 (本地)   <br/> |SharePoint Online  <br/> |
||SharePoint Server 2013 与 SharePoint Online 的混合  <br/> |SharePoint Server 2016 (本地)   <br/> |
| | |SharePoint 云混合搜索  <br/> |
   
如果您选择规模低端的选项 (好的选项) ，则在从 SharePoint Server 2010 迁移完成后，您需要立即开始规划另一次升级。 

若要避免停止 SharePoint Server 2010 支持，可以采用三种途径。

![SharePoint Server 2010 升级路径](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

>[!Note]
>SharePoint Server 2010 和 SharePoint Foundation 2010 的支持计划于4月13日，2021，但 *请注意* ，应始终检查 [产品生命周期网站](https://support.microsoft.com/lifecycle) 的最新日期。
>

  
## <a name="where-should-i-go-next"></a>下一步应转到哪里？

可以在自己的服务器上的本地安装 SharePoint Server 2013 和 SharePoint Foundation 2013。 否则，您可以使用 SharePoint Online，这是 Microsoft Microsoft 365 中的一种联机服务。 您可以选择执行以下操作：
  
- 迁移到 SharePoint Online
    
- 本地升级 SharePoint Server 或 SharePoint Foundation
    
- 执行上述两项操作
    
- 实现 [SharePoint 混合](https://docs.microsoft.com/sharepoint/hybrid/hybrid) 解决方案 
    
了解与维护服务器场以继续、维护或迁移自定义设置以及升级 SharePoint Server 所依赖的硬件相关的隐藏成本。 如果你意识到所有这些都是在内的，则继续在本地进行升级会更容易。 否则，如果在不进行大量自定义的旧版 SharePoint 服务器上运行服务器场，则可以从计划迁移到 SharePoint Online 中获益。 此外，对于您的本地 SharePoint Server 环境，也可以选择将一些数据放在 SharePoint Online 中，以减少保留本地数据的硬件管理量。 将一些数据移动到 SharePoint Online 可能会更经济。
  
> [!NOTE]
> SharePoint 管理员可以创建 Microsoft 365 订阅，设置新的 SharePoint Online 网站，然后将其完全从 SharePoint Server 2010 中完全删除，仅将最重要的文档放在全新的 SharePoint Online 网站中。 在这里，任何剩余的数据可能会从 SharePoint Server 2010 网站排出到本地存档中。 
  
|**SharePoint Online**|**SharePoint Server 本地**|
|:-----|:-----|
|高成本的时间 (规划/执行/验证)   <br/> |高成本的时间 (规划/执行/验证)   <br/> |
|降低资金成本， (不购买硬件)   <br/> |资金 (硬件购买时的成本较高)   <br/> |
|迁移的一次性成本  <br/> |每次迁移时重复的一次性成本  <br/> |
|低总拥有成本/维护  <br/> |高总拥有成本/维护  <br/> |
   
当您迁移到 Microsoft 365 时，一次性移动将会花费较重的时间，在您组织数据和确定要在云中留下的内容以及在) 背后留下的内容时，需要较 (长时间。 但是，一旦迁移了数据，升级将从该点自动进行查看，因为您不再需要管理硬件和软件更新，并且您的服务器场的启动时间将由 Microsoft 服务级别协议 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) 支持。
  
### <a name="migrate-to-sharepoint-online"></a>迁移到 SharePoint Online

请确保 SharePoint Online 通过查看其 [服务说明](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description)来提供你所需的所有功能。
  
目前尚无一种方法可直接从 SharePoint Server 2010 (或 SharePoint Foundation 2010) 迁移到 SharePoint Online，因此大部分工作是手动进行的。 这将使您有机会在移动之前存档和修剪不再需要的数据和网站。 您可以将其他数据存档到存储中。 另请注意，SharePoint Server 2010 和 SharePoint Foundation 2010 都不会在支持结束时停止工作，因此，如果客户忘记移动某些数据，则管理员可能会有一段时间，在此期间，SharePoint 仍在运行。
  
如果升级到 SharePoint Server 2013 或 SharePoint Server 2016，并决定将数据放入 SharePoint Online 中，则移动可能还涉及使用 [SharePoint 迁移 API](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (将信息迁移到 OneDrive for business) 中。 
  
|**SharePoint Online 优势**|**SharePoint Online 的缺点**|
|:-----|:-----|
|Microsoft 提供 SPO 硬件和所有硬件管理。  <br/> |SharePoint Server 本地和 SPO 之间的可用功能可能有所不同。  <br/> |
|你是订阅的全局管理员，并且可能会向管理员分配 SPO 网站。  <br/> |本地 SharePoint Server 中的服务器场管理员可以使用某些操作， () 或在 Microsoft 365 中的 SharePoint 管理员角色中不存在，但 SharePoint 管理、网站集管理和网站所有权对您的组织而言是本地的。  <br/> |
|Microsoft 会对基础硬件和软件 (应用修补程序、修补程序和更新，包括 SharePoint Online 在其上运行) 的 SQL server。  <br/> |由于对服务中的基础文件系统没有访问权限，因此某些自定义项受到限制。  <br/> |
|Microsoft 发布 [服务级别协议](https://go.microsoft.com/fwlink/?linkid=843153) 并快速移动以解决服务级别事件。  <br/> |备份和还原和其他恢复选项通过 SharePoint Online 中的服务自动进行，如果不使用，则会覆盖备份。  <br/> |
|Microsoft 在服务中不断执行安全测试和服务器性能调整。  <br/> |对用户界面和其他 SharePoint 功能的更改由服务安装，并且可能需要开启或关闭。  <br/> |
|Microsoft 365 符合多种行业标准： [microsoft 合规性服务](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |迁移的[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)协助受到限制。  <br/> 大部分升级都是手动进行的，也可以通过 [SharePoint Online 和 OneDrive 迁移内容路线图](https://go.microsoft.com/fwlink/?linkid=843184)中介绍的 SPO 迁移 API 进行。  <br/> |
|Microsoft 支持工程师和数据中心中的员工都不受无限制地对订阅进行管理员访问。  <br/> |如果需要升级硬件基础结构以支持较新版本的 SharePoint，或者如果升级需要辅助服务器场，则可能会有额外的成本。  <br/> |
|解决方案提供商可协助将您的数据迁移到 SharePoint Online 的一次性作业。  <br/> |并非对 SharePoint Online 所做的所有更改都在您的控制范围内。 迁移之后，菜单、库和其他功能中的设计差异可能会暂时影响可用性。  <br/> |
|在线产品通过服务自动更新意味着，尽管功能可能弃用，但没有真正的支持生命周期的结束。  <br/> |SharePoint Server (或 SharePoint Foundation) 以及基础 SQL server 的支持生命周期已结束。  <br/> |
   
如果您已决定创建新的 Microsoft 365 网站，并将在需要时手动将数据迁移到它，则可以查看您的 [Microsoft 365 选项](https://www.microsoft.com/microsoft-365/)。
  

  
### <a name="upgrade-sharepoint-server-on-premises"></a>升级本地 SharePoint Server

从最新版本的 SharePoint 本地产品 (SharePoint Server 2019) 中，SharePoint Server 升级必须以  *串行*方式进行，这意味着无法直接从 sharepoint server 2010 升级到 sharepoint server 2016 或 sharepoint 2019。 
  
串行升级路径： 

- SharePoint Server 2010 sharepoint server \> 2013 \> sharepoint server 2016
   
如果选择跟踪从 SharePoint 2010 到 SharePoint Server 2016 的整个路径，将需要花费时间和进行规划。 升级涉及升级的硬件的成本 (请注意，还必须升级 SQL server) 、软件和管理。 此外，可能还需要升级自定义项，甚至放弃自定义项。 在升级 SharePoint Server 服务器场之前，请务必先收集所有关键自定义项的注释。
  
> [!NOTE]
> 可以保持您的 2010 SharePoint Server 2016 服务器场的结束，在新的硬件 (上安装 SharePoint Server 场，以便单独的服务器场并行运行) ，然后规划和执行内容 (的手动迁移，以下载和重新上载内容，例如) 。 这些手动移动会带来潜在的缺陷 (例如，来自2010的文档具有当前最后修改的帐户，该帐户具有执行手动移动) 的帐户别名，并且必须提前完成一些工作， (重新创建网站、子网站、权限和列表结构) 。 最好是考虑哪些数据可以移动到存储，或者不再需要。 这样可以降低迁移的影响。 无论哪种方式，都要在升级之前清理环境。 请确保你的现有服务器场在升级之前可以正常运行，并 (以确保在你停止之前) 。 
  
请记住查看 **支持的和不受支持的升级路径**： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您具有 **自定义项**，则在迁移路径中为每个步骤规划升级都很重要： 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**内部部署优势**|**本地缺点**|
|:-----|:-----|
|完全控制 SharePoint 场的所有方面 (及其在服务器硬件上的 SQL) 。  <br/> |所有中断和修复都是贵公司 (的责任，但如果你的产品不在支持的末尾，你可以与付费 Microsoft 支持部门联系) ：  <br/> |
|SharePoint Server 本地的完整功能集以及通过混合将本地服务器场连接到 SharePoint Online 订阅的选项。  <br/> |SharePoint Server 的升级、修补程序、安全修补程序、硬件升级和所有维护都将在本地管理其 SQL 服务器场。  <br/> |
|对比 SharePoint Online 更高的自定义选项的完全访问权限。  <br/> |[Microsoft 合规性产品](https://go.microsoft.com/fwlink/?linkid=843165) 必须在本地手动配置。  <br/> |
|安全测试和服务器性能调整，在您的控制) 下，在您的本地 (执行。  <br/> |Microsoft 365 可能会对 SharePoint Online 可用的功能，这些功能无法与本地 SharePoint Server 进行互操作  <br/> |
|解决方案提供商可以帮助将数据迁移到下一版本的 SharePoint Server (和) 之外。  <br/> |您的 SharePoint Server 网站不会自动使用在 SharePoint Online 中显示的 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 证书。  <br/> |
|在本地 SharePoint Server 中完全控制命名约定、备份和还原以及其他恢复选项。  <br/> |本地 SharePoint Server 对产品生命周期非常敏感。  <br/> |
   
### <a name="upgrade-resources"></a>升级资源

首先比较硬件和软件要求。 如果您不符合对当前硬件的升级的基本要求，这可能意味着您需要先升级服务器场或 SQL server 中的硬件，或者您可能决定将一些站点的一部分移动到 SharePoint Online 的 "长绿" 硬件。 完成评估后，请遵循受支持的升级途径和方法。
  
- **的硬件/软件要求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **的软件边界和限制**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- 以下项**的升级过程概述**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>在 SharePoint Online 和本地 SharePoint Server 之间创建 SharePoint 混合解决方案

另一项 (可能是本地和在线领域的最佳选择为了满足某些迁移需求) 是混合使用的，则可以将 SharePoint Server 2013 或2016或2019场连接到 SharePoint Online 以创建 SharePoint 混合： [了解 sharepoint 混合解决方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)。
  
如果你决定将 SharePoint Server 场混合为你的迁移目标，请务必规划应将哪些网站和用户移动到联机，以及需要在本地部署。 对 SharePoint Server 服务器场内容的审阅和排名 (确定对公司) 的高、中或低影响可能对您做出此决定非常有帮助。 您可能只需要与 SharePoint Online 共享 () 用户帐户进行登录，并 (b) SharePoint Server 搜索索引--这可能在您查看网站的使用方式之前不可清除。 如果您的公司后来决定将所有内容迁移到 SharePoint Online，您可以将所有剩余的帐户和数据联机移动，并使您的本地服务器场退役，并且 SharePoint 服务器场的管理/管理将从该点开始通过 Microsoft 365 控制台完成。
  
请务必熟悉混合的现有类型，以及如何配置您的本地 SharePoint 场和 Microsoft 365 订阅之间的连接。

| 选项 | 说明 |
|:-----|:-----|
|[Microsoft 合规性服务](https://go.microsoft.com/fwlink/?linkid=843165)。  <br/> |迁移的[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365)协助受到限制。  <br/> 大部分升级都是手动进行的，也可以通过 [SharePoint Online 和 OneDrive 迁移内容路线图](https://go.microsoft.com/fwlink/?linkid=843184)中介绍的 SPO 迁移 API 进行。  <br/> |
|Microsoft 支持工程师和数据中心中的员工都不受无限制地对订阅进行管理员访问。  <br/> |如果需要升级硬件基础结构以支持较新版本的 SharePoint，或者如果升级需要辅助服务器场，则可能会有额外的成本。  <br/> |
|合作伙伴可协助将数据迁移到 SharePoint Online 的一次性作业。  <br/> ||
|在线产品是通过服务自动更新的，这意味着功能可能弃用，但不提供真正的支持结束。  <br/> ||
   
如果您已决定创建新的 Microsoft 365 网站，并将在需要时手动将数据迁移到它，则可以查看您的 [Microsoft 365 选项](https://www.microsoft.com/microsoft-365/)。
  
### <a name="upgrade-sharepoint-server-on-premises"></a>升级本地 SharePoint Server

目前没有办法跳过 SharePoint 升级中的版本，至少是在发布 SharePoint Server 2016 时才会跳过。 这意味着升级以串行方式进行：
  
- SharePoint 2007 \> Sharepoint server 2010 \> sharepoint server 2013 \> sharepoint server 2016
   
若要从 SharePoint 2007 到 SharePoint Server 2016 的完整路径是一项显著的投入时间，并且会在升级的 (硬件方面花费一定代价，请注意，SQL server 也必须升级) 、软件和管理。 根据功能的关键程度，需要升级或放弃自定义项。
  
> [!NOTE]
> 可以维护您的生命期结束的 SharePoint 2007 场，将 SharePoint Server 2016 场安装在新的硬件 (，以便单独的服务器场并行运行) ，然后规划和执行内容 (的手动迁移，以下载和重新上载内容，例如) 。 请注意，手动移动的一些陷阱 (例如，文档移动将上次修改的帐户替换为执行手动移动) 的帐户别名，并且必须在一定 (时间之前完成的工作（如重新创建网站、子网站、权限和列表结构) ）。 同样，这也是考虑可以移动到存储或不再需要的数据的时间，可降低迁移影响的操作。
  
无论哪种方式，都要在升级之前清理环境。 请确保你的现有服务器场在升级之前可以正常运行，并 (以确保在你停止之前) 。 
  
请记住查看 **支持的和不受支持的升级路径**： 
  
- [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
如果您具有 **自定义项**，则在迁移路径中为每个步骤规划升级都很重要： 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**本地 Pro**|**本地 Con**|
|:-----|:-----|
|从服务器硬件上完全控制 SharePoint 场的各个方面。  <br/> |所有中断和修复都是公司的责任 (如果你的产品不在支持的末尾，则可以与付费 Microsoft 支持部门联系) ：  <br/> |
|SharePoint Server 本地的完整功能集以及通过混合将本地服务器场连接到 SharePoint Online 订阅的选项。  <br/> |在本地托管的 SharePoint Server 的升级、修补程序、安全修补程序和所有维护。  <br/> |
|完全访问权限以进行更好的自定义。  <br/> |[Microsoft 合规性产品](https://go.microsoft.com/fwlink/?linkid=843165) 必须在本地手动配置。  <br/> |
|在您的本地 (执行的安全测试和服务器性能调整由您的控制) 。  <br/> |Microsoft 365 可能会对 SharePoint Online 可用的功能，这些功能无法与本地 SharePoint Server 进行互操作  <br/> |
|合作伙伴可以协助将数据迁移到下一版本的 SharePoint Server (，但不能迁移到) 之外。  <br/> |您的 SharePoint Server 网站不会自动使用在 SharePoint Online 中显示的 [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 证书。  <br/> |
|在本地 SharePoint Server 中完全控制命名约定、备份和还原以及其他恢复选项。  <br/> |本地 SharePoint Server 对产品生命周期非常敏感。  <br/> |
   
### <a name="upgrade-resources"></a>升级资源

先知道您是否满足硬件和软件要求，然后再遵循受支持的升级方法。
  
- **的硬件/软件要求**： 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **的软件边界和限制**： 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245)  | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- 以下项**的升级过程概述**： 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250)  | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>在 SharePoint Online 和本地部署之间创建 SharePoint 混合解决方案

如果迁移的答案需要在本地提供的自控制之间，以及 SharePoint Online 提供的较低的所有权成本，则可以通过混合将 SharePoint Server 2013 或2016服务器场连接到 SharePoint Online。 [了解 SharePoint 混合解决方案](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
如果你确定混合 SharePoint 服务器场将对你的业务带来好处，请熟悉现有的混合类型，以及如何配置你的本地 SharePoint 场和 Microsoft 365 订阅之间的连接。
  
若要了解其工作原理，一种很好的方法是创建 Microsoft 365 开发/测试环境，您可以使用 [测试实验室指南](m365-enterprise-test-lab-guides.md)对其进行设置。 在试用版或购买的 Microsoft 365 订阅后，您将能够在 SharePoint Online 中创建网站集、web 和文档库，您可以通过使用迁移 API 手动迁移数据，也可以通过混合向导) 将 "我的网站" 内容迁移到 OneDrive for business 中 (。
  
> [!NOTE]
> 请注意，您的 SharePoint Server 2010 服务器场首先需要升级到 SharePoint Server 2013 或 SharePoint Server 2016，才能使用 "混合" 选项。 SharePoint Foundation 2010 和 SharePoint Foundation 2013 无法创建与 SharePoint Online 的混合连接。 

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 客户端和服务器以及 Windows 7 的选项的摘要

有关 Office 2010 客户端和服务器以及 Windows 7 的升级、迁移和移动到云选项的直观摘要，请参阅[终止支持海报](../downloads/Office2010Windows7EndOfSupport.pdf)。

[![Office 2010 客户端和服务器及 Windows 7 终止支持海报图像](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

此海报包含一页内容，可借助它快速了解用于避免 Office 2010 客户端和服务器产品及 Windows 7 停止提供支持的各种方式，突出显示了 Microsoft 365 企业版中的首选方式和选项支持。

还可以[下载](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf)此海报并按 letter、legal 或 tabloid (11 x 17) 格式打印。
        
## <a name="related-topics"></a>相关主题

[可帮助您从 Office 2007 或2010服务器和客户端进行升级的资源](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/mt493301%28v=office.16%29.aspx)
  
[从 SharePoint 2010 升级到 SharePoint 2013 的最佳做法](https://technet.microsoft.com/library/mt493305%28v=office.16%29.aspx)
  
[在 SharePoint 2013 中解决数据库升级问题](https://go.microsoft.com/fwlink/?linkid=843195)
  
[搜索 Microsoft 解决方案提供商以帮助你进行升级](https://go.microsoft.com/fwlink/?linkid=841249)
  
[SharePoint 2013 的更新产品服务策略](https://technet.microsoft.com/library/mt493253%28v=office.16%29.aspx)
  
[SharePoint Server 2016 的更新产品服务策略](https://technet.microsoft.com/library/mt782882%28v=office.16%29.aspx)
  

