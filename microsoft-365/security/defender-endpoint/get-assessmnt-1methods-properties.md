---
title: 导出每个设备的评估方法和属性
description: 提供有关拉取"危险和漏洞管理"数据的 API 的信息。 不同的 API 调用用于获取不同类型的数据。 通常，每个 API 调用都包含组织中设备的必要数据。 由于数据量可能非常大，因此有两种方法可以检索数据
keywords: api， api， 导出评估， 按设备评估， 漏洞评估报告， 设备漏洞评估， 设备漏洞报告， 安全配置评估， 安全配置报告， 软件漏洞评估， 软件漏洞报告， 计算机漏洞报告，
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
ms.custom: api
ms.openlocfilehash: 851c792265375e5905c0c427bfc77a2366bc962d
ms.sourcegitcommit: 727a75b604d5ff5946a0854662ad5a8b049f2874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2021
ms.locfileid: "52653623"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>导出每个设备的评估方法和属性

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>API 说明

提供有关基于每个设备拉取数据危险和漏洞管理 API 的方法和属性详细信息。 不同的 API 调用用于获取不同类型的数据。 通常，每个 API 调用都包含组织中设备的必要数据。

> [!Note]
>
> 除非另有说明，否则列出的所有导出评估方法都是 **** 完全导出 (**** 也称作按设备 **_) 。_**

不同的 API 调用用于获取不同类型的数据。 由于数据量可能很大，因此有两种方法可以检索数据：

- **OData**  API 按照 OData 协议提取组织的所有数据作为 Json 响应。 此方法最适合设备 _数少于 10 万的小组织_。 响应会分页，因此您可以使用响应中的 \@ odata.nextLink 字段获取下一个结果。

- **通过文件** 此 API 解决方案允许更快、更可靠地提取大量数据。 因此，建议拥有 10 万台以上设备的大型组织使用。 此 API 将组织的所有数据提取为下载文件。 该响应包含从网站下载所有数据的Azure 存储。 此 API 使你能够按如下方式从Azure 存储数据：

  - 调用 API 获取包含所有组织数据的下载 URL 列表。

  - 使用下载 URL 下载所有文件并处理您喜欢的数据。

为 _OData_ 或 (文件收集的数据) 当前状态的当前快照，不包含历史数据。 为了收集历史数据，客户必须将数据保存在自己的数据存储中。

除非另有说明，否则列出的所有导出评估方法都是 **** 完全导出 (**** 也称作按设备 **_) 。_**

## <a name="1-export-secure-configurations-assessment"></a>1. 导出安全配置评估

基于每个设备返回所有配置及其状态。

### <a name="11-methods"></a>1.1 方法

Method | 数据类型 | 说明
:---|:---|:---
[导出 OData (安全) ](get-assessmnt-secure-cfg.md#1-export-secure-configuration-assessment-odata) | 按设备集合的安全配置。 请参阅 [：1.2 OData (属性) ](#12-properties-odata) | 返回一个表，该表包含 DeviceId、ConfigurationId 每个唯一组合的条目。 为 _OData_ 或 (文件收集的数据) 当前状态的当前快照，不包含历史数据。 为了收集历史数据，客户必须将数据保存在自己的数据存储中。
[导出通过文件 (安全配置) ](get-assessmnt-secure-cfg.md#2-export-secure-configuration-assessment-via-files) | 通过设备文件进行安全配置。 请参阅 [：1.3 属性 (文件) ](#13-properties-via-files) | 返回一个表，该表包含 DeviceId、ConfigurationId 每个唯一组合的条目。 此 API 解决方案允许更快、更可靠地提取大量数据。 因此，建议拥有 10 万台以上设备的大型组织使用。 此 API 将组织的所有数据提取为下载文件。 该响应包含从网站下载所有数据的Azure 存储。 此 API 使你能够下载所有数据Azure 存储如下所示：1.  调用 API 获取包含所有组织数据的下载 URL 列表。 2.  使用下载 URL 下载所有文件并处理您喜欢的数据。

### <a name="12-properties-odata"></a>1.2 OData (属性) 

属性 (ID)  | 数据类型 | 说明
:---|:---|:---
ConfigurationCategory | string | 配置所属的类别或分组：应用程序、OS、网络、帐户、安全控件
ConfigurationId | string | 特定配置的唯一标识符
ConfigurationImpact | string | 配置对总体配置评分的影响程度 (1-10)
ConfigurationName | string | 配置的显示名称
ConfigurationSubcategory | string | 配置所属的子类别或子组。 在许多情况下，它用于描述特定的功能。
DeviceId | string | 服务中设备的唯一标识符。
DeviceName | string | 设备的完全限定 (FQDN) FQDN。
IsApplicable | bool | 指示配置或策略是否适用
IsCompliant | bool | 指示是否正确配置了配置或策略
IsExpectedUserImpact | bool | 指示是否将应用配置时影响用户
OSPlatform | string | 在设备上运行的操作系统的平台。 这表示特定操作系统，包括同一系列中的变体，如 Windows 10 和 Windows 7。 有关详细信息，请参阅 tvm 支持的操作系统和平台。
RbacGroupName | string | 基于角色的访问控制 (RBAC) 组。 如果此设备未分配给任何 RBAC 组，则值将为"Unassigned"。 如果组织不包含任何 RBAC 组，则值为"None"。
RecommendationReference | string | 对此软件相关建议 ID 的引用。
Timestamp | string | 上次在设备上看到配置的时间

### <a name="13-properties-via-files"></a>1.3 属性 (文件) 

属性 (ID)  | 数据类型 | 说明
:---|:---|:---
导出文件 | 数组 \[ 字符串\] | 保存组织当前快照的文件的下载 URL 列表。
GeneratedTime | string | 导出的生成时间。

## <a name="2-export-software-inventory-assessment"></a>2. 导出软件清单评估

返回每台设备上安装的所有软件及其详细信息。

### <a name="21-methods"></a>2.1 方法

Method | 数据类型 | 说明
:---|:---|:---
[导出 OData (软件清单) ](get-assessmnt-software-inventory.md#1-export-software-inventory-assessment-odata) | 按设备集合列出软件清单。 请参阅 [：2.2 OData (2.2) ](#22-properties-odata) | 返回一个表，该表包含 DeviceId、SoftwareVendor、SoftwareName、SoftwareVersion 每个唯一组合的条目。 为 _OData_ 或 (文件收集的数据) 当前状态的当前快照，不包含历史数据。 为了收集历史数据，客户必须将数据保存在自己的数据存储中。
[通过文件库导出 (清单) ](get-assessmnt-software-inventory.md#2-export-software-inventory-assessment-via-files) | 按设备文件列出软件清单。 请参阅 [：2.3 属性 (文件) ](#23-properties-via-files) | 返回一个表，该表包含 DeviceId、SoftwareVendor、SoftwareName、SoftwareVersion 每个唯一组合的条目。 此 API 解决方案允许更快、更可靠地提取大量数据。 因此，建议拥有 10 万台以上设备的大型组织使用。 此 API 将组织的所有数据提取为下载文件。 该响应包含从网站下载所有数据的Azure 存储。 此 API 使你能够下载所有数据Azure 存储如下所示：1.  调用 API 获取包含所有组织数据的下载 URL 列表。 2.  使用下载 URL 下载所有文件并处理您喜欢的数据。

### <a name="22-properties-odata"></a>2.2 OData (2.2) 

属性 (ID)  | 数据类型 | 说明
:---|:---|:---
DeviceId | string | 服务中设备的唯一标识符。
DeviceName | string | 设备的完全限定 (FQDN) FQDN。
DiskPaths | Array[string]  | 表明产品已安装在设备的磁盘证据。
EndOfSupportDate | string | 此软件支持已结束或将终止的日期。
EndOfSupportStatus | string | 停止提供支持状态。 可以包含以下可能的值：None、EOS Version、Upcoming EOS Version、EOS Software、Upcoming EOS Software。
Id | string | 记录的唯一标识符。
NumberOfWeaknesses | int|此设备上此软件上漏洞的数量
OSPlatform | string | 在设备上运行的操作系统的平台。 这表示特定操作系统，包括同一系列中的变体，如 Windows 10 和 Windows 7。 有关详细信息，请参阅 tvm 支持的操作系统和平台。
RbacGroupName | string | 基于角色的访问控制 (RBAC) 组。 如果此设备未分配给任何 RBAC 组，则值将为"Unassigned"。 如果组织不包含任何 RBAC 组，则值为"None"。
RegistryPaths | Array[string] | 注册表证据，表明产品已安装在设备中。
SoftwareFirstSeenTimestamp | string | 首次在设备上看到此软件。
SoftwareName | string | 软件产品的名称。
SoftwareVendor | string | 软件供应商的名称。
SoftwareVersion | string | 软件产品的版本号。

### <a name="23-properties-via-files"></a>2.3 属性 (文件) 

属性 (ID)  | 数据类型 | 说明
:---|:---|:---
导出文件 | 数组 \[ 字符串\] | 保存组织当前快照的文件的下载 URL 列表。
GeneratedTime | string | 导出的生成时间。

## <a name="3-export-software-vulnerabilities-assessment-per-device"></a>3. 导出每个设备的软件漏洞评估

返回设备上所有设备的已知漏洞及其详细信息。

### <a name="31-methods"></a>3.1 方法

Method | 数据类型 | 说明
:---|:---|:---
[导出 OData (软件) ](get-assessmnt-software-vulnerabilities.md#1-export-software-vulnerabilities-assessment-odata) | 调查集合，请参阅 [：3.2 属性 (OData) ](#32-properties-odata) | 返回一个包含 DeviceId、SoftwareVendor、SoftwareName、SoftwareVersion、CveId 每个唯一组合的条目的表。 为 _OData_ 或 (文件收集的数据) 当前状态的当前快照，不包含历史数据。 为了收集历史数据，客户必须将数据保存在自己的数据存储中。
[导出通过文件 (软件漏洞) ](get-assessmnt-software-vulnerabilities.md#2-export-software-vulnerabilities-assessment-via-files) | 调查实体 请参阅 [：3.3 通过文件 (的属性) ](#33-properties-via-files) | 返回一个包含 DeviceId、SoftwareVendor、SoftwareName、SoftwareVersion、CveId 每个唯一组合的条目的表。 此 API 解决方案允许更快、更可靠地提取大量数据。 因此，建议拥有 10 万台以上设备的大型组织使用。 此 API 将组织的所有数据提取为下载文件。 该响应包含从网站下载所有数据的Azure 存储。 此 API 使你能够下载所有数据Azure 存储如下所示：1.  调用 API 获取包含所有组织数据的下载 URL 列表。 2.  使用下载 URL 下载所有文件并处理您喜欢的数据。

### <a name="32-properties-odata"></a>3.2 OData (属性) 

属性 (ID)  | 数据类型 | 说明
:---|:---|:---
CveId | string | 分配给 CVE 安全机制中常见漏洞和 (漏洞) 标识符。
CvssScore | string | CVE 的 CVSS 分数。
DeviceId | string | 服务中设备的唯一标识符。
DeviceName | string | 设备的完全限定 (FQDN) FQDN。
DiskPaths | 数组 \[ 字符串\] | 表明产品已安装在设备的磁盘证据。
ExploitabilityLevel | string | 此漏洞的利用级别 (NoExploit、ExploitIsPublic、ExploitIsVerified、ExploitIsInKit) 
FirstSeenTimestamp | string | 首次在设备上看到此产品的 CVE 时。
Id | string | 记录的唯一标识符。
LastSeenTimestamp | string | 上次在设备上看到 CVE 的时间。
OSPlatform | string | 在设备上运行的操作系统的平台。 这表示特定操作系统，包括同一系列中的变体，如 Windows 10 和 Windows 7。 有关详细信息，请参阅 tvm 支持的操作系统和平台。
RbacGroupName | string | 基于角色的访问控制 (RBAC) 组。 如果此设备未分配给任何 RBAC 组，则值将为"Unassigned"。 如果组织不包含任何 RBAC 组，则值为"None"。
RecommendationReference | string | 对此软件相关建议 ID 的引用。
RecommendedSecurityUpdate | string | 软件供应商提供的用于解决漏洞的安全更新的名称或说明。
RecommendedSecurityUpdateId | string | 相应指南或知识库的适用安全更新或标识符的标识符 (KB) 文章
注册表路径 数组 \[ 字符串\] | 注册表证据，表明产品已安装在设备中。
SoftwareName | string | 软件产品的名称。
SoftwareVendor | string | 软件供应商的名称。
SoftwareVersion | string | 软件产品的版本号。
VulnerabilitySeverityLevel | string | 根据 CVSS 分数和受威胁环境影响的动态因素为安全漏洞分配的严重性级别。

### <a name="33-properties-via-files"></a>3.3 属性 (文件) 

属性 (ID)  | 数据类型 | 说明
:---|:---|:---
导出文件 | 数组 \[ 字符串\]  | 保存组织当前快照的文件的下载 URL 列表。
GeneratedTime | string | 导出的生成时间。

## <a name="see-also"></a>另请参阅

- [导出每个设备的安全配置评估](get-assessmnt-secure-cfg.md)

- [导出每个设备的软件清单评估](get-assessmnt-software-inventory.md)

- [导出每个设备的软件漏洞评估](get-assessmnt-software-vulnerabilities.md)

其他相关

- [基于风险的威胁& 漏洞管理](next-gen-threat-and-vuln-mgt.md)

- [组织中漏洞](tvm-weaknesses.md)