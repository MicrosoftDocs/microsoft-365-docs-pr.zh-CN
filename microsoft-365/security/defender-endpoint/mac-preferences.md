---
title: 在 Mac 上设置 Microsoft Defender for Endpoint 的首选项
description: 在企业组织中为 Mac 上的终结点配置 MMicrosoft Defender。
keywords: microsoft， defender， Microsoft Defender for Endpoint， mac， 管理， 首选项， 企业， intune， jamf， macos， catalina， mojave， high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
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
ms.openlocfilehash: b706cb8dbd43d545768c1c573021b5ef401e3c09
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2021
ms.locfileid: "52346398"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>在 macOS 上设置适用于终结点的 Microsoft Defender 的首选项

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**

- [macOS 上的 Microsoft Defender for Endpoint](microsoft-defender-endpoint-mac.md)

>[!IMPORTANT]
>本文包含有关如何在企业组织中为 macOS 上的 Microsoft Defender for Endpoint 设置首选项的说明。 若要使用命令行界面在 macOS 上配置适用于终结点的 Microsoft Defender，请参阅 [资源](mac-resources.md#configuring-from-the-command-line)。

## <a name="summary"></a>摘要

在企业组织中，可以通过使用多种管理工具之一部署的配置文件管理 macOS 上的 Microsoft Defender for Endpoint。 由安全操作团队管理的首选项优先于在设备上本地设置的首选项。 更改通过配置文件设置的首选项需要提升的权限，并且对于没有管理权限的用户不可用。

本文介绍配置文件的结构，包括可用于入门的推荐配置文件，并提供有关如何部署配置文件的说明。

## <a name="configuration-profile-structure"></a>配置文件结构

配置文件是一个 *.plist* 文件，它由键 (标识的条目表示首选项) 的名称，后跟一个值，具体取决于首选项的性质。 值可以是简单的 (，如数值) 或复杂，如嵌套的首选项列表。

>[!CAUTION]
>配置文件的布局取决于你使用的管理控制台。 以下各节包含 JAMF 和 Intune 的配置文件示例。

配置文件的顶级包括产品范围的首选项和 Microsoft Defender for Endpoint 子区域条目，下一节将详细介绍这些首选项和条目。

### <a name="antivirus-engine-preferences"></a>防病毒引擎首选项

配置文件 *的 antivirusEngine* 部分用于管理 Microsoft Defender for Endpoint 的防病毒组件的首选项。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | antivirusEngine |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

#### <a name="enable--disable-real-time-protection"></a>启用/禁用实时保护

指定是否启用实时保护，以在访问文件时对文件进行扫描。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | enableRealTimeProtection |
| **数据类型** | Boolean |
| **可能的值** | true (默认值)  <br/> false |

#### <a name="enable--disable-passive-mode"></a>启用/禁用被动模式

指定防病毒引擎是否在被动模式下运行。 被动模式具有以下含义： 
- 实时保护已关闭
- 按需扫描已打开
- 自动威胁修正已关闭
- 启用安全智能更新
- 状态菜单图标处于隐藏状态

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | passiveMode |
| **数据类型** | Boolean |
| **可能的值** | false（默认值） <br/> true |
| **备注** | 适用于终结点版本 100.67.60 或更高版本的 Microsoft Defender 中可用。 |

#### <a name="exclusion-merge-policy"></a>排除合并策略

指定排除项的合并策略。 它可以是管理员定义的排除项和用户定义的排除项 () 管理员定义的排除项 `merge` `admin_only` () 。 此设置可用于限制本地用户定义自己的排除项。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | exclusionsMergePolicy |
| **数据类型** | String |
| **可能的值** | 合并 (默认)  <br/> admin_only |
| **备注** | 适用于终结点版本 100.83.73 或更高版本的 Microsoft Defender 中可用。 |

#### <a name="scan-exclusions"></a>扫描排除项

指定被扫描排除的实体。 排除项可以通过完整路径、扩展名或文件名指定。
 (排除项指定为项目数组，则管理员可以按任意顺序指定所需数量的元素) 

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | 排除项 |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

##### <a name="type-of-exclusion"></a>排除类型

按类型指定被排除的内容。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | $type |
| **数据类型** | String |
| **可能的值** | excludedPath <br/> excludedFileExtension <br/> excludedFileName |

##### <a name="path-to-excluded-content"></a>排除内容的路径

指定未由完整文件路径扫描的内容。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | path |
| **数据类型** | String |
| **可能的值** | 有效路径 |
| **备注** | 仅在 *排除$type**时适用* |

## <a name="supported-exclusion-types"></a>支持的排除类型

下表显示了 Mac 上的 Defender for Endpoint 支持的排除类型。

排除 | 定义 | 示例
---|---|---
文件扩展名 | 扩展名位于设备上任意位置的所有文件 | `.test`
文件 | 由完整路径标识的特定文件 | `/var/log/test.log`<br/>`/var/log/*.log`<br/>`/var/log/install.?.log`
文件夹 | 指定文件夹下的所有 (以递归)  | `/var/log/`<br/>`/var/*/`
流程 | 特定进程 (的完整路径或文件名指定，) 它打开的所有文件 | `/bin/cat`<br/>`cat`<br/>`c?t`

> [!IMPORTANT]
> 上述路径必须是硬链接，而不是符号链接，才能成功排除。 可以通过运行 来检查路径是否为符号链接 `file <path-name>` 。

文件、文件夹和进程排除项支持以下通配符：

通配符 | 说明 | 示例 | 匹配 | 不匹配
---|---|---|---|---
\* |    匹配任意数目的任何字符，包括无 (请注意，当在路径内使用此通配符时，它将仅替换一个)  | `/var/\*/\*.log` | `/var/log/system.log` | `/var/log/nested/system.log`
? | 匹配任何单个字符 | `file?.log` | `file1.log`<br/>`file2.log` | `file123.log`

##### <a name="path-type-file--directory"></a>文件 (目录的路径) 

指示 *path 属性* 是否引用文件或目录。 

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | isDirectory |
| **数据类型** | Boolean |
| **可能的值** | false（默认值） <br/> true |
| **备注** | 仅在 *排除$type**时适用* |

##### <a name="file-extension-excluded-from-the-scan"></a>从扫描中排除的文件扩展名

指定文件扩展名无法扫描的内容。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | extension |
| **数据类型** | String |
| **可能的值** | 有效的文件扩展名 |
| **备注** | 仅在 *排除**$type FileExtension 时适用* |

##### <a name="process-excluded-from-the-scan"></a>从扫描中排除的进程

指定一个进程，所有文件活动都从扫描中排除。 可以通过进程的名称指定进程， (例如) 或完整路径 (`cat` 例如 `/bin/cat`) 。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | name |
| **数据类型** | String |
| **可能的值** | 任何字符串 |
| **备注** | 仅在 *排除**$type FileName 时适用* |

#### <a name="allowed-threats"></a>允许的威胁

按名称指定未由 Mac 上的 Defender for Endpoint 阻止的威胁。 将允许运行这些威胁。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | allowedThreats |
| **数据类型** | 字符串数组 |

#### <a name="disallowed-threat-actions"></a>不允许威胁操作

限制设备的本地用户在检测到威胁时可采取的操作。 此列表中包含的操作不会显示在用户界面中。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | disallowedThreatActions |
| **数据类型** | 字符串数组 |
| **可能的值** | 允许 (限制用户允许威胁)  <br/> restore (限制用户从隔离网站还原)  |
| **备注** | 适用于终结点版本 100.83.73 或更高版本的 Microsoft Defender 中可用。 |

#### <a name="threat-type-settings"></a>威胁类型设置

指定 macOS 上的 Microsoft Defender for Endpoint 如何处理某些威胁类型。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | threatTypeSettings |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

##### <a name="threat-type"></a>威胁类型

指定威胁类型。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | 注册表项 |
| **数据类型** | String |
| **可能的值** | potentially_unwanted_application <br/> archive_bomb |

##### <a name="action-to-take"></a>要采取的措施

指定在检测到上一节中指定的类型的威胁时要采取什么操作。 从以下选项中进行选择：

- **审核**：你的设备不受此类型威胁的保护，但会记录关于威胁的条目。
- **阻止**：你的设备受到此类型威胁的保护，并且你将在用户界面和安全控制台中收到通知。
- **关闭**：你的设备不受此类型威胁的防御，并且不会记录任何内容。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | 值 |
| **数据类型** | String |
| **可能的值** | 审核 (默认)  <br/> block <br/> off |

#### <a name="threat-type-settings-merge-policy"></a>威胁类型设置合并策略

指定威胁类型设置的合并策略。 这可以是管理员定义的设置和用户定义的设置的组合， () 管理员 `merge` 定义的设置 `admin_only` () 。 此设置可用于限制本地用户为不同的威胁类型定义自己的设置。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | threatTypeSettingsMergePolicy |
| **数据类型** | String |
| **可能的值** | 合并 (默认)  <br/> admin_only |
| **备注** | 适用于终结点版本 100.83.73 或更高版本的 Microsoft Defender 中可用。 |

#### <a name="antivirus-scan-history-retention-in-days"></a>防病毒扫描历史记录保留 (天数) 

指定结果在设备的扫描历史记录中保留的天数。 旧扫描结果将从历史记录中删除。 也从磁盘中删除的旧隔离文件。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | scanResultsRetentionDays |
| **数据类型** | String |
| **可能的值** | 90 (默认值) 。 允许的值从 1 天到 180 天。 |
| **备注** | 适用于终结点版本 101.07.23 或更高版本的 Microsoft Defender 中可用。 |

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>防病毒扫描历史记录中的最大项目数

指定在扫描历史记录中保留的最大条目数。 条目包括过去执行的所有按需扫描以及所有防病毒检测。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | scanHistoryMaximumItems |
| **数据类型** | String |
| **可能的值** | 10000 (默认值) 。 允许的值从 5000 个项目到 15000 个项目。 |
| **备注** | 适用于终结点版本 101.07.23 或更高版本的 Microsoft Defender 中可用。 |

### <a name="cloud-delivered-protection-preferences"></a>云提供的保护首选项

在 macOS 上配置 Microsoft Defender for Endpoint 的云驱动保护功能。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | cloudService |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

#### <a name="enable--disable-cloud-delivered-protection"></a>启用/禁用云保护

指定是否启用云保护设备。 若要提高服务的安全性，我们建议保持启用此功能。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | enabled |
| **数据类型** | Boolean |
| **可能的值** | true (默认值)  <br/> false |

#### <a name="diagnostic-collection-level"></a>诊断集合级别

诊断数据用于使 Microsoft Defender for Endpoint 保持安全和最新，检测、诊断和修复问题，并改进产品。 此设置确定 Microsoft Defender for Endpoint 发送给 Microsoft 的诊断级别。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | diagnosticLevel |
| **数据类型** | String |
| **可能的值** | 可选 (默认)  <br/> 必需 |

#### <a name="enable--disable-automatic-sample-submissions"></a>启用/禁用自动示例提交

确定是否将 (可能包含威胁的可疑) 发送到 Microsoft。 系统将提示你提交的文件是否可能包含个人信息。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | automaticSampleSubmission |
| **数据类型** | Boolean |
| **可能的值** | true (默认值)  <br/> false |

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>启用/禁用自动安全智能更新

确定是否自动安装安全智能更新：

|节|值|
|:---|:---|
| **Key** | automaticDefinitionUpdateEnabled |
| **数据类型** | Boolean |
| **可能的值** | true (默认值)  <br/> false |

### <a name="user-interface-preferences"></a>用户界面首选项

管理 macOS 上适用于终结点的 Microsoft Defender 用户界面的首选项。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | userInterface |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

#### <a name="show--hide-status-menu-icon"></a>显示/隐藏状态菜单图标

指定是显示还是隐藏屏幕右上角的状态菜单图标。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | hideStatusMenuIcon |
| **数据类型** | Boolean |
| **可能的值** | false（默认值） <br/> true |

#### <a name="show--hide-option-to-send-feedback"></a>显示/隐藏发送反馈的选项

指定用户是否可以通过访问 向 Microsoft 提交反馈 `Help`  >  `Send Feedback` 。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | userInitiatedFeedback |
| **数据类型** | String |
| **可能的值** | 已启用 (默认)  <br/> disabled |
| **备注** | 适用于终结点版本 101.19.61 或更高版本的 Microsoft Defender 中可用。 |

### <a name="endpoint-detection-and-response-preferences"></a>终结点检测和响应首选项

管理 macOS 上 Microsoft Defender for Endpoint (EDR) 的终结点检测和响应的首选项。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | edr |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

#### <a name="device-tags"></a>设备标记

指定标记名称及其值。 

- GROUP 标记使用指定值标记设备。 标记反映在设备页面下的门户中，可用于筛选和分组设备。

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | tags |
| **数据类型** | 字典 (嵌套首选项)  |
| **备注** | 有关字典内容的说明，请参阅以下部分。 |

##### <a name="type-of-tag"></a>标记类型

指定标记的类型

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | 注册表项 |
| **数据类型** | String |
| **可能的值** | `GROUP` |

##### <a name="value-of-tag"></a>tag 的值

指定 tag 的值

|节|值|
|:---|:---|
| **域** | `com.microsoft.wdav` |
| **Key** | 值 |
| **数据类型** | String |
| **可能的值** | 任何字符串 |

> [!IMPORTANT]  
> - 每个标记类型只能设置一个值。
> - 标记类型是唯一的，并且不应在同一配置文件中重复。

## <a name="recommended-configuration-profile"></a>建议的配置文件

若要开始，我们建议你的企业采用以下配置，以利用 Microsoft Defender for Endpoint 提供的所有保护功能。

以下配置文件 (，或者，对于 JAMF，可以上载到自定义设置配置文件中的属性列表) ：
- 启用实时保护 (RTP) 
- 指定如何处理以下威胁类型：
  - **阻止 PUA (可能不需要)** 的应用程序
  - **使用高** (率存档存档) 将审核到 Microsoft Defender 终结点日志
- 启用自动安全智能更新
- 启用云保护
- 启用自动提交示例

### <a name="property-list-for-jamf-configuration-profile"></a>JAMF 配置文件的属性列表

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enableRealTimeProtection</key>
        <true/>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
</dict>
</plist>
```

### <a name="intune-profile"></a>Intune 配置文件

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enableRealTimeProtection</key>
                    <true/>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="full-configuration-profile-example"></a>完整配置文件示例

以下模板包含本文档中所述的所有设置的条目，可用于更高级的方案，你想要在 macOS 上对 Microsoft Defender for Endpoint 进行更多控制。

### <a name="property-list-for-jamf-configuration-profile"></a>JAMF 配置文件的属性列表

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enableRealTimeProtection</key>
        <true/>
        <key>passiveMode</key>
        <false/>
        <key>exclusions</key>
        <array>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <false/>
                <key>path</key>
                <string>/var/log/system.log</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/home</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/Users/*/git</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileExtension</string>
                <key>extension</key>
                <string>pdf</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileName</string>
                <key>name</key>
                <string>cat</string>
            </dict>
        </array>
        <key>exclusionsMergePolicy</key>
        <string>merge</string>
        <key>allowedThreats</key>
        <array>
            <string>EICAR-Test-File (not a virus)</string>
        </array>
        <key>disallowedThreatActions</key>
        <array>
            <string>allow</string>
            <string>restore</string>
        </array>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
        <key>threatTypeSettingsMergePolicy</key>
        <string>merge</string>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>diagnosticLevel</key>
        <string>optional</string>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
    <key>edr</key>
    <dict>
        <key>tags</key>
        <array>
            <dict>
                <key>key</key>
                <string>GROUP</string>
                <key>value</key>
                <string>ExampleTag</string>
            </dict>
        </array>
    </dict>
    <key>userInterface</key>
    <dict>
        <key>hideStatusMenuIcon</key>
        <false/>
        <key>userInitiatedFeedback</key>
        <string>enabled</string>
    </dict>
</dict>
</plist>
```

### <a name="intune-profile"></a>Intune 配置文件

```XML
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enableRealTimeProtection</key>
                    <true/>
                    <key>passiveMode</key>
                    <false/>
                    <key>exclusions</key>
                    <array>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <false/>
                            <key>path</key>
                            <string>/var/log/system.log</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/home</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/Users/*/git</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileExtension</string>
                            <key>extension</key>
                            <string>pdf</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileName</string>
                            <key>name</key>
                            <string>cat</string>
                        </dict>
                    </array>
                    <key>exclusionsMergePolicy</key>
                    <string>merge</string>
                    <key>allowedThreats</key>
                    <array>
                        <string>EICAR-Test-File (not a virus)</string>
                    </array>
                    <key>disallowedThreatActions</key>
                    <array>
                        <string>allow</string>
                        <string>restore</string>
                    </array>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                    <key>threatTypeSettingsMergePolicy</key>
                    <string>merge</string>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>diagnosticLevel</key>
                    <string>optional</string>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
                <key>edr</key>
                <dict>
                    <key>tags</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>GROUP</string>
                            <key>value</key>
                            <string>ExampleTag</string>
                        </dict>
                    </array>
                </dict>
                <key>userInterface</key>
                <dict>
                    <key>hideStatusMenuIcon</key>
                    <false/>
                    <key>userInitiatedFeedback</key>
                    <string>enabled</string>
                </dict>
            </dict>
        </array>
```

## <a name="property-list-validation"></a>属性列表验证

属性列表必须是有效的 *.plist* 文件。 可通过执行：

```bash
plutil -lint com.microsoft.wdav.plist
```
```Output
com.microsoft.wdav.plist: OK
```

如果文件格式良好，则上述命令将输出 `OK` 并返回 的退出代码 `0` 。 否则，将显示描述该问题的错误，并且该命令将返回 的退出代码 `1` 。

## <a name="configuration-profile-deployment"></a>配置文件部署

为企业生成配置文件后，可以通过企业使用的管理控制台部署配置文件。 以下各节提供有关如何使用 JAMF 和 Intune 部署此配置文件的说明。

### <a name="jamf-deployment"></a>JAMF 部署

从 JAMF 控制台中，打开 **计算机** 配置文件，导航到你要使用的配置文件，  >  然后选择自定义设置。  使用 创建用作 `com.microsoft.wdav` 首选项域的条目并上载之前生成的 *.plist。*

>[!CAUTION]
>必须输入正确的首选项域 `com.microsoft.wdav` () ;否则，Microsoft Defender for Endpoint 无法识别首选项。

### <a name="intune-deployment"></a>Intune 部署

1. 打开 **"管理**  >  **设备配置"。** 选择 **"管理**  >  **配置文件**  >  **""创建配置文件"。**

2. 选择配置文件的名称。 将 **Platform=macOS** 更改为 **配置文件类型=自定义**。 选择"配置"。

3. 将之前生成的 .plist 另存为 `com.microsoft.wdav.xml` 。

4. 输入 `com.microsoft.wdav` 作为 **自定义配置文件名称**。

5. 打开配置文件并上载 `com.microsoft.wdav.xml` 文件。  (此文件是在步骤 3.) 

6. 选择“**确定**”。

7. 选择 **"管理**  >  **工作分配"。** 在"**包含"** 选项卡中，**选择"分配给&所有设备"。**

>[!CAUTION]
>必须输入正确的自定义配置文件名称;否则，Microsoft Defender for Endpoint 无法识别这些首选项。

## <a name="resources"></a>资源

- [配置文件首选项（Apple 开发人员文档）](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
