---
title: Exchange 2010 支持终止路线图
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 09/16/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2010 即将停止支持。 将此规划路线图用作准备升级到 Exchange Online 或部署到本地 Exchange Server 的更新版本的指南。
ms.openlocfilehash: 128abd1e98c3e9d1ec4dd8a58683ee0ab019af18
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950816"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 支持终止路线图

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

在 **2020 年10月 13**日，Exchange Server 2010 将达到支持的结尾。 如果尚未开始从 Exchange 2010 迁移到 Microsoft 365、Office 365 或 Exchange 2016，现在是开始规划的时间。

## <a name="what-does-end-of-support-mean"></a>支持终止的含义是什么？

与几乎所有 Microsoft 产品一样，Exchange Server 都具有支持生命周期，在此期间我们提供了新的功能、缺陷修补程序、安全修补程序等。 此生命周期通常是从产品初始发布之日起10年的时间，而此生命周期的结束时间也称为产品的支持终止的期限。 当 Exchange 2010 在2020上到达其支持结束时，Microsoft 将不再提供：

- 可能出现的问题的技术支持。
- 针对所发现的问题的 Bug 修复，并且可能会影响服务器的稳定性和可用性。
- 针对发现的漏洞的安全修补程序，并且可能会使服务器容易受到安全破坏。
- 时区更新。

在此日期之后，你的 Exchange 2010 安装将继续运行。 但是，由于上面列出了所做的更改，强烈建议您尽快从 Exchange 2010 迁移。

有关即将结束支持的 Office 2010 服务器的详细信息，请参阅可 [帮助您从 Office 2010 服务器和客户端进行升级的资源](upgrade-from-office-2010-servers-and-products.md)。

## <a name="what-are-my-options"></a>我的选项是什么？

随着 Exchange 2010 的支持终止，这是浏览选项并准备迁移计划的良好时间。 可执行下列操作：

- 完全迁移到 Microsoft 365。 使用直接转换、最小混合或完全混合迁移迁移邮箱，然后删除本地 Exchange 服务器和 Active Directory。
- 将 Exchange 2010 服务器迁移到本地服务器上的 Exchange 2016。

> [!IMPORTANT]
> 如果你的组织选择将邮箱迁移到 Microsoft 365，但打算就地保留 DirSync 或 Azure AD Connect，以继续从本地 Active Directory 中管理用户帐户，则需要在本地至少保留一台 Exchange server。 如果删除了最后一台 Exchange 服务器，将无法更改 Exchange Online 中的 Exchange 收件人。 这是因为颁发机构的来源仍保留在本地 Active Directory 中，需要进行更改。 在这种情况下，您有以下几种选择：

-  (**建议** 的) 如果您可以将邮箱迁移到 Microsoft 365 并在10月 13 2020 日升级服务器，请使用 Exchange 2010 连接到 Microsoft 365 并迁移邮箱。 接下来，将 Exchange 2010 迁移到 Exchange 2016 并取消所有剩余的 Exchange 2010 服务器。
- 如果在10月 13 2020 日之前无法完成邮箱迁移和内部部署服务器升级，请先将本地 Exchange 2010 服务器升级到 Exchange 2016，然后使用 Exchange 2016 连接到 Microsoft 365 并迁移邮箱。

> [!NOTE]
> 稍微复杂一些，你也可以将邮箱迁移到 Microsoft 365，同时将你的本地 Exchange 2010 服务器迁移到 Exchange 2016。

若要避免停止对 Exchange Server 2010 的支持，可以采用三种途径。

![Exchange Server 2010 升级路径](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

以下各节更详细地探讨了每个选项。

## <a name="migrate-to-microsoft-365"></a>迁移到 Microsoft 365

将电子邮件迁移到 Microsoft 365 是帮助您停用 Exchange 2010 部署的最简单且最简单的选项。 通过迁移到 Microsoft 365，你可以从旧技术到一流功能的单一跃点，如下所示：

- 合规性功能，如保留策略、就地和诉讼保留、就地电子数据展示等。
- Microsoft Teams
- Power BI
- 重点收件箱
- MyAnalytics

Microsoft 365 还会先获取新功能并体验，你的用户通常可以立即开始使用它们。 除了新功能之外，您无需担心：

- 购买和维护硬件。
- 支付服务器加热和冷却的费用。
- 及时了解安全性、产品和时区的修补程序
- 维护存储和软件以支持合规性要求
- 升级到新版本的 Exchange-始终在 Microsoft 365 中的最新版本的 Exchange 中。

### <a name="how-should-i-migrate-to-microsoft-365"></a>我应该如何迁移到 Microsoft 365？

根据你的组织，你有几个可帮助你获取 Microsoft 365 的选项。 选择迁移选项时，需要考虑几个因素，如需要移动的座位或邮箱数、您希望迁移的持续时间，以及在迁移过程中是否需要在您的本地安装和 Microsoft 365 之间实现无缝集成。 此表显示了您的迁移选项和最重要的因素，这些因素将决定您将使用哪种方法。

|迁移选项|组织大小|持续时间|
|---|---|---|
|直接转换迁移|座位数少于150|一周或更少|
|最小混合迁移|座位数少于150|几个星期或更少|
|完全混合迁移|超过150的座位|几周或更多|

以下各节提供了这些方法的概述。 请查看 [迁移路径](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) ，以了解每个方法的详细信息。

### <a name="cutover-migration"></a>直接转换迁移

直接转换迁移是指在预先选择的日期和时间，将所有邮箱、通讯组、联系人等迁移到 Office 365。 完成后，你将关闭本地 Exchange 服务器，并以独占方式开始使用 Microsoft 365。

对于没有很多邮箱的小型组织来说，直接转换迁移方法非常有用，希望快速访问 Microsoft 365，并且不希望处理其他方法中的一些复杂性。 但它也受到限制，因为它应在一周或更短的时间内完成，因为它要求用户重新配置其 Outlook 配置文件。 虽然直接转换迁移最多可以处理2000个邮箱，但我们强烈建议您使用此方法最多迁移150个邮箱。 如果您尝试迁移超过150个邮箱，则可能会在你的截止时间之后停止转移所有邮箱，并且 IT 支持人员可能会在帮助用户重新配置 Outlook 时遇到大量的情况。

如果你正在考虑进行直接转换迁移，请考虑以下几点：

- Microsoft 365 将需要通过 TCP 端口443使用 Outlook Anywhere 连接到 Exchange 2010 服务器。
- 所有内部部署邮箱都将移至 Microsoft 365。
- 你将需要本地管理员帐户，该帐户有权读取用户邮箱的内容。
- 要在 Microsoft 365 中使用的 Exchange 2010 接受的域需要添加为服务中的已验证域。
- 在开始迁移和开始完成阶段之间的时间内，Microsoft 365 将定期同步 Microsoft 365 和本地邮箱。 这样，你就可以完成迁移，而无需担心你的内部部署邮箱中留下的电子邮件。
- 用户将收到其 Microsoft 365 帐户的新的临时密码，这些密码将在首次登录邮箱时需要更改。
- 你将需要一个 Microsoft 365 许可证，其中包含你迁移的每个用户邮箱的 Exchange Online。
- 用户需要在各自的每台设备上设置一个新的 Outlook 配置文件，并再次下载他们的电子邮件。 Outlook 将下载的电子邮件数量可能有所不同。 有关详细信息，请参阅 [Outlook 中的脱机工作](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633)。

若要了解有关直接转换迁移的详细信息，请查看以下内容：

- [关于直接转换电子邮件迁移，您需要了解的内容](https://docs.microsoft.com/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [执行电子邮件到 Office 365 的直接转换迁移](https://docs.microsoft.com/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>最小混合迁移

最小混合或快速迁移是指您有几百个要迁移到 Microsoft 365 的邮箱，可以在几周内完成迁移，而不需要任何高级混合迁移功能，如共享的忙/闲日历信息。

最小混合迁移对于需要花费更多时间将其邮箱迁移到 Microsoft 365 的组织非常有用，但仍计划在几个星期内完成迁移。 你可以获得更高级完全混合迁移的一些好处，而不是很复杂。 您可以控制在给定时间迁移邮箱的数量。 将使用本地帐户的用户名和密码创建 Microsoft 365 邮箱。 与直接转换迁移不同，用户不需要重新创建其 Outlook 配置文件。

如果您正在考虑执行最少混合迁移，请考虑以下几点：

- 你将需要在内部部署 Active Directory 服务器和 Microsoft 365 之间执行一次性目录同步。
- 用户将能够使用其邮箱迁移时使用的用户名和密码登录到 Microsoft 365 邮箱。
- 你将需要一个 Microsoft 365 许可证，其中包含你迁移的每个用户邮箱的 Exchange Online。
- 用户无需在大多数设备上设置新的 Outlook 配置文件 (某些旧的 Android 手机可能需要新的配置文件) ，并且不需要重新下载其电子邮件。

若要了解有关最简单的混合迁移的详细信息，请参阅 [使用最少混合，将 Exchange 邮箱快速迁移到 Office 365](https://docs.microsoft.com/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate)。

### <a name="full-hybrid"></a>完全混合

完全混合迁移是指组织有多个数百个、多达数万个的邮箱，并且您希望将其中的部分或全部移动到 Microsoft 365。 由于这些迁移的时间通常较长，混合迁移使其能够：

- 向本地用户显示 Microsoft 365 中用户的忙/闲日历信息，反之亦然。
- 请参阅包含内部部署和 Microsoft 365 中的收件人的统一全局地址列表。
- 查看所有用户的完整 Outlook 收件人收件人属性，而不管他们是在本地还是在 Microsoft 365 中。
- 使用 TLS 和证书在本地 Exchange 服务器和 Office 365 之间进行安全的电子邮件通信。
- 将在内部部署 Exchange 服务器和 Microsoft 365 之间发送的邮件视为内部邮件，使其能够：
  - 由传输和合规性代理对内部邮件进行正确评估和处理。
  - 绕过反垃圾邮件筛选器。

完全混合迁移最适用于希望在多个月或更多个月内保持混合配置的组织。 您将获得本部分前面列出的功能，以及目录同步、更好的集成合规性功能，以及使用在线邮箱移动将邮箱移动到 Microsoft 365 的能力。 Microsoft 365 成为本地组织的扩展。

如果你想要执行完全混合迁移，请考虑以下几点：

- 完全混合迁移不适合于所有类型的组织。 由于完全混合迁移的复杂性，少于几百个邮箱的组织通常不会看到好处，从而证明了设置一个好的工作量和成本所需的好处。 如果这听起来像是你的组织，强烈建议你改为考虑转换或最少的混合迁移。
- 你将需要使用 Azure Active Directory (Azure AD) 在本地 Active Directory 服务器和 Microsoft 365 之间建立目录同步。
- 用户将能够使用登录本地网络时使用的用户名和密码登录到其 Microsoft 365 邮箱， (需要使用密码同步和/或 Active Directory 联合身份验证服务的 Azure AD 连接) 。
- 你将需要一个 Microsoft 365 许可证，其中包含你迁移的每个用户邮箱的 Exchange Online。
- 用户无需在大多数设备上设置新的 Outlook 配置文件 (某些旧的 Android 手机可能需要新的配置文件) ，并且不需要重新下载其电子邮件。

> [!IMPORTANT]
> 如果你的组织选择将邮箱迁移到 Microsoft 365，但打算就地保留 DirSync 或 Azure AD Connect，以继续从本地 Active Directory 中管理用户帐户，则需要在本地至少保留一台 Exchange server。 如果删除了最后一台 Exchange 服务器，将无法更改 Exchange Online 中的 Exchange 收件人。 这是因为颁发机构的来源仍保留在本地 Active Directory 中，需要进行更改。

如果完全混合迁移听起来非常适合你，请查看以下资源，以帮助你进行迁移：

- [Exchange 部署助理](https://aka.ms/exdeploy)
- [Exchange Server 混合部署](https://docs.microsoft.com/exchange/exchange-hybrid)
- [混合配置向导](https://docs.microsoft.com/exchange/hybrid-configuration-wizard)
- [混合配置向导常见问题解答](https://docs.microsoft.com/exchange/hybrid-configuration-wizard-faqs)
- [混合部署先决条件](https://docs.microsoft.com/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>升级到本地 Exchange Server 的较新版本

虽然我们强烈认为您可以通过完全迁移到 Microsoft 365 来实现最佳价值和用户体验，但我们还会了解某些组织需要将一些 Exchange 服务器保留在本地。 这可能是因为法规要求，以保证数据不存储在位于其他国家/地区的数据中心中，也可能是因为您在云中无法满足唯一的设置或要求，也可能只是需要 Exchange 来管理云邮箱，因为您仍在本地使用 Active Directory。 在选择或需要保留 Exchange 本地的任何情况下，应确保将 Exchange 2010 环境升级到至少 Exchange 2013 或 Exchange 2016，并在支持日期结束之前删除 exchange 2010。

为了获得最佳体验，我们建议您将其余的本地环境升级到 Exchange 2016。 如果要直接从 Exchange Server 2010 转到 Exchange Server 2016，则无需安装 Exchange Server 2013。

Exchange 2016 包括早期版本的 Exchange 中附带的所有功能和改进，并且与 Microsoft 365 (的体验最为匹配，尽管某些功能仅在 Microsoft 365) 中可用。 请查看你缺少的几个内容：

|Exchange 发布|功能|
|---|---|
|**Exchange 2013**|简化的体系结构将服务器角色的数量减少到三个 (邮箱、客户端访问和边缘传输) |
||数据丢失防护策略 (DLP) ，可帮助防止敏感信息泄露|
||显著改进的 Outlook Web App 体验|
|**Exchange 2016**|*Exchange 2013 中的功能和 .。。*|
||将服务器角色进一步简化为仅限邮箱和边缘传输|
||改进了 DLP 以及与 SharePoint 的集成|
||改进的数据库恢复能力|
||在线文档协作|

|方面|更多信息|
|---|---|
|支持日期结束|与 Exchange 2010 一样，每个 Exchange 版本都有自己的支持日期结尾：|
||**Exchange 2013** -4 月2023|
||**Exchange 2016** -10 月2025|
||在较早的支持日期结束时，您将需要执行另一个迁移。 4月2023比你想像的要大得多！|
|迁移到 Exchange 2013 或2016的路径|无论您选择 Exchange 2013 还是 Exchange 2016，从 Exchange 2010 到较新版本的迁移路径都是相同的：|
||将 Exchange 2013 或2016安装到现有的 Exchange 2010 组织中。若要 Exchange 2013 或2016，请将邮箱和公用文件夹移动到 Exchange 2013 或2016停止其余的 Exchange 2010 服务器|
|版本共存|迁移到 Exchange 2013 或 Exchange 2016 时，您可以将其中一个版本安装到现有的 Exchange 2010 组织中。 这使您可以安装一个或多个 Exchange 2013 或 Exchange 2016 服务器并执行迁移。|
|服务器硬件|服务器硬件要求已从 Exchange 2010 更改。 您需要确保要使用的硬件是兼容的。 您可以在此处查找有关每个版本的硬件要求的详细信息：|
||[Exchange 2016 系统要求](https://docs.microsoft.com/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016)|
||[Exchange 2013 系统要求](https://docs.microsoft.com/Exchange/exchange-2013-system-requirements-exchange-2013-help)|
||你会发现 Exchange 性能的显著改进以及较新的服务器中计算的计算能力和存储容量的增加，可能需要较少的服务器来支持相同数量的邮箱。|
|操作系统版本|每个版本支持的最低操作系统版本为：|
||**Exchange 2016** Windows Server 2012|
||**Exchange 2013** Windows Server 2008 R2 SP1|
||您可以在 Exchange 可支持性 [矩阵](https://docs.microsoft.com/exchange/plan-and-deploy/supportability-matrix)中找到有关操作系统支持的详细信息。|
|Active Directory 林功能级别|每个版本支持的最小 Active Directory 林功能级别为：|
||**Exchange 2016** Windows Server 2008 R2 SP1|
||**Exchange 2013** Windows Server 2003|
||可以在 [Exchange 可支持性矩阵](https://docs.microsoft.com/exchange/plan-and-deploy/supportability-matrix)中找到有关林功能级别支持的详细信息。|
|Office 客户端版本|每个版本的受支持的 Office 客户端版本最低为：|
||**Exchange 2016** Office 2010 (，并提供最新的更新) |
||**Exchange 2013** Office 2007 SP3|
||您可以在 Exchange 可支持性 [矩阵](https://docs.microsoft.com/exchange/plan-and-deploy/supportability-matrix)中找到有关 Office 客户端支持的详细信息。|

您可以使用以下资源来帮助您进行迁移：

- [Exchange 部署助理](https://aka.ms/exdeploy)
- Exchange [2016](https://docs.microsoft.com/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016)、 [2013](https://docs.microsoft.com/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)的 Active Directory 架构更改
- Exchange [2016](https://docs.microsoft.com/exchange/plan-and-deploy/system-requirements?view=exchserver-2016)、 [2013](https://docs.microsoft.com/Exchange/exchange-2013-system-requirements-exchange-2013-help)的系统要求
- Exchange [2016](https://docs.microsoft.com/exchange/plan-and-deploy/prerequisites?view=exchserver-2016)、 [2013](https://docs.microsoft.com/Exchange/exchange-2013-prerequisites-exchange-2013-help)的先决条件

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 客户端和服务器以及 Windows 7 的选项的摘要

有关 Office 2010 客户端和服务器以及 Windows 7 的升级、迁移和移动到云选项的直观摘要，请参阅[终止支持海报](../downloads/Office2010Windows7EndOfSupport.pdf)。

[![Office 2010 客户端和服务器及 Windows 7 终止支持海报图像](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

此海报包含一页内容，可借助它快速了解用于避免 Office 2010 客户端和服务器产品及 Windows 7 停止提供支持的各种方式，突出显示了 Microsoft 365 企业版中的首选方式和选项支持。

还可以[下载](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf)此海报并按 letter、legal 或 tabloid (11 x 17) 格式打印。

## <a name="what-if-i-need-help"></a>如果我需要帮助，该怎么办？

如果你正在迁移到 Microsoft 365，你可能有资格使用我们的 Microsoft FastTrack 服务。 FastTrack 提供了最佳实践、工具和资源，使您能够以尽可能顺畅的方式迁移到 Microsoft 365。 尤其可贵的是，你将拥有真正的支持工程师，它将引导你完成迁移，从规划和设计一直到迁移你的最后一个邮箱。 若要了解有关 FastTrack 的详细信息，请参阅 [Microsoft FastTrack](https://fasttrack.microsoft.com/)。

如果您在迁移到 Microsoft 365 期间遇到任何问题，并且您不使用 FastTrack，或迁移到较新版本的 Exchange Server，我们将在这里为你提供帮助。 以下是您可以使用的一些资源：

- [技术社区](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [客户支持](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>相关主题

[帮助从 Office 2010 服务器和客户端升级的相关资源](upgrade-from-office-2010-servers-and-products.md)
