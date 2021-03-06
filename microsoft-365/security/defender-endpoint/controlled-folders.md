---
title: 保护重要文件夹免受勒索软件攻击，防止通过受控文件夹访问权限加密文件
description: 可以保护默认文件夹中的文件免受恶意应用更改。 阻止勒索软件加密文件。
keywords: 受控文件夹访问权限， windows 10， windows defender， 勒索软件， 保护， 文件， 文件夹
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.date: 06/10/2021
ms.reviewer: v-maave
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: c60620d2a589c8473764b810d1fcb0e24f674451
ms.sourcegitcommit: 33d19853a38dfa4e6ed21b313976643670a14581
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2021
ms.locfileid: "52904052"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>使用受控文件夹访问权限保护重要文件夹

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>什么是受控文件夹访问权限？

受控文件夹访问权限有助于保护你有价值的数据免受恶意应用和威胁（如勒索软件）的侵害。 受控文件夹访问权限通过针对已知受信任应用列表检查应用来保护你的数据。 在 Windows Server 2019 和 Windows 10 客户端上受支持，可针对托管设备) 使用 Windows 安全中心 应用、Microsoft Endpoint Configuration Manager 或 Intune (打开受控文件夹) 。 

> [!NOTE]
> 脚本引擎不受信任，你无法允许它们访问受控的受保护文件夹。  例如，即使允许使用证书和文件指示器，PowerShell 也不受受控文件夹访问权限 [信任](/microsoft-365/security/defender-endpoint/indicator-certificates)。 

受控文件夹访问权限最适用于 [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md)，它为你提供有关受控文件夹访问权限事件的详细报告，并作为常用的警报调查方案的一 [部分进行阻止](investigate-alerts.md)。

> [!TIP]
> 受控文件夹访问块不会在警报队列中 [生成警报](alerts-queue.md)。 但是，可以在设备时间线视图中查看有关受控文件夹访问块的信息[](investigate-machines.md)，同时使用高级搜寻或[](advanced-hunting-overview.md)[自定义检测规则](custom-detection-rules.md)。

## <a name="how-does-controlled-folder-access-work"></a>受控文件夹访问权限是如何工作的？

受控文件夹访问权限的工作方式是仅允许受信任的应用访问受保护的文件夹。 在配置受控文件夹访问权限时指定受保护的文件夹。 通常，常用文件夹（如用于文档、图片、下载等的文件夹）包含在受控文件夹列表中。 

受控文件夹访问权限适用于受信任应用列表。 受信任软件列表中包含的应用将正常工作。 列表中未包含的应用无法对受保护文件夹内的文件进行任何更改。 

根据应用的普遍程度和信誉将应用添加到列表中。 在整个组织中非常普遍且从未显示任何被视为恶意行为的应用被视为可信赖。 这些应用会自动添加到列表中。

还可使用 Configuration Manager 或 Intune 将应用手动添加到受信任的列表中。 其他操作（如 [添加](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file) 应用的文件指示器）可以从安全中心控制台执行。

## <a name="why-controlled-folder-access-is-important"></a>受控文件夹访问权限为什么很重要

受控文件夹访问权限在帮助保护文档和信息免受勒索软件攻击 [方面尤其有用](https://www.microsoft.com/wdsi/threats/ransomware)。 在勒索软件攻击中，你的文件可以加密并保存。 受控文件夹访问权限就位后，应用尝试对受保护文件夹中的文件进行更改的计算机上将显示一条通知。 可以使用 [公司详细信息和](customize-attack-surface-reduction.md#customize-the-notification) 联系信息自定义通知。 您还可以单独启用规则以自定义功能监视的技术。

受保护的 [文件夹包括](#review-controlled-folder-access-events-in-windows-event-viewer) 公用系统文件夹 (包括启动) ，你可以 [添加更多文件夹](customize-controlled-folders.md#protect-additional-folders)。 还可以允许 [应用](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) 向它们授予对受保护文件夹的访问权限。

可以使用审核 [模式评估](audit-windows-defender.md) 受控文件夹访问权限启用后对组织的影响。 您还可以访问 Windows Defender Test ground[网站，demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground)确认功能是否正常工作并查看其工作方式。

受控文件夹访问权限支持以下版本的 Windows：
- [Windows 10版本 1709](/windows/whats-new/whats-new-windows-10-version-1709)及更高版本
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

## <a name="windows-system-folders-are-protected-by-default"></a>Windows默认保护系统文件夹

Windows默认保护系统文件夹以及其他一些文件夹： 

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

> [!NOTE]
> 可以将其他文件夹配置为受保护，但无法删除Windows系统文件夹。

## <a name="requirements-for-controlled-folder-access"></a>受控文件夹访问权限的要求

受控文件夹访问权限需要启用Microsoft Defender 防病毒[实时保护](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)。

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>在 Defender 门户中查看受控Microsoft 365访问事件

Defender for Endpoint 提供事件的详细报告和阻止，作为在[](investigate-alerts.md)Microsoft 365 Defender 门户中警报调查方案的一部分。  (请参阅 Microsoft [Defender for Endpoint in Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).) 

可以使用高级搜寻查询 Microsoft Defender 的终结点 [数据](/microsoft-365/security/defender-endpoint/advanced-hunting-windows-defender-advanced-threat-protection)。 如果你使用的是审核[模式](audit-windows-defender.md)，可以使用高级搜寻查看受控文件夹[](advanced-hunting-overview.md)访问权限设置在启用后将如何影响你的环境。

示例查询：

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>在事件查看器中查看受控Windows访问事件

你可以查看Windows事件日志，以查看当受控文件夹访问权限阻止应用 (或审核) 创建的事件：

1. 下载 [评估包](https://aka.ms/mp7z2w) ，将文件 *cfa-events.xml* 到设备上易于访问的位置。
2. 在 **"开始**"菜单中键入事件查看器以打开Windows事件查看器。
3. 在左侧面板的"操作 **"下**，选择 **"导入自定义视图..."。**
4. 导航到提取 *内容cfa-events.xml并选择* 它。 或者，[直接复制 XML。](event-views.md)
5. 选择“**确定**”。

下表显示与受控文件夹访问权限相关的事件：

|事件 ID | 说明 |
|:---|:---|
|5007 | 更改设置时的事件 |
|1124 | 已审核的受控文件夹访问事件 | 
|1123 | 阻止的受控文件夹访问事件 |

## <a name="view-or-change-the-list-of-protected-folders"></a>查看或更改受保护的文件夹列表

可以使用该Windows 安全中心查看受受控文件夹访问权限保护的文件夹列表。 

1. 在 Windows 10 设备上，打开Windows 安全中心应用。
2. 选择“**病毒和威胁防护**”。
3. 在 **勒索软件保护下**，选择 **管理勒索软件保护**。
4. 如果关闭受控文件夹访问权限，你需要将其打开。 选择 **受保护的文件夹**。
5. 采取以下步骤之一：
   - 若要添加文件夹，请选择 **" + 添加受保护的文件夹"。**
   - 若要删除文件夹，请选择该文件夹，然后选择"删除 **"。** 

> [!NOTE]
> [Windows默认保护](#windows-system-folders-are-protected-by-default)系统文件夹，并且无法从列表中删除它们。


