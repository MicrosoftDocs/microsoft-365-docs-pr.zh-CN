---
title: 更新计算机实体 API
description: 了解如何使用此 API 更新计算机标记。 你可以更新标记和设备值属性。
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 8f08b1fdafd653561ac2aae10a73f37b21874b59
ms.sourcegitcommit: 34c06715e036255faa75c66ebf95c12a85f8ef42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2021
ms.locfileid: "52985570"
---
# <a name="update-machine"></a>更新计算机 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API 说明
更新现有 [Machine 的属性](machine.md)。
<br>可更新的属性包括： ```machineTags``` 和 ```deviceValue``` 。


## <a name="limitations"></a>限制
1. 你可以更新 API 中可用的计算机。 
2. 更新计算机仅将标记追加到标记集合。 如果存在标记，则必须在正文的标记集合中包含这些标记。
3. 此 API 的速率限制是每分钟 100 个调用和每小时 1500 个调用。


## <a name="permissions"></a>权限
若要调用此 API，需要以下权限之一。 若要了解更多信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API](apis-intro.md)

权限类型 |   权限  |   权限显示名称
:---|:---|:---
应用程序 |   Machine.ReadWrite.All | "读取和写入所有计算机的计算机信息"
委派（工作或学校帐户） | Machine.ReadWrite | "读取和写入计算机信息"

>[!Note]
> 使用用户凭据获取令牌时：
>- 用户至少需要具有以下角色权限："警报调查"。 有关详细信息，请参阅创建 [和管理角色](user-roles.md)。
>- 用户需要根据设备组设置访问与警报关联的设备。 有关详细信息，请参阅创建 [和管理设备组](machine-groups.md)。

## <a name="http-request"></a>HTTP 请求
```
PATCH /api/machines/{machineId}
```

## <a name="request-headers"></a>请求标头

名称 | 类型 | 说明
:---|:---|:---
Authorization | String | Bearer {token}。 **必需**。
Content-Type | String | application/json. **必需**。


## <a name="request-body"></a>请求正文
在请求正文中，提供应更新的相关字段的值。
<br>请求正文中不包括的现有属性将保留其以前的值，或根据对其他属性值的更改重新计算。 
<br>为获得最佳性能，不应包含尚未更改的现有值。

属性 | 类型 | 说明
:---|:---|:---
machineTags | 字符串集合 | 计算机 [标记](machine.md) 集。
deviceValue | Nullable Enum | [设备 的值](tvm-assign-device-value.md)。 可能的值包括："Normal"、"Low"和"High"。

## <a name="response"></a>响应
如果成功，此方法在响应正文中返回 200 OK 和 [计算机](machine.md) 实体以及更新的属性。 如果正文中的计算机标记集合不包含现有计算机标记 - 400"输入无效"，并且有消息通知缺少标记/s。
如果未找到具有指定 ID 的机器 - 404 未找到。


## <a name="example"></a>示例

**请求**

下面是一个请求示例。

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10",
                     "Windows Insider - Fast"
    ]
}
```
