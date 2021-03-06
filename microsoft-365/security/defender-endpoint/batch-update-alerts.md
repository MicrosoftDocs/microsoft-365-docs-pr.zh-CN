---
title: 批更新警报实体 API
description: 了解如何使用此 API 批量更新 Microsoft Defender 终结点警报。 可以更新状态、确定、分类和 assignedTo 属性。
keywords: api， 图形 api， 受支持的 api， 获取， 警报， 信息， id
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
ms.technology: mde
ms.openlocfilehash: 80f88b31c1e07d1f40f3f58a1bd21b4a5c58c60b
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2021
ms.locfileid: "53290203"
---
# <a name="batch-update-alerts"></a>批更新通知

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：Microsoft** [Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

- 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API 说明

更新一批现有 [警报的属性](alerts.md)。

提供 **或不** 更新属性的注释提交。

可更新的属性包括 `status` ：、 `determination` 和 `classification` `assignedTo` 。

## <a name="limitations"></a>限制

1. 你可以更新 API 中可用的警报。 有关详细信息 [，请参阅列出](get-alerts.md) 警报。
2. 此 API 的速率限制是每分钟 10 个调用和每小时 500 个调用。

## <a name="permissions"></a>权限

若要调用此 API，需要以下权限之一。 若要了解更多信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API](apis-intro.md)

权限类型 | 权限 | 权限显示名称
:---|:---|:---
Application | Alerts.ReadWrite.All | "读取和写入所有警报"
委派（工作或学校帐户） | Alert.ReadWrite | "读取和写入警报"

> [!NOTE]
> 使用用户凭据获取令牌时：
>
> - 用户至少需要具有以下角色权限："警报调查" (有关详细信息，请参阅创建和管理) [](user-roles.md)
> - 用户需要具有与警报关联的设备的访问权限，根据设备组设置 (请参阅创建和管理 [设备](machine-groups.md) 组，了解) 

## <a name="http-request"></a>HTTP 请求

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>请求标头

名称 | 类型 | 说明
:---|:---|:---
Authorization | 字符串 | Bearer {token}。 **必需**。
Content-Type | String | application/json. **必需**。

## <a name="request-body"></a>请求正文

在请求正文中，提供要更新的警报的 ID 以及要针对这些警报更新的相关字段的值。

请求正文中不包括的现有属性将保留其以前的值，或根据对其他属性值的更改重新计算。

为了实现最佳性能，不得添加未变化的现有值。

属性 | 类型 | 说明
:---|:---|:---
alertIds | 列表 &lt; 字符串&gt;| 要更新的警报的 ID 列表。 **Required**
状态 | 字符串 | 指定指定警报的更新状态。 属性值为："New"、InProgress 和"Resolved"。
assignedTo | String | 指定警报的所有者
classification | 字符串 | 指定指定警报的规范。 属性值为："Unknown"、"FalsePositive"和"TruePositive"。 
确定 | 字符串 | 指定指定警报的确定。 属性值包括："NotAvailable"、"Apt"、"Malware"、SecurityPersonnel、"SecurityTesting"、"UnwantedSoftware"和"Other"
注释 | String | 要添加到指定警报的注释。

## <a name="response"></a>响应

如果成功，此方法返回 200 OK，响应正文为空。

## <a name="example"></a>示例

### <a name="request"></a>请求

下面是一个请求示例。

```http
POST https://api.securitycenter.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
