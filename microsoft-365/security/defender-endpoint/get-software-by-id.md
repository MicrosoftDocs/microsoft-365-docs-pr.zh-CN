---
title: 按 ID 获取软件
description: 按设备组检索曝光评分列表。
keywords: api， 图形 api， 受支持的 api， 获取， 软件， mdatp tvm api
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 57d6ccd2c5387d478b75cfb6fb32a5b1052e491c
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51198585"
---
# <a name="get-software-by-id"></a>按 ID 获取软件

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：Microsoft** [Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

按 ID 检索软件详细信息。

## <a name="permissions"></a>权限
若要调用此 API，需要以下权限之一。 若要了解详细信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API](apis-intro.md) 了解详细信息。

权限类型 |   权限  |   权限显示名称
:---|:---|:---
应用程序 | Software.Read.All | "读取威胁和漏洞管理软件信息"
委派（工作或学校帐户） | Software.Read | "读取威胁和漏洞管理软件信息"

## <a name="http-request"></a>HTTP 请求
```
GET /api/Software/{Id}
```

## <a name="request-headers"></a>请求标头

| 名称        | 类型 | 说明
|:--------------|:-------|:--------------|
| Authorization | 字符串 | Bearer {token}。**必需**。

## <a name="request-body"></a>请求正文
Empty

## <a name="response"></a>响应
如果成功，此方法在正文中返回 200 OK 以及指定的软件数据。 


## <a name="example"></a>示例

**请求**

下面是一个请求示例。

```
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge
```

**响应**

下面是一个响应示例。

```json

{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software/$entity",
    "id": "microsoft-_-edge",
    "name": "edge",
    "vendor": "microsoft",
    "weaknesses": 467,
    "publicExploit": true,
    "activeAlert": false,
    "exposedMachines": 172,
    "impactScore": 2.39947438
}
```

## <a name="related-topics"></a>相关主题
- [基于风险的威胁&漏洞管理](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [威胁&漏洞软件清单](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-software-inventory)