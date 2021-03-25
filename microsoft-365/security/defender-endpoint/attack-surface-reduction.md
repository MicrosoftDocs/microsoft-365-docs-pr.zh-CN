---
title: 使用攻击面减少规则防止恶意软件感染
description: 攻击面减少规则有助于防止攻击使用应用和脚本感染带恶意软件的设备。
keywords: 攻击面减少规则， asr， hips， 主机入侵防护系统， 保护规则， 反攻击， 攻击， 感染防护， Microsoft Defender for Endpoint， Microsoft Defender ATP
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: sugamar, jcedola
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.openlocfilehash: 2bd8442dd8e119a57c490773b6e01a7c5f7adcac
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056238"
---
# <a name="use-attack-surface-reduction-rules-to-prevent-malware-infection"></a>使用攻击面减少规则防止恶意软件感染

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



## <a name="why-attack-surface-reduction-rules-are-important"></a>攻击面减少规则为什么很重要

组织的攻击面包括攻击者可能损害组织设备或网络的所有位置。 减少攻击面意味着保护组织的设备和网络，这使攻击者能够执行攻击的方法更少。 在 Microsoft Defender for Endpoint 中配置攻击面减少规则可以提供帮助！

攻击面减少规则针对某些软件行为，例如：

- 启动尝试下载或运行文件的可执行文件和脚本;
- 运行混淆的或可疑的脚本;和 
- 执行应用在正常日常工作期间通常不会启动的行为。

此类软件行为有时在合法应用程序中可见;但是，这些行为通常被视为有风险，因为它们通常被攻击者通过恶意软件滥用。 攻击面减少规则可以限制风险行为，并有助于保证组织安全。

有关配置攻击面减少规则的信息，请参阅启用 [攻击面减少规则](enable-attack-surface-reduction.md)。

## <a name="assess-rule-impact-before-deployment"></a>在部署之前评估规则影响  

可以通过在威胁和漏洞管理中打开该规则的安全建议来评估攻击面减少规则可能会 [如何影响你的网络](https://docs.microsoft.com/windows/security/threat-protection/#tvm)。 

:::image type="content" source="images/asrrecommendation.png" alt-text="攻击面减少规则的安全重新成本":::

在建议详细信息窗格中，检查用户影响以确定设备可接受在阻止模式下启用规则的新策略的百分比，而不会对工作效率产生不利影响。

## <a name="audit-mode-for-evaluation"></a>评估审核模式

使用 [审核模式](audit-windows-defender.md) 评估攻击面减少规则启用后对组织的影响。 首先在审核模式下运行所有规则，以便了解它们如何影响业务线应用程序。 许多业务线应用程序都是以有限的安全问题编写，它们执行任务的方式可能类似于恶意软件。 通过监视审核数据 [并添加](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) 必要应用程序的排除项，你可以部署攻击面减少规则，而不会降低工作效率。

## <a name="warn-mode-for-users"></a>用户警告模式

 (**新**！) 警告模式功能之前，已启用的攻击面减少规则可以设置为审核模式或阻止模式。 使用新的警告模式，只要内容被攻击面减少规则阻止，用户就会看到一个指示内容被阻止的对话框。 该对话框还允许用户选择取消阻止内容。 然后，用户可以重试其操作，操作完成。 当用户取消阻止内容时，该内容将保持取消阻止状态 24 小时，然后阻止恢复。

警告模式可帮助组织制定攻击面减少规则，而不会阻止用户访问执行其任务所需的内容。 

### <a name="requirements-for-warn-mode-to-work"></a>警告模式运行的要求

运行以下版本的 Windows 的设备支持警告模式：
- [Windows 10 版本 1809](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1809) 或更高版本
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809) 或更高版本
 
Microsoft Defender 防病毒必须在活动模式下使用实时 [保护运行](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state)。

此外，请确保安装了 [Microsoft Defender 防病毒和](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) 反恶意软件更新。
- 最低平台发布要求： `4.18.2008.9`  
- 最低引擎发布要求： `1.1.17400.5`

有关详细信息和获取更新，请参阅 [Microsoft Defender 反恶意软件平台的更新](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform)。

### <a name="cases-where-warn-mode-is-not-supported"></a>不支持警告模式的情况

以下攻击面减少规则不支持警告模式：

- [阻止 JavaScript 或 VBScript 使用](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) GUID (下载的可执行 `d3e037e1-3eb8-44c8-a917-57927947596d`) 
- [通过 WMI 事件订阅和 GUID](#block-persistence-through-wmi-event-subscription) (阻止 `e6db77e5-3df2-4cf1-b95a-636979351e5b` 持久性) 
- [使用高级防护抵御勒索软件](#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`) 

此外，运行较早版本的 Windows 的设备上不支持警告模式。 在这种情况下，配置为在警告模式下运行的攻击面减少规则将在阻止模式下运行。

## <a name="notifications-and-alerts"></a>通知和警报

每当触发攻击面减少规则时，都会在设备上显示通知。 可以使用 [公司详细信息和](customize-attack-surface-reduction.md#customize-the-notification) 联系信息自定义通知。

此外，当触发某些攻击面减少规则时，将生成警报。 

可在 Microsoft Defender 安全中心 () 和 Microsoft 365 安全中心 () 中查看生成的通知 [https://securitycenter.windows.com](https://securitycenter.windows.com) [https://security.microsoft.com](https://security.microsoft.com) 和任何警报。

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>高级搜寻和攻击面减少事件

可以使用高级搜寻来查看攻击面减少事件。 为了简化传入数据的数量，使用高级搜寻仅可查看每小时的唯一进程。 攻击面减少事件的时间是一小时内首次看到该事件。

例如，假设在下午 2：00 小时内在 10 台设备上发生攻击面减少事件。 假设第一个事件在 2：15 发生，最后一个事件在 2：45 发生。 借助高级搜寻，你将看到该事件的一个实例 (即使该事件实际发生在 10 台设备上) ，其时间戳将为下午 2：15。 

有关高级搜寻详细信息，请参阅使用高级搜寻主动 [搜寻威胁](advanced-hunting-overview.md)。

## <a name="attack-surface-reduction-features-across-windows-versions"></a>跨 Windows 版本的攻击面减少功能

你可以为运行以下任一版本的 Windows 的设备设置攻击面减少规则：
- Windows 10 专业 [版版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 或更高版本
- Windows 10 企业版 [版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 或更高版本
- Windows Server [版本 1803 (半年 ](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803) 频道) 或更高版本
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

尽管攻击面减少规则不需要 [Windows E5](https://docs.microsoft.com/windows/deployment/deploy-enterprise-licenses)许可证，但如果拥有 Windows E5，则获得高级管理功能。 这些功能仅在 Windows E5 中可用，包括 [Defender for Endpoint](microsoft-defender-advanced-threat-protection.md)中提供的监视、分析和工作流，以及 Microsoft [365](https://docs.microsoft.com/microsoft-365/security/defender/overview-security-center)安全中心中的报告和配置功能。 这些高级功能不适用于 Windows Professional 或 Windows E3 许可证;但是，如果你有这些许可证，可以使用事件查看器和 Microsoft Defender 防病毒日志查看攻击面减少规则事件。

## <a name="review-attack-surface-reduction-events-in-the-microsoft-defender-security-center"></a>查看 Microsoft Defender 安全中心的攻击面减少事件

Defender for Endpoint 提供事件和阻止的详细报告，作为警报调查方案的一部分。

可以使用高级搜寻查询 Defender 的终结点 [数据](advanced-hunting-query-language.md)。 如果你运行的是审核 [模式](audit-windows-defender.md)，可以使用高级搜寻了解攻击面减少规则可能会如何影响你的环境。

下面是一个示例查询：

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>在 Windows 事件查看器中查看攻击面减少事件

你可以查看 Windows 事件日志以查看攻击面减少规则生成的事件：

1. 下载 [评估包](https://aka.ms/mp7z2w) ，将文件 *cfa-events.xml* 到设备上易于访问的位置。
2. 在"开始"菜单中 *输入单词"事件* 查看器"以打开 Windows 事件查看器。
3. 在 **"操作"** 下，**选择"导入自定义视图..."。**
4. 选择从 *cfa-events.xml* 文件的位置创建的文件。 或者，[直接复制 XML。](event-views.md)
5. 选择“**确定**”。

您可以创建一个自定义视图，该视图筛选事件以只显示下列事件，所有这些事件均与受控文件夹访问权限相关：

|事件 ID | 说明 |
|:---|:---|
|5007 | 更改设置时的事件 |
|1121 | 在阻止模式下触发规则时的事件 |
|1122 | 在审核模式下触发规则时的事件 |

针对事件日志中的攻击面减少事件列出的"引擎版本"由 Defender for Endpoint 生成，而不是由操作系统生成。 Defender for Endpoint 与 Windows 10 集成，因此此功能适用于安装了 Windows 10 的所有设备。

## <a name="attack-surface-reduction-rules"></a>攻击面减少规则

下表和子部分介绍了 15 个攻击面减少规则中的每个规则。 攻击面减少规则按规则名称的字母顺序列出。 

如果要使用组策略或 PowerShell 配置攻击面减少规则，则需要 GUID。 另一方面，如果你使用 Microsoft Endpoint Manager 或 Microsoft Intune，则不需要 GUID。


| 规则名称 | GUID | 文件&文件夹排除项 | 支持的最低操作系统 |
|:-----|:-----:|:-----|:-----|
|[阻止 Adobe Reader 创建子进程](#block-adobe-reader-from-creating-child-processes) | `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止所有 Office 应用程序创建子进程](#block-all-office-applications-from-creating-child-processes) | `D4F940AB-401B-4EFC-AADC-AD5F3C50688A` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止从 Windows 本地安全机构子系统中窃取 (lsass.exe) ](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止来自电子邮件客户端和 Webmail 的可执行内容](#block-executable-content-from-email-client-and-webmail) | `BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止可执行文件运行，除非它们满足普遍标准、年龄或受信任的列表条件](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | `01443614-cd74-433a-b99e-2ecdc07bfc25` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止执行可能混淆的脚本](#block-execution-of-potentially-obfuscated-scripts) | `5BEB7EFE-FD9A-4556-801D-275E5FFC04CC` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止 JavaScript 或 VBScript 启动下载的可执行内容](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | `D3E037E1-3EB8-44C8-A917-57927947596D` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止 Office 应用程序创建可执行内容](#block-office-applications-from-creating-executable-content) | `3B576869-A4EC-4529-8536-B80A7769E899` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止 Office 应用程序将代码注入其他进程](#block-office-applications-from-injecting-code-into-other-processes) | `75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止 Office 通信应用程序创建子进程](#block-office-communication-application-from-creating-child-processes) |`26190899-1602-49e8-8b27-eb1d0a1ce869` |支持 |[Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高  |
|[通过 WMI 事件订阅阻止持久性](#block-persistence-through-wmi-event-subscription) | `e6db77e5-3df2-4cf1-b95a-636979351e5b` | 不支持 | [Windows 10 版本 1903 (](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903) 版本 18362) 或更高 |
|[阻止源自 PSExec 和 WMI 命令的进程创建](#block-process-creations-originating-from-psexec-and-wmi-commands) | `d1e49aac-8f56-4280-b9ba-993a6d77406c` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止从 USB 运行的不受信任的和未签名的进程](#block-untrusted-and-unsigned-processes-that-run-from-usb) | `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[阻止从 Office 宏调用 Win32 API](#block-win32-api-calls-from-office-macros) | `92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |
|[使用高级防护抵御勒索软件](#use-advanced-protection-against-ransomware) | `c1db55ab-c21a-4637-bb3f-a12568109d35` | 支持 | [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) (RS3，内部版本 16299) 或更高 |

### <a name="block-adobe-reader-from-creating-child-processes"></a>阻止 Adobe Reader 创建子进程

此规则通过阻止 Adobe Reader 创建进程来阻止攻击。

通过社交工程或攻击，恶意软件可以下载和启动有效负载，并退出 Adobe Reader。 通过阻止 Adobe Reader 生成子进程，尝试将其用作矢量的恶意软件可防止传播。

此规则是在： 
- [Windows 10 版本 1809](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1809)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

Intune 名称： `Process creation from Adobe Reader (beta)`

Configuration Manager 名称：尚不可用

GUID：`7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

### <a name="block-all-office-applications-from-creating-child-processes"></a>阻止所有 Office 应用程序创建子进程

此规则阻止 Office 应用创建子进程。 Office 应用程序包括 Word、Excel、PowerPoint、OneNote 和 Access。

创建恶意子进程是常见的恶意软件策略。 滥用 Office 作为矢量的恶意软件通常会运行 VBA 宏并攻击代码以下载并尝试运行更多有效负载。 但是，某些合法的业务线应用程序也可能出于恶意目的生成子进程，例如生成命令提示符或使用 PowerShell 配置注册表设置。

此规则是在： 
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Office apps launching child processes`

Configuration Manager 名称： `Block Office application from creating child processes`

GUID：`D4F940AB-401B-4EFC-AADC-AD5F3C50688A`

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>阻止从 Windows 本地安全机构子系统窃取凭据

此规则通过锁定 LSASS 服务中的本地安全机构子系统服务 (凭据) 。

LSASS 对在 Windows 计算机上登录的用户进行身份验证。 Windows 10 中的 Microsoft Defender Credential Guard 通常会阻止尝试从 LSASS 提取凭据。 但是，某些组织无法在所有计算机上启用 Credential Guard，因为自定义智能卡驱动程序或其他加载到本地安全机构 (LSA) 的程序的兼容性问题。 在这些情况下，攻击者可以使用 Mimikatz 等黑客工具从 LSASS 中清除明文密码和 NTLM 哈希。

> [!NOTE]
> 在某些应用中，该代码枚举所有正在运行的进程，并尝试以详尽的权限打开它们。 此规则拒绝应用的进程打开操作，将详细信息记录到安全事件日志中。 此规则会产生大量噪音。 如果你的应用仅枚举 LSASS，但在功能方面没有实际影响，则无需将其添加到排除列表。 此事件日志条目本身不一定表示恶意威胁。

此规则是在：
- [Windows 10 版本 1803](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Flag credential stealing from the Windows local security authority subsystem`

Configuration Manager 名称： `Block credential stealing from the Windows local security authority subsystem`

GUID：`9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

### <a name="block-executable-content-from-email-client-and-webmail"></a>阻止来自电子邮件客户端和 Webmail 的可执行内容

此规则阻止以下文件类型从 Microsoft Outlook 应用程序内打开的电子邮件启动，Outlook.com 其他热门 Web 邮件提供程序启动：

- 可执行文件 (.exe、.dll 或 .scr) 
- 脚本文件 (如 PowerShell .ps、Visual Basic .vbs 或 JavaScript .js) 

此规则是在： 
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Microsoft Endpoint Manager CB 1710](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager 名称： `Block executable content from email client and webmail`

GUID：`BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550`

> [!NOTE]
> 规则 **"阻止来自电子邮件客户端和 Webmail** 的可执行内容"具有以下替代说明，具体取决于你使用的应用程序：
> - Intune (Configuration Profiles) ： Execution of executable content (exe， dll， ps， js， vbs， etc.) dropped from email (webmail/mail client)  (no exceptions) .
> - 终结点管理器：阻止从电子邮件和 Webmail 客户端下载可执行内容。
> - 组策略：阻止来自电子邮件客户端和 Webmail 的可执行内容。

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>阻止可执行文件运行，除非它们满足普遍标准、年龄或受信任的列表条件

此规则阻止启动以下文件类型，除非它们符合普遍或年龄条件，或者它们位于受信任的列表或排除列表中：

- 可执行文件 (.exe、.dll 或 .scr) 

启动不受信任的或未知的可执行文件可能会存在风险，因为最初可能不明确这些文件是否恶意。

> [!IMPORTANT]
> 必须 [启用云保护才能](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) 使用此规则。 <br/><br/> 规则 **阻止可执行文件运行** ，除非它们符合普遍标准、年龄或受信任列表条件（具有 GUID）归 Microsoft 所有，且未由管理员 `01443614-cd74-433a-b99e-2ecdc07bfc25` 指定。 此规则使用云提供的保护定期更新其受信任的列表。
>
>可以使用文件夹路径或完全限定的资源 (指定单个文件或文件夹) 但无法指定适用于哪些规则或排除项。

此规则是在： 
- [Windows 10 版本 1803](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Executables that don't meet a prevalence, age, or trusted list criteria`

Configuration Manager 名称： `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID：`01443614-cd74-433a-b99e-2ecdc07bfc25`

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>阻止执行可能混淆的脚本

此规则在混淆的脚本中检测可疑属性。

脚本模糊处理是恶意软件作者和合法应用程序都用于隐藏知识产权或缩短脚本加载次数的常见技术。 恶意软件作者还使用模糊处理使恶意代码更难阅读，这可防止人员和安全软件进行严格的审查。

此规则是在：
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Obfuscated js/vbs/ps/macro code`

Configuration Manager 名称： `Block execution of potentially obfuscated scripts`

GUID：`5BEB7EFE-FD9A-4556-801D-275E5FFC04CC`

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>阻止 JavaScript 或 VBScript 启动下载的可执行内容

此规则阻止脚本启动潜在恶意下载的内容。 用 JavaScript 或 VBScript 编写的恶意软件通常充当从 Internet 提取和启动其他恶意软件的下载程序。

虽然不常见，但业务线应用程序有时会使用脚本下载和启动安装程序。

此规则是在：  
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `js/vbs executing payload downloaded from Internet (no exceptions)`

Configuration Manager 名称： `Block JavaScript or VBScript from launching downloaded executable content`

GUID：`D3E037E1-3EB8-44C8-A917-57927947596D`

### <a name="block-office-applications-from-creating-executable-content"></a>阻止 Office 应用程序创建可执行内容

此规则阻止将恶意代码写入磁盘，从而阻止 Office 应用（包括 Word、Excel 和 PowerPoint）创建潜在恶意可执行内容。

滥用 Office 作为矢量的恶意软件可能会尝试从 Office 中中断，将恶意组件保存到磁盘。 这些恶意组件在计算机重新启动后将一直保留于系统。 因此，此规则可防御常见的持久性技术。

此规则是在： 
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [System Center Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/manage/updates) (SCCM) CB 1710 (SCCM 现在是 Microsoft Endpoint Configuration Manager) 

Intune 名称： `Office apps/macros creating executable content`

SCCM 名称： `Block Office applications from creating executable content`

GUID：`3B576869-A4EC-4529-8536-B80A7769E899`

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>阻止 Office 应用程序将代码注入其他进程

此规则阻止从 Office 应用向其他进程注入代码的尝试。

攻击者可能会尝试使用 Office 应用通过代码注入将恶意代码迁移到其他进程中，因此代码可以伪装成一个干净流程。

使用代码注入没有已知的合法业务用途。

此规则适用于 Word、Excel 和 PowerPoint。

此规则是在： 
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Office apps injecting code into other processes (no exceptions)`

Configuration Manager 名称： `Block Office applications from injecting code into other processes`

GUID：`75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84`

### <a name="block-office-communication-application-from-creating-child-processes"></a>阻止 Office 通信应用程序创建子进程

此规则阻止 Outlook 创建子进程，同时仍允许合法的 Outlook 功能。

此规则可防止社会工程攻击，并防止利用代码滥用 Outlook 中的漏洞。 它还可抵御 [Outlook](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) 规则和表单攻击，攻击者可以在用户凭据遭到泄露时使用这些漏洞。

> [!NOTE]
> 此规则仅适用于 Outlook 和 Outlook.com。

此规则是在： 
- [Windows 10 版本 1809](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1809)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

Intune 名称： `Process creation from Office communication products (beta)`

Configuration Manager 名称：不可用

GUID：`26190899-1602-49e8-8b27-eb1d0a1ce869`

### <a name="block-persistence-through-wmi-event-subscription"></a>通过 WMI 事件订阅阻止持久性

此规则可防止恶意软件滥用 WMI 在设备上获得持久性。

> [!IMPORTANT]
> 文件和文件夹排除项不适用于此攻击面减少规则。

无文件威胁采用各种策略来保持隐藏，以避免在文件系统中可见，并获得定期执行控制。 某些威胁可能会滥用 WMI 存储库和事件模型来保持隐藏状态。

此规则是在： 
- [Windows 10 版本 1903](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903)
- [Windows Server 1903](https://docs.microsoft.com/windows-server/get-started-19/whats-new-in-windows-server-1903-1909)

Intune 名称：不可用

Configuration Manager 名称：不可用

GUID：`e6db77e5-3df2-4cf1-b95a-636979351e5b`

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>阻止源自 PSExec 和 WMI 命令的进程创建

此规则阻止通过 [PsExec](https://docs.microsoft.com/sysinternals/downloads/psexec) 和 [WMI 创建](https://docs.microsoft.com/windows/win32/wmisdk/about-wmi) 的进程运行。 PsExec 和 WMI 都可以远程执行代码，因此存在恶意软件滥用此功能以用于命令和控制目的，或在整个组织的网络中传播感染的风险。

> [!WARNING]
> 仅在使用 [Intune](https://docs.microsoft.com/intune) 或其他 MDM 解决方案管理设备时使用此规则。 此规则与通过 Microsoft [Endpoint Configuration Manager](https://docs.microsoft.com/configmgr) 管理不兼容，因为此规则会阻止 Configuration Manager 客户端用于正常运行的 WMI 命令。

此规则是在： 
- [Windows 10 版本 1803](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

Intune 名称： `Process creation from PSExec and WMI commands`

Configuration Manager 名称：不适用

GUID：`d1e49aac-8f56-4280-b9ba-993a6d77406c`

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>阻止从 USB 运行的不受信任的和未签名的进程

通过此规则，管理员可以阻止未签名或不受信任的可执行文件从 USB 可移动驱动器（包括 SD 卡）运行。 阻止的文件类型包括可执行 (文件，如 .exe、.dll 或 .scr) 

此规则是在： 
- [Windows 10 版本 1803](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Untrusted and unsigned processes that run from USB`

Configuration Manager 名称： `Block untrusted and unsigned processes that run from USB`

GUID：`b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

### <a name="block-win32-api-calls-from-office-macros"></a>阻止从 Office 宏调用 Win32 API

此规则阻止 VBA 宏调用 Win32 API。

Office VBA 支持 Win32 API 调用。 恶意软件可能会滥用此功能，例如调用 [Win32 API 以启动恶意 shellcode，](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) 而无需将任何内容直接写入磁盘。 大多数组织不依赖于在日常运行中调用 Win32 API 的功能，即使它们以其他方式使用宏。

此规则是在：
- [Windows 10 版本 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Win32 imports from Office macro code`

Configuration Manager 名称： `Block Win32 API calls from Office macros`

GUID：`92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B`

### <a name="use-advanced-protection-against-ransomware"></a>使用高级防护抵御勒索软件

此规则提供针对勒索软件的额外保护层。 它会扫描进入系统的可执行文件，以确定它们是否可信。 如果文件与勒索软件非常类似，此规则会阻止它们运行，除非它们位于受信任的列表或排除列表中。

> [!NOTE]
> 必须 [启用云保护才能](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) 使用此规则。

此规则是在： 
- [Windows 10 版本 1803](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server 版本 1809](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](https://docs.microsoft.com/configmgr/core/servers/manage/updates)

Intune 名称： `Advanced ransomware protection`

Configuration Manager 名称： `Use advanced protection against ransomware`

GUID：`c1db55ab-c21a-4637-bb3f-a12568109d35`

## <a name="see-also"></a>另请参阅

- [攻击面减少常见问题解答](attack-surface-reduction-faq.md)
- [启用攻击面减少规则](enable-attack-surface-reduction.md)
- [评估攻击面减少规则](evaluate-attack-surface-reduction.md)
- [Microsoft Defender 防病毒与其他防病毒/反恶意软件解决方案的兼容性](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)