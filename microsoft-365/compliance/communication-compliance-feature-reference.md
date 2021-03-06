---
title: 通信合规性功能参考
description: 通信合规性功能参考Microsoft 365。 了解每个功能组件的详细信息和规范。
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 8a81c65d65704262230e6eb6245d882b63a18bab
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322289"
---
# <a name="communication-compliance-feature-reference"></a>通信合规性功能参考

## <a name="policies"></a>策略

> [!IMPORTANT]
> 不支持使用 PowerShell 创建和管理通信合规性策略。 若要创建和管理这些策略，必须使用 [Microsoft 365 通信合规性解决方案](https://compliance.microsoft.com/supervisoryreview) 中的策略管理控件。

你可以在 Microsoft 365 合规中心为 Microsoft 365 组织创建通信合规性策略。 通信合规性策略定义组织中需要审阅哪些通信和用户，定义通信必须满足的自定义条件，并指定应进行审阅的用户。 分配了通信合规性 *管理员* 角色的用户可以设置策略，分配了此角色的任何人都可以访问"通信合规性"页和Microsoft 365 合规中心。 如果需要，可以将策略修改历史记录导出到 .csv (逗号分隔值) 文件中，该文件还包括挂起审阅的警报、升级的项目和已解决项目的状态。 策略无法重命名，并且可在不再需要时删除。

> [!NOTE]
> 无法在安全与合规&中心为订阅创建的Office 365策略迁移到Microsoft 365。 如果要从 Office 365 订阅迁移到 Microsoft 365 订阅，则需要创建新的通信合规性策略来替换现有监督策略。

## <a name="policy-templates"></a>策略模板

策略模板是预定义的策略设置，可用于快速创建策略以解决常见的合规性方案。 其中每个模板在条件和范围上都有差异，并且所有模板都使用相同的扫描信号类型。 可以从以下策略模板中选择：

|**区域**|**策略模板**|**Details**|
|:-----|:-----|:-----|
| **冒犯性语言和反冒犯性语言** | 监视冒犯性语言的通信 | - 位置：Exchange Online、Microsoft Teams、Yammer、Skype for Business <br> - 方向：入站、出站、内部 <br> - 审阅百分比：100% <br> - 条件：冒犯性语言分类器 |
| **敏感信息** | 监视敏感信息的通信 | - 位置：Exchange Online、Microsoft Teams、Yammer、Skype for Business <br> - 方向：入站、出站、内部 <br> - 审阅百分比：10% <br> - 条件：敏感信息、开箱用内容模式和类型、自定义词典选项、大于 1 MB 的附件 |
| **法规遵从性** | 监视与财务监管合规性有关的信息的通信 | - 位置：Exchange Online、Microsoft Teams、Yammer、Skype for Business <br> - 方向：入站、出站 <br> - 审阅百分比：10% <br> - 条件：自定义词典选项，附件大于 1 MB |
| **冲突** | 监视两个组或两个用户之间的通信，以帮助避免兴趣冲突 | - 位置：Exchange Online、Microsoft Teams、Yammer、Skype for Business <br> - 方向：内部 <br> - 审阅百分比：100% <br> - 条件：无 |

自创建策略起，每 24 小时扫描一次通信。 例如，如果你在上午 11：00 创建冒犯性语言策略，该策略将每 24 小时在每天上午 11：00 收集通信合规性信号。 编辑策略不会更改这一次。 若要查看策略的上次扫描日期和时间，请导航到"策略"页上的"上次策略扫描 **"** 列。 创建新策略后，可能需要 24 小时才能查看第一次策略扫描日期和时间。 上次扫描的日期和时间将转换为本地系统的时区。

## <a name="pausing-a-policy-preview"></a>暂停策略 (预览) 

创建通信合规性策略后，如果需要，该策略可能会暂时暂停。 暂停策略可用于测试或解决策略匹配项问题，或优化策略条件。 在这些情况下，暂停策略还会保留现有策略警报和消息，用于正在进行的调查和审查，而不是删除策略。 暂停策略可阻止在策略暂停时检查策略中定义的所有用户邮件条件并生成警报。 若要暂停或重新启动策略，用户必须是 *Communication Compliance Admin 角色组* 的成员。

若要暂停策略，请导航到" **策略** "页，选择一个策略，然后从操作工具栏 **中选择"暂停** 策略"。 在 **"暂停策略** "窗格中，通过选择"暂停"确认要 **暂停该策略**。 在某些情况下，可能需要 24 小时才能暂停策略。 策略暂停后，不会创建与策略匹配的邮件警报。 但是，与在暂停策略之前创建的警报关联的邮件仍可用于调查、审阅和修正。

暂停的策略的策略状态可能指示以下几种状态：

- **Active：** 策略处于活动状态
- **已暂停**：策略已完全暂停。
- **暂停**：策略正在被暂停。
- **恢复**：正在恢复的策略。
- **恢复时出错**：恢复策略时遇到错误。 对于错误堆栈跟踪，将鼠标悬停在"策略"页上"状态"列中的"恢复状态时出错"上。
- **暂停时出错**：暂停策略时遇到错误。 对于错误堆栈跟踪，将鼠标悬停在"策略"页上"状态"列中的"暂停状态错误"上。

若要恢复策略，请导航到"策略 **"页，** 选择一个策略，然后从操作工具栏中选择" **恢复** 策略"。 在 **"恢复策略** "窗格中，通过选择"恢复"确认要恢复 **策略**。 在某些情况下，可能需要 24 小时才能恢复策略。 恢复策略后，将创建与策略匹配的邮件警报，并可用于调查、审阅和修正。

## <a name="permissions"></a>权限

> [!IMPORTANT]
> 默认状态下，全局管理员没有对通信合规性功能的访问权限。 在可以访问任何通信合规性功能之前，必须在此步骤中分配角色。

共有 5 个角色组，用于配置权限以管理通信合规性功能。 若要在 Microsoft 365 合规中心中将 **通信合规性** 作为菜单选项提供并继续执行这些配置步骤，必须将你分配给 *通信符合性* 或 *通信符合性管理员* 角色组。 若要在初始配置后访问和管理通信合规性功能，用户必须是至少一个通信合规性角色组的成员。

根据希望管理通信策略和警报的方式，你需要将用户分配到特定的角色组。 可以选择将具有不同的合规性职责的用户分配给特定角色组，以管理通信合规性功能的不同区域。 或者可以决定将指定管理员、分析者、调查者和查看者的所有用户账户分配到 *通信合规性* 角色组。 使用单个角色组或多个角色组，以充分符合你的合规性管理要求。

配置通信合规性时，请从这些角色组中进行选择：

|**角色组**|**角色组权限**|
|:-----|:-----|
| **通信合规性** | 使用此角色组在单个组中管理组织的通信合规性。 通过添加指定管理员、分析者、调查者和查看者的所有用户账户，可以在单个组中配置通信合规性权限。 此角色组包含所有通信合规性权限角色。 这一配置是通信合规性快速入门的最简单方式，非常适合不需要为单独用户组定义单独权限的组织。 |
| **通信合规性管理员** | 使用此角色组进行通信合规性初始配置，后期可将通信合规性管理员隔离到已定义组中。 分配到此角色组的用户可以创建、读取、更新和删除通信合规性策略、全局设置和角色组分配。 分配到此角色组的用户无法查看消息警报。 |
| **通信合规性分析者** | 使用此组向执行通信合规性分析者操作的用户分配权限。 分配给此角色组的用户可以查看分配为审阅者的策略、查看邮件元数据 (而不是邮件内容) 、升级为其他审阅者或向用户发送通知。 分析者不能解决挂起的警报。 |
| **通信合规性调查者** | 使用此组向执行通信合规性调查者操作的用户分配权限。 分配给此角色组的用户可以查看邮件元数据和内容、上报给其他审阅者、上报至 Advanced eDiscovery 案例、向用户发送通知以及解决警报。 |
| **通信合规性查看者** | 使用此组向管理通信报告的用户分配权限。 分配到此角色组的用户可以访问通信合规性主页上的所有报告小组件，并且可以查看所有通信合规性报告。 |

### <a name="for-organizations-using-the-original-permissions-and-role-groups"></a>对于使用原始权限和角色组的组织

新的角色组结构取代了用于通信合规性的初始角色组结构。 对于已使用通信合规性的组织，需要分配有监管审核管理员角色，才能开始了解组织中通信Microsoft 365 合规中心。 此外，您必须为具有监管审核管理员、案例管理、合规性管理员和审阅角色的审阅者创建新角色组，以调查和修正具有策略匹配项的邮件。 实质上，所有管理员和审阅者都在同一个角色组中，并且每个人都具有相同的访问和管理权限。 随着通信合规性的最新更新，您应计划从以前的角色组结构迁移到新的角色组结构。 对以前的角色组结构的支持将逐步淘汰。

为了帮助规划迁移，请考虑以下示例。 目前组织中有三种类型的用户，即 IT 管理员、会审和审阅者。 这三种类型的用户位于以前的角色组结构中，并且都是分配了以下角色的单个角色组的所有成员：

- 监管审核管理员
- 案例管理
- 合规性管理员
- 审阅

若要为这些用户更新新角色组结构的角色，并分隔用户的访问和管理权限，可以考虑使用三个新组和关联的新角色组分配：

- **IT 管理员**：分配到新的 *通信合规性管理员角色* 组。
- **会审**：分配到 *通信合规性分析员* 角色组。
- **审阅者**：分配到新的通信合规调查 *组* 角色组。

## <a name="supervised-users"></a>受监督用户

在开始使用通信合规性之前，必须确定需要审查谁的通信。 在策略中，用户的电子邮件地址可以标记需要接受监管的人员或组。 这些组的一些示例包括Microsoft 365组Exchange通讯组列表、Yammer社区以及Microsoft Teams频道。 你也可以设置特定的排除组或排除组列表，将特定的用户或组排除在审查范围外。 有关通信合规性策略中支持的组类型详细信息，请参阅 [通信合规性入门](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance)。

> [!IMPORTANT]
> 通信合规性策略涵盖的用户必须具有 Microsoft 365 E5 合规 许可证、Office 365 企业版 高级合规性加载项的 E3 许可证，或包含在 Office 365 企业版 E5 订阅中。 如果你没有现有的 E5 Enterprise，并且想要尝试通信合规性，可以注册[E5](https://go.microsoft.com/fwlink/p/?LinkID=698279)Office 365 企业版试用版。

## <a name="reviewers"></a>审阅者

创建通信合规性策略时，必须确定审阅受监督用户消息的用户。 在策略中，用户的电子邮件地址可以标记负责审查通信的人员或组。 所有审阅者都必须在邮箱上托管Exchange Online且必须分配到 *通信* 合规性分析或 *通信合规性调查* 角色。 审阅 (分析员或研究人员) 还必须分配 *通信合规性案例管理* 角色。 审阅者添加到策略时，他们会自动收到一封电子邮件，通知他们分配到此策略，并提供有关审阅过程的信息的链接。

## <a name="groups-for-supervised-users-and-reviewers"></a>受监督用户和审阅者的组

若要简化设置，请为需要审阅其通信的人创建组，为审阅这些通信的人创建组。 如果你已经在使用组，可能需要创建若干个组。 例如，如果想要监管两个不同组人员之间的通信，或者指定一个不受监管的组，这时候就需要创建若干个组。

在策略中分配通讯组时，该策略监视来自通讯组中每个用户的所有电子邮件。 在策略中Microsoft 365组时，策略将监视发送到该组的所有电子邮件，而不是每个组成员收到的单个电子邮件。

向通信合规性策略添加组和通讯组列表是整体条件和规则集的一部分，因此策略支持的最大组和通讯组列表数因也添加到策略中的条件数而异。 每个策略应支持大约 20 个组或通讯组列表，具体取决于策略中出现的其他条件数。

## <a name="supported-communication-types"></a>支持的通信类型

使用通信合规性策略，可以选择作为组或作为独立源扫描以下一个或多个通信平台中的邮件。 默认情况下，每个策略会保留跨这些平台捕获的通信七年，即使用户离开您的组织并删除其邮箱。

- **Microsoft Teams：** 可以扫描公共和专用Microsoft Teams和单个聊天中的聊天通信。 当用户分配到通信合规性策略，Microsoft Teams范围时，将在用户是成员的所有 Microsoft Teams自动监视用户的聊天通信。 Microsoft Teams策略模板自动包含此范围，并且默认情况下会在自定义策略模板中选中此范围。 Teams合规性策略条件匹配的聊天最多可能需要 48 小时才能处理。 使用以下组管理配置来监督用户聊天和频道中Teams：

    - **对于Teams通信：** 分配单个用户或 [将通讯组](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE)分配给通信合规性策略。 这个设置适用于一对一或一对多聊天。
    - **对于Teams频道通信：** 将Microsoft Teams要Microsoft 365的特定用户的组分配给通信合规性策略。 如果你将同一用户添加到其他 Microsoft Teams 频道或者 Microsoft 365 组，要确保将这些新频道和组也添加到通信合规性策略中。 如果频道的任何成员是策略中的受监督用户，并且策略中配置了入站方向，那么在频道内发送的所有邮件都需接受审阅，并且可能的策略与 (即使对于未明确监督) 的频道中的用户也一样。 例如，用户 A 是频道的所有者或成员。 用户 B 和用户 C 是同一频道的成员，并且使用与仅监督用户 A 的冒犯性语言策略相匹配的语言。用户 B 和用户 C 为频道内的对话创建策略匹配，即使这些对话未在冒犯性语言策略中直接监督。 Teams包括用户 A 的频道之外的用户 B 和用户 C 之间的对话不会受包含用户 A 的冒犯性语言策略影响。若要在频道的其他成员受到明确监督时排除频道成员监督，请关闭适用通信合规性策略中的入站通信方向设置。
    - **For Teams chat communications with hybrid email environments**： Communication compliance can monitor chat messages for organizations with an Exchange on-premises deployment or an external email provider that have enabled Microsoft Teams. 您必须为具有要监视本地邮箱或外部邮箱的用户创建通讯组。 创建通信合规性策略时，您将此通讯组分配为策略向导中的监督用户和组选择。 有关为本地用户启用基于云的存储和 Teams 支持的要求和限制，请参阅搜索本地用户的 Teams 聊天[数据](search-cloud-based-mailboxes-for-on-premises-users.md)。

- **Exchange电子邮件**：托管在 Exchange Online 或 Microsoft 365 Office 365 订阅中的邮箱均有资格进行邮件扫描。 Exchange合规性策略条件匹配的电子邮件和附件可能需要 24 小时才能处理。 通信合规性支持的附件类型与 [Exchange 邮件流规则内容检查支持的文件类型](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection)相同。

- **Yammer：** 可以扫描私人邮件和公用对话以及Yammer社区中的关联附件。 将用户添加到将 Yammer定义为定义的频道的通信合规性策略时，该用户是其中成员的所有 Yammer 社区之间的通信将包含在扫描过程中。 Yammer合规性策略条件匹配的聊天和附件最多可能需要 24 小时处理。 Yammer必须进入[本机模式](/yammer/configure-your-yammer-network/overview-native-mode)，通信合规性策略Yammer通信和附件。 在本机模式下，Yammer用户都Azure Active Directory (AAD) ，所有组Office 365组，所有文件都存储在 SharePoint Online 中。

- **Skype for Business Online**：可以审查 Skype for Business Online 中的聊天消息和有关附件。 Skype for Business Online 中匹配通信合规性策略条件的聊天内容和附件可能需要 24 小时处理。 监督聊天对话来自之前保存在[Skype for Business Online 的对话](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2)。  使用以下组管理配置监督 Skype for Business Online 中的用户聊天通信：

    - **For Skype for Business Online chat communications**： Assign individual users or assign a distribution [group](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) to the communication compliance policy. 这个设置适用于一对一或一对多聊天。

- **第三方源**：你可以扫描通信，以搜索从 Instant [Bloomberg、Slack、Zoom、SMS](archive-instant-bloomberg-data.md)等第三方源导入 Microsoft 365 [](archive-slack-data.md)组织中 [](archive-zoommeetings-data.md)邮箱的数据。 有关通信合规性支持的连接器的完整列表，请参阅存档 [第三方数据](archiving-third-party-data.md)。

    必须先为组织配置第三方Microsoft 365，然后才能将连接器分配到通信合规性策略。 通信 **合规性策略** 向导的"第三方源"部分仅显示当前配置的第三方连接器。

## <a name="policy-settings"></a>策略设置

### <a name="users"></a>用户

可以选择"所有用户 **"或在** 通信合规性策略中定义特定用户。 选择 **所有用户** 会将策略应用到所有用户和用户作为成员的所有组。 选择特定用户会将策略应用到特定用户和特定用户作为成员的所有组。

### <a name="direction"></a>方向

默认情况下，将显示 **Direction 为** 条件，并且无法删除。 单独或一起选择策略中的通信方向设置：

- **入站****：检测从** 外部和内部发件人（包括策略中其他受监督用户）发送给受监督用户的通信。
- **出站**：检测从受监督用户发送到外部和内部收件人（包括策略中其他受监督用户）的通信。
- **内部**：检测 **策略** 中受监督用户或组之间的通信。

### <a name="sensitive-information-types"></a>敏感信息类型

您可以选择将敏感信息类型作为通信合规性策略的一部分。 敏感信息类型是预定义的或自定义的数据类型，可帮助识别和保护信用卡号、银行帐号、护照号等。 作为 [了解数据丢失](dlp-learn-about-dlp.md)防护的一部分，敏感信息配置可以使用模式、字符邻近度、可信度甚至自定义数据类型来帮助标识和标记可能敏感的内容。 默认敏感信息类型为：

- 金融
- 医疗和健康
- 隐私
- 自定义信息类型

若要了解有关敏感信息详细信息以及默认类型中包含的模式的详细信息，请参阅 [敏感信息类型实体定义](sensitive-information-type-entity-definitions.md)。

### <a name="custom-keyword-dictionaries"></a>自定义关键字词典

配置自定义关键字词典 (或词典) ，以提供对特定于您的组织或行业的关键字的简单管理。 关键字词典最多支持 100 KB 的字词 (词典中的) 压缩后关键字，并支持任何语言。 压缩后租户限制也是 100 KB。 如果需要，可以将多个自定义关键字词典应用于一个策略，或者每个策略具有一个关键字词典。 这些字典在通信合规性策略中分配，并且可以从文件 (如 .csv 或 .txt 列表) ，或者从可以在合规性中心导入[的列表。](create-a-keyword-dictionary.md) 当你需要支持特定于你的组织和策略的术语或语言时，请使用自定义词典。

### <a name="classifiers"></a>分类器

内置的可训练和全局分类器扫描组织中所有通信渠道发送或接收的邮件，以发现不同类型的合规性问题。 分类器将人工智能和关键字组合来识别消息中可能违背反骚扰策略的内容。 内置分类器当前支持多种语言的邮件关键字标识：

- 简体中文
- 英语
- 法语
- 德语
- 意大利语
- 日语
- 葡萄牙语
- 西班牙语

通信合规性内置可训练和全局分类器扫描针对以下类型语言和内容的术语、图像和情绪的通信：

- **成人图像**：扫描本质上非常明确的图像。
- **种族 (预览) ：** 扫描明确的语言，与其他社区相比，对英语（美国）/非洲黑色社区尤其敏感。
- **Gory 图像**：扫描描述暴力和暴力的图像。
- **亵亵**：扫描使大多数人为难的亵亵表达式。
- **Racy 图像**：扫描本质上是建议但包含的显式内容少于视为成人的图像的图像。
- **针对性的冒犯**：扫描针对有关种族、颜色、种族、国家/地区的人的冒犯性行为。
- **威胁**：扫描对人员或属性实施暴力或身体损害的威胁。

*"成人**"、Racy* 和 *Gory* 图像分类器扫描 .jpeg、.png、.gif 和 .bmp 格式的文件。 图像文件的大小必须小于 4 MB (MB) 并且图像的尺寸必须大于 50x50 像素和大于 50 KB (KB) ，图像才符合评估条件。 图像标识受电子邮件Exchange Online频道和聊天Microsoft Teams支持。

内置可训练和全局分类器并未提供这些领域的术语或图像的详尽列表。 此外，语言和文化标准会不断改变，因此，Microsoft 保留自行决定更新分类器的权利。 虽然分类器可帮助组织监视这些方面，但分类器并不适合提供组织监视或处理此类语言或图像的唯一方式。 你的组织（而非 Microsoft）仍负责与监视、扫描和阻止这些领域的语言和图像相关的所有决策，包括遵守本地隐私和其他适用法律。 Microsoft 鼓励在部署和使用之前咨询法律顾问。

> [!NOTE]
> 使用分类器的策略将检查和评估字数为 6 或更大值的邮件。 在使用分类器的策略中，不评估包含少于 6 个单词的邮件。 若要识别包含不当内容的较短邮件并采取措施，我们建议在监控此类内容的通信合规性策略中包含自定义关键字词典。

有关可训练分类器在Microsoft 365的信息，请参阅可[训练分类器入门](classifier-get-started-with.md)。

### <a name="optical-character-recognition-ocr"></a>光学字符识别 (OCR)

配置内置或自定义通信合规性策略，以扫描和识别组织中可能不适合的图像中的打印或手写文本。 集成的 [Azure 认知服务和](/azure/cognitive-services/computer-vision/overview-ocr) 用于识别图像文本的光学扫描支持可帮助分析员和研究人员检测并处理在主要非文本通信中可能错过不当行为的实例。

可以从模板、 (自定义策略) 新策略中启用光学字符识别功能，以扩展对处理嵌入图像和附件的支持。 在从策略模板创建的策略中启用时，电子邮件和聊天消息中的嵌入或附加图像Microsoft Teams自动扫描。 对于自定义策略，必须在策略中配置一个或多个与关键字、内置分类器或敏感信息类型关联的条件设置，以允许选择 OCR 扫描。

扫描和处理采用以下图像格式的 50 KB 到 4 MB 的图像：

- .jpg/.jpeg (联合图像专家组) 
- .png (可移植网络图形) 
- .bmp (位图) 
- .tiff (标记图像文件格式) 
- .pdf (可移植文档格式) 

> [!NOTE]
> 目前，仅电子邮件.pdf嵌入和附加图像进行扫描和提取。

在查看启用 OCR 的策略的挂起警报时，标识并匹配策略条件的图像将显示为关联警报的子项。 可以查看原始图像，以在原始邮件的上下文中评估标识的文本。 检测到的图像最多可能需要 48 小时才能与警报一起提供。

### <a name="conditional-settings"></a>条件设置
<a name="ConditionalSettings"> </a>

为策略选择的条件适用于来自组织中电子邮件和第三方源的通信， (Instant Bloomberg) 。

下表对每种条件进行进一步说明。

|**Condition**|**如何使用此条件**|
|:-----|:-----|
| **内容与这些分类器中的任意一个匹配** | 当邮件中包含或排除任何分类器时，应用于策略。 某些分类器在租户中预定义，自定义分类器必须单独配置，然后才能用于此条件。 策略中只能将一个分类器定义为条件。 有关配置分类器的详细信息，请参阅了解可训练分类器 ([预览) 。 ](classifier-learn-about.md) |
| **内容包含这些敏感信息类型中的任意一种** | 在邮件中包含或排除任何敏感信息类型时，应用于策略。 某些分类器在租户中预定义，自定义分类器可以单独配置，也可以作为条件分配过程的一部分进行配置。 您选择的每个敏感信息类型都单独应用，只有其中一种敏感信息类型才能将策略应用于邮件。 有关自定义敏感信息类型的信息，请参阅了解 [敏感信息类型](sensitive-information-type-learn-about.md)。 |
| **从这些域中的任何域接收邮件**  <br><br> **未从这些域中收到邮件** | 应用策略以包含或排除接收的邮件中的特定域或电子邮件地址。 输入每个域或电子邮件地址，用逗号分隔多个域或电子邮件地址。 每个输入的域或电子邮件地址将单独应用，只有一个域或电子邮件地址才能将策略应用于邮件。 <br><br> 如果要扫描来自特定域的所有电子邮件，但希望排除不需要查看 (新闻稿、公告等) 的邮件，则必须配置"未从这些域接收邮件"条件，以排除电子邮件地址 (例如"newsletter@contoso.com") 。  |
| **邮件发送到这些域中的任何域**  <br><br> **不会将邮件发送到这些域中的任何域** | 应用策略以在已发送的邮件中包括或排除特定域或电子邮件地址。 输入每个域或电子邮件地址，用逗号分隔多个域或电子邮件地址。 每个域或电子邮件地址单独应用，只有一个域或电子邮件地址才能将策略应用于邮件。 <br><br> 如果要扫描发送到特定域的所有电子邮件，但希望排除不需要审阅的已发送邮件，则必须配置两个条件： <br> - **将邮件发送到** 定义域名称的任一域 ("contoso.com") ， AND <br> - **不会向这些域条件** 中的任一域发送邮件，该条件会 ("subscriptions@contoso.com") 。 |
| **邮件通过这些标签中的任意一个进行分类**  <br><br> **邮件未使用这些标签中的任一分类** | 在邮件中包含或排除某些保留标签时应用策略。 保留标签必须单独配置，并且已配置的标签将选作此条件的一部分。 你选择的每个标签将单独应用 (其中一个标签必须应用，策略才能应用于邮件) 。 有关保留标签详细信息，请参阅 [了解保留策略和保留标签](retention.md)。|
| **邮件包含以下任何词语**  <br><br> **邮件不包含这些词语** | 若要在邮件中包含或排除某些字词或短语时应用该策略，请输入每个用逗号分隔的单词。 对于两个或多个单词的短语，请使用引号将短语括起来。 您输入的每个单词或短语将单独 (一个单词，才能将策略应用于邮件) 。 若要详细了解如何输入字词或短语，请参阅下一部分[Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords)。|
| **Attachment 包含以下任何词语**  <br><br> **Attachment 不包含这些词语** | 若要在邮件附件中包含或排除某些字词或短语时应用该策略 (如 Word 文档) ，请输入每个用逗号分隔的单词。 对于两个或多个单词的短语，请使用引号将短语括起来。 您输入的每个单词或短语将单独 (一个单词，才能将策略应用于附件) 。 若要详细了解如何输入字词或短语，请参阅下一部分[Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords)。|
| **附件是其中任一文件类型**  <br><br> **附件不是这些文件类型** | 若要监督包含或排除特定类型的附件的通信，请输入文件扩展名 (如.exe或.pdf) 。 如果要包含或排除多个文件扩展名，请在单独的行中输入这些扩展名。 只有一个附件扩展名才能应用策略。|
| **邮件大小大于**  <br><br> **邮件大小不大于** | 若要根据特定大小查看邮件，请使用这些条件指定邮件在经过审阅之前可以达到的最大或最小大小。 例如，如果指定邮件大小大于 \> **1.0 MB，** 则所有大于 1.01 MB 的邮件都需接受审阅。 这种情况下，您可以选择字节、千字节、兆字节或千兆字节。|
| **附件大于**  <br><br> **附件大小不超过** | 若要根据邮件附件的大小检查邮件，请指定邮件及其附件受审阅之前附件可以达到的最大或最小大小。 例如，如果指定 **Attachment 大于** \> **2.0 MB，** 则所有附件为 2.01 MB 及更大的邮件都需接受审阅。 这种情况下，您可以选择字节、千字节、兆字节或千兆字节。|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>将字词和短语与电子邮件或附件匹配
<a name="Matchwords"> </a>

每个输入和用逗号分隔的单词将单独应用 (只有一个单词适用于策略条件才能应用于电子邮件或附件) 。 例如，让我们使用条件"邮件包含以下任何词语"，关键字"银行"、"机密"和"内部交易"之间用逗号 (，机密，"预览体验成员交易") 分隔。 该策略适用于包含字词"银行"、"机密"或短语"insider trading"的任何邮件。 只有出现其中一个字词或短语，才能应用此策略条件。 邮件或附件中的单词必须与输入内容完全匹配。

> [!IMPORTANT]
>
> 导入自定义词典文件时，必须使用回车符和单独的行分隔每个单词或短语。 例如：
>
> *一个* <br>
> *confidential* <br>
> *预览体验成员交易*

若要扫描电子邮件和附件中的相同关键字，请创建一个数据丢失防护[](create-test-tune-dlp-policy.md)策略，该策略包含自定义[](create-a-keyword-dictionary.md)关键字词典，用于查找想要在邮件中扫描的术语。 此策略配置标识电子邮件或电子邮件附件中 **已定义的关键字** 。 使用标准条件策略设置 (*Message* 包含其中任何词语，并且 *Attachment* 包含以下任何词语) 来标识邮件和附件中的术语，需要术语同时存在于邮件和附件中。

#### <a name="enter-multiple-conditions"></a>输入多个条件

如果输入多个条件，Microsoft 365条件一起确定何时将通信合规性策略应用于通信项目。 设置多个条件时，必须满足所有条件才能应用策略，除非输入例外。 例如，您需要一个在邮件包含单词"trade"且大于 2 MB 时应用的策略。 但是，如果邮件还包含单词"Contoso financial approved by Contoso financial"，则不应应用该策略。 本示例中，将按如下方式定义三个条件：

- **邮件包含以下任何词语**，关键字为"trade"
- **邮件大小大于 ，** 值为 2 MB
- **邮件不包含这些单词，** 关键字为"由 Contoso 财务团队批准"

### <a name="review-percentage"></a>审阅百分比

如果要减少要审阅的内容量，可以指定由通信合规性策略控制的所有通信的百分比。 一个随机的样本会从匹配所选策略条件的内容中被实时选取出来。 如果你想要审查者所有项目，可以在通信合规性策略中配置 **100%** 审查。

## <a name="privacy"></a>隐私

保护具有策略匹配项的用户的隐私非常重要，并且有助于在通信合规性警报的数据调查和分析审查中提高对象的性。 此设置仅适用于显示通信合规性解决方案的用户名。 它不会影响名称在其他合规性解决方案或管理中心中的显示方式。

对于通信合规性匹配的用户，可以在通信合规性设置中选择以下 **设置之一**：

- **显示用户名的** 匿名版本：用户名被匿名处理，以防止 *Communication Compliance Analyst* 角色组的用户看到与策略警报相关联的用户。 通信合规 *调查角色* 组的用户将始终看到用户名，而不是匿名版本。 例如，在通信合规性体验的所有方面，用户"Grace Grace"都会显示随机化假名，如"AnonIS8-988"。 选择此设置会匿名处理具有当前和过去策略匹配项的所有用户，并适用于所有策略。 选择此选项后，通信合规性警报详细信息中的用户配置文件信息将不可用。 但是，将新用户添加到现有策略或向新策略分配用户时，将显示用户名。 如果选择关闭此设置，将显示具有当前或过去策略匹配项的所有用户的用户名。
- **不显示用户名的** 匿名版本：将显示通信合规性警报的所有当前和过去策略匹配项的用户名。 用户配置文件信息 (所有通信合规性警报) 显示的名称、职务、别名以及组织或部门信息。

## <a name="notice-templates"></a>通知模板

如果要在问题解决过程中向用户发送策略匹配的电子邮件提醒通知，可以创建通知模板。 通知只能发送到与生成特定警报进行修正的策略匹配关联的用户电子邮件地址。 选择要作为修正工作流的一部分应用于策略违反的通知模板时，可以选择接受模板中定义的字段值或根据需要覆盖这些字段。

通知模板是自定义电子邮件模板，可以在其中定义通信合规性设置区域中的以下 **邮件** 字段：

|**Field**|**Required**| **Details** |
|:-----|:-----|:-----|
|**模板名称** | 是 | 修复过程中将在通知工作流中选择的通知模板的友好名称支持文本字符。 |
| **发件人地址** | 是 | 一个或多个用户或组的地址，这些用户或组通过策略匹配（从订阅的 Active Directory 选择）向用户发送邮件。 |
| **抄送和密件抄送地址** | 否 | 要接收策略匹配通知的可选用户或组（从订阅的 Active Directory 中选择）。 |
| **Subject** | 是 | 邮件主题行中显示的信息支持文本字符。 |
| **邮件正文** | 是 | 邮件正文中显示的信息支持文本或 HTML 值。 |

### <a name="html-for-notices"></a>通知的 HTML

如果要为通知创建多个基于文本的简单电子邮件，可以在通知模板的邮件正文字段中使用 HTML 来创建更详细的邮件。 以下示例提供基于 HTML 的基本电子邮件通知模板的邮件正文格式：

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

> [!NOTE]
> 通信合规性通知模板中的 HTML href 属性实现当前仅支持单引号，而不支持 URL 引用的双引号。

## <a name="filters"></a>筛选器

通信合规性筛选器允许你筛选和排序警报消息，以便更快地调查和修正操作。 筛选在每个策略的 **"** 挂起" **和"** 已解决"选项卡上可用。 若要将筛选器或筛选器集另存为保存的筛选器查询，必须将一个或多个值配置为筛选器选择。 下表概述了筛选器详细信息：

|**Filter**|**Details**|
|:-----|:-----|
| **Date** | 组织中用户发送或接收邮件的日期。 若要筛选一天，请选择一个日期范围，从希望结果的日期开始，到第二天结束。 例如，如果要筛选 9/20/2020 的结果，请选择筛选日期范围 9/20/2020-9/21/2020。|
| **文件类** | 基于邮件类型（邮件或附件）*的邮件**类*。 |
| **具有附件** | 邮件中的附件状态。 |
| **Item 类** | 基于消息类型、电子邮件、Microsoft 团队聊天、Bloomberg 等的消息源。有关常见项目类型和邮件类的详细信息，请参阅 [项目类型和邮件类](/office/vba/outlook/concepts/forms/item-types-and-message-classes)。 |
| **收件人域** | 邮件发送到的域。 默认情况下，此域Microsoft 365订阅域。 |
| **收件人** | 邮件发送到的用户。 |
| **Sender** | 发送消息的人。 |
| **发件人域** | 发送邮件的域。 |
| **Size** | 邮件的大小（以 KB 为单位）。 |
| **主题/标题** | 消息主题或聊天标题。 |
| **Tags** | 分配给邮件的标记，可以是 *Questionable* *、Compliant* 或 *Non-compliant*。 |
| **Language** | 邮件中检测到的文本语言。 邮件根据大多数邮件文本的语言进行分类。 例如，对于同时包含德语和意大利语文本的邮件，但大多数文本为德语，该邮件被归类为德语 (DE) 。 支持以下语言：简体中文 (-ZH) 、英语 (EN) 、法语 (FR) 、德语 (DE) 、意大利语 (IT) 、日语 (JP) 、葡萄牙语 (PT) 和西班牙语 (ES) 。 例如，若要筛选分类为德语和意大利语的邮件，请在"语言 (搜索框中输入"DE，IT") 2 位数字的语言代码。 若要查看检测到的邮件语言分类，请选择一封邮件，选择"查看邮件详细信息"，然后滚动到 EmailDetectedLanguage 字段。 |
| **升级到** | 作为邮件升级操作一部分包含的用户的用户名。 |
| **分类器** | 应用于邮件的内置和自定义分类器的名称。 一些示例 *包括冒犯性语言*、*定向冒犯**、冒犯性*、*威胁* 等。

## <a name="alert-policies"></a>警报策略

配置策略后，将自动创建相应的警报策略，并针对与策略中定义的条件匹配的邮件生成警报。 默认情况下，所有策略匹配警报触发器在关联的警报策略中均分配有中等严重性级别。 在关联的警报策略中达到聚合触发器阈值级别后，会为通信合规性策略生成警报。

对于通信合规性策略，默认情况下配置以下警报策略值：

|**警报策略触发器**|**默认值**|
|:-----|:-----|
| 聚合 | 简单聚合 |
| 阈值 | 4 个活动 |
| Window | 60 分钟 |

> [!NOTE]
> 活动的警报策略阈值触发器设置支持通信合规性策略的最小值为 3 或更高。

可以在安全与合规中心的警报策略页面上更改针对活动数、活动的时间段和警报策略中特定用户的触发器&默认设置。 

### <a name="change-the-severity-level-for-an-alert-policy"></a>更改警报策略的严重性级别

如果要更改特定通信合规性策略的警报策略中分配的严重性级别，请完成以下步骤：

1. 使用 Microsoft 365 组织中的管理员账户凭据登录 [https://compliance.microsoft.com](https://compliance.microsoft.com)。

2. 在"Microsoft 365 合规中心中，转到"**策略"。**

3. 选择 **Office 365** 策略"页上的"警报策略"页面，打开"Office 365安全与合规 **&"页面**。

4. 选中要更新的通信合规性策略的复选框，然后选择"编辑 **策略"。**

5. 在" **说明** "选项卡上，选择" **严重性"** 下拉列表以配置策略警报级别。

6. 选择 **"** 保存"将新严重性级别应用于策略。

7. 选择 **"关闭** "退出警报策略详细信息页面。

## <a name="power-automate-flows"></a>Power Automate流

[Microsoft Power Automate](/power-automate/getting-started)是一种工作流服务，可跨应用程序和服务自动执行操作。 通过使用来自模板的流或手动创建的流，可以自动执行与这些应用程序和服务关联的常见任务。 启用通信Power Automate流时，可以自动执行警报和用户的重要任务。 您可以配置Power Automate流，以在用户具有通信合规性警报和其他应用程序时通知管理员。

具有包含Microsoft 365合规性的订阅的客户无需额外的 Power Automate 许可证，就可使用建议的默认通信合规性Power Automate模板。 可以自定义默认模板以支持您的组织并涵盖核心通信合规性方案。 如果您选择使用这些模板中的高级 Power Automate 功能、使用 Microsoft 365 合规性连接器创建自定义模板或使用 Microsoft 365 中其他合规性领域的 Power Automate 模板，您可能需要其他 Power Automate 许可证。

> [!IMPORTANT]
> 在测试流时是否收到有关其他许可证验证Power Automate提示？ 您的组织可能尚未收到此预览功能的服务更新。 更新正在部署中，具有 Microsoft 365 订阅（包括通信合规性）的所有组织都应具有到 2020 年 10 月 30 日从推荐的 Power Automate 模板创建的流的许可证支持。

![通信合规性Power Automate](../media/communication-compliance-power-automate.png)

以下Power Automate模板提供给客户，以支持通信合规性警报的流程自动化：

- **当用户具有通信合规性警报** 时通知经理：当用户具有通信合规性警报时，某些组织可能需要立即发送管理通知。 配置和选择此流后，会向案例用户的经理发送一封电子邮件，包含有关所有警报的以下信息：
  - 警报的适用策略
  - 警报的日期/时间
  - 警报的严重性级别

### <a name="create-a-power-automate-flow"></a>创建Power Automate流

若要从Power Automate模板创建流，在警报中直接操作时 **，你将** 使用"自动化"控件中的"管理 Power Automate 流"选项。 若要使用管理Power Automate **流创建Power Automate** 流，您必须是至少一个通信合规性角色组的成员。

完成以下步骤以创建Power Automate模板的流：

1. In the Microsoft 365 合规中心， go to **Communication compliance**  >  **Policies** and select the policy with the alert you want review.
2. 从策略中选择"挂起 **"** 选项卡并选择挂起的警报。
3. Select **Power Automate** from the alert action menu.
4. 在 **"Power Automate"** 页上，从页面上的"通信合规性模板 **"部分选择** 默认模板。
5. 该流将列出该流所需的嵌入连接，并显示连接状态是否可用。 如果需要，请更新任何未显示为可用的连接。 选择 **继续**。
6. 默认情况下，推荐流预配置了推荐的通信合规性，Microsoft 365为流完成分配的任务所需的服务数据字段。 如果需要，使用"显示高级选项"控件并配置流组件的可用属性来自定义流组件。
7. 如果需要，通过选择"新建步骤"按钮将任何其他步骤 **添加到** 流中。 在大多数情况下，建议的默认模板不需要此更改。
8. 选择 **"保存草稿**"以保存流以稍后进行进一步配置，或选择"保存"以完成流的配置。
9. 选择 **"** 关闭"返回到"Power Automate"页面。 新模板将在"我的流"选项卡上作为流列出，并自动从 Power Automate 控件中为在使用通信合规性警报时创建流的用户使用。

### <a name="share-a-power-automate-flow"></a>共享Power Automate流

默认情况下，Power Automate创建的流仅对该用户可用。 若要使其他通信合规性用户具有访问权限并使用流，流创建者必须共享该流。 若要共享流，在警报中直接操作 **时** Power Automate控件。

若要共享Power Automate流，您必须至少是一个通信合规性角色组的成员。
完成以下步骤以共享Power Automate流：

1. In the Microsoft 365 合规中心， go to **Communication compliance**  >  **Policies** and select the policy with the alert you want review.
2. 从策略中选择"挂起 **"** 选项卡并选择挂起的警报。
3. Select **Power Automate** from the alert action menu.
4. 在 **"Power Automate流**"页上，选择"**我的** 流"或"**团队流"** 选项卡。
5. 选择要共享的流 **，然后从** "流选项"菜单中选择"共享"。
6. 在"流共享"页上，输入要添加为流所有者的用户或组的名称。
7. 在" **已使用** 连接"对话框中，选择 **"确定** "确认添加的用户或组将具有对流的完全访问权限。

### <a name="edit-a-power-automate-flow"></a>编辑Power Automate流

如果需要编辑流，则直接在警报中Power Automate控件。  若要编辑Power Automate流，您必须至少是一个通信合规性角色组的成员。

完成以下步骤以编辑Power Automate流：

1. In the Microsoft 365 合规中心， go to **Communication compliance**  >  **Policies** and select the policy with the alert you want review.
2. 从策略中选择"挂起 **"** 选项卡并选择挂起的警报。
3. Select **Power Automate** from the alert action menu.
4. 在 **"Power Automate流"** 页上，选择要编辑的流。 从 **流控制** 菜单中选择"编辑"。
5. 选择省略 **号设置** 更改流组件设置或省略号"删除"  >    >  以删除流组件。
6. 选择 **"保存****"，** 然后选择"关闭"以完成流的编辑。

### <a name="delete-a-power-automate-flow"></a>删除Power Automate流

如果需要删除流，则直接在警报中Power Automate控件。  若要删除Power Automate流，您必须至少是一个通信合规性角色组的成员。

完成以下步骤以删除Power Automate流：

1. In the Microsoft 365 合规中心， go to **Communication compliance**  >  **Policies** and select the policy with the alert you want review.
2. 从策略中选择"挂起 **"** 选项卡并选择挂起的警报。
3. Select **Power Automate** from the alert action menu.
4. 在 **"Power Automate流**"页上，选择要删除的流。 从 **流控制** 菜单中选择"删除"。
5. 在删除确认对话框中，选择 **"删除** "以删除流，或选择" **取消** "退出删除操作。

## <a name="reports"></a>报表

新的 **"报告** "仪表板是查看所有通信合规性报告的中央位置。 报告小组件提供对通信合规性活动状态进行总体评估最常用的见解的快速视图。 报表小部件中包含的信息不可导出。 详细报告提供与特定通信合规性领域相关的深入信息，并提供在查看时筛选、分组、排序和导出信息的能力。

![通信合规性报告仪表板](../media/communication-compliance-reports-dashboard.png)

" **报告"** 仪表板包含以下报表小组件和详细报告链接：

- **最近的策略匹配** 小组件：按活动策略显示一段时间的匹配数。
- **按策略小部件解析** 的项目：显示策略在一段时间之后解析的策略匹配警报数。
- **具有大多数策略匹配** 小组件的用户：显示用户 (匿名用户名或匿名) 指定时间段的策略匹配数。
- **具有最多匹配项** 的策略小组件：显示给定时段的策略和匹配项数，对匹配项的排名从高到低。
- **按策略小部件进行** 升级：显示给定时间内每个策略的升级数。
- **策略设置和状态** 详细报告：详细查看策略配置和设置，以及邮件上每个策略 (和操作) 的常规状态。 包括策略信息以及策略如何与用户和组、位置、审阅百分比、审阅者、状态以及策略的上次修改时间相关联。 使用 *"* 导出"选项创建.csv报告详细信息的报表文件。
- **每个策略的项目和操作详细** 报告：查看和导出匹配的项以及每个策略的修正操作。 包括策略信息以及策略如何与：

    - 匹配的项
    - 已升级项目
    - 已解决项目
    - 标记为合规
    - 标记为不兼容
    - 标记为有问题
    - 待审阅的项目
    - 已通知用户
    - 已创建案例

    使用 *"* 导出"选项创建.csv报告详细信息的报表文件。
- **每个位置的项目和操作** 详细报告：查看和导出每个位置的匹配项目和Microsoft 365操作。 包括有关工作负荷平台如何与以下平台关联的信息：

    - 匹配的项
    - 已升级项目
    - 已解决项目
    - 标记为合规
    - 标记为不兼容
    - 标记为有问题
    - 待审阅的项目
    - 已通知用户
    - 已创建案例

    使用 *"* 导出"选项创建.csv报告详细信息的报表文件。
- **按用户详细** 报告的活动：查看和导出匹配项以及每个用户的修正操作。 包括有关用户如何关联的信息：

    - 匹配的项
    - 已升级项目
    - 已解决项目
    - 标记为合规
    - 标记为不兼容
    - 标记为有问题
    - 待审阅的项目
    - 已通知用户
    - 已创建案例

    使用 *"* 导出"选项创建.csv报告详细信息的报表文件。

- **每个位置的敏感信息** 类型详细报告 (预览) ：查看和导出有关检测通信合规性策略中的敏感信息类型和关联源的信息。 包括组织中配置的源中的敏感信息类型实例的总体总数和具体细目。 示例包括：

    - **电子邮件**：在电子邮件中检测到Exchange类型。
    - **Teams：** 在聊天频道和聊天Microsoft Teams检测到的敏感信息类型。
    - **Skype for Business：** 在用于业务通信Skype检测到的敏感信息类型。
    - **Yammer：** 在收件箱、Yammer、聊天和回复中检测到的敏感信息类型。
    - **第三方源**：为与组织中配置的第三方连接器关联的活动检测到的敏感信息类型。 若要查看报告中特定敏感信息类型的第三方源细分，请将鼠标悬停在"第三方源"列中敏感信息类型的值上。
    - **其他**：用于内部系统处理的敏感信息类型。 选择或取消选择报表的此源不会影响任何值。

    使用 *"* 导出"选项创建.csv报告详细信息的报表文件。 每个第三方源的值都显示在第三方源文件.csv列中。

## <a name="audit"></a>Audit

在某些情况下，您必须向法规或合规性审核员提供相关信息，以证明监督用户活动和通信。 此信息可能是与已定义的组织策略相关联的所有活动的摘要，或者通信合规性策略发生更改时。 通信合规性策略具有内置的审核跟踪，可完全准备内部或外部审核。 通信策略会捕获每个创建、编辑和删除操作的详细审核历史记录，以提供监管程序的证明。

> [!IMPORTANT]
> 必须先为组织启用审核，然后才能记录通信合规性事件。 若要启用审核，请参阅[启用审核日志。](communication-compliance-configure.md#step-2-required-enable-the-audit-log) 当活动触发在 Microsoft 365 审核日志 捕获的事件时，可能需要 48 小时才能在通信合规性策略中查看这些事件。

若要查看通信合规性策略更新活动，请在任何策略的主页上选择"导出策略更新"控件。 必须分配有全局管理员或 *通信合规性管理员* 角色才能导出更新活动。 此操作将生成包含以下信息.csv审核文件：

|**Field**|**Details**|
|:-----|:-----|
| **CreationDate** | 在策略中执行更新活动的日期。 |
| **UserIds** | 在策略中执行更新活动的用户。 |
| **Operations** | 对策略执行的更新操作。 |
| **AuditData** | 此字段是所有策略更新活动的主数据源。 所有更新活动都记录和用逗号分隔符分隔。 |

若要查看策略的通信合规性审阅活动，请选择特定策略的"概述"页上的"导出审阅活动"控件。 必须分配有全局管理员或 *通信合规性管理员* 角色才能导出审阅活动。 此操作将生成包含以下信息.csv审核文件：

|**Field**|**Details**|
|:-----|:-----|
| **CreationDate** | 在策略中执行审阅活动的日期。 |
| **UserIds** | 在策略中执行审阅活动的用户。 |
| **Operations** | 对策略执行的审阅操作。 |
| **AuditData** | 此字段是所有策略审阅活动的主数据源。 所有审阅活动都由逗号分隔符进行记录和分隔。 |

您还可以在统一部署中或审核日志 [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell cmdlet 查看审核活动。 若要了解有关保留策略审核日志，请参阅管理审核日志 [保留策略](audit-log-retention-policies.md)。

例如，以下示例返回所有监管审核活动的活动， (策略和规则) ：

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

此示例返回通信合规性策略的更新活动：

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

此示例返回与当前通信合规性策略匹配的活动：

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

通信合规性策略匹配项存储在每个策略的监督邮箱中。 在某些情况下，您可能需要检查监督邮箱的大小，以确保未接近当前 50 GB 的限制。 如果达到邮箱限制，则不捕获策略匹配项，并且您需要创建一个使用相同设置 (的新策略) 以继续捕获相同活动的匹配项。

若要检查策略监督邮箱的大小，请完成以下步骤：

1. 使用 连接 PowerShell V2 模块中的[Exchange Online-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline) cmdlet，使用新式Exchange Online连接到 PowerShell。
2. 在 PowerShell 中运行以下命令：

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```

## <a name="transitioning-from-supervision-in-office-365"></a>在管理中从监督Office 365

使用组织中监督策略Office 365应立即计划转换为组织中通信合规性策略Microsoft 365并需要了解以下要点：

- Office 365中的监督解决方案已被 Microsoft 365 中的通信合规性解决方案完全Microsoft 365。 我们建议在通信合规性中创建新策略，这些策略的设置与现有监督策略相同，以使用新的调查和修正改进。
- 在策略匹配中Office 365保存在监督中的邮件不能移动或共享到 Microsoft 365。
- 对于在转换过程中并行使用这两个解决方案的组织，每个解决方案中使用的策略必须具有唯一的策略名称。 在过渡期间，可以在两种策略之间共享组和自定义关键字词典。

有关停用信息，Office 365，请参阅Microsoft 365[路线图](https://www.microsoft.com/microsoft-365/roadmap)了解详细信息。

## <a name="ready-to-get-started"></a>准备好开始了吗?

若要为组织配置通信合规性Microsoft 365，请参阅为组织配置通信[Microsoft 365合规性](communication-compliance-configure.md)。
