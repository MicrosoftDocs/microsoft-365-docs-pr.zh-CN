---
title: Mac 上的 Microsoft Defender for Endpoint 的新增功能
description: 了解 Mac 上早期版本的 Microsoft Defender for Endpoint 的主要更改。
keywords: microsoft， defender， Microsoft Defender for Endpoint， mac， 安装， macos， whatsnew
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6ef594d4ccb25f688be21b4e8fe6aac2f024eb1d
ms.sourcegitcommit: 41c7f7bd5c808ee5ceca0f6efe13d4e67da0262b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2021
ms.locfileid: "53419747"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Mac 上的 Microsoft Defender for Endpoint 的新增功能

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!IMPORTANT]
> 在 macOS 11 (Sur) 上，Microsoft Defender for Endpoint 需要额外的配置文件。 如果你是从 macOS 早期版本升级的现有客户，请确保部署此页中列出的其他 [配置文件](mac-sysext-policies.md)。

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0) 

- Bug 修复

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0) 

- [macOS 的设备](mac-device-control-overview.md) 控件现已一般可用
- 解决了无法从 macOS 11 上的"大 Sur"菜单 (快速扫描) 
- 其他 Bug 修复

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0) 

- 解决了从 Microsoft Defender for Endpoint 和其他应用程序并发访问密钥链可能导致密钥链损坏的问题。

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0) 

- 从此版本开始，在通过命令行客户端触发的按需防病毒扫描期间检测到的威胁将自动修正。 扫描期间通过用户界面触发的威胁仍然需要手动操作。
- `mdatp diagnostic real-time-protection-statistics` 现在支持两个其他开关：
  - `--sort`：按扫描的文件总数对输出进行降序排序
  - `--top N`：显示前 N 个 (仅在指定了值 `--sort` 时) 
- 性能改进 (在 BUG 修复中) &使用时的性能改进

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0) 

- 修复以适应 macOS Catalina 和更早版本 Apple 证书过期。 此修补程序还原 TVM &威胁 (漏洞) 功能。

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0) 

- macOS 上的 Microsoft Defender for Endpoint 现在可供美国政府客户预览使用。 有关详细信息，请参阅 [Microsoft Defender for Endpoint for US Government customers](gov.md)。
- 性能改进 (专为使用 XCode 模拟器应用修复错误) &的情况。

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0) 

- 向命令行工具添加了一个新选项，用于查看有关上次按需扫描的信息。 若要查看有关上次按需扫描的信息，请运行 `mdatp health --details antivirus`
- Bug 修复&性能改进

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0) 

- Bug 修复&性能改进

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0) 

- Bug 修复&性能改进

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0) 

> [!NOTE]
> 此版本已弃用旧的命令行工具语法。 有关新语法的信息，请参阅 [Resources](mac-resources.md#configuring-from-the-command-line)。

- 添加了一个新的命令行开关以禁用网络扩展 `mdatp system-extension network-filter disable` ：。 此命令可用于解决与 Mac 上的 Microsoft Defender for Endpoint 相关的网络问题
- Bug 修复&性能改进

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0) 

- Bug 修复

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0) 

- 改进了在 macOS 11 Big Sur 上运行的代理的可靠性
- 添加了一个新的命令行开关 () 自定义扫描过程中忽略 `--ignore-exclusions` AV 排除 `mdatp scan custom` () 
- Bug 修复&性能改进

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0) 

- 删除了 Microsoft Defender for Endpoint 触发 macOS 11 (大 Sur) 清单到内核内核错误时的条件
- 修复了在 Mac 11 和 Big Sur (运行时 Endpoint Security 系统扩展) 
- Bug 修复

## <a name="1011072"></a>101.10.72

- Bug 修复

## <a name="1010961"></a>101.09.61

- 添加了用于禁用 [发送反馈选项的新托管首选项](mac-preferences.md#show--hide-option-to-send-feedback)
- "状态"菜单图标现在在管理产品设置时显示正常状态。 以前，状态菜单图标显示警告或错误状态，即使产品设置由管理员管理
- Bug 修复&性能改进

## <a name="1010950"></a>101.09.50

- 该产品版本已在 macOS Big Sur 11 beta 9 上经过验证

- 命令行工具的新 `mdatp` 语法现在是默认语法。 有关新语法详细信息，请参阅[macOS](mac-resources.md#configuring-from-the-command-line)上的 Microsoft Defender for Endpoint 的资源

  > [!NOTE]
  > **2021** 年 1 月 1 日将从产品中删除旧的命令行工具语法。

- 使用新的参数扩展 () ，该参数允许将诊断日志 `mdatp diagnostic create` `--path [directory]` 保存到其他目录
- Bug 修复&性能改进

## <a name="1010949"></a>101.09.49

- 用户界面改进，用于区分由 IT 管理员管理的排除项与本地用户定义的排除项
- 按需扫描期间改进的 CPU 使用率
- Bug 修复&性能改进

## <a name="1010723"></a>101.07.23

- 向 输出添加了新字段，用于检查被动模式的状态和EDR `mdatp --health` ID

  > [!NOTE]
  > `mdatp --health` 将在将来的 `mdatp health` 产品更新中替换为 。

- 修复了在用户界面中自动提交示例未标记为托管的错误
- 添加了用于控制防病毒扫描历史记录中项目的保留的新设置。 现在可以指定 [在扫描历史记录](mac-preferences.md#antivirus-scan-history-retention-in-days) 中保留项目的天数，并指定扫描历史记录中 [的最大项目数](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Bug 修复

## <a name="1010663"></a>101.06.63

- 解决了版本 中引入的性能回归 `101.05.17` 问题。 该回归与修复一起引入，以消除一些客户在访问 SMB 共享时观察到的内核错误。 我们已还原此代码更改，并正在调查消除内核内核错误的替代方法。

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> 我们正在为命令行工具开发新的增强 `mdatp` 语法。 新语法当前是预览体验成员 -快和预览体验成员 - 慢更新频道中的默认语法。 我们鼓励你使用这种新语法来自我激励。
> 
> 我们将继续支持旧语法与新语法并行，并针对即将推出的几个月中的旧语法弃用计划提供更多通信。

- 解决了访问 SMB 文件共享时有时发生的内核内核问题
- Bug 修复&性能改进

## <a name="1010516"></a>101.05.16

- 对快速扫描逻辑的改进，可显著减少扫描的文件数
- 添加了 [对命令行](mac-resources.md#how-to-enable-autocompletion) 工具的自动完成支持
- Bug 修复

## <a name="1010312"></a>101.03.12

- Bug 修复&性能改进

## <a name="1010154"></a>101.01.54

- 有关与时间机兼容性的改进
- 辅助功能改进
- Bug 修复&性能改进

## <a name="1010031"></a>101.00.31

- 为 [Intune 用户改进了产品载入体验](/mem/intune/apps/apps-advanced-threat-protection-macos)
- 防病毒 [排除项现在支持通配符](mac-exclusions.md#supported-exclusion-types)
- 添加了从 macOS 上下文菜单触发防病毒扫描的能力。 现在，你可以右键单击查找器中的文件或文件夹，然后选择使用 **Microsoft Defender for Endpoint 扫描**
- 安装程序现在明确不允许就地产品降级。 如果需要降级，请先卸载现有版本并重新配置设备
- Bug 修复&性能改进

## <a name="1009027"></a>100.90.27

- 现在可以在 macOS [上](mac-updates.md#set-the-channel-name) 为 Microsoft Defender for Endpoint 设置与系统范围的更新通道不同的更新通道
- 新产品图标
- 其他用户体验改进
- Bug 修复

## <a name="1008692"></a>100.86.92

- 有关与时间机兼容性的改进
- 解决了产品有时在卸载期间未清理所有 `/Library/Application Support/Microsoft/Defender` 文件的问题
- 通过 Microsoft AutoUpdate 更新 Microsoft 产品时降低了产品的 CPU 使用率
- Bug 修复&性能改进

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> 为了确保对 macOS 设备进行最完整的保护，并符合 Apple 停止将 macOS 本机安全更新交付到低于 [current – 2] 的操作系统版本，macOS Sierra [10.12] 上将不再支持适用于 Mac 的 MDATP 部署和更新。 适用于 Mac 的 MDATP 更新和增强功能将传递到运行版本 Catalina [10.15]、Mojave [10.14] 和 High Sierra [10.13] 的设备。 
>
> 如果你已经将适用于 Mac 的 MDATP 部署到 Sierra [10.12] 设备，请升级到最新的 macOS 版本以消除丢失保护的风险。

- Bug 修复&性能改进

## <a name="1008373"></a>100.83.73

- 为 IT 管理员添加了更多有关排除[管理](mac-preferences.md#exclusion-merge-policy)、威胁类型[](mac-preferences.md#threat-type-settings-merge-policy)设置管理和禁止[威胁操作的控制](mac-preferences.md#disallowed-threat-actions)
- 当设备上未启用"完全磁盘访问"时，现在状态菜单中将显示一条警告
- Bug 修复&性能改进

## <a name="1008260"></a>100.82.60

- 解决了产品无法开始关注定义更新的问题。

## <a name="1008042"></a>100.80.42

- Bug 修复

## <a name="1007942"></a>100.79.42

- 修复了 Mac 上的 Microsoft Defender for Endpoint 有时干扰时间计算机的问题
- 向命令行实用工具添加了一个新开关，用于测试与后端服务的连接
  ```bash
  mdatp connectivity test
  ```
- 添加了在用户界面中查看完整威胁历史记录 (可以从"保护历史记录"视图访问) 
- Bug 修复&性能改进

## <a name="1007215"></a>100.72.15

- Bug 修复

## <a name="1007099"></a>100.70.99

- 解决了在启用实时保护时影响某些用户升级到 macOS 加泰罗尼亚语的能力的问题。 此个别问题由 Microsoft Defender for Endpoint 在Catalina 升级包中锁定文件，同时扫描它们以发现威胁导致升级序列失败导致的。

## <a name="1006899"></a>100.68.99

- 添加了将防病毒功能配置为在被动模式下 [运行的功能](mac-preferences.md#enable--disable-passive-mode)
- Bug 修复&性能改进

## <a name="1006528"></a>100.65.28

- 增加了对 macOS 加泰罗尼亚语的支持

  > [!CAUTION]
  > macOS 10.15 (Catalina) 新增了安全和隐私增强功能。 从此版本开始，默认情况下，应用程序无法访问磁盘上的某些位置 (如文档、下载、桌面等) 未经明确同意。 如果没有此同意，Microsoft Defender for Endpoint 将无法完全保护你的设备。
  >
  > 授予此同意的机制取决于你部署适用于终结点的 Microsoft Defender 的方式：
  >
  > - 有关手动部署，请参阅手动部署主题 [中的更新](mac-install-manually.md#how-to-allow-full-disk-access) 说明。
  > - 有关托管部署，请参阅基于[JAMF](mac-install-with-jamf.md)的部署和基于Microsoft Intune[部署主题中的更新](mac-install-with-intune.md#create-system-configuration-profiles)说明。

- Bug 修复&性能改进
