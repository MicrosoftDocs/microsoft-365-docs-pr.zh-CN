---
title: 修正在 Office 365 中传递的恶意电子邮件
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.service: Microsoft Threat Protection
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: ''
search.appverid: MET150
description: 威胁补救措施
appliesto:
- Microsoft Threat Protection
ms.openlocfilehash: eb86c0b8e5368a42daa1002de5ac361613037090
ms.sourcegitcommit: 41bc923bb31598cea8f02923792c1cd786e39616
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "45086687"
---
# <a name="remediate-malicious-email-that-was-delivered-in-office-365"></a>修正在 Office 365 中传递的恶意电子邮件

修正是指针对威胁采取禁止操作。 发送到组织中的恶意邮件可能会通过系统、ZAP （零小时自动清除）或安全团队（如 "移动到收件箱"、"移动到垃圾邮件"、"移动到已删除邮件" 文件夹、"软删除" 或 "硬删除"）清除。 Office 高级威胁防护（Office ATP） P2/E5 为安全操作团队提供了通过手动搜寻和自动调查来调解电子邮件和协作问题中的威胁的能力。

> [!NOTE]
> 为了使安全小组能够修正电子邮件，需要向其分配搜索和清除角色。 角色分配通过安全与合规中心中的权限完成。 <p>

## <a name="what-you-need-to-know-before-you-begin"></a>开始之前需要了解的内容

若要执行某些操作（如查看邮件头或下载电子邮件内容），您必须具有一个名为*Preview*的新角色，并将其添加到另一个相应的角色组。 下表阐明了所需的角色和权限。

|活动  |角色组 |是否需要预览角色？  |
|---------|---------|---------|
|使用威胁浏览器（和实时检测）分析威胁     |全局管理员 <br> 安全管理员 <br> 安全读取者     | 否   |
|使用威胁资源管理器（和实时检测）查看电子邮件的邮件头，以及预览和下载隔离的电子邮件    |全局管理员 <br> 安全管理员 <br>安全读取者   |       否  |
|使用威胁浏览器查看邮件头并下载传递给邮箱的电子邮件     |全局管理员 <br>安全管理员 <br> 安全读取者 <br> Preview   |   是      |

> [!NOTE]
> *预览*是一个角色，而不是角色组;必须将预览角色添加到 Office 365 的现有角色组中。 全局管理员角色分配了 Microsoft 365 管理中心（ [https://admin.microsoft.com](https://admin.microsoft.com) ），安全管理员和安全读者角色是在安全 & 合规中心（）中分配的 [https://protection.office.com](https://protection.office.com) 。 若要了解有关角色和权限的详细信息，请参阅[Security & 合规性中心中的权限。](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?view=o365-worldwide)

> [!NOTE]
> 管理员可以对电子邮件执行所需的操作，但若要获得批准的操作，必须通过安全和合规中心 > 权限为其分配 "搜索和清除" 角色。

## <a name="manual-and-automated-remediation"></a>手动和自动修正

当安全团队使用威胁资源管理器中的搜索和筛选功能手动识别威胁时，将进行**手动搜寻**。 在找到需要修正的一组电子邮件之后，可以通过任何电子邮件视图（恶意软件、网络钓鱼或所有电子邮件）触发电子邮件的手动修正。

![按日期手动搜寻 Office 365 中的威胁资源管理器。](../../../media/tp-RemediationArticle1.png "威胁资源管理器")

可以通过威胁资源管理器以多种方式完成电子邮件的选择：

1. 手动选择电子邮件：这意味着安全操作团队可以在各自的视图中使用筛选器，并从需要修正的威胁资源管理器中选择几封电子邮件。 选择电子邮件的上限值为100（100）。 安全操作团队无法手动挑选超过一百封电子邮件。

2. 查询选择：安全操作团队可以使用顶部的 "全选" 按钮来选择整个查询。 同样的查询也会显示在操作中心邮件提交详细信息中。

3. 具有排除的查询选择：有时，安全操作团队决定通过选择整个查询并从查询中排除几封电子邮件来修正电子邮件。 若要执行此操作，管理员可以使用 "全选" 复选框，然后向下滚动以手动排除几封电子邮件。 查询可以容纳的最大电子邮件数为1000（1000），最大排除数为100（100），在此示例中。

从威胁 Explorer 中选择电子邮件后，修复创建可以通过直接操作来开始，也可以通过对电子邮件进行排队以进行操作：

1. 直接批准：当使用适当权限的安全人员选择 "移动到收件箱"、"移动到垃圾邮件"、"移动到已删除的项目"、"软删除"、"硬删除" 等操作时，安全人员将选择具有适当权限的操作，修正过程将开始执行选定的操作。 临时浮出控件将显示正在进行的修正。

2. 两步批准：不具有适当权限的管理员或需要等待更长时间执行该操作的管理员可以采取 "添加到修正" 操作。 在这种情况下，不会直接执行修正操作。 相反，电子邮件将添加到必须经过审批才能执行的修正容器中。 在对修正进行批准之前，将不会修正该电子邮件。 在批准了补救措施之后，将对电子邮件执行操作。

**自动调查和响应（空中）** 操作由警报资源管理器中的警报或安全操作团队触发。 它们可能包括安全操作团队必须批准的一些建议中介。 自动调查中的 "操作" 选项卡上包含这些修正操作。  

:::image type="content" source="../../../media/tp-RemediationArticle3.png" alt-text="包含恶意软件的邮件是 Zapped 页，显示了 Zap 执行的时间。":::

通过威胁浏览器创建的所有中介（直接批准或两步审批）以及来自自动调查的批准的操作将显示在操作中心中，可通过 "*审阅* >  **操作中心**" 下的左侧导航进行访问。

:::image type="content" source="../../../media/tp-RemediationArticle4.png" alt-text="包含受日期和严重性的威胁列表的操作中心。":::

操作中心显示过去30天内的所有修正操作。 通过资源管理器执行的操作显示在创建修正时由安全操作团队提供的相同名称。 通过自动调查进行的操作是通过与触发调查的相关警报（例如 "Zap 电子邮件群集 ..."）开始的标题共同展示的。

可以打开每个补救项以查看有关它的详细信息。 在打开修正项目时，将显示基本修正详细信息、修正名称、创建日期、说明、威胁严重性和状态。 它还显示两个选项卡。 

1. **"邮件提交" 选项卡**：这些是通过威胁浏览器提交的电子邮件数或要修正的自动调查数。 这些电子邮件可以是：

可操作：可对以下云邮箱位置中的电子邮件进行**操作**和移动，即 remediable 类别中的任何电子邮件都可以从一个位置移动到另一个位置：
  - Inbox 
  - 可疑  
  - 已删除文件夹
  - 软删除文件夹

>[!NOTE]
> 目前，只有拥有邮箱访问权限的最终用户才能恢复软删除文件夹中的项目。

**不可行**：以下位置的电子邮件不能作为电子邮件操作的一部分进行操作或移动，例如，非 remediable 类别中的电子邮件不能移动到非 remediable 类别中，也不能移动到 remediable 中。 非 remediable 位置为：

  - 隔离
  - 硬删除文件夹
  - 本地/external
  - 失败/丢弃
  
提交的可疑邮件被分类为 remediable 或非 remediable。 在大多数情况下，remediable 和非 remediable 邮件应添加到提交的邮件总数。 但是，在极少数情况下，提交的邮件可能不会添加到 remediable 和非 remediable 项目的总和，并且可以高于或低于提交的邮件总数。 出现这种情况的原因可能是系统延迟、超时或过期邮件。 邮件将根据您的组织的浏览器保留期而过期。

除非您在组织的浏览器保留期之后修正旧邮件，否则，如果您发现数字不一致，则建议重新尝试修正项目。 对于系统延迟，修复更新通常在几小时内进行刷新。

如果组织在浏览器中的电子邮件保留期为30天，并且您正在修正29-30 天后的电子邮件，则邮件提交次数可能不会因为电子邮件可能已开始移出保留期而无法总添加。

如果中介在一段时间内处于 "正在进行" 状态，则可能是由于系统延迟。 修正可能需要几个小时的时间。 由于系统延迟，在邮件提交计数中可能会发现，由于某些电子邮件不是查询的一部分，因此可能会出现在邮件提交计数方面的变化。 在这种情况下，最好重新尝试修正。  

为获得最佳结果，应在50k 或更低的电子邮件的较小批次中完成补救措施。  

在邮件提交过程中的所有电子邮件中，remediable 电子邮件是在修正期间将对其进行处理的唯一电子邮件。 Office 365 电子邮件系统无法修正非 remediable 电子邮件，因为它们不存储在云邮箱中。

对于隔离中找到的电子邮件，管理员可以转到隔离，以对这些电子邮件采取操作（如果需要），但如果不手动清除，电子邮件将过期。 最终用户无法访问由于恶意内容而隔离的电子邮件，因此安全人员无需采取任何特定操作来消除隔离威胁。 如果电子邮件是本地或外部电子邮件，则可以联系最终用户来解决可疑电子邮件，或使用单独的电子邮件服务器/安全工具进行删除。 可以通过在威胁资源管理器中应用传递位置 = 本地/external filter 来识别这些电子邮件。 对于失败或丢失的电子邮件，或者最终用户无法访问的电子邮件，由于无法访问邮箱，因此不应使用电子邮件进行缓解。

这是提交在操作中心中显示的方式。 修正可以包含多个提交。 如果通过一次自动调查批准了多个操作，则每个电子邮件或电子邮件群集操作将显示与不同提交相同的补救措施。

:::image type="content" source="../../../media/tp-RemediationArticle6.png" alt-text="Zap 电子邮件群集飞出面板。":::

单击邮件提交项将显示该修正的详细信息，如查询（在通过选择查询的自动调查或威胁资源管理器触发修正）、开始时间和结束时间（修正）。 它还显示提交以进行修正的邮件的列表。 当邮件移出浏览器保留期时，邮件将从该列表中消失。 此列表还显示了列表中 remediable 的单个邮件。

2. "**操作日志" 选项卡**：此选项卡显示修正的邮件的结果，包括 "批准日期"、"审批者" （"批准操作的管理员"）、"操作"、"状态" 和 "计数"。  

状态是修正的总体状态。 状态可以是：

  - **已启动**：触发修正时。
  - 已**排队**：在修补程序排队等待电子邮件缓解时。
  - **正在进行**：正在进行缓解。
  - **已完成**：当所有 remediable 电子邮件的缓解成功完成或发生故障时。 
  - **失败**：当没有 remediations 成功时。

由于只能对 remediable 电子邮件进行操作，因此会将每封电子邮件的清除视为成功或失败。 从 total remediable 电子邮件中，我们公开了成功和失败的缓解。

  - **成功**：当 remediable 电子邮件上的所需操作完成并与管理员的意图相匹配时。例如：管理员希望删除邮箱中的电子邮件，以便执行软删除电子邮件的操作。 如果在执行操作后原始文件夹中找不到 remediable 电子邮件，则状态将显示为 "成功"。  

  - **失败**：当 remediable 电子邮件上的所需操作失败时。 例如：管理员想要删除邮箱中的电子邮件，以便执行软删除电子邮件的操作。 如果仍在邮箱中找到 remediable 电子邮件，则状态将显示为 "失败"。

单击 "操作日志" 中的任何项将显示修正的详细信息。 对于成功的项目，如果详细信息说、成功或未在邮箱中找到，则表示已从邮箱中删除了项目。 有时，由于修正过程中出现系统错误而发生故障，在这些情况下，最好重新尝试修正。  

修正是缓解威胁和解决可疑电子邮件的强大工具。 它有助于确保组织的安全和安全。  

## <a name="more-info"></a>详细信息

参考<https://docs.microsoft.com/microsoft-365/security/office-365-security/investigate-malicious-email-that-was-delivered?view=o365-worldwide>