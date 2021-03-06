---
title: 启用和配置Microsoft Defender 防病毒保护功能
description: 启用和Microsoft Defender 防病毒实时保护功能，如行为监视、启发和机器学习
keywords: 防病毒， 实时保护， rtp， 机器学习， 行为监视， 启发
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.date: 12/16/2019
manager: dansimp
ms.custom: nextgen
ms.openlocfilehash: 313646c69417082583b27bcfbab540131043ce76
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/14/2021
ms.locfileid: "52926663"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>在组策略中启用和配置 Microsoft Defender 防病毒软件始终启用保护


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

始终持续保护包括实时保护、行为监视和启发，以根据已知的可疑和恶意活动识别恶意软件。

这些活动包括事件，如进程对现有文件进行异常更改、修改或创建自动启动注册表项和启动位置 (也称为自动启动扩展点或 ASP) ，以及文件系统或文件结构的其他更改。

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>在组策略中启用和配置始终启用保护

可以使用本地 **组策略编辑器** 启用和配置Microsoft Defender 防病毒始终启用的保护设置。

启用和配置始终启用保护：

1. 打开 **"本地组策略编辑器"。** 为此，请执行以下操作:  

    1. 在任务栏Windows 10框中，键入 **gpedit**。
    
    1. 在 **"最佳匹配"** 下 **，单击"编辑组策略**"以启动 **"本地组策略编辑器"。**
    
       ![GPEdit 任务栏搜索结果](images/gpedit-search.png)

2. 在本地组策略 **编辑器** 的左窗格中，将树展开到计算机配置管理  >    >  **模板 Windows 组件**  >  **Microsoft Defender 防病毒**。 

3. 配置Microsoft Defender 防病毒反恶意软件服务策略设置。 为此，请执行以下操作:  

    1. 在Microsoft Defender 防病毒 **详细信息**"窗格中，双击下表中指定的策略设置：

       | 设置 | 说明 | 默认设置 |
       |-----------------------------|------------------------|-------------------------------|
       | 允许反恶意软件服务以普通优先级启动 | 你可以降低 Microsoft Defender 防病毒 引擎的优先级，在希望尽可能精简启动过程的轻型部署中，这可能很有用。 这可能会影响对终结点的保护。 | 已启用
       | 允许反恶意软件服务始终运行 | 如果已禁用保护更新，你可以将Microsoft Defender 防病毒仍运行。 这将降低终结点上的保护。 | 禁用 |
    
    1. 配置相应设置，然后单击"确定 **"。**
    
    1. 对表中的每个设置重复上述步骤。

4. 配置Microsoft Defender 防病毒实时保护策略设置。 为此，请执行以下操作:

    1. 在 **"Microsoft Defender 防病毒** 详细信息"窗格中，双击"**实时保护"。** 或者，**在左Microsoft Defender 防病毒** 树中，单击"**实时保护"。**
    
    1. 在 **右侧"实时保护** "详细信息窗格中，双击下表中指定的策略设置：  

       | 设置 | 说明 | 默认设置 |
       |-----------------------------|------------------------|-------------------------------|
       | 打开行为监视 | AV 引擎将监视终结点上的文件进程、文件和注册表更改以及其他事件，以发现可疑和已知的恶意活动。 | 已启用 |
       | 扫描所有下载的文件和附件 | 将自动扫描下载的文件和附件。 除了 SmartScreen 筛选器之外，此操作Windows Defender SmartScreen 筛选器，该筛选器在下载之前和下载过程中扫描文件。 | 已启用 |
       | 监视您的计算机上的文件和程序活动 | Microsoft Defender 防病毒 引擎会记录 (文件写入的任何文件更改，例如移动、复制或修改) 以及打开或运行的导致其他程序运行) 的常规程序活动 (程序。 | 已启用 |
       | 打开原始卷写入通知 | 行为监视将分析有关原始卷写入的信息。 | 已启用 |
       | 启用实时保护时打开进程扫描 | 你可以独立启用Microsoft Defender 防病毒引擎扫描正在运行的进程，以发现可疑的修改或行为。 如果你暂时禁用了实时保护，并且想要自动扫描在禁用时启动的进程，这将非常有用。 | 已启用 |
       | 定义要扫描的已下载文件和附件的最大大小 | 可以定义大小（以 KB 为单位）。 | 已启用 |
       | 配置本地设置替代以启用行为监视 | 为行为监视的配置配置本地替代。 此设置只能由组策略设置。 如果启用此设置，本地首选项设置将优先于组策略。 如果禁用或不配置此设置，则组策略将优先于本地首选项设置。| 已启用 |
       | 配置用于扫描所有下载的文件和附件的本地设置替代 | 配置用于配置扫描的所有已下载文件和附件的本地覆盖。 此设置只能由组策略设置。 如果启用此设置，本地首选项设置将优先于组策略。 如果禁用或不配置此设置，则组策略将优先于本地首选项设置。| 已启用 |
       | 配置本地设置覆盖以监视您的计算机上的文件和程序活动 | 为计算机上文件和程序活动的监视配置配置本地覆盖。 此设置只能由组策略设置。 如果启用此设置，本地首选项设置将优先于组策略。 如果禁用或不配置此设置，则组策略将优先于本地首选项设置。| 已启用 |
       | 配置本地设置覆盖以启用实时保护 | 为配置配置配置配置本地覆盖以启用实时保护。 此设置只能由组策略设置。 如果启用此设置，本地首选项设置将优先于组策略。 如果禁用或不配置此设置，则组策略将优先于本地首选项设置。| 已启用 |
       | 配置本地设置覆盖以监视传入和传出文件活动 | 为传入和传出文件活动的监视配置配置本地覆盖。 此设置只能由组策略设置。 如果启用此设置，本地首选项设置将优先于组策略。 如果禁用或不配置此设置，则组策略将优先于本地首选项设置。 | 已启用 |
       | 配置对传入和传出文件和程序活动的监视 | 指定监控应在传入、传出和/或两个方向上执行。 这适用于Windows服务器安装，其中定义了特定服务器或服务器角色，这些服务器角色仅看到一个方向中的大量文件更改，并且希望提高网络性能。 网络上 (和) 的完全更新的终结点将几乎看不到性能影响，无论文件更改的数量或方向如何。 | 启用 (两个方向)  |

    1. 配置相应设置，然后单击"确定 **"。**
    
    1. 对表中的每个设置重复上述步骤。

5. 配置Microsoft Defender 防病毒扫描策略设置。 为此，请执行以下操作:  

    1. 从左 **Microsoft Defender 防病毒** 树中，单击"扫描 **"。**
    
       ![Microsoft Defender 防病毒扫描选项](images/gpedit-windows-defender-antivirus-scan.png)

    1. 在右侧 **"** 扫描详细信息"窗格中，双击下表中指定的策略设置：

       | 设置 | 说明 | 默认设置 |
       |-----------------------------|------------------------|-------------------------------|    
       | 打开启发式 | 启发式保护将在系统要求引擎立即Microsoft Defender 防病毒或阻止可疑活动。 | 已启用 |

    1. 配置相应设置，然后单击"确定 **"。**
    
6. 关闭 **本地组策略编辑器**。


## <a name="disable-real-time-protection-in-group-policy"></a>在组策略中禁用实时保护

> [!WARNING]
> 禁用实时保护会大大降低终结点上的保护，不建议这样做。

默认启用主要实时保护功能，但可以使用本地组策略编辑器 **禁用该功能**。

在组策略中禁用实时保护：

1. 打开 **"本地组策略编辑器"。**

   1. 在任务栏Windows 10框中，键入 **gpedit**。
   
   1. 在 **"最佳匹配"** 下 **，单击"编辑组策略**"以启动 **"本地组策略编辑器"。**

2.  在本地组策略编辑器的左窗格中，将树展开到计算机配置管理模板  >    >  **Windows 组件** Microsoft Defender 防病毒  >    >  **实时保护**。

3. 在 **右侧"实时保护"** 详细信息窗格中，双击"**关闭实时保护"。**

   ![关闭实时保护](images/gpedit-turn-off-real-time-protection.png)

4. 在 **关闭实时保护设置** 窗口中，将选项设置为 **已启用**。

   ![关闭启用实时保护](images/gpedit-turn-off-real-time-protection-enabled.png)
   
5. 单击“**确定**”。

6. 关闭 **本地组策略编辑器**。

## <a name="related-articles"></a>相关文章

- [配置方案、高要求和实时保护](configure-protection-features-microsoft-defender-antivirus.md)
- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)
