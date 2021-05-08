---
title: 第 3 步。 对第一个事件执行事后评审
description: 如何在 defender 中查看第一个Microsoft 365事件。
keywords: 事件, 警报, 调查, 关联, 攻击, 计算机, 设备, 用户, 标识, 标识, 邮箱, 电子邮件, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 1ceea1dbdb3f9d149f4e5a0bd892eda2bb9128aa
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114535"
---
# <a name="step-3-perform-a-post-incident-review-of-your-first-incident"></a><span data-ttu-id="afa29-105">步骤 3.</span><span class="sxs-lookup"><span data-stu-id="afa29-105">Step 3.</span></span> <span data-ttu-id="afa29-106">对第一个事件执行事后评审</span><span class="sxs-lookup"><span data-stu-id="afa29-106">Perform a post-incident review of your first incident</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

<span data-ttu-id="afa29-107">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="afa29-107">**Applies to:**</span></span>
- <span data-ttu-id="afa29-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="afa29-108">Microsoft 365 Defender</span></span>

<span data-ttu-id="afa29-109">国家标准与技术协会 (NIST) 建议，一旦采取所有步骤从攻击中恢复，组织必须查看事件以从事件中学习，了解并改进安全状况或流程。</span><span class="sxs-lookup"><span data-stu-id="afa29-109">National Institute of Standards and Technology (NIST) recommends that once all steps have been taken to recover from the attack, organizations must review the incident to learn from it and learn and improve security posture or processes.</span></span> <span data-ttu-id="afa29-110">在准备下一个事件时，评估事件处理的各个方面变得非常重要。</span><span class="sxs-lookup"><span data-stu-id="afa29-110">Assessing the different aspects of incident-handling becomes important in preparing for the next incident.</span></span>

<span data-ttu-id="afa29-111">Microsoft 365Defender 可以通过向组织提供符合[MITRE ATT](https://attack.mitre.org/)和 CK Framework 的警报来帮助&活动。</span><span class="sxs-lookup"><span data-stu-id="afa29-111">Microsoft 365 Defender can assist in performing post-incident activities by providing an organization with alerts that align with [MITRE ATT&CK Framework](https://attack.mitre.org/).</span></span> <span data-ttu-id="afa29-112">所有 Microsoft Defender 解决方案都根据 ATT 和 CK 策略&标记攻击。</span><span class="sxs-lookup"><span data-stu-id="afa29-112">All Microsoft Defender solutions label attacks in accordance with an ATT&CK tactic or technique.</span></span> 

<span data-ttu-id="afa29-113">通过向此行业框架映射警报，你可以：</span><span class="sxs-lookup"><span data-stu-id="afa29-113">By mapping alerts to this industry framework, you can:</span></span>

- <span data-ttu-id="afa29-114">对安全范围差距进行分析。</span><span class="sxs-lookup"><span data-stu-id="afa29-114">Conduct an analysis of gaps in security coverage.</span></span>
- <span data-ttu-id="afa29-115">确定对手和宣传活动属性。</span><span class="sxs-lookup"><span data-stu-id="afa29-115">Determine adversary and campaign attribution.</span></span>
- <span data-ttu-id="afa29-116">执行趋势分析。</span><span class="sxs-lookup"><span data-stu-id="afa29-116">Perform trend analysis.</span></span>
- <span data-ttu-id="afa29-117">确定攻击方法感知中的技能差异。</span><span class="sxs-lookup"><span data-stu-id="afa29-117">Identify skill gaps in attack method awareness.</span></span>
- <span data-ttu-id="afa29-118">创建一Power Automate Playbook，以加快修正速度。</span><span class="sxs-lookup"><span data-stu-id="afa29-118">Create a Power Automate Playbook for faster remediation.</span></span> 

<span data-ttu-id="afa29-119">事件后审阅活动还可以微调安全配置和安全团队的流程，从而增强组织的响应功能。</span><span class="sxs-lookup"><span data-stu-id="afa29-119">Post-incident review activity can also result in fine-tuning your security configuration and security team's processes, enhancing your organization’s response capabilities.</span></span>

## <a name="next-step"></a><span data-ttu-id="afa29-120">后续步骤</span><span class="sxs-lookup"><span data-stu-id="afa29-120">Next step</span></span>

<span data-ttu-id="afa29-121">请参阅以下其他调查路径：</span><span class="sxs-lookup"><span data-stu-id="afa29-121">See these additional investigation paths:</span></span>

- [<span data-ttu-id="afa29-122">钓鱼电子邮件</span><span class="sxs-lookup"><span data-stu-id="afa29-122">Phishing email</span></span>](first-incident-path-phishing.md)
- [<span data-ttu-id="afa29-123">基于身份的攻击</span><span class="sxs-lookup"><span data-stu-id="afa29-123">Identity-based attack</span></span>](first-incident-path-identity.md)


## <a name="see-also"></a><span data-ttu-id="afa29-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afa29-124">See also</span></span>

- [<span data-ttu-id="afa29-125">事件概述</span><span class="sxs-lookup"><span data-stu-id="afa29-125">Incidents overview</span></span>](incidents-overview.md)
- [<span data-ttu-id="afa29-126">分析事件</span><span class="sxs-lookup"><span data-stu-id="afa29-126">Analyze incidents</span></span>](investigate-incidents.md)
- [<span data-ttu-id="afa29-127">管理事件</span><span class="sxs-lookup"><span data-stu-id="afa29-127">Manage incidents</span></span>](manage-incidents.md)