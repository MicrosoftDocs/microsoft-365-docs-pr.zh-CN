---
title: 计算机资源类型
description: 了解 Microsoft Defender for Endpoint 中 Machine 资源类型的方法和属性。
keywords: api， 受支持的 api， 获取， 计算机
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
ms.openlocfilehash: f96cfd56cb8d61bc62c34e2b1ee08d6313c6a8ad
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186637"
---
# <a name="machine-resource-type"></a>计算机资源类型

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>方法

方法|返回类型 |说明
:---|:---|:---
[列出计算机](get-machines.md) | [计算机](machine.md) 集合 | 列出 [组织中的计算机](machine.md) 实体集。
[获取计算机](get-machine-by-id.md) | [计算机](machine.md) | 按 [计算机标识](machine.md) 获取计算机。
[获取登录用户](get-machine-log-on-users.md) | [user](user.md) 集合 | 获取登录到 [计算机](user.md) 的用户 [集](machine.md)。
[获取相关警报](get-machine-related-alerts.md) | [警报](alerts.md)集合 | 获取 [计算机上引发](alerts.md) 警报实体 [集](machine.md)。
[获取已安装的软件](get-installed-software.md) | [software](software.md) 集合 | 检索与给定计算机 ID 相关的已安装软件的集合。
[获取发现的漏洞](get-discovered-vulnerabilities.md) | [漏洞](vulnerability.md) 集合 | 检索与给定计算机 ID 相关的已发现漏洞的集合。
[获取安全建议](get-security-recommendations.md) | [建议](recommendation.md) 集合 | 检索与给定计算机 ID 相关的安全建议集合。
[添加或删除计算机标记](add-or-remove-machine-tags.md) | [计算机](machine.md) | 向特定计算机添加或删除标记。
[按 IP 查找计算机](find-machines-by-ip.md) | [计算机](machine.md) 集合 | 查找使用 IP 查看的计算机。
[按标记查找计算机](find-machines-by-tag.md) | [计算机](machine.md) 集合 | 按标记 查找 [计算机](machine-tags.md)。
[获取缺少的 KB](get-missing-kbs-machine.md) | KB 集合 | 获取与计算机 ID 关联的缺失的 KB 列表
[设置设备值](set-device-value.md)| [计算机](machine.md) 集合 | 设置 [设备 的值](tvm-assign-device-value.md)。

## <a name="properties"></a>属性

属性 |   类型   |   说明
:---|:---|:---
id | String | [计算机](machine.md) 标识。
computerDnsName | String | [计算机](machine.md) 完全限定的名称。
firstSeen | DateTimeOffset | Microsoft Defender for [](machine.md) Endpoint 观测到计算机的第一个日期和时间。
lastSeen | DateTimeOffset |上次接收的完整设备报告的时间和日期。 设备通常每 24 小时发送一次完整报告。
osPlatform | String | 操作系统平台。
osProcessor | String | 操作系统处理器。
version | String | 操作系统版本。
osBuild | Nullable long | 操作系统内部版本编号。
lastIpAddress | String | 计算机上本地 NIC 上的最后一[个 IP。](machine.md)
lastExternalIpAddress | String | 计算机访问 Internet [的最后](machine.md) 一个 IP。
healthStatus | 枚举 | [计算机](machine.md) 运行状况状态。 可能的值包括："Active"、"Inactive"、"ImpairedCommunication"、"NoSensorData"、"NoSensorDataImpairedCommunication"和"Unknown"。 
rbacGroupName | String | 计算机组名称。
riskScore | Nullable Enum | 由 Microsoft Defender 终结点评估的风险评分。 可能的值包括："None"、"Informational"、"Low"、"Medium"和"High"。
exposureScore | Nullable Enum | [由](tvm-exposure-score.md) Microsoft Defender for Endpoint 评估的曝光评分。 可能的值包括："None"、"Low"、"Medium"和"High"。
aadDeviceId | Nullable 表示形式 Guid | 当计算机已 (AAD [时](machine.md) ，AAD 设备 ID) 。
machineTags | String collection | 计算机 [标记](machine.md) 集。
exposureLevel | Nullable Enum | 由 Microsoft Defender for Endpoint 评估的曝光级别。 可能的值包括："None"、"Low"、"Medium"和"High"。
deviceValue | Nullable Enum | [设备 的值](tvm-assign-device-value.md)。 可能的值包括："Normal"、"Low"和"High"。
ipAddresses | IpAddress 集合 | ***IpAddress 对象*** 集。 请参阅[获取计算机 API。](get-machines.md)

