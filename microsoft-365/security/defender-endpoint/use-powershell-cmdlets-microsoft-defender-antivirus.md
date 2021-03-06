---
title: 使用 PowerShell cmdlet 配置和运行 Microsoft Defender AV
description: 在Windows 10中，可以使用 PowerShell cmdlet 运行扫描、更新安全智能以及更改 Microsoft Defender 防病毒。
keywords: 扫描， 命令行， mpcmdrun， defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 07/23/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.openlocfilehash: d6fb8dc510e004fa88bf99583cc2cc33ae8c63bb
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765295"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>使用 PowerShell cmdlet 配置和管理Microsoft Defender 防病毒

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

可以使用 PowerShell 在 Windows Defender 中执行各种Windows Defender。 与命令提示符或命令行类似，PowerShell 是基于任务的命令行 shell 和脚本语言，专为系统管理设计。 可以在 MSDN 上的 [PowerShell 中心中阅读有关它的更多信息](/previous-versions/msdn10/mt173057(v=msdn.10))。

有关 cmdlet 及其函数和可用参数的列表，请参阅 [Defender cmdlet 主题](/powershell/module/defender) 。

PowerShell cmdlet 在 Windows Server 环境中最有用，这些环境不依赖图形用户界面 (GUI) 来配置软件。

> [!NOTE]
> PowerShell cmdlet 不应用作完整网络策略管理基础结构（如[Microsoft Endpoint Configuration Manager、](/configmgr)组策略管理控制台或 Microsoft Defender 防病毒[](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))[组策略 ADMX 模板）的](https://www.microsoft.com/download/101445)替换。

使用 PowerShell 所做的更改将影响部署或进行更改的终结点上的本地设置。 这意味着，使用组策略、Microsoft Endpoint Configuration Manager或Microsoft Intune部署策略可能会覆盖使用 PowerShell 所做的更改。

你可以 [配置哪些设置可以使用本地策略覆盖在本地覆盖](configure-local-policy-overrides-microsoft-defender-antivirus.md)。

PowerShell 通常安装在 文件夹 下 `%SystemRoot%\system32\WindowsPowerShell` 。

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>使用 Microsoft Defender 防病毒 PowerShell cmdlet

1. 在搜索Windows中，键入 **powershell**。
2. Select **Windows PowerShell** from the results to open the interface.
3. 输入 PowerShell 命令和任何参数。

> [!NOTE]
> 您可能需要在管理员模式下打开 PowerShell。 右键单击"开始"菜单中的项，单击"以管理员角色运行 **"，** 在权限提示符下单击"是"。

若要打开任何 cmdlet 的联机帮助，请键入以下内容：

```PowerShell
Get-Help <cmdlet> -Online
```

省略 `-online` 参数可获取本地缓存的帮助。

## <a name="related-topics"></a>相关主题

- [有关管理和配置工具的参考主题](configuration-management-reference-microsoft-defender-antivirus.md)
- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender 防病毒Cmdlet](/powershell/module/defender)