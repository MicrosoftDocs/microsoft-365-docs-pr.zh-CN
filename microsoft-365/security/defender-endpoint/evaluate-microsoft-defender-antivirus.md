---
title: 评估 Microsoft Defender 防病毒
description: 各种规模的企业都可以使用本指南评估和测试 Windows 10 中的 Microsoft Defender 防病毒所提供的保护。
keywords: Microsoft Defender 防病毒， 云保护， 云， 反恶意软件， 安全性， defender， 评估， 测试， 保护， 比较， 实时保护
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: de9c7e845188f47ab5b8e1f9d97871ea36340d19
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690226"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>评估 Microsoft Defender 防病毒

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

使用本指南确定 Microsoft Defender 防病毒如何保护你免受病毒、恶意软件和可能不需要的应用程序的攻击。

>[!TIP]
>还可以访问 Microsoft Defender for Endpoint 演示[](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground)网站，demo.wd.microsoft.com 以确认以下功能是否正常工作并查看这些功能如何工作：
>- 云保护
>- 快速学习 (包括首次看到时阻止) 
>- 可能不需要的应用程序阻止

它介绍了适用于小型企业和大型企业的 Microsoft Defender 防病毒的下一代重要保护功能，以及这些功能如何增强整个网络的恶意软件检测和保护。

可以选择单独配置和评估每个设置，也可以一次配置和评估所有设置。 我们已根据典型评估方案对类似的设置进行分组，并包括有关使用 PowerShell 启用设置的说明。

本指南以 PDF 格式提供，以便脱机查看：

- [下载 PDF 格式的指南](https://www.microsoft.com/download/details.aspx?id=54795)

还可以下载 PowerShell，以自动启用指南中所述的所有设置。 你可以与上述 PDF 下载一起获取脚本，也可以从 PowerShell 库单独获取：

- [下载 PowerShell 脚本以自动配置设置](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> 本指南当前适用于 Microsoft Defender 防病毒的单台计算机评估。 启用本指南中所有设置可能不适合实际部署。
>
> 有关跨网络实际部署和监视 Microsoft Defender 防病毒的最新建议，请参阅 [部署 Microsoft Defender 防病毒](deploy-manage-report-microsoft-defender-antivirus.md)。

## <a name="related-topics"></a>相关主题

- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)
- [部署 Microsoft Defender 防病毒](deploy-manage-report-microsoft-defender-antivirus.md)