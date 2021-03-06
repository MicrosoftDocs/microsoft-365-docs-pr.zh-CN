---
title: 使用 WMI Microsoft Defender 防病毒配置应用程序
description: 了解如何使用 WMI 脚本Microsoft Defender 防病毒 Microsoft Defender for Endpoint 中的检索、修改和更新设置来配置和管理自定义设置。
keywords: wmi， 脚本， windows management instrumentation， 配置
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.openlocfilehash: 25518383131e4f7ecb7451965ef7a42b1c6eee4b
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2021
ms.locfileid: "51764059"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>使用 Windows Management Instrumentation (WMI) 配置和管理Microsoft Defender 防病毒

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

WindowsManagement Instrumentation (WMI) 是一个脚本界面，允许您检索、修改和更新设置。

有关 WMI 的更多内容，Microsoft 开发人员网络 [System Administration 库](/windows/win32/wmisdk/wmi-start-page)。

Microsoft Defender 防病毒具有许多特定的 WMI 类，可用于执行与组策略和其他管理工具相同的大多数功能。 许多类都类似于 Defender [PowerShell cmdlet。](use-powershell-cmdlets-microsoft-defender-antivirus.md)

[MSDN Windows Defender WMIv2 提供程序](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)参考库列出了适用于 Microsoft Defender 防病毒 的可用 WMI 类，并包括示例脚本。

使用 WMI 所做的更改将影响部署或进行更改的终结点上的本地设置。 这意味着，使用组策略、Microsoft Endpoint Configuration Manager或Microsoft Intune策略部署可能会覆盖使用 WMI 所做的更改。 

你可以 [配置哪些设置可以使用本地策略覆盖在本地覆盖](configure-local-policy-overrides-microsoft-defender-antivirus.md)。

## <a name="related-topics"></a>相关主题

- [有关管理和配置工具的参考主题](configuration-management-reference-microsoft-defender-antivirus.md)
- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)