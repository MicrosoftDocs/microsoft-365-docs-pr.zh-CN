---
title: '基于硬件的隔离 (Windows 10) '
ms.reviewer: ''
description: 了解软件中基于硬件的隔离Windows 10恶意软件的防护。
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.author: macapara
ms.date: 09/07/2018
ms.technology: mde
ms.openlocfilehash: b3babf858ac19e70119a2dc6a58b25359f1b05c1
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842982"
---
# <a name="hardware-based-isolation-in-windows-10"></a>Windows 10 中基于硬件的隔离

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


基于硬件的隔离可帮助保护 Windows 10系统完整性，并且与 Microsoft Defender for Endpoint 集成。 

| 功能 | 说明 |
|------------|-------------|
| [Windows Defender 应用程序防护](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview.md) | 应用程序防护可保护你的设备免受高级攻击，同时保持你的工作效率。 使用基于硬件的独特隔离方法，目标是将不受信任的网站和 PDF 文档隔离在轻型容器内，该容器通过本机虚拟机监控程序与操作系统Windows隔离。 如果不受信任的站点或 PDF 文档是恶意的，它仍包含在应用程序防护的安全容器中，使桌面电脑受到保护，并且攻击者不会访问企业数据。 |
| [Windows DefenderSystem Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows.md) | System Guard 在系统启动时和运行后保护和维护系统的完整性，并且使用证明验证系统完整性。  |

