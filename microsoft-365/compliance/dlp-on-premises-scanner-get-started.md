---
title: Microsoft 365 本地扫描仪数据丢失防护入门（预览）
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: 设置 Microsoft 365 本地扫描仪数据丢失防护
ms.openlocfilehash: 0390ac48b351b30b75109a3e3a5d18c80847c9d2
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2021
ms.locfileid: "53289195"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner-preview"></a>开始进行本地扫描仪的数据丢失防护（预览）

本文将引导你完成 Microsoft 365 本地扫描仪数据丢失防护的先决条件和配置。

## <a name="before-you-begin"></a>准备工作

### <a name="skusubscriptions-licensing"></a>SKU/订阅许可

在开始使用终结点 DLP 之前，应该先确认 [Microsoft 365 订阅](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)以及任何加载项。 若要参与预览版，设置 DLP 规则的管理员帐户必须分配以下其中一个许可证：

- Microsoft 365 E5
- Microsoft 365 E5 合规
- Microsoft 365 E5 信息保护和管控 


有关许可的详细信息，请参阅[适用于安全与合规性的 Microsoft 365 许可指南](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)。

### <a name="permissions"></a>权限


可在[活动资源管理器](data-classification-activity-explorer.md)中查看终结点 DLP 中的数据。 有四个角色可向活动资源管理器授予权限，用于访问数据的帐户必须是其中任何一个的成员。

- 全局管理员
- 合规性管理员
- 安全管理员
- 合规性数据管理员

### <a name="dlp-on-premises-scanner-prerequisites"></a>DLP 本地扫描仪先决条件

- Azure 信息保护 （AIP） 扫描仪实现 DLP 策略匹配和策略执行。将扫描仪作为 AIP 客户端一部分进行安装，因此安装必须满足 AIP、AIP 客户端和 AIP 统一标签扫描仪的所有先决条件。
- 部署 AIP 客户端和扫描仪。 若要详细了解 [AIP 统一标签客户端](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) 和 []，请参阅 [配置和安装 Azure 信息保护统一标签扫描仪](/azure/information-protection/deploy-aip-scanner-configure-install)。
- 必须至少在租户中发布一个标签和策略，即使所有检测规则都只基于敏感信息类型。

## <a name="deploy-the-dlp-on-premises-scanner"></a>部署 DLP 本地扫描仪

1. 请按照 [安装AIP统一标签客户端](/azure/information-protection/rms-client/install-unifiedlabelingclient-app)中的过程。 
2. 按照以下过程 [安装 Azure 信息保护统一标签扫描仪](/azure/information-protection/deploy-aip-scanner-configure-install) 完成扫描仪安装。
    1. 网络发现作业配置是一个可选步骤。 可以跳过它，并定义要扫描内容扫描作业的特定存储库。
    2. 必须创建内容扫描作业，并指定 DLP 引擎需要评估的托管文件的存储库。
    3. 在已创建的内容扫描作业中启用 DLP 规则，将 **强制** 选项设置为 **关闭**，除非想要直接进入 DLP 强制阶段。
3. 验证内容扫描作业是否分配给了右群集。如果仍未创建内容扫描作业，请创建新的扫描作业，将其分配到包含运行公共预览版本的扫描仪节点群集。

4. 连接到 Azure 门户 [Azure 信息保护扩展](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) 将存储库添加到将执行扫描的内容扫描作业。

5. 执行下列操作之一以运行扫描：
    1. 设置扫描仪计划
    1. 在门户 **手动** 立即扫描"选项
    1. 或运行 **-AIPScan** PowerShell cmdlet

   > [!IMPORTANT]
   > 请记住，默认情况下，扫描仪运行存储库的增量扫描，并且会跳过在上一扫描周期中扫描的文件，除非文件发生更改或启动完全重新扫描。 可以通过使用UI中的 **“重新扫描所有文件”** 选项或通过运行 **Start-AIPScan-Reset** 来启动完全重新扫描。

6.  在 Microsoft 365 合规性管理中心中，打开“[数据丢失防护页面](https://compliance.microsoft.com/datalossprevention?viewid=policies)”。

7. 选择 **创建策略** 并创建测试 DLP 策略。 如果你需要 [帮助创建策略，请参阅](create-a-dlp-policy-from-a-template.md) 模板创建 DLP 策略。 请务必在测试中运行它，直到熟悉此功能。 将以下参数用于策略：
    1. 如有必要，将 DLP 本地扫描仪规则的范围设置到特定位置。 如果将扫描 **的位置****所有**，则通过扫描仪扫描的所有文件将受制于 DLP 规则匹配和强制。
    1. 指定位置时，可以使用排除列表或包含列表。 在公共预览期间，不能同时设置两者。 可定义规则仅与包含列表中列出的其中一个模式相匹配的路径相关，与包含列表中列出的所有文件（与包含列表中列出的模式相匹配的文件除外）的所有文件除外。 不支持任何本地路径。 以下是一些有效路径的示例：
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\folder1
      - \*secret\*.docx
      - \*secret\*.\*
      - https:// sp2010.local/sites/HR
      - https://\*/HR 
    3. 以下是使用不可接受的值的一些示例：
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> 排除列表优先于包含项列表。

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>在 DLP Alerts 管理仪表板中查看 DLP 本地扫描仪警报

1. 在 Microsoft 365 合规 [打开](https://compliance.microsoft.com/datalossprevention?viewid=policies) 数据丢失防护"页面，然后选择 **警报**。

2. 请参阅 [如何配置和查看 DLP 策略的警报](dlp-configure-view-alerts-policies.md) 中的过程，以查看你的终结点 DLP 策略警报。

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>在活动资源管理器中查看 DLP 本地扫描仪和审核日志

> [!NOTE]
> 需要启用审核。本地扫描仪需要启用审核。 在 Microsoft 365 中，默认启用审核。

1. 在 Microsoft 365 合规 [打开域](https://compliance.microsoft.com/dataclassification?viewid=overview) 数据分类页面，然后选择活动资源管理器。

2. 请参阅活动 [工具入门](data-classification-activity-explorer.md) 中的过程，以访问和筛选本地扫描仪位置的所有数据。

3. 在合规 [中打开"审核"](https://security.microsoft.com/auditlogsearch)。 在公共预览期间，DLP 规则匹配项在审核日志 UI 中可用，或由 [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell 访问 


## <a name="next-steps"></a>后续步骤
现在，你已载入设备，并且可以在“活动资源管理器”中查看活动数据，那么就可以继续下一步，在其中创建保护敏感项目的 DLP 策略。

- [使用本地 DLP（预览）](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>另请参阅

- [了解 DLP 本地扫描仪（预览）](dlp-on-premises-scanner-learn.md)
- [使用 DLP 本地扫描仪（预览）](dlp-on-premises-scanner-use.md)
- [了解数据丢失防护](dlp-learn-about-dlp.md)
- [创建、测试和优化 DLP 策略](create-test-tune-dlp-policy.md)
- [活动资源管理器入门](data-classification-activity-explorer.md)
- [Microsoft 365 订阅](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)