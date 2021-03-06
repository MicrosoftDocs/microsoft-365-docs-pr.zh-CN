---
title: '在 Microsoft 隐私管理中心预览版 (和管理) '
f1.keywords:
- CSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- M365-privacy-management
search.appverid:
- MOE150
- MET150
description: 了解如何创建和管理用于处理组织中个人数据的策略，Microsoft 365响应警报以及修正问题。
ms.openlocfilehash: f9df027d01ffe4629654db1ddd006d141d57e387
ms.sourcegitcommit: 022d9d91263994c48efcebe08a84319573dc3a8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2021
ms.locfileid: "53378485"
---
# <a name="create-and-manage-policies-in-privacy-management-preview"></a>在隐私管理与预览版 (和管理) 

本文内容：了解如何构建和自定义用于处理个人数据的策略、获取有关策略匹配项的警报以及修正 **问题**。

## <a name="purpose-of-policies"></a>策略的用途

策略允许你定义在公司的 Microsoft 365 数据中查找的隐私风险类型，并针对找到匹配项的方案建立首选结果。 你的组织可以从生成的警报中工作，以检查任何匹配的数据和修正问题，所有这些都来自隐私管理解决方案中。

隐私管理提供了模板，便于你轻松开始制定策略，并允许你通过大量自定义选项微调你的方法。 隐私管理模板涵盖的关键方案包括：

- **数据过度曝光**：检测过度曝光的个人数据，并提示用户保护这些数据。
- **数据传输**：发现并帮助限制跨部门或区域边界传输个人数据。
- **数据最小化**：帮助用户识别和减少未使用的个人数据量。

若要了解有关每个模板的功能的详细信息，请参阅下文。

## <a name="policy-types"></a>策略类型

### <a name="data-overexposure"></a>数据过度显示

隐私管理可帮助你检测和处理存储的数据不够安全的情况。 例如，如果对内部网站的访问权限对一个组开放得过宽，或者权限设置尚未保持最新，则存储在该站点上的个人数据可能很容易遭到泄露。 可以使用隐私管理的数据策略模板来评估数据，并提醒你注意潜在问题。

### <a name="data-transfer"></a>数据传输

跨部门或区域边界传输数据可能会增加数据泄露的风险，例如，如果通过未加密的电子邮件或未经授权的收件人发送数据。 此类操作可能会影响法规，也可能违反既定的隐私实践。 使用数据传输模板创建隐私管理策略可以发现并帮助限制此类传输。

> [!NOTE]
> 在公共预览版期间，某些运行数据传输策略以检测跨区域的传输的租户可能会遇到同步问题，这些问题会影响对 Exchange 和 Teams 匹配项的可见性。 我们建议在预览此策略SharePoint时OneDrive和定义数据。 预计 2021 年秋季将更新此问题。

### <a name="data-minimization"></a>数据最小化

随着时间的推移，公司可以从客户或员工收集大量的个人数据。 有时，这包括已收集的超出需求或未使用且应减少的数据，以限制该信息的隐私风险。 数据最小化模板可用于应对这种类型的风险。

## <a name="get-started-with-default-templates"></a>默认模板入门

隐私管理将有助于启动数据评估过程，方法为创建三个使用默认设置的策略，使用用于数据最小化、数据过度利用和数据传输的模板。 默认情况下，这些策略将启用，但不会自动触发通知邮件或修正提示。 初始设置后，可以继续创建和自定义自己的策略。

## <a name="create-a-privacy-management-policy"></a>创建隐私管理策略

创建隐私管理策略有两种途径。 第一个选项是选择预定义模板集。 您还可以自定义自己的策略，以这些模板中的任一模板作为起点。

### <a name="create-a-policy-from-a-template"></a>从模板创建策略

若要开始使用策略，请选择三种预先设置的策略类型之一。 若要查看有关其中任何一项的详细信息，可以选择"查看设置"以查看策略的特定属性，包括数据类型、数据位置以及触发策略匹配的条件。

当直接从模板创建策略时，将自动选择许多设置。 这包括在默认情况下打开策略。 如果你想要在完全激活策略之前预览它，可在创建后在列表中找到它，编辑该策略，然后将其切换到测试模式。 有关详细信息，请参阅测试 [策略](#test-your-policy)。

### <a name="create-custom-policy"></a>创建自定义策略

若要精细控制策略设置，可以使用现有模板之一作为基准创建自定义策略。 隐私管理提供了向导，可指导你完成这些步骤。

可自定义的属性包括：

- **名称和类型**：选择构建策略的模板，然后命名并描述你的版本。
- **要监视的数据**：选择策略将监视的个人数据类型。 从可用的分类组中选择，或从单个敏感信息类型的列表中选择。 若要了解更多信息，请参阅下面的选择数据监视选项。
- **用户**：选择此策略是应用于所有用户还是所选用户。 如果选择第二个选项，则最多可以从提供的列表中选择 300 个用户。
- **位置**：选择策略应Microsoft 365的位置，例如组织的SharePoint或Exchange数据。
- **条件**：为策略类型选择相关条件。 例如，可以指定数据传输策略应查找的传输类型，或最近使用数据最小化策略的数据。
- **结果**：定义检测到策略匹配时的结果。 你的选项取决于你开始的策略类型。 可能的结果包括：
  - **电子邮件通知**：此设置允许你触发摘要电子邮件通知，包括指向相关培训的链接。 有关详细信息，请参阅下面的设置用户电子邮件通知。
  - **Teams：** 为用户提供Teams提示和建议，以及指向相关培训的链接。 此选项可用于数据传输策略。
- **警报**：确定检测到策略匹配时向管理员发出警报的频率。 选项包括无警报、每个策略匹配项的警报或达到特定阈值时发出警报。 如果选择阈值选项，请设置所需的参数。
- **模式**：决定是先在测试模式下运行策略，还是立即打开它。 有关详细信息，请参阅测试策略。
完成向导中所有设置后，请查看设置，必要时进行任何最终编辑，并保存策略。

#### <a name="choose-data-monitoring-options"></a>选择数据监视选项

设置自定义策略时，将要求您选择策略应监视的数据类型。 相关选项如下所示：

- **分类组**：基于关键隐私法规（如 GDPR 或 HIPAA）的数据集的可搜索列表。 查看任何组的详细信息，以查看其涵盖的敏感信息类型。 选择其中一个或多个集以按其用途使用。 当前可用的组如下所示：
  - 澳大利亚健康记录法案 (HRIP 法案) 增强
  - 澳大利亚隐私法案增强
  -  (欧盟) 一般数据保护条例 (GDPR) 增强
  - 日本个人身份信息 (PII) 数据增强
  - 日本增强的个人信息保护
  - 美国格雷姆-格雷姆-巴雷法案 (GLBA) 增强版
  - 美国健康保险法案 (HIPAA) 增强
  - 增强美国爱国者法案
  - 美国个人身份信息 (PII) 数据增强
  - 增强的州泄露通知法律
- **单个敏感信息** 类型：通过自行选择特定敏感信息类型（如社会保险号或驾驶证信息）可以自定义要查找的一组或多组数据。 此向导允许你从隐私管理中的敏感信息类型的完整列表中选择。 每个信息类型都有自己的属性。 使用其中任何一个旁边的"信息"按钮了解有关建议设置的详细信息和注释。 如果创建多个组，向导允许您应用布尔运算符来关联它们并定义它们的操作顺序。

如果使用预先设置的分类组，则不能同时选择单个类型或创建自己的组。 为获得最大灵活性，请选择各个敏感信息类型。 若要使用最常见的标准，请从分类组中选择。

#### <a name="test-your-policy"></a>测试策略

如果你想要在完全激活新策略之前评估它，请设置你的策略以测试模式。 通过测试模式，你可以查找过去 30 天内的匹配项、衡量策略的行为并查看生成的警报类型。 我们建议至少运行五天的测试策略，以获得具有代表性的结果。 在测试阶段，可以选择编辑和调整策略设置。 通过运行测试获得见解后，可以继续启用策略。 当策略在测试模式下运行时，不会传递任何用户通知邮件。

#### <a name="set-user-email-notifications"></a>设置用户电子邮件通知

使用电子邮件通知，用户可以收到有关策略匹配项和要完成的重要任务的直接通知。 收件人将收到汇总要审阅的数据和可能的操作的电子邮件摘要，例如使文档成为私有文档、将其保留为文件、报告任何误报匹配以及添加备注供将来参考。 这些电子邮件还包括一些链接，供培训收件人了解如何处理这些情况。 在最初设置通知时，需要提供这些链接，并且应指向您自己的有关流程和最佳做法的内部文档。

可以在自定义策略创建期间或编辑任何策略时为个别策略启用通知。 使用"结果"部分定义在检测到策略匹配时会发生什么情况，包括启用这些通知的选项，并设置希望这些摘要传送多久。

电子邮件通知功能在全局范围内设置。 默认情况下处于启用状态。 关闭此设置将停止所有电子邮件，即使已在单个策略级别配置了特定通知。 有关详细信息，请参阅隐私管理入门 [下的配置设置](privacy-management-setup.md#configure-settings)。

## <a name="view-policy-details"></a>查看策略详细信息

创建策略后，在主策略页面上选择 **它以查看其** 完整概述。 "策略详细信息"页将提供对数据的见解，使您可以查看有关特定策略匹配的内容，并提供有关下一步的建议。 如果策略在测试模式下运行，此页面也是在测试完成后启用策略的地方。

策略处于活动状态后，可以继续查看其策略详细信息页面，以查看对问题区域、警报严重性和趋势以及采取的更正措施持续进行的见解。

## <a name="resolve-policy-alerts-and-issues"></a>解决策略警报和问题

一旦激活了策略，隐私管理将通知你策略匹配项、对策略严重性进行评分，以及通过创建和解决问题来采取措施，从而让你了解重要发现。

隐私管理的"概述"页提供了这些发现，其中提供了有关关键关注领域的动态更新，例如匹配最多的策略和当前处于活动状态的策略警报。 您还可以通过主策略页访问有关警报和问题的详细信息。

### <a name="alerts"></a>警报

若要评估活动警报并指定需要跟进的问题，请访问 **"警报"** 页面。 它提供策略生成的警报的可筛选列表，您可以单独查看这些警报以确定触发它们的情况。

选择任何警报将打开一个包含其他详细信息（如策略类型、匹配项目数和策略设置判断的严重性）的飞过窗格。 在 **"内容** "选项卡下，你可以查看此警报中涉及的文件。 此信息可提供有关触发警报的特定事件、文件所在的位置以及所涉及的个人数据类型的其他见解。 警报触发器由每个策略的特定条件确定。 例如，如果隐私管理检测到策略的指定部门或区域之间的传输，则可能会触发数据传输策略上的警报。

评估列表中的任何警报后，可以使用创建 **问题操作来** 提示进一步调查和操作。 将要求你为问题命名并添加任何相关的上下文注释。 如果警报不需要跟进，也可以在此处消除警报。

### <a name="issues"></a>问题

如警报部分中所述，在评估有关策略匹配的警报时将创建问题。 若要跟进并解决指示的问题，请访问"问题"页。 你可以在此处查看各个问题、调查诉讼条件、查看数据，然后采取必要步骤来关闭案例。

此页面提供所有未解决问题的列表。 问题按名称列出，并按严重性排序，以帮助你确定事例的优先级，包括高、中和低类别以及未分配。 选择列表中的任何问题，查看其内容并采取措施解决该问题。 可以在审阅期间为未分配的问题提供严重级别。

#### <a name="issue-overview"></a>问题概述

问题详细信息页面有助于指导你完成解决已识别的隐私风险并正确处理指示的文件的过程。 On the **Overview** tab you can see the current step to take， indicating the status of the issue and the next recommended actions. 还可以查看有关所涉及的内容、关联策略、警报详细信息和时间线的基本信息。

后续选项卡提供有关关联警报和内容的更多详细信息，以及团队中正在解决该问题的其他人提供的任何注释。 可以通过"协作者"选项卡管理活动 **参与者** 列表。

#### <a name="share-the-issue"></a>共享问题

通过将人员添加为协作者，你可以通过安全的 Microsoft Teams 频道、公司电子邮件或通过在隐私管理中直接共享问题页面的链接来与企业的其他成员共享问题。 这些选项在"共享"按钮 **下** 可用。 通过 Teams 进行共享时，将要求您从组织中可用的团队中选择，选择特定频道，并留下与指定频道共享的问题消息。

#### <a name="review-content-and-remediate"></a>查看内容和修正

若要查看与问题关联的内容，请选择"查看内容"操作（如果提示）或打开"内容"选项卡。选择列表中的任意文件以完整查看。 如果已执行之前的步骤来管理此文件，则你可以在此处查看有关文件的详细信息、记录的任何活动及其修正历史记录。

使用 **"修正"** 按钮为此内容做出自己的数据处理决策。 选择该按钮后，您可以从一个或多个修正操作中选择。 选项包括：

**所有策略**

- **通知**：通知内容所有者检测到的问题。
- **应用保留标签**：为此项添加有关数据保留的标签。 
- **应用敏感度标签**：添加关于此项数据的敏感度的标签。
- **标记为不匹配**：将搜索结果标识为误报，以从考虑事项中删除内容项。

**数据最小化**

- **回收/删除**：使用此选项软删除数据。 内容将移动到已删除邮件文件夹或回收站 (Exchange、SharePoint、OneDrive) ，或者选择恢复 (Teams邮件) 。 可以在一段设定时间内撤销删除操作，具体取决于服务的设置。

**数据过度使用和数据传输**

- **取消共享**：停止共享指向此内容项的链接。

每个选项都会提示您先为内容所有者留下注释和任何其他必需的支持信息，然后再确认您的选择。

执行所有修正步骤并准备好关闭问题后，请使用"解决"按钮，在提交之前添加最终注释。

## <a name="delete-a-policy"></a>删除策略

如果需要删除现有隐私管理策略，请在"策略"页上的列表中找到它，选择"操作"菜单 ("垂直省略号) "删除策略"操作。 在删除为最终删除并永久删除策略之前，将要求您确认您的选择。 删除策略不会影响之前由策略评估的任何文件，并且策略生成的问题和警报将保留。
