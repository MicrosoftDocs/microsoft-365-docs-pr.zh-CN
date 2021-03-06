---
title: 在 Microsoft 合规性管理器中生成和管理评估
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 在 Microsoft 合规性管理器中生成评估，帮助你满足对组织非常重要的法规和认证要求。
ms.openlocfilehash: 7014e294454095456acdac8e2c60895c400ced3f
ms.sourcegitcommit: 41c7f7bd5c808ee5ceca0f6efe13d4e67da0262b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2021
ms.locfileid: "53419603"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>在合规性管理器中生成和管理评估

**本文内容：** 了解如何通过创建和管理评估来为组织自定义合规性 **管理器**。 本文将指导你完成如何创建评估、如何将评估组织到组中、使用控件 **、接受更新** 以及导出 **评估报告**。

## <a name="introduction-to-assessments"></a>评估简介

合规性管理器可帮助你创建评估是否符合适用于组织的行业和区域法规的评估。 评估基于评估模板的框架构建，该框架包含必要的控制措施、改进措施以及 Microsoft 完成评估的操作（如果适用）。 为组织设置最相关的评估可以帮助您实施策略和运营过程，以限制合规性风险。

所有评估都列在合规性管理器的评估选项卡上。 了解有关如何 [筛选评估视图和解释状态状态的信息](compliance-manager-setup.md#assessments-page)。

> [!IMPORTANT]
> 组织可用于生成评估的模板取决于您的许可协议。 [查看许可详细信息](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)。

## <a name="data-protection-baseline-default-assessment"></a>数据保护基线默认评估

为了开始操作，Microsoft 在合规性管理器中提供了针对Microsoft 365 **基准的默认评估**。 此基线评估具有一组针对数据保护关键法规和标准以及一般数据管理的控制措施。 此基线主要来自 NIST CSF (国家标准和技术网络安全协会) 和 ISO (国际标准化组织) ，以及 FedRAMP (联邦风险和授权管理计划) 以及欧盟) 的 GDPR (一般数据保护条例。

此评估用于在配置任何其他评估之前，在首次访问合规性管理器时计算初始合规性分数。 合规性管理器从你的解决方案中收集Microsoft 365信号。 你可以一目了然地查看组织相对于关键数据保护标准和法规的表现，并查看建议的改进措施。

随着构建和管理自己的评估以满足组织的特定需求，合规性管理器将变得更加有用。

## <a name="understand-groups-before-creating-assessments"></a>在创建评估之前了解组

创建评估时，需要将其分配给组。 组是一些容器，允许您按符合逻辑的方式（如按年份或法规，或基于组织的部门或地理位置）组织评估。 这就是我们建议你在创建评估之前规划分组策略的原因。

下面是两个组及其基础评估的示例：

- **FFIEC IS assessment 2020**
  - FFIEC IS
- **数据安全和隐私评估**
  - ISO 27001：2013
  - ISO 27018：2014

一个或多个组内的不同评估可能会共享改进操作。 改进操作可能是你在映射到租户的技术解决方案（如启用双重身份验证）中所做的更改，或者是对在系统外部执行的非技术操作（如制定新的工作场所策略）所做的更改。 对技术改进操作进行的详细信息或状态的任何更新都将由所有组的评估选取。 非技术改进行动更新将由应用这些更新的组中评估识别。 这样，您可以同时实施一个改进操作并满足多个要求。

### <a name="create-a-group"></a>创建群组

可以在创建新评估时创建一个组。 组不能创建为独立实体。

### <a name="what-to-know-when-working-with-groups"></a>使用组时要了解哪些方面

- 一个组必须至少包含一个评估。
- 组名称在组织中必须是唯一的。
- 组没有安全属性。 所有权限都与评估相关联。
- 向组添加评估后，无法更改分组。
- 如果向现有组添加新评估，则该组中评估的常见信息将复制到新评估。
- 完成时，同一组内不同评估中的相关评估控制措施将自动更新。
- 组可以包含针对相同认证或法规的评估，但每个组只能包含一个特定产品认证对的评估。 例如，一个组不能包含针对 Office 365 和 NIST CSF 的两个评估。 只有在针对同一产品的相应认证或法规不同时，组才能包含针对同一产品的多个评估。
- 删除评估会破坏该评估与组之间的关系。
- 无法手动删除组。

## <a name="create-assessments"></a>创建评估

若要创建评估，你将使用向导选择它应该使用的模板并设置评估的属性。 模板包含基于不同隐私法规和标准认证的评估控制措施和操作建议。 您组织的可用模板可能包括作为许可协议的一部分包含的一个或多个模板，以及您购买的其他高级模板。 每个模板（无论是包含还是高级模板）都存在于两个版本中：一个版本用于 Microsoft 365，另一个版本可针对您使用的其他产品进行定制。 若要详细了解模板，请参阅 [使用评估模板](compliance-manager-templates.md)。

> [!NOTE]
> 只有具有全局管理员、合规性管理器管理或合规性管理器评估员角色的用户才能创建和修改评估。 详细了解角色 [和权限](compliance-manager-setup.md#set-user-permissions-and-assign-roles)。

若要开始构建评估，请按照以下步骤操作。

1. 了解您将评估分配到哪个组，或者准备为此评估创建新组。

2. 打开评估向导。 可以从两处之一访问此飞出窗格：
    - Go to your **assessments** page in Compliance Manager and select **Add assessment**;或
    - 在评估模板选项卡上找到想要使用的模板，查看其详细信息，然后选择创建 **评估**。 这将填充向导的模板选择字段。

3. **选择模板**：如果还没有在步骤 2 中选择模板，请选择模板作为评估的基础。 你将看到分为包含和高级类别的模板列表， ([模板](compliance-manager-templates.md#template-availability-and-licensing) 类型了解) 。 选择所选模板旁边的单选按钮，然后选择"下一 **步"。**

4. **产品、名称和组：** 设置这些属性以标识评估、选择要评估的产品，并将其分配给组。

    - **产品**：如果你使用的是通用模板，请选择你是为新产品创建此评估，还是为已在合规性管理器中定义的现有自定义产品创建此评估。 如果您选择新产品，请输入其名称。 请注意，在使用通用Microsoft 365时，不能选择产品作为产品。 如果使用自定义Microsoft 365，将填充此字段以指示Microsoft 365无法更改。
    - **名称**：在"评估名称"字段中输入 **评估的名称** 。 评估名称在组中必须是唯一的。 如果你的评估名称与任意给定组中另一个评估的名称相匹配，你将收到一个错误，要求您创建其他名称。
    - **组**：将评估分配到组。 您可以：
        - 选择 **"使用现有** 组"将其分配给已创建的组;或
        - 选择 **创建新组** 以创建新组，并将此评估分配给它：
            - 确定组的名称，在单选按钮下方的字段中输入该名称。
            - 通过 **选择相应的框，** 可以从现有组（如实现和测试详细信息和文档）复制数据。

    完成后，选择下一 **步**。

5. **查看并完成：** 向导的最后一个屏幕显示为评估选择的模板、名称和组。 你可以从屏幕上的链接编辑其中任何设置，这将返回到向导中的相关步骤。 准备就绪后，选择创建 **评估**。

6. 下一个屏幕将确认已成功创建新评估。 选择 **"** 完成"关闭向导，屏幕上将显示新评估的详细信息页面。

如果在选择"创建评估"**后** 看到"评估失败"屏幕，请选择"重试"以重新创建评估。

创建评估后，可以通过选择评估详细信息页面右上角的"编辑名称"按钮来[更改评估名称](#monitor-assessment-progress-and-controls)。

## <a name="monitor-assessment-progress-and-controls"></a>监视评估进度和控制

每个评估都有一个详细信息页面，其中提供了完成评估的进度的概览。 该页显示您完成控件的进度，以及这些控件中关键改进操作的测试状态。

### <a name="overview-tab"></a>"概述"选项卡

"概述"选项卡包含显示完成评估的百分比的图形。 此图包含你拥有的操作的分项细目和 Microsoft 拥有的操作的分数，因此你可以看到完成评估还需要多少点。

评估中控制措施的关键改进措施按获得分数的潜在影响最大顺序列出。 关联的图表详细介绍了改进操作聚合的测试状态，以便快速判断已经过测试的情况以及需要完成的操作。

若要访问单个改进操作，请访问" **控件** "选项卡或" **你的改进操作"** 选项卡。

### <a name="controls-tab"></a>控件选项卡

"控件"选项卡显示映射到评估的每个控制措施的详细信息。 控件 **状态细分** 图表按系列显示控件的状态，因此您可以一目了然地查看哪些控件分组需要关注。

在图表下方，表格列出了评估中每个控件的详细信息。 控件按控件系列进行分组。 展开每个系列名称以显示其包含的单个控件。 每个控件列出的信息包括：

- **控件标题**
- **状态**：反映控件中改进操作的测试状态 
    - **通过** - 所有改进操作均具有"通过"的测试状态，或至少一项通过，其余操作均"超出范围"
    -  **失败** - 至少有一个改进操作的测试状态为"失败"
    - **无** - 所有改进操作都未经过测试
    - **超出范围** - 所有改进操作均超出此评估范围
    - **进行** 中 - 改进操作的状态与上面列出的不同，可能包括"正在进行"、"部分信用"或"未检测"
- **控件 ID：** 控件的标识号，由相应的法规、标准或策略分配
- **获得点数**：完成操作获得的点数（总可实现分数数） 
- **操作**：要完成的操作总数中的完成操作数
- **Microsoft 操作**：Microsoft 完成的操作数

若要查看控件的详细信息，请从控件在表格中的行中选择它。 "控件详细信息"页显示一个指示该控件内操作的测试状态的图形。 此图下方的表格显示了该控件的关键改进操作。

从列表中选择改进操作以深入了解改进操作的详细信息页。 详细信息页面显示测试状态和实现说明，并启动到建议的解决方案中。

### <a name="your-improvement-actions-tab"></a>"改进操作"选项卡

改进操作选项卡列出了评估中由组织管理的所有控制措施。 状态栏详细介绍评估中改进操作聚合的测试状态，以便快速判断已测试内容以及需要完成的操作。 栏下方是改进操作的完整列表和关键详细信息，包括：测试状态、潜在和挣点的数量、关联的法规和标准、适用的解决方案、操作类型和控制系列。 详细了解操作 [如何参与合规性分数](compliance-score-calculation.md#action-types-and-points)。

选择改进操作以查看其详细信息页面，然后选择"立即启动"链接以打开解决方案以采取操作。

### <a name="microsoft-actions-tab"></a>Microsoft 操作选项卡

将显示"Microsoft 操作"选项卡，用于基于Microsoft 365版本的评估。 它列出了评估中由 Microsoft 管理的所有操作。 该列表显示了关键操作详细信息，包括：测试状态、参与整体合规性分数的分数、相关的法规和标准、适用的解决方案、操作类型和控制系列。 选择改进操作以查看其详细信息页面。

详细了解如何 [跟踪控制措施和改进操作并评分。](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>接受评估更新

当更新可用于评估时，你将看到一条通知，并且可以选择接受更新或延迟更新以稍后进行。

### <a name="what-causes-an-update"></a>导致更新的原因

当存在影响评分的基础模板更改时，将发生评估更新。 更改可能涉及根据法规更改或产品更改调整控制映射或其他指南。 评估更新可能源自 (，例如，在 Microsoft 和 Microsoft [](compliance-manager-templates.md#modify-a-template)) 修改自定义模板时。

如果 Microsoft 更新你扩展的合规性管理器模板，则你的评估将在你接受这些更新后继承这些更新。 在扩展评估时，评估将保留应用于评估的其他属性。

您创建的自定义评估不会收到来自 Microsoft 的任何模板更新。 自定义评估可以接收改进行动更新，但用于控制评估与改进行动之间的映射的任何 Microsoft 更新不适用于自定义模板。

> [!NOTE]
> 评估更新仅适用于组级别。 如果你有两个基于同一模板构建的评估，它们存在于两个不同的组中，则每个评估将具有一个挂起的更新通知，并且你将需要分别接受对各自组中每个评估的更新。

#### <a name="where-youll-see-assessment-update-notifications"></a>你将在哪里看到评估更新通知

评估详细信息页面还会在评估 **旁边** 显示"挂起的更新"标签以及更新。 选择该评估以进入其详细信息页面。

评估详细信息页面顶部附近的一条消息显示该评估提供了更新。 选择 **横幅中的"** 查看更新"按钮，查看特定更改并接受或延迟更新。

评估详细信息页面可能还列出了旁边有"挂起 **的更新"** 标签的改进操作。 这些更新适用于对改进操作本身进行的特定更改，需要单独接受。 若要 [了解更多信息，请访问接受更新以改进](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) 操作。

#### <a name="review-update-to-accept-or-defer"></a>查看更新以接受或延迟

从 **评估详细信息页面** 选择"审阅更新"后，屏幕右侧将显示一个飞出窗格。 该飞出窗格提供了以下有关挂起更新的关键详细信息：

- 模板标题
- Microsoft、 (或特定用户的更新源) 
- 更新的创建日期
- 说明更新的概述
- 有关更改的特定详细信息，包括对合规性分数的影响、评估完成进度以及改进操作和控制措施的特定更改数。

选择 **"更新的模板**"链接将下载一Excel文件，其中包含包含挂起更新的模板版本的控件数据。 选择 **"当前模板** "链接将下载现有模板的文件，而不进行更改。

若要接受更新并更改评估，请选择"接受 **更新"。** 接受的更改是永久性的。

如果选择" **取消"，** 则更新不会应用于评估。 但是，您将继续看到"挂起的更新" **通知，** 直到您接受更新。

**为何我们建议接受更新**

接受更新有助于确保你拥有有关使用解决方案和采取相应改进操作的最新指南，以帮助你满足当前认证的要求。

**为什么您可能需要延迟更新**

如果正在完成评估，你可能希望确保在接受可能中断控制映射的评估更新之前已完成对评估的工作。 可以在审阅更新飞出窗格中选择"取消"，将更新延迟一段时间。

## <a name="export-an-assessment-report"></a>导出评估报告

可以将评估导出到组织Excel合规性利益干系人或外部审核员和监管机构的配置文件。 在评估详细信息页面上，选择页面顶部附近的"生成报告"按钮，这将创建一Excel可保存和共享的报告文件。

该报告是自导出日期和时间起评估的快照。 它包含由你和 Microsoft 管理的控制措施的详细信息，包括实现状态、测试日期和测试结果。

## <a name="delete-an-assessment"></a>删除评估

删除评估会将其从评估页面的列表中删除。 请注意以下有关删除评估的重要要点：

- **删除评估是永久性的;你无法返回它。** 如果要再次使用相同的评估，则需要重新创建它。
- 如果评估中的改进操作未显示在任何其他评估中，则删除评估后，这些操作将被删除。
- 建议 [在永久删除](#export-an-assessment-report) 评估前导出评估报告。

若要删除评估，请按照以下步骤操作：

1. 从 **评估页面** ，选择要删除的评估以打开该评估的详细信息页面。

2. 选择 **屏幕** 右上角的"删除评估"。

3. 将显示一个窗口，要求您确认是否要永久删除评估。 选择 **"删除评估** "以关闭该窗口。 你会收到一个确认窗口，表明你的评估已从合规性管理器中删除。

如果删除组中唯一的评估，则该组也将从合规性管理器中删除。

> [!NOTE]
> 无法删除所有评估。 组织至少需要一项评估，合规性管理器正常运行。 如果要删除的评估是唯一一个，在删除另一个评估之前添加另一个评估。
