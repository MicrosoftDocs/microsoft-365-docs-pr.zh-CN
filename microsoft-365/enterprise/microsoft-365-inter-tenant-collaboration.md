---
title: Microsoft 365 租户间协作
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/21/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: 了解 Microsoft 365 协作如何跨租户和组织工作，从而使不同的组织能够安全地协同工作。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8064543f771927f539d09e3136663bb0df56d5be
ms.sourcegitcommit: 4ee683c18442386f6fc5c76ffabfad2c28b81d42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "48214795"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 租户间协作

假定两个组织（Fabrikam 和 Contoso）都有 Microsoft 365 for business 租户，他们希望在多个项目中协同工作;其中一些运行时间有限，有些时间正在进行。 Fabrikam 和 Contoso 如何使他们的人员和团队能够以安全的方式更有效地跨其不同的 Microsoft 365 租户进行协作？ Microsoft 365 与 Azure Active Directory (Azure AD) B2B 协作）提供了几个选项。 本文介绍了 Fabrikam 和 Contoso 可以考虑的几个关键方案。
  
Microsoft 365-租户之间的协作选项包括使用文件和对话的中央位置、共享日历、使用 IM、音频/视频呼叫进行通信以及保护对资源和应用程序的访问。 使用下表选择解决方案并了解详细信息。
  
## <a name="exchange-online-collaboration-options"></a>Exchange Online 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|与其他 Microsoft 365 组织共享日历 |管理员可以在 Exchange Online 中设置不同级别的日历访问权限，以允许企业与其他公司进行协作，并让用户共享) 与其他人 (的忙/闲信息的日程安排。 | <ul><li>[共享](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) </li><li> [组织关系](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) </li><li> [创建组织关系](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) </li><li> [修改组织关系 ](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) </li><li> [删除组织关系](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) </li><li> [与外部用户共享日历](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|控制用户如何与组织外部的人员共享其日历 | 管理员将共享策略应用于用户邮箱，以控制可以共享的用户和授予的访问权限级别 |  <ul><li> [共享策略](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) </li><li> [创建共享策略](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) </li><li> [将共享策略应用于邮箱](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) </li><li> [修改、禁用或删除共享策略](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) </li></ul> |
|配置安全的电子邮件通道并控制合作伙伴组织的邮件流 | 管理员创建连接器以将安全性应用于与合作伙伴组织或服务提供商进行的邮件交换。 连接器通过传输层安全性 (TLS) 实施加密，并允许对合作伙伴发送电子邮件的域名或 IP 地址范围进行限制。 |  <ul><li> [Exchange Online 如何使用 TLS 保护电子邮件连接](https://technet.microsoft.com/library/mt163898.aspx) </li><li> [使用连接器配置邮件流](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) </li><li> [远程域](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) </li><li> [设置连接器以实现与合作伙伴组织的安全邮件流](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) </li><li> [邮件流最佳实践 (概述) ](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) </li></ul> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online 和 OneDrive for business 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|与外部用户共享网站和文档 | 管理员在租户或网站集级别配置 Microsoft 帐户身份验证、工作或学校帐户身份验证或来宾帐户的网站集级别的共享 |  <ul><li> [管理 SharePoint Online 环境的外部共享](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [限制 SharePoint 和 OneDrive 内容的共享（按域）](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) </li><li> [使用 SharePoint Online 作为企业到企业 (B2B) extranet 解决方案](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|跟踪和控制最终用户的外部共享 | OneDrive for Business 文件所有者和 SharePoint Online 最终用户配置网站和文档共享并建立通知以跟踪共享 |  <ul><li> [为 OneDrive for business 的外部共享配置通知](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [共享 SharePoint 文件或文件夹](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype for Business 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|Skype for business Online-与其他 Skype for Business 用户的 IM、呼叫和状态 | 管理员可以为其 Skype for Business Online 用户启用 IM，发出音频/视频呼叫，并与另一 Microsoft 365 租户中的用户查看状态。 | [允许用户连接外部 Skype for Business 用户](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)| 
|Skype for business Online-Skype (消费者) 用户的 IM、呼叫和状态 | 管理员可以让其 Skype for business Online 用户使用 Skype (消费者) 用户在即时消息中进行呼叫和查看状态。 | [允许 Skype for Business 用户添加 Skype 联系人](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)| 
   
## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|Azure AD B2B 协作-通过将外部用户添加到组织目录中的组中的内容共享 | 一个 Microsoft 365 租户的全局管理员可以邀请另一个 Microsoft 365 租户中的人员加入其目录，将这些外部用户添加到一个组，并授予对内容的访问权限，如组的 SharePoint 网站和库。 |  <ul><li> [什么是 Azure AD B2B 协作预览？](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B：新的更新使跨业务 collab 变得轻松](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [外部共享和 Azure Active Directory B2B 协作](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Azure Active Directory B2B 协作 API 和自定义](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD 和 Identity Show： Azure AD B2B 协作 (企业到企业](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |
   
## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|Microsoft 365 组-在中心位置的电子邮件、日历、OneNote 和共享文件 | 在业务重点、商业高级版、教育版、企业版 E1、E3 和 E5 计划中支持组。 一个 Microsoft 365 租户中的人员可以创建一个组，并将另一个 Microsoft 365 租户中的人员邀请为来宾用户。 也适用于 Dynamics CRM。 |  <ul><li> [了解 Microsoft 365 组](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Microsoft 365 组中的来宾访问](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [部署 Microsoft 365 组](https://technet.microsoft.com/library/dn896591.aspx) </li></ul> |
   
## <a name="yammer-collaboration-options"></a>Yammer 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|Yammer-通过企业社交媒体进行协作 | 除非 Yammer 管理员禁用了创建外部组的功能，否则用户可以创建外部组以通过对话、喜欢和关注帖子、共享文件和在线聊天的能力在 Yammer 中进行协作。 | [在 Yammer 中创建和管理外部组](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)| 
   
## <a name="teams-collaboration-options"></a>团队协作选项

|共享目标|管理操作|操作方法信息|
|:-----|:-----|:-----|
|在团队中与组织外部的用户进行协作 | 邀请 Microsoft 365 租户的全局管理员需要在团队中启用外部协作。 全局管理员和团队所有者现在将能够使用电子邮件地址邀请任何人在团队中进行协作。  <br/> 管理员还可以管理和编辑其租户中已有的来宾。 |  <ul><li> [授权来宾访问](https://docs.microsoft.com/microsoftteams/teams-dependencies) </li><li> [在团队中打开或关闭来宾访问](https://docs.microsoft.com/microsoftteams/set-up-guests) </li><li> [使用 PowerShell 控制来宾访问](https://docs.microsoft.com/microsoftteams/guest-access-powershell) </li><li> [来宾访问清单](https://docs.microsoft.com/microsoftteams/guest-access-checklist) </li><li> [查看来宾用户](https://docs.microsoft.com/microsoftteams/view-guests) </li><li> [编辑来宾用户信息](https://docs.microsoft.com/microsoftteams/edit-guests-information) </li></ul> |
|团队所有者可以邀请和管理来宾在其团队中进行协作的方式。  </li><li> |团队所有者对来宾在其团队中可以执行的操作具有其他控制。 |  <ul><li> [添加来宾](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [向团队添加来宾](https://docs.microsoft.com/microsoftteams/add-guests) </li><li> [管理团队中的来宾访问](https://docs.microsoft.com/microsoftteams/manage-guests) </li><li> [查看团队或频道中的人员](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|其他租户的来宾可以查看团队中的内容，并与其他成员协作 | 无。 | [来宾访问体验](https://docs.microsoft.com/microsoftteams/guest-experience)| 

## <a name="power-bi-collaboration-options"></a>Power BI 协作选项

| 共享目标 | 管理操作 | 操作方法信息 |
|:-----|:-----|:-----|
|Power BI 使外部来宾用户能够使用通过链接共享的内容。 这使组织中的用户能够跨组织以安全的方式分发内容。<br/> | Power BI 管理员可以控制用户是否可以邀请外部用户查看组织内的内容。| [使用 Azure AD B2B 将 Power BI 内容分发给外部来宾用户](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) | 
 
## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>了解 Microsoft 365 内部租户协作的相关要点

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>用户帐户、许可证、订阅和存储的共享

每个组织都维护自己的用户帐户、标识、安全组、订阅、许可证和存储。 用户将 Microsoft 365 中的协作功能与共享策略和安全设置结合使用，以提供对所需信息的访问权限，同时控制公司资产。
  
- **用户帐户：** 帐户无法共享，并且在内部部署 Active Directory 目录服务中的租户或分区之间无法复制帐户。 
    
- **许可证 &amp; 订阅：** 在 Microsoft 365 中，许可计划中的许可证也称为 sku 或 Microsoft 365 计划) 授予用户对为这些计划定义的 Microsoft 365 服务的访问权限 (。 
    
- **存储：** 在 Microsoft 365 计划中，SharePoint Online 的软件边界和限制与邮箱存储限制分开管理。 邮箱存储限制通过使用 Exchange Online 进行设置和管理。 在这两种情况下，存储不能跨租户共享。 
    
### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>我们可以跨 Microsoft 365 租户共享域命名空间吗？

否。 虚域（例如 fabrikam.com 或 tailspintoys.com）一次只能与一个租户关联和使用。 每个租户都必须具有自己的命名空间;UPN、SMTP 和 SIP 命名空间无法在租户之间共享。
  
### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>混合组件和 Microsoft 365 之间的组织之间的协作是什么？

内部部署混合组件（如 Exchange 组织和 Azure AD Connect）无法跨多个租户拆分。
  

