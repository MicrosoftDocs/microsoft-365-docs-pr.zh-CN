---
title: Microsoft Defender for Endpoint 设备控制可移动存储保护
description: 了解有助于防止用户或计算机或两者使用未经授权的可移动存储媒体的功能
keywords: 可移动存储媒体
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-smandalika
author: v-smandalika
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 55171429d3ea447de32eb7e2ec12b8b2c3542e95
ms.sourcegitcommit: 3e971b31435d17ceeaa9871c01e88e25ead560fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2021
ms.locfileid: "52861703"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender for Endpoint 设备控制可移动存储保护

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender for Endpoint 设备控制可移动存储保护可防止用户或计算机使用未经授权的可移动存储媒体。

## <a name="protection-policies"></a>保护策略

### <a name="device-installation"></a>设备安装

**功能** - 根据各种设备属性阻止安装（包括或不排除）。

**Windows 10支持详细信息**
- 在计算机级别应用：同一策略适用于任何登录的用户。
- 支持 MEM 和 GPO。
- 支持的'[设备属性](#device-properties)'，如所列。
- 有关此Windows，请参阅如何使用 Microsoft Defender for Endpoint 控制 USB 设备和其他[可移动媒体](control-usb-devices-using-intune.md)。

**支持的平台**- Windows 10

**macOS 支持详细信息**
- 在计算机级别应用：相同的策略适用于任何登录的用户
- 有关 macOS 特定的信息，请参阅 [macOS 的设备控件](mac-device-control-overview.md)。
 
**支持的平台** - macOS Catalina 10.15.4+ (启用了系统扩展) 

### <a name="removable-storage-access-control"></a>可移动存储访问控制

**Capabilities**
- *审核* 基于各种设备属性对可移动存储的读取、写入或执行访问（带排除或不排除）。
- *阻止* 读取或写入或执行访问（带排除或不排除） - 允许基于各种设备属性的特定设备。

**Windows 10支持详细信息**
- 在计算机或用户或两者中应用 – 仅允许对特定计算机上特定可移动存储执行读/写/执行访问的特定人员。
- 支持 MEM OMA-URI 和 GPO。
- 支持的'[设备属性](#device-properties)'，如所列。
- 有关 Windows 中的功能，请参阅[可移动存储访问控制](device-control-removable-storage-access-control.md)。

**支持的平台**- Windows 10

**macOS 支持详细信息**
- 在计算机级别应用：同一策略适用于任何登录的用户。
- 有关 macOS 特定的信息，请参阅 [macOS 的设备控件](mac-device-control-overview.md)。
 
**支持的平台** - macOS Catalina 10.15.4+ (启用了系统扩展) 

### <a name="windows-portable-device-access-control"></a>Windows便携设备访问控制

**功能**- 拒绝对可移植设备Windows [](/windows-hardware/drivers/portable/)读取或写入访问，例如：平板电脑、iPhone。

**描述**
- 在计算机或用户或两者中应用。
- 支持 MEM OMA-URI 和 GPO。

**支持的平台**- Windows 10

### <a name="endpoint-dlp-removable-storage"></a>终结点 DLP 可移动存储

**功能** - 审核或警告或阻止用户将项目或信息复制到可移动媒体或 USB 设备。

**说明**- 若要详细了解Windows，请参阅了解Microsoft 365 [终结点数据丢失防护](../../compliance/endpoint-dlp-learn-about.md)。

**支持的平台**- Windows 10

### <a name="bitlocker"></a>BitLocker 

**Capabilities**
- 阻止将数据写入到不受保护的BitLocker驱动器。
- 除非在组织拥有的计算机上对可移动驱动器进行了加密，否则阻止访问可移动驱动器
 
**说明**- 有关此Windows，请参阅BitLocker [– 可移动驱动器设置。](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings)

**支持的平台**- Windows 10

## <a name="device-properties"></a>设备属性

Microsoft Defender for Endpoint Device Control Removable 存储 Protection 允许你根据下表中描述的属性限制可移动存储访问：


|属性名  |适用的策略  |适用于操作系统  |说明  |
|---------|---------|---------|---------|
|设备类    |     [如何使用 Microsoft Defender for Endpoint 控制 USB 设备和其他可移动媒体](control-usb-devices-using-intune.md)     |   Windows      |  有关设备 ID 格式的信息，请参阅 [设备设置类](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors)。 **注意**：设备安装可以应用于任何设备，而不仅是可移动存储。       |
|主 ID   |     可移动存储访问控制    |   Windows      |      主 ID 包括可移动存储和 CD/DVD。   |
|设备 ID     |  如何使用 Microsoft Defender for Endpoint 控制[USB 设备和其他可移动媒体](control-usb-devices-using-intune.md);可移动存储访问控制       |      Windows   |    有关设备 ID 格式的信息，请参阅标准 [USB](/windows-hardware/drivers/install/standard-usb-identifiers)标识符，例如 USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07      |
|硬件 ID     |     如何使用 Microsoft Defender for Endpoint 控制[USB 设备和其他可移动媒体](control-usb-devices-using-intune.md);可移动存储访问控制    |     Windows    |    一个标识系统中设备的字符串，例如 USBSTOR\DiskGeneric_Flash_Disk______8.07; **注意**：硬件 ID 不是唯一的;不同设备可能共享相同的值。|
|实例 ID    | 设备安装;可移动存储访问控制     |     Windows    |   唯一标识系统中设备的字符串，例如 USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0      |
|友好名称     |     可移动存储访问控制    |   Windows      |    附加到设备的字符串，例如通用闪存磁盘 USB 设备     |
|供应商 ID/产品 ID     |  可移动存储访问控制       |   WindowsMac      |     供应商 ID 是 USB 委员会分配给供应商的四位数供应商代码。 产品 ID 是供应商分配给设备的四位数产品代码;支持通配符。    |
|Serial NumberId     |     可移动存储访问控制    |      WindowsMac   |     例如 <SerialNumberId>，002324B534BCB431B000058A</SerialNumberId>    |

## <a name="related-topic"></a>相关主题

- [Microsoft Defender for Endpoint 设备控件可移动存储访问控制](device-control-removable-storage-access-control.md)

