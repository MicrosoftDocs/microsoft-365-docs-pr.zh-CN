---
title: 在 Microsoft Defender for Endpoint 中检查传感器的运行状况
description: 检查设备的传感器运行状况，以确定哪些设备配置不正确、处于非活动状态或未报告传感器数据。
keywords: 传感器， 传感器运行状况， 错误配置， 非活动， 无传感器数据， 传感器数据， 通信受损， 通信
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 0361b7956339670d006c9f050274e07d4e979bca
ms.sourcegitcommit: 13ce4b31303a1a21ca53700a54bcf8d91ad2f8c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2021
ms.locfileid: "51904160"
---
# <a name="check-sensor-health-state-in-microsoft-defender-for-endpoint"></a>检查 Microsoft Defender for Endpoint 中的传感器运行状况

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-checksensor-abovefoldlink)

" **具有传感器问题的设备"** 磁贴位于安全操作仪表板上。 此磁贴提供有关单个设备提供传感器数据并与 Defender for Endpoint 服务通信的能力的信息。 它报告需要关注的设备数，并帮助你识别有问题的设备并采取措施纠正已知问题。

磁贴上有两个状态指示器，它们提供有关未正确报告给服务的设备数量的信息：
- **配置错误** - 这些设备可能部分向 Defender for Endpoint 服务报告传感器数据，并且可能有需要更正的配置错误。
- **非** 活动 - 在过去一个月内停止向 Defender for Endpoint 服务报告超过七天的设备。

单击任何组将你引导到 **设备列表**，该列表根据你的选择进行筛选。

![具有传感器问题的设备的屏幕截图磁贴](images/atp-devices-with-sensor-issues-tile.png)

在 **"设备"** 列表上，可以按以下状态筛选运行状况列表：
- **Active** - 主动向 Defender for Endpoint 服务报告的设备。
- **错误配置** - 这些设备可能部分向 Defender for Endpoint 服务报告传感器数据，但具有需要更正的配置错误。 配置错误的设备可能具有以下一个问题或以下问题的组合：
  - **无传感器数据** - 设备已停止发送传感器数据。 可以从设备触发有限警报。
  - **通信受损** - 与设备通信的能力受损。 发送文件进行深入分析、阻止文件、将设备与网络隔离以及需要与设备通信的其他操作可能不起作用。
- **非** 活动 - 停止向 Defender for Endpoint 服务报告的设备。

您还可以使用导出功能以 CSV 格式下载 **整个** 列表。 有关筛选器的信息，请参阅 [查看和组织设备列表](machines-view-overview.md)。

>[!NOTE]
>导出 CSV 格式的列表以显示未筛选的数据。 CSV 文件将包含组织的所有设备，而不考虑视图本身应用的任何筛选，并且可能需要大量时间来下载，具体取决于你的组织规模。

![设备列表页面的屏幕截图](images/atp-devices-list-page.png)

单击错误配置或不活动的设备时，可以查看设备详细信息。

## <a name="related-topic"></a>相关主题
- [修复 Defender for Endpoint 中的不正常传感器](fix-unhealthy-sensors.md)
