---
title: 配置Microsoft Defender 防病毒通知
description: 了解如何在终结点上配置和自定义标准Microsoft Defender 防病毒通知。
keywords: 通知， defender， 防病毒， 终结点， 管理， 管理员
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/16/2021
ms.reviewer: ''
manager: dansimp
ms.openlocfilehash: a7a838bb15cd011b750fbfa3d6df100ddf9f713c
ms.sourcegitcommit: 34c06715e036255faa75c66ebf95c12a85f8ef42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2021
ms.locfileid: "52985404"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>配置Microsoft Defender 防病毒终结点上显示的通知

**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

在Windows 10中，有关恶意软件检测和修正的应用程序通知更加可靠、一致且简洁。 Microsoft Defender 防病毒扫描完成并检测到威胁时，终结点上会显示通知。 通知遵循计划扫描和手动触发的扫描。 这些通知还会显示在 **通知中心** 中，并且扫描和威胁检测的摘要会定期显示。

如果你是组织安全团队的一员，可以配置通知在终结点上的显示方式，例如提示系统重启或指示已检测并修复威胁的通知。

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>使用组策略或应用配置Windows 安全中心通知

可以在应用和组策略中配置其他通知的显示，如Windows 安全中心[威胁](microsoft-defender-security-center-antivirus.md)检测摘要。

> [!NOTE]
> 在 Windows 10 版本 1607 中，该功能称为增强型通知，在 Windows 设置  >  **Update & security Windows Defender**  >  **下配置**。 在所有版本的通知的组策略Windows 10，通知功能称为增强 **型通知**。

### <a name="use-group-policy-to-disable-additional-notifications"></a>使用组策略禁用其他通知

1. 在组策略管理计算机上，打开 [策略管理控制台](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))。

2. 右键单击要配置的组策略对象， **然后选择编辑**。

3. 在组 **策略管理编辑器中** ，转到计算机 **配置**。

4. 选择 **"管理模板"。**

5. 展开树以Windows   >  **Reporting**Microsoft Defender 防病毒>** 组件。

6. 双击关闭 **增强型通知**，将选项设置为 **已启用**。 然后，选择“**确定**”。 这将阻止显示其他通知。

> [!IMPORTANT]
> 禁用其他通知不会禁用关键通知，例如威胁检测和修正警报。

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>使用 Windows 安全中心 应用禁用其他通知

1. 通过Windows 安全中心任务栏中的防护图标或搜索"安全"的"开始"菜单打开"安全 **"菜单。**

2. 选择 **病毒&威胁** 防护磁贴 (或左侧菜单栏上的防护图标) ，然后选择病毒防护& **威胁防护设置**

3. 滚动到通知 **部分** ，然后选择更改 **通知设置**。

4. 将开关滑动到 **"关闭"** 或" **打开** "以禁用或启用其他通知。

> [!IMPORTANT]
> 禁用其他通知不会禁用关键通知，例如威胁检测和修正警报。

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>使用组策略配置终结点上的标准通知

可以使用组策略：

- 当用户需要执行一个操作时，在终结点上显示其他自定义文本
- 隐藏终结点上的所有通知
- 隐藏终结点上的重启通知

当你无法隐藏整个通知界面时，隐藏通知Microsoft Defender 防病毒很有用。 有关详细信息[，请参阅防止用户查看 Microsoft Defender 防病毒用户界面](prevent-end-user-interaction-microsoft-defender-antivirus.md)或与之交互。 隐藏通知将仅在策略已部署到的终结点上发生。 与在监视仪表板和报告上 (必须) 操作Microsoft Endpoint Manager Endpoint Protection[通知](/configmgr/protect/deploy-use/monitor-endpoint-protection)。 

若要将自定义联系人信息添加到终结点通知，请参阅[自定义](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center)组织的 Windows 安全中心 应用。

### <a name="use-group-policy-to-hide-notifications"></a>使用组策略隐藏通知

1. 在组策略管理计算机上，打开 [策略管理控制台](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))。

2. 右键单击要配置的组策略对象， **然后选择编辑**。

3. 在组 **策略管理编辑器中** ，转到计算机 **配置** ，然后选择 **管理模板**。

4. 展开树以Windows **客户端**  >  **Microsoft Defender 防病毒**  >  **组件**。 

5. 双击"**取消所有通知"，** 将该选项设置为 **"已启用"。** 

6. 选择“**确定**”。 这将阻止显示其他通知。

### <a name="use-group-policy-to-hide-reboot-notifications"></a>使用组策略隐藏重启通知

1. 在组策略管理计算机上，打开 [策略管理控制台](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))。

2. 右键单击要配置的组策略对象， **然后选择编辑**。

2. 在组 **策略管理编辑器中** ，转到计算机 **配置**。

3. 单击 **"管理模板"。**

4. 展开树以Windows **客户端**  >  **Microsoft Defender 防病毒**  >  **组件**。

5. 双击取消 **重启通知，** 将选项设置为 **已启用**。 

5. 选择“**确定**”。 这将阻止显示其他通知。

