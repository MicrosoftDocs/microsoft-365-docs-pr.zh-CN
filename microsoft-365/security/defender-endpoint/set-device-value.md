---
title: 设置设备值 API
description: 了解如何使用 Microsoft Defender for Endpoint API 指定设备的值。
keywords: api， 图形 api， 受支持的 api， 标记， 计算机标记
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: e14e696169a2d1cd76e4fb5b2ee8de951e9e1280
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771394"
---
# <a name="set-device-value-api"></a>设置设备值 API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**适用于：Microsoft** [Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API 说明

设置特定计算机 的设备 [值](machine.md)。<br>
有关详细信息 [，请参阅分配](tvm-assign-device-value.md) 设备值。

## <a name="limitations"></a>限制

1. 你可以根据配置的保留期在上次看到的设备上发布。

2. 此 API 的速率限制是每分钟 100 个调用和每小时 1500 个调用。


## <a name="permissions"></a>权限

若要调用此 API，需要以下权限之一。 若要了解更多信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API](apis-intro.md)

权限类型 |    权限    |    权限显示名称
:---|:---|:---
应用程序 |    Machine.ReadWrite.All |    "读取和写入所有计算机信息"
委派（工作或学校帐户） | Machine.ReadWrite | "读取和写入计算机信息"

>[!Note]
> 使用用户凭据获取令牌时：
>
>- 用户至少需要具有以下角色权限："管理安全性设置"。 有关详细信息 (请参阅 [创建和管理角色，](user-roles.md) 了解) 
>- 用户需要具有计算机访问权限，根据计算机组设置 (请参阅创建和管理计算机组，了解[](machine-groups.md)) 

## <a name="http-request"></a>HTTP 请求

```http
POST https://api.securitycenter.microsoft.com/api/machines/{machineId}/setDeviceValue
```

## <a name="request-headers"></a>请求标头

名称 | 类型 | 说明
:---|:---|:---
Authorization | String | Bearer {token}。 **必需**。
Content-Type | string | application/json. **必需**。

## <a name="request-body"></a>请求正文

在请求正文中，提供具有以下参数的 JSON 对象：

参数 |    类型    | 说明
:---|:---|:---
DeviceValue |    枚举 |    设备值。 允许的值包括："Normal"、"Low"和"High"。 **必需**。

## <a name="response"></a>响应

如果成功，此方法在响应正文中返回 200 - 正常响应代码和更新的 Machine。

## <a name="example"></a>示例

**请求**

下面是添加计算机标记的请求示例。

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/setDeviceValue
```

```json
{
  "DeviceValue" : "High"
}
```
