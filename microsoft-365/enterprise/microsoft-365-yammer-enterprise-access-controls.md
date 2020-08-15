---
title: Microsoft 365 Yammer 企业访问控制
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 本文包含有关生产环境中 Yammer 企业访问控制的简短摘要。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8bdf357ddd7f5c0b549d291fd4732924608085b9
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46695521"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="b3edb-103">Yammer 企业访问控制</span><span class="sxs-lookup"><span data-stu-id="b3edb-103">Yammer enterprise access controls</span></span> 

<span data-ttu-id="b3edb-104">对 Yammer 生产环境的物理和逻辑访问仅限于一小组用户 (基础结构和运营) 。</span><span class="sxs-lookup"><span data-stu-id="b3edb-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="b3edb-105">与其他 Microsoft 365 工程师一样，Yammer 工程师可以获得对客户数据的零访问权限。</span><span class="sxs-lookup"><span data-stu-id="b3edb-105">As with other Microsoft 365 engineers, Yammer engineers have zero standing access to customer data.</span></span> <span data-ttu-id="b3edb-106">必须使用基于审批的实时访问控制系统请求访问，这类似于具有有限数量的审批者的密码箱。</span><span class="sxs-lookup"><span data-stu-id="b3edb-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="b3edb-107">审批者验证请求 (例如，他们根据需求、业务案例、时间等 ) 验证请求是否合法，然后批准或拒绝该请求。</span><span class="sxs-lookup"><span data-stu-id="b3edb-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="b3edb-108">如果请求得到批准，则会为已定义和有限的时间授予 JIT 访问权限。</span><span class="sxs-lookup"><span data-stu-id="b3edb-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="b3edb-109">超出访问时间后，访问将自动过期。</span><span class="sxs-lookup"><span data-stu-id="b3edb-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="b3edb-110">与其他 Microsoft 365 服务一样，对 Yammer 生产环境的所有访问都将使用多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3edb-110">As with other Microsoft 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="b3edb-111">所有访问和命令历史记录都属于用户，并定期由 Yammer 安全团队记录和查看。</span><span class="sxs-lookup"><span data-stu-id="b3edb-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="b3edb-112">有关 Yammer 管理和管理的详细信息，请参阅 [Yammer 管理员帮助](https://docs.microsoft.com/yammer/yammer-landing-page)。</span><span class="sxs-lookup"><span data-stu-id="b3edb-112">For more information about Yammer administration and management, see [Yammer admin help](https://docs.microsoft.com/yammer/yammer-landing-page).</span></span>