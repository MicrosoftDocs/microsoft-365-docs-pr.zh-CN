---
title: Microsoft Defender for Endpoint 设备时间线事件标志
description: 使用 Microsoft Defender for Endpoint 设备时间线事件标志
keywords: 适用于终结点的 Defender 设备时间线、事件标志
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a34efc171d3bb3aa1fcf33e0f56700149885ac2e
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165149"
---
# <a name="microsoft-defender-for-endpoint-device-timeline-event-flags"></a>Microsoft Defender for Endpoint 设备时间线事件标志

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Defender for Endpoint 设备时间线中的事件标志可帮助你在调查潜在攻击时筛选和组织特定事件。

Defender for Endpoint 设备时间线提供设备上观测到的事件和相关警报的时间顺序视图。 通过此事件列表，可以完全查看在设备上观测到的任何事件、文件和 IP 地址。 列表有时可能很长。 设备时间线事件标志可帮助你跟踪可能相关的事件。 

完成设备时间线后，你可以排序、筛选和导出已标记的特定事件。

在导航设备时间线时，你可以搜索和筛选特定事件。 可以通过：设置事件标志： 

- 突出显示最重要的事件 
- 标记需要深入探究的事件 
- 构建干净泄露时间线



## <a name="flag-an-event"></a>标记事件
1. 查找要标记的事件
2. 单击"标志"列中的标志图标。 
![设备时间线标志的图像](images/device-flags.png)

## <a name="view-flagged-events"></a>查看标记的事件  
1. 在"时间线 **筛选器"** 部分，启用 **"已标记的事件"。**
2. 单击“**应用**”。 只显示标记的事件。
可以通过单击时间栏来应用其他筛选器。 这将只显示标记事件之前的事件。  
![具有筛选功能的设备时间线标志的图像](images/device-flag-filter.png)
