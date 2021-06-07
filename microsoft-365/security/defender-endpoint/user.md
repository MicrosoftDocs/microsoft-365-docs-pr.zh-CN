---
title: 用户资源类型
description: 检索最近与用户相关的 Microsoft Defender for Endpoint 警报。
keywords: api， 图形 api， 受支持的 api， 获取， 警报， 最近
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 39b73772bcc626590aa784bb5b21357f66229816
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772133"
---
# <a name="user-resource-type"></a><span data-ttu-id="18c6c-104">用户资源类型</span><span class="sxs-lookup"><span data-stu-id="18c6c-104">User resource type</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="18c6c-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="18c6c-105">**Applies to:**</span></span>
- [<span data-ttu-id="18c6c-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="18c6c-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/?linkid=2154037)
- [<span data-ttu-id="18c6c-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="18c6c-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="18c6c-108">想要体验 Microsoft Defender for Endpoint？</span><span class="sxs-lookup"><span data-stu-id="18c6c-108">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="18c6c-109">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="18c6c-109">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


<span data-ttu-id="18c6c-110">方法</span><span class="sxs-lookup"><span data-stu-id="18c6c-110">Method</span></span>|<span data-ttu-id="18c6c-111">返回类型</span><span class="sxs-lookup"><span data-stu-id="18c6c-111">Return Type</span></span> |<span data-ttu-id="18c6c-112">说明</span><span class="sxs-lookup"><span data-stu-id="18c6c-112">Description</span></span>
:---|:---|:---
[<span data-ttu-id="18c6c-113">列出与用户相关的警报</span><span class="sxs-lookup"><span data-stu-id="18c6c-113">List User related alerts</span></span>](get-user-related-alerts.md) | <span data-ttu-id="18c6c-114">[警报](alerts.md)集合</span><span class="sxs-lookup"><span data-stu-id="18c6c-114">[alert](alerts.md) collection</span></span> |  <span data-ttu-id="18c6c-115">列出与用户关联的所有 [警报](user.md)。</span><span class="sxs-lookup"><span data-stu-id="18c6c-115">List all the alerts that are associated with a [user](user.md).</span></span>
[<span data-ttu-id="18c6c-116">列出与用户相关的设备</span><span class="sxs-lookup"><span data-stu-id="18c6c-116">List User related devices</span></span>](get-user-related-machines.md) | <span data-ttu-id="18c6c-117">[计算机](machine.md) 集合</span><span class="sxs-lookup"><span data-stu-id="18c6c-117">[machine](machine.md) collection</span></span> | <span data-ttu-id="18c6c-118">列出用户登录的所有 [设备](user.md)。</span><span class="sxs-lookup"><span data-stu-id="18c6c-118">List all the devices that were logged on by a [user](user.md).</span></span>
