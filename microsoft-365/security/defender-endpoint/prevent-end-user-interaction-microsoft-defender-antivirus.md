---
title: 隐藏 Microsoft Defender 防病毒界面
description: 你可以隐藏 Windows 安全应用中的病毒和威胁防护磁贴。
keywords: ui 锁定， 无头模式， 隐藏应用， 隐藏设置， 隐藏界面
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 6b5ce018db436aee35bfa1899fb42f1dca31efa6
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690178"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>阻止用户查看 Microsoft Defender 防病毒用户界面或与之交互

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

可以使用组策略阻止终结点上的用户看到 Microsoft Defender 防病毒界面。 还可以阻止他们暂停扫描。

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>隐藏 Microsoft Defender 防病毒界面

在 Windows 10 版本 1703 中，隐藏界面将隐藏 Microsoft Defender 防病毒通知，并防止病毒 & 威胁防护磁贴显示在 Windows 安全应用中。

将设置设置为"**已启用"：**

![无防护图标和病毒和威胁防护部分 Windows 安全屏幕截图](images/defender/wdav-headless-mode-1703.png)

将设置设置为"已 **禁用"** 或未配置：

![显示防护图标以及病毒和威胁防护部分 Windows 安全性的屏幕截图](images/defender/wdav-headless-mode-off-1703.png)

>[!NOTE]
>隐藏界面还会阻止在终结点上显示 Microsoft Defender 防病毒通知。 Microsoft Defender for Endpoint 通知仍将显示。 还可以单独 [配置终结点上显示的通知](configure-notifications-microsoft-defender-antivirus.md)

在早期版本的 Windows 10 中，该设置将隐藏Windows Defender客户端接口。 如果用户尝试打开它，他们将收到一条警告，指出"你的系统管理员已限制对此应用的访问"。

![在早于 1703 的 Windows 10 版本中启用无头模式时显示警告消息](images/defender/wdav-headless-mode-1607.png)

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>使用组策略向用户隐藏 Microsoft Defender AV 界面

1. 在组策略管理计算机上，打开组 [策略管理控制台](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)，右键单击要配置的组策略对象，**然后单击编辑。**

2. 使用组 **策略管理编辑器转到** 计算机 **配置**。

3. 单击 **"管理模板"。**

4. 将树展开到 **Microsoft Defender 防病毒>客户端**> Windows 组件。

5. 双击启用 **无头 UI 模式** 设置，将选项设置为 **已启用**。 单击“**确定**”。 

有关 [阻止用户修改其电脑保护](configure-local-policy-overrides-microsoft-defender-antivirus.md) 的更多选项，请参阅防止用户在本地修改策略设置。

## <a name="prevent-users-from-pausing-a-scan"></a>阻止用户暂停扫描

你可以阻止用户暂停扫描，这有助于确保计划扫描或按需扫描不会被用户中断。

> [!NOTE]
> 此设置在 Windows 10 上不受支持。

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>使用组策略阻止用户暂停扫描

1. 在组策略管理计算机上，打开组 [策略管理控制台](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)，右键单击要配置的组策略对象，**然后单击编辑。**

2. 使用组 **策略管理编辑器转到** 计算机 **配置**。

3. 单击 **"管理模板"。**

4. 将树展开到 **Windows 组件** Microsoft Defender  >  **防病毒**  >  **扫描**。

5. 双击允许用户暂停 **扫描设置** ，将选项设置为 **已禁用**。 单击“**确定**”。 

## <a name="related-articles"></a>相关文章

- [配置终结点上显示的通知](configure-notifications-microsoft-defender-antivirus.md)

- [配置最终用户与 Microsoft Defender 防病毒的交互](configure-end-user-interaction-microsoft-defender-antivirus.md)

- [Windows 10 中的 Microsoft Defender 防病毒](microsoft-defender-antivirus-in-windows-10.md)