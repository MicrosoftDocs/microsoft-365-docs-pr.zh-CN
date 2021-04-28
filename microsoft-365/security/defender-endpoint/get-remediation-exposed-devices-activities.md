---
title: 列出一个修正活动的公开设备
description: 返回有关指定修正任务的公开设备的信息。
keywords: api， 修正， 修正 api， 获取， 修正任务，
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 097d8d784ca7c02fce1fc0e9fc51bdc272951f4a
ms.sourcegitcommit: e5b1a900043e2e41650ea1cbf4227043729c6053
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2021
ms.locfileid: "52061116"
---
# <a name="list-exposed-devices-of-one-remediation-activity"></a><span data-ttu-id="05937-104">列出一个修正活动的公开设备</span><span class="sxs-lookup"><span data-stu-id="05937-104">List exposed devices of one remediation activity</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="05937-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="05937-105">**Applies to:**</span></span>

- [<span data-ttu-id="05937-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="05937-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [<span data-ttu-id="05937-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="05937-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="05937-108">想要体验 Microsoft Defender for Endpoint？</span><span class="sxs-lookup"><span data-stu-id="05937-108">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="05937-109">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="05937-109">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a><span data-ttu-id="05937-110">API 说明</span><span class="sxs-lookup"><span data-stu-id="05937-110">API Description</span></span>

<span data-ttu-id="05937-111">返回有关指定修正任务的公开设备的信息。</span><span class="sxs-lookup"><span data-stu-id="05937-111">Returns information about exposed devices for the specified remediation task.</span></span>

<span data-ttu-id="05937-112">[详细了解修正活动](tvm-remediation.md)。</span><span class="sxs-lookup"><span data-stu-id="05937-112">[Learn more about remediation activities](tvm-remediation.md).</span></span>

## <a name="list-exposed-devices-associated-with-a-remediation-task-id"></a><span data-ttu-id="05937-113">列出与修正任务关联的公开设备 (id) </span><span class="sxs-lookup"><span data-stu-id="05937-113">List exposed devices associated with a remediation task (id)</span></span>

<span data-ttu-id="05937-114">**URL：** GET： /api/remediationTasks/ \{ id \} /machineReferences</span><span class="sxs-lookup"><span data-stu-id="05937-114">**URL:** GET: /api/remediationTasks/\{id\}/machineReferences</span></span>

<span data-ttu-id="05937-115">**属性** 详细信息</span><span class="sxs-lookup"><span data-stu-id="05937-115">**Properties** details</span></span>

<span data-ttu-id="05937-116">属性 (id) </span><span class="sxs-lookup"><span data-stu-id="05937-116">Property (id)</span></span> | <span data-ttu-id="05937-117">数据类型</span><span class="sxs-lookup"><span data-stu-id="05937-117">Data type</span></span> | <span data-ttu-id="05937-118">说明</span><span class="sxs-lookup"><span data-stu-id="05937-118">Description</span></span> | <span data-ttu-id="05937-119">示例</span><span class="sxs-lookup"><span data-stu-id="05937-119">Example</span></span>
:---|:---|:---|:---
<span data-ttu-id="05937-120">id</span><span class="sxs-lookup"><span data-stu-id="05937-120">id</span></span> | <span data-ttu-id="05937-121">String</span><span class="sxs-lookup"><span data-stu-id="05937-121">String</span></span> | <span data-ttu-id="05937-122">设备 ID</span><span class="sxs-lookup"><span data-stu-id="05937-122">Device ID</span></span> | <span data-ttu-id="05937-123">w2957837fwda8w9ae7f023dba081059dw8d94503</span><span class="sxs-lookup"><span data-stu-id="05937-123">w2957837fwda8w9ae7f023dba081059dw8d94503</span></span>
<span data-ttu-id="05937-124">computerDnsName</span><span class="sxs-lookup"><span data-stu-id="05937-124">computerDnsName</span></span> | <span data-ttu-id="05937-125">String</span><span class="sxs-lookup"><span data-stu-id="05937-125">String</span></span> | <span data-ttu-id="05937-126">设备名称</span><span class="sxs-lookup"><span data-stu-id="05937-126">Device name</span></span> | <span data-ttu-id="05937-127">PC-SRV2012R2Foo.UserNameVldNet.local</span><span class="sxs-lookup"><span data-stu-id="05937-127">PC-SRV2012R2Foo.UserNameVldNet.local</span></span>
<span data-ttu-id="05937-128">osPlatform</span><span class="sxs-lookup"><span data-stu-id="05937-128">osPlatform</span></span> | <span data-ttu-id="05937-129">String</span><span class="sxs-lookup"><span data-stu-id="05937-129">String</span></span> | <span data-ttu-id="05937-130">设备操作系统</span><span class="sxs-lookup"><span data-stu-id="05937-130">Device operating system</span></span> | <span data-ttu-id="05937-131">WindowsServer2012R2</span><span class="sxs-lookup"><span data-stu-id="05937-131">WindowsServer2012R2</span></span>
<span data-ttu-id="05937-132">rbacGroupName</span><span class="sxs-lookup"><span data-stu-id="05937-132">rbacGroupName</span></span> | <span data-ttu-id="05937-133">String</span><span class="sxs-lookup"><span data-stu-id="05937-133">String</span></span> | <span data-ttu-id="05937-134">与此设备关联的设备组的名称</span><span class="sxs-lookup"><span data-stu-id="05937-134">Name of the device group this device is associated with</span></span> | <span data-ttu-id="05937-135">服务器</span><span class="sxs-lookup"><span data-stu-id="05937-135">Servers</span></span>

## <a name="example"></a><span data-ttu-id="05937-136">示例</span><span class="sxs-lookup"><span data-stu-id="05937-136">Example</span></span>

<span data-ttu-id="05937-137">**请求** 示例</span><span class="sxs-lookup"><span data-stu-id="05937-137">**Request** example</span></span>

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c/machinereferences
```

<span data-ttu-id="05937-138">**响应** 示例</span><span class="sxs-lookup"><span data-stu-id="05937-138">**Response** example</span></span>

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "3cb5df6bb3640a2d37ad09fcd357b182d684fafc",
            "computerDnsName": "ComputerPII_2ea21b2d97c9df23c143ad9e3e454cb674232529.DomainPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",
            
        },
        {
            "id": "3d9b1ca53e8f077199c7dcbfc9dbfa78f9bf1918",
            "computerDnsName": "ComputerPII_001d606fc149567c192747f48fae304b43c0ddba.DomainxPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",
            
        },
        {
            "id": "3db8b27e6172951d7ea2e2d75945abec56feaf82",
            "computerDnsName": "ComputerPII_ce60cfbjj4b82a091deb5eae560332bba99a9bd7.DomainPII_0bc1aee0fa396d175e514bd61a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",
            
        },
        {
            "id": "3bad326dcda5b53fab47408cd4a7080f3f3cc8ab",
            "computerDnsName": "ComputerPII_b6b35960dd6539d1d1cef5ada02e235e7b357408.DomainPII_21eed80b089e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",
            
        }
]
}
```

## <a name="see-also"></a><span data-ttu-id="05937-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05937-139">See also</span></span>

- [<span data-ttu-id="05937-140">修正方法和属性</span><span class="sxs-lookup"><span data-stu-id="05937-140">Remediation methods and properties</span></span>](get-remediation-methods-properties.md)

- [<span data-ttu-id="05937-141">按 ID 获取一个修正活动</span><span class="sxs-lookup"><span data-stu-id="05937-141">Get one remediation activity by Id</span></span>](get-remediation-one-activity.md)

- [<span data-ttu-id="05937-142">列出所有修正活动</span><span class="sxs-lookup"><span data-stu-id="05937-142">List all remediation activities</span></span>](get-remediation-all-activities.md)

- [<span data-ttu-id="05937-143">基于风险的威胁&漏洞管理</span><span class="sxs-lookup"><span data-stu-id="05937-143">Risk-based threat & vulnerability management</span></span>](next-gen-threat-and-vuln-mgt.md)

- [<span data-ttu-id="05937-144">组织中漏洞</span><span class="sxs-lookup"><span data-stu-id="05937-144">Vulnerabilities in your organization</span></span>](tvm-weaknesses.md)
