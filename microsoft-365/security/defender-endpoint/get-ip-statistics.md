---
title: 获取 IP 统计信息 API
description: 使用 Microsoft Defender for Endpoint 获取你的 IP 的最新统计信息。
keywords: api， 图形 api， 受支持的 api， 获取， ip， 统计信息， 普遍程度
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
ms.openlocfilehash: 4919f082c115d8a57960ec49532b6cda6a63833f
ms.sourcegitcommit: 787fb30fdae6d49347a87f4baae3cd140067e573
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2021
ms.locfileid: "52998724"
---
# <a name="get-ip-statistics-api"></a>获取 IP 统计信息 API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API 说明
检索给定 IP 的统计信息。

## <a name="limitations"></a>限制
1. 此 API 的速率限制是每分钟 100 个调用和每小时 1500 个调用。

## <a name="permissions"></a>权限
若要调用此 API，需要以下权限之一。 若要了解更多信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API](apis-intro.md)

权限类型 |   权限  |   权限显示名称
:---|:---|:---
应用程序 |   Ip.Read.All |   "读取 IP 地址配置文件"
委派（工作或学校帐户） | Ip.Read.All |  "读取 IP 地址配置文件"

>[!NOTE]
> 使用用户凭据获取令牌时：
>- 用户至少需要具有以下角色权限："查看数据"权限 (有关详细信息，请参阅创建和管理) [](user-roles.md)

## <a name="http-request"></a>HTTP 请求

```http
GET /api/ips/{ip}/stats
```

## <a name="request-headers"></a>请求标头

名称 | 类型 | 说明
:---|:---|:---
Authorization | String | Bearer {token}。 **必需**。

## <a name="request-uri-parameters"></a>请求 URI 参数

名称 | 类型 | 说明
:---|:---|:---
lookBackHours | Int32 | 定义我们重新搜索以获取统计信息的小时数。 默认为 30 天。 **可选。**

## <a name="request-body"></a>请求正文
Empty

## <a name="response"></a>响应
如果成功且 ip 存在 - 200 正常，正文中具有统计数据。 IP 不存在 - 404 未找到。


## <a name="example"></a>示例

**请求**

下面是一个请求示例。

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/stats?lookBackHours=48
```

**响应**

下面是一个响应示例。


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgIPStats",
    "ipAddress": "10.209.67.177",
    "organizationPrevalence": 63515,
    "orgFirstSeen": "2017-07-30T13:36:06Z",
    "orgLastSeen": "2017-08-29T13:32:59Z"
}
```


| 名称 | 说明 |
| :--- | :---------- |
| 组织普遍程度 | 打开到此 IP 的网络连接的设备数。 |
| 首次看到组织 | 组织中此 IP 的第一个连接。 |
| 上次查看组织  | 组织中此 IP 的最后一个连接。 |

> [!NOTE]
> 此统计信息基于过去 30 天的数据。 
