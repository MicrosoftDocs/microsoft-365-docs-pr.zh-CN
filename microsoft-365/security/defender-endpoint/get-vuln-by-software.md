---
title: 按软件列出漏洞
description: 检索已安装软件中的漏洞列表。
keywords: api， 图形 api， 受支持的 api， 获取， 漏洞列表， Microsoft Defender for Endpoint tvm api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 18a2cf87cd0e6b898a9f2aa4d6ecd47a86a8c7f6
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769913"
---
# <a name="list-vulnerabilities-by-software"></a>按软件列出漏洞

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

检索已安装软件中的漏洞列表。 

## <a name="permissions"></a>权限
若要调用此 API，需要以下权限之一。 若要了解详细信息（包括如何选择权限），请参阅使用 [Microsoft Defender for Endpoint API](apis-intro.md) 了解详细信息。

权限类型 |   权限  |   权限显示名称
:---|:---|:---
应用程序 | Software.Read.All | "读取威胁和漏洞管理软件信息"
委派（工作或学校帐户） | Software.Read | "读取威胁和漏洞管理软件信息"

## <a name="http-request"></a>HTTP 请求
```
GET /api/Software/{Id}/vulnerabilities
```

## <a name="request-headers"></a>请求标头

| 名称        | 类型 | 说明
|:--------------|:-------|:--------------|
| Authorization | String | Bearer {token}。**必需**。

## <a name="request-body"></a>请求正文
Empty

## <a name="response"></a>响应
如果成功，此方法返回 200 OK，并列出指定软件公开的漏洞。 


## <a name="example"></a>示例

**请求**

下面是一个请求示例。

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/vulnerabilities 
```

**响应**

下面是一个响应示例。

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
            {
                "id": "CVE-2017-0140",
                "name": "CVE-2017-0140",
                "description": "A security feature bypass vulnerability exists when Microsoft Edge improperly handles requests of different origins. The vulnerability allows Microsoft Edge to bypass Same-Origin Policy (SOP) restrictions, and to allow requests that should otherwise be ignored. An attacker who successfully exploited the vulnerability could force the browser to send data that would otherwise be restricted.In a web-based attack scenario, an attacker could host a specially crafted website that is designed to exploit the vulnerability through Microsoft Edge and then convince a user to view the website. The attacker could also take advantage of compromised websites, and websites that accept or host user-provided content or advertisements. These websites could contain specially crafted content that could exploit the vulnerability.The security update addresses the vulnerability by modifying how affected Microsoft Edge handles different-origin requests.",
                "severity": "Medium",
                "cvssV3": 4.2,
                "exposedMachines": 1,
                "publishedOn": "2017-03-14T00:00:00Z",
                "updatedOn": "2019-10-03T00:03:00Z",
                "publicExploit": false,
                "exploitVerified": false,
                "exploitInKit": false,
                "exploitTypes": [],
                "exploitUris": []
            }
            ...
        ]
}
```

