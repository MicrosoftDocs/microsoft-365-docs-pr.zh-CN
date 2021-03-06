---
title: Microsoft 365 合规中心更新信息
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: 无论是将新解决方案添加到合规中心、根据反馈更新现有功能，还是推出最新更新的文档，Microsoft 365都可以帮助您随时了解不断变化的合规性环境。 了解我们本月已经进行了哪些工作。
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 4e298a9dc8b23e3977db51d5a3b96f7b0723a0d1
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394937"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Microsoft 365 合规中心更新信息

无论是向[Microsoft 365 合规中心](microsoft-365-compliance-center.md)添加新解决方案、根据反馈更新现有功能，还是推出最新更新的文档，Microsoft 365 都可以帮助您随时了解不断变化的合规性环境。 查看下面的内容，了解当前Microsoft 365的新增功能。

> [!NOTE]
> 一些合规性功能以不同的速度为客户提供推出。 如果尚未看到功能，请尝试将自己添加到 [定向发布](/office365/admin/manage/release-options-in-office-365)。

> [!TIP]
> 有兴趣了解其他管理中心中如何工作？ 请查看以下文章：
>
> - [最新功能Microsoft 365 管理中心](/office365/admin/whats-new-in-preview)
> - [SharePoint管理中心的新增功能](/sharepoint/what-s-new-in-admin-center)
> - [Microsoft 365 Defender 的新增功能](../security/defender/whats-new.md)
>
> 请访问Microsoft 365[路线图](https://www.microsoft.com/microsoft-365/roadmap)，了解Microsoft 365、即将推出、正在开发、已取消或以前发布的新功能。

## <a name="june-2021"></a>2021 年 6 月

### <a name="customer-key"></a>客户密钥

- [使用客户密钥 (](customer-key-overview.md)客户密钥租户级别的服务加密现在加密 Microsoft 信息保护.) 

### <a name="ediscovery"></a>电子数据展示

- [使用新的](review-set-search.md) UX 格式 (查询和筛选审阅集内容，以筛选和搜索审阅集内容) 
- [在审阅集](tagging-documents.md)内标记文档Advanced eDiscovery (新的标记功能和 UX，以便更快、更轻松地标记审阅集内的文档;包括使用查询和使用筛选器根据项目标记项目来快速查找或排除审阅集项目的新功能) 
- [为电子数据展示](set-up-compliance-boundaries.md)调查设置合规性 (Microsoft 已取消联系 MS 支持以请求将合规性属性同步到OneDrive的要求;现在，邮箱搜索权限筛选器用于强制实施邮箱搜索权限OneDrive) 

### <a name="sensitivity-labels"></a>敏感度标签

- 敏感度标签策略向导现在支持Outlook标签[](sensitivity-labels-office-apps.md#outlook-specific-options-for-default-label-and-mandatory-labeling)和强制标签的特定选项，作为比 (仍受 PowerShell) 支持更简单的配置。
- 现已[推出 Word、Excel](sensitivity-labels-office-apps.md#dynamic-markings-with-variables )和 PowerPoint web 版
- 对于[自动标记策略](apply-sensitivity-label-automatically.md)Exchange，如果标签配置为加密，则不应用该加密。 此外Exchange自动标记策略，现在可以配置例外和以下新条件：主题、收件人地址或发件人地址匹配模式;收件人地址包含词语;sender domain is， recipient is a member of;sender 是。
- 将敏感度标签与团队、组和网站一同使用时，可以将 Set-SPOTenant 与 BlockSendLabelMismatchEmail 参数一同使用，以防止在记录审核事件检测到文档敏感度不匹配时自动生成的电子邮件。  有关详细信息，请参阅审核 [敏感度标签活动](sensitivity-labels-teams-groups-sites.md#auditing-sensitivity-label-activities )。
- 现在 [，敏感度](sensitivity-labels-teams-groups-sites.md#more-information-about-the-dependencies-for-the-authentication-context-option) 标签的身份验证上下文设置已完全推出预览版。 此外，此配置现在受 Microsoft Teams。
- 为 SharePoint 和 OneDrive 中的 Office 文件启用敏感度标签后，现在可以在 Office 网页版 中打开由服务原则名称 (（如 Microsoft Cloud App Security) ）标记和加密然后上传到 SharePoint 和[OneDrive 的文件](sensitivity-labels-sharepoint-onedrive-files.md)。
- [](sensitivity-labels-coauthoring.md)使用版本 2105 时，共同创作和自动保存不再局限于测试租户，现在支持生产：6 月 18 日针对 Windows，版本 16.50+ for macOS。 请注意，此功能仍不受 iOS 和 Android 支持，仍保持预览状态。

## <a name="may-2021"></a>2021 年 5 月

### <a name="data-loss-prevention"></a>数据丢失防护

- 规划数据丢失 [防护策略的新](dlp-overview-plan-for-dlp.md) 指南。

### <a name="retention-and-records-management"></a>保留和记录管理

- 如果从 SharePoint 或 OneDrive 帐户发布保留策略，则无需再等待 30 天的宽限期，然后才能删除站点或帐户。 客户提出的一个热门请求，此更改现已针对所有租户完成。
- 在预览版 **中**，多阶段处置评审：管理员现在可以为保留标签添加最多五个连续的 [](disposition.md)处置评审阶段，审阅者可以将其他用户添加到其处置评审阶段。 你还可以自定义电子邮件通知和提醒。

### <a name="sensitive-information-types"></a>敏感信息类型

- 新增了可帮助您修改 [关键字词典的信息](sit-modify-keyword-dictionary.md)。

### <a name="sensitivity-labels"></a>敏感度标签

- 在预览版中，当您为组和网站配置敏感度标签时，身份验证[上下文的新设置现在可用](sensitivity-labels-teams-groups-sites.md)。 此选项与 Azure AD 条件访问策略结合使用，以在用户访问应用了标签SharePoint网站时强制实施更严格的条件。 在配置此设置 [之前，请务必](sensitivity-labels-teams-groups-sites.md#more-information-about-the-dependencies-for-the-authentication-context-option) 先阅读依赖项和限制。
- [仅针对 Exchange](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)配置的自动标记策略现在支持敏感度标签，这些标签使用"允许用户分配不要转发"或"Encrypt-Only权限"来应用加密。
- [强制标记现在](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents)适用于所有平台Office应用。

## <a name="april-2021"></a>2021 年 4 月

### <a name="advanced-ediscovery"></a>高级电子数据展示

- [中Advanced eDiscovery。](/microsoft-365/compliance/limits-ediscovery20#export-limits---final-export-out-of-review-set) 组织现在可以在一次从审阅集导出项目时导出多达 500 万个项目或 500 MB（以较小者为准）。

### <a name="data-classification"></a>数据分类

- [活动资源管理器中可用的标记活动](/microsoft-365/compliance/data-classification-activity-explorer-available-events)

### <a name="data-connectors"></a>数据连接器

- [设置连接器以在 Oracle 数据上存档 Cisco Jabber](/microsoft-365/compliance/archive-ciscojabberonoracle-data)
- [设置连接器以在 PostgreSQL 数据上存档 Cisco Jabber](/microsoft-365/compliance/archive-ciscojabberonpostgresql-data)

### <a name="data-loss-prevention"></a>数据丢失防护

- 数据丢失防护 [策略提示的新主题参考](/microsoft-365/compliance/dlp-policy-tips-reference)。
- 了解数据丢失 [防护的新主题](/microsoft-365/compliance/dlp-learn-about-dlp)。
- 数据丢失防护 [警报仪表板入门的新主题](/microsoft-365/compliance/dlp-alerts-dashboard-get-started)。

### <a name="retention-policies-and-retention-label-policies"></a>保留策略和保留标签策略

- "Microsoft 365 组"位置现在支持将保留设置仅应用于 Microsoft 365 邮箱，或仅将 [Set-RetentionCompliancePolicy PowerShell](/powershell/module/exchange/set-retentioncompliancepolicy) cmdlet 与 Applications 参数一同应用于连接的 SharePoint *站点*。

### <a name="sensitivity-labels"></a>敏感度标签

Outlook版本和更新：

- [默认标签和强制标签的不同](sensitivity-labels-office-apps.md#outlook-specific-options-for-default-label-and-mandatory-labeling) 设置现在支持内置标签。 以前，这些设置仅受 AIP 统一标记客户端支持。
- [](encryption-sensitivity-labels.md#let-users-assign-permissions) macOS、iOS 和 Android 现在支持仅加密。
- [强制标记](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents) 将推出到其余平台。
- [所有客户端都支持](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)使用所有变量的动态Outlook标记。

## <a name="march-2021"></a>2021 年 3 月

下面是 3 月对Microsoft 365解决方案和内容的一些更改。

### <a name="advanced-ediscovery"></a>高级电子数据展示

- **Advanced eDiscovery集合** 现在支持 [新的集合工具和工作流](/microsoft-365/compliance/collections-overview)。 其他新主题包括[创建草稿集合](/microsoft-365/compliance/create-draft-collection)、[将草稿集合提交到审阅集](/microsoft-365/compliance/commit-draft-collection)[以及集合统计信息和报告](/microsoft-365/compliance/collection-statistics-reports)。
- **将审阅** 集内的文档 [导出到Azure 存储](/microsoft-365/compliance/download-export-jobs)帐户。
- **Advanced eDiscovery 预测编码模块**。 首先 [查看替换停用](/microsoft-365/compliance/predictive-coding-overview) 的相关性模块的新预测编码功能。

### <a name="data-classification"></a>数据分类

- **数据分类资源管理器**。 [数据](/microsoft-365/compliance/data-classification-activity-explorer) 分类资源管理器入门。

### <a name="data-connectors"></a>数据连接器

- **私钥 。** 对私钥的支持已添加到 Bloomberg [邮件](/microsoft-365/compliance/archive-bloomberg-message-data#set-up-a-connector-using-public-keys) 数据 [、ICE 聊天](/microsoft-365/compliance/archive-icechat-data#set-up-a-connector-using-public-keys) 数据和 [Instant Bloomberg](/microsoft-365/compliance/archive-instant-bloomberg-data#set-up-a-connector-using-public-keys) 数据连接器。

### <a name="data-loss-prevention"></a>数据丢失防护

- **Microsoft Teams支持**。 数据丢失防护支持[扩展到Microsoft Teams。](/microsoft-365/compliance/dlp-teams-default-policy)
- **Microsoft 合规性扩展**。 Microsoft 合规性 [扩展入门](/microsoft-365/compliance/dlp-chrome-get-started)。

### <a name="encryption"></a>加密

- **客户密钥Microsoft 365。** [租户级别的客户密钥](/microsoft-365/compliance/customer-key-tenant-level)Microsoft 365公共预览版 (客户) 。
- **双密钥加密**。 了解有关在文档和[文档中](/microsoft-365/compliance/double-key-encryption)启用对已标记和受保护SharePoint OneDrive for Business。

### <a name="insider-risk-management"></a>内部风险管理

以下内部风险管理功能更新于 3 月发布公开预览版：

- 用于创建内部风险策略之前识别风险的新分析功能
- 新的风险活动序列检测支持和管理
- 新的累积 exfiltration 检测支持
- 新的应用内策略运行状况报告和建议支持
- 新的审核日志功能和报告
- 策略创建向导的增强功能
- 内容资源管理器更新
- 新用户管理过程/支持 (策略策略中添加/删除) 
- 新的 AAD 集成支持 (离开的用户策略支持) 
- 更新了 REGEX 策略 (域) 
- 策略模板增强功能和改进

更新或添加了以下主题以支持这些新功能：

- [了解内部风险管理](/microsoft-365/compliance/insider-risk-management)
- [内部风险管理计划](/microsoft-365/compliance/insider-risk-management-plan)
- [内部风险管理设置入门](/microsoft-365/compliance/insider-risk-management-settings)
- [内部风险管理入门](/microsoft-365/compliance/insider-risk-management-configure)
- [创建和管理内部风险策略](/microsoft-365/compliance/insider-risk-management-policies)
- [调查内部风险警报](/microsoft-365/compliance/insider-risk-management-alerts)
- [对内部风险案例采取措施](/microsoft-365/compliance/insider-risk-management-cases)
- [与内部风险审核日志一起查看活动](/microsoft-365/compliance/insider-risk-management-audit-log)
- [使用内部风险内容资源管理器查看数据](/microsoft-365/compliance/insider-risk-management-content-explorer)
- [使用用户仪表板管理工作流](/microsoft-365/compliance/insider-risk-management-users)

### <a name="records-management"></a>记录管理

- **文件计划改进**。 文件计划 [更新将](file-plan-manager.md) 删除或改进以前的导入长度限制。
- **删除记录的保留标签**。 预览版本支持删除 [将项目标记为记录的](create-apply-retention-labels.md#deleting-retention-labels) 保留标签。

### <a name="sensitive-information-types"></a>敏感信息类型

在下列主题中添加或更新了内容：

- [自定义敏感信息类型入门](/microsoft-365/compliance/create-a-custom-sensitive-information-type)
- [了解敏感信息类型](/microsoft-365/compliance/sensitive-information-type-learn-about)
- [使用基于精确数据匹配的分类创建自定义敏感信息类型](/microsoft-365/compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification)
- [创建精确数据匹配活动通知](/microsoft-365/compliance/sit-edm-notifications-activities)
- [敏感信息类型实体定义](/microsoft-365/compliance/sensitive-information-type-entity-definitions)
- [使用 PowerShell 创建自定义敏感信息类型](/microsoft-365/compliance/create-a-custom-sensitive-information-type-in-scc-powershell)
- [创建关键字字典](/microsoft-365/compliance/create-a-keyword-dictionary)

### <a name="sensitivity-labels"></a>敏感度标签

- **DoD 支持**。 支持具有 DoD 环境的美国政府租户。
- **仅对加密Outlook。** 选择"允许用户分配Outlook时，Encrypt-Only加密选项[现在包括加密选项](encryption-sensitivity-labels.md#let-users-assign-permissions)。
- **强制在应用应用中Office标签**。 更新[了](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-the-azure-information-protection-client)在安装 Azure 信息保护统一标签客户端Office应用中强制执行内置标签的指南。

## <a name="february-2021"></a>2021 年 2 月

下面是 2 月对Microsoft 365解决方案和内容的一些更改。

### <a name="auditing"></a>审核

- **管理审核日志保留策略。** 详细了解新的审核保留 [策略仪表板](/microsoft-365/compliance/audit-log-retention-policies#manage-audit-log-retention-policies-1)。
- **搜索审核日志**。 [使用 PowerShell 脚本搜索审核日志。](/microsoft-365/compliance/audit-log-search-script)

### <a name="data-classification-content-explorer"></a>数据分类内容资源管理器

在下列主题中添加或更新了内容：

- [内容浏览器入门](/microsoft-365/compliance/data-classification-content-explorer)
- [数据分类发行说明](/microsoft-365/compliance/data-classification-pub-preview-relnotes)

### <a name="data-loss-prevention"></a>数据丢失防护

在下列主题中添加或更新了内容：

- [了解 Endpoint DLP](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [发送电子邮件通知并显示 DLP 策略的策略提示](/microsoft-365/compliance/use-notifications-and-policy-tips)
- [了解Microsoft 365数据丢失防护本地扫描程序](/microsoft-365/compliance/dlp-on-premises-scanner-learn)
- [数据丢失防护本地扫描程序入门](/microsoft-365/compliance/dlp-on-premises-scanner-get-started)
- [创建 DLP 策略来保护具有 FCI 或其他属性的文档](/microsoft-365/compliance/protect-documents-that-have-fci-or-other-properties)
- [使用终结点数据丢失防护](/microsoft-365/compliance/endpoint-dlp-using)
- [终结点数据丢失防护入门](/microsoft-365/compliance/endpoint-dlp-getting-started)

### <a name="ediscovery"></a>电子数据展示

在下列主题中添加或更新了内容：

- [电子数据展示Microsoft 365中的解密](/microsoft-365/compliance/ediscovery-decryption)
- [关键字查询和搜索条件](/microsoft-365/compliance/keyword-queries-and-search-conditions#limitations-for-searching-sensitive-data-types)
- [停用中的相关性模块Advanced eDiscovery](/microsoft-365/compliance/relevance-module-retirement)
- [使用脚本将用户添加到核心电子数据展示案例中的保留](/microsoft-365/compliance/use-a-script-to-add-users-to-a-hold-in-ediscovery)

### <a name="encryption"></a>加密

在下列主题中添加或更新了内容：

#### <a name="azure-rights-management-service-rms"></a>Azure 权限管理服务 (RMS) 

- [客户管理的加密功能](/microsoft-365/compliance/office-365-customer-managed-encryption-features)
- [Exchange Online AD RMS 进行邮件加密](/microsoft-365/compliance/information-rights-management-in-exchange-online)。 对此服务的支持已弃用。 您不再可以在混合环境中使用 AD RMS Exchange使用。 相反，请迁移到 Azure RMS。

#### <a name="customer-key"></a>客户密钥

- [租户级别Microsoft 365客户密钥](/microsoft-365/compliance/customer-key-tenant-level)
- [安全性和合规性概述](/microsoftteams/security-compliance-overview)

#### <a name="information-rights-management-irm"></a>信息权限管理 (IRM)

- [将信息权限管理 (IRM) 列表或库。](/microsoft-365/compliance/configure-irm-to-use-an-on-premises-ad-rms-server) 这些国家云不支持此设置：
  - Microsoft Cloud for US Government
  - Microsoft 云德国
  - 由中国Microsoft 365世纪网络运营的 Azure 和) 
- [将 IRM 配置为使用内部部署 AD RMS 服务器](/microsoft-365/compliance/configure-irm-to-use-an-on-premises-ad-rms-server)。 已弃用Exchange环境中对此服务的支持。

### <a name="sensitive-information-types"></a>敏感信息类型

在下列主题中添加或更新了内容：

- [了解敏感信息类型](/microsoft-365/compliance/sensitive-information-type-learn-about)
- [使用 PowerShell 创建自定义敏感信息类型](/microsoft-365/compliance/create-a-custom-sensitive-information-type-in-scc-powershell)
- [使用基于精确数据匹配的分类创建自定义敏感信息类型](/microsoft-365/compliance/create-custom-sensitive-information-types-with-exact-data-match-based-classification)
- [敏感信息类型属性定义](/microsoft-365/compliance/sensitive-information-type-entity-definitions)

### <a name="sensitivity-labels"></a>敏感度标签

在下列主题中添加或更新了内容：

- **SharePoint外部共享**。 对于[容器标签](sensitivity-labels-teams-groups-sites.md)，外部共享选项SharePoint现在发布为公开发布。 此外，Microsoft 365 管理中心和 Planner 现在支持应用这些敏感度标签。 
- **共同创作和自动保存**。 对 [加密文件共同创作](sensitivity-labels-coauthoring.md) 和自动保存的支持发布为预览版，用于测试非生产租户。

## <a name="january-2021"></a>2021 年 1 月

### <a name="support-for-card-content-in-teams"></a>支持卡片内容Teams

以下Microsoft 365合规性解决方案现在支持检测通过邮件中的应用生成的Teams[](/microsoftteams/platform/task-modules-and-cards/what-are-cards)内容：

- **核心和Advanced eDiscovery**。 现在可以将卡片内容[置于保留](create-ediscovery-holds.md#preserve-card-content)状态或包含在搜索 ([](/microsoftteams/ediscovery-investigation#search-for-card-content)内容搜索以及) 。
- **审核**。 卡片活动现在[记录到审核日志。](/microsoftteams/audit-log-events#teams-activities)
- **保留策略**。 现在可以使用保留策略 [来保留和删除卡片内容](retention-policies-teams.md#whats-included-for-retention-and-deletion)。

### <a name="information-governance-and-records-management"></a>信息管理和记录管理

[用于解决](retention-regulatory-requirements.md#new-zealand-public-records-act) 使用信息管理和记录管理以帮助履行新西兰公共记录法案的合规性义务的新评估。

### <a name="sensitivity-labels"></a>敏感度标签

- 敏感度标签现在支持美国政府租户 (GCC GCC-H) 。
- macOS [的新](sensitivity-labels-office-apps.md) 自动标记支持。
