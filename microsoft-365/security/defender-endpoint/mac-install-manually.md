---
title: 适用于 macOS 的 Microsoft Defender ATP 的手动部署
description: 从命令行手动安装适用于 macOS 的 Microsoft Defender ATP。
keywords: microsoft， defender， atp， mac， 安装， 部署， 卸载， intune， jamf， macos， catalina， mojave， high sierra
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
ms.openlocfilehash: 382abd78ffa5e30c79804f9eaed211dffba7589c
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51054965"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-for-macos"></a>适用于 macOS 的 Microsoft Defender 终结点的手动部署

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

本主题介绍如何手动部署适用于 macOS 的 Microsoft Defender for Endpoint。 要成功部署，需要完成以下所有步骤：
- [下载安装和载入程序包](#download-installation-and-onboarding-packages)
- [macOS (10.15 及早期版本的应用程序安装) ](#application-installation-macos-1015-and-older-versions)
- [macOS 11 (更高版本的应用程序安装) ](#application-installation-macos-11-and-newer-versions)
- [客户端配置](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>先决条件和系统要求

在开始使用之前，请参阅 [主 Microsoft Defender for Endpoint for macOS](microsoft-defender-endpoint-mac.md) 页面，了解当前软件版本的先决条件和系统要求。

## <a name="download-installation-and-onboarding-packages"></a>下载安装和载入程序包

从 Microsoft Defender 安全中心下载安装和载入程序包：

1. 在 Microsoft Defender 安全中心中，转到"设备>**设置>载入"。**
2. 在页面的第 1 部分中，将操作系统设置为 **macOS，** 将 Deployment 方法设置为 **本地脚本**。
3. 在页面的第 2 部分中，选择 **下载安装程序包**。 将其另存为 wdav.pkg 到本地目录。
4. 在页面的第 2 部分中，选择 **下载载入程序包**。 将其另存WindowsDefenderATPOnboardingPackage.zip同一目录。

    ![Microsoft Defender 安全中心屏幕截图](images/atp-portal-onboarding-page.png)

5. 在命令提示符下，验证您是否具有这两个文件。
    
## <a name="application-installation-macos-1015-and-older-versions"></a>macOS (10.15 及早期版本的应用程序安装) 

若要完成此过程，你必须在设备上拥有管理员权限。

1. 导航到 Finder 中下载的 wdav.pkg 并打开它。

    ![应用安装屏幕截图1](/windows/security/threat-protection/microsoft-defender-antivirus/images/mdatp-28-appinstall)

2. 选择 **"继续**"，同意许可条款，在系统提示时输入密码。

    ![应用安装屏幕截图2](/windows/security/threat-protection/microsoft-defender-antivirus/images/mdatp-29-appinstalllogin)

   > [!IMPORTANT]
   > 系统将提示你允许从 Microsoft 安装驱动程序， ("系统扩展被阻止"或"安装已保留"或两者同时安装。 必须允许安装驱动程序。

   ![应用安装屏幕截图3](/windows/security/threat-protection/microsoft-defender-antivirus/images/mdatp-30-systemextension)

3. 选择 **"打开安全首选项"** 或"打开系统首选项 **>安全&隐私"。** 选择 **"允许"：**

    ![安全和隐私窗口屏幕截图](/windows/security/threat-protection/microsoft-defender-antivirus/images/mdatp-31-securityprivacysettings)

   继续安装。

   > [!CAUTION]
   > 如果未选择"允许 **"，** 则安装将在 5 分钟后继续。 Microsoft Defender for Endpoint 将加载，但某些功能（如实时保护）将被禁用。 请参阅 [内核扩展问题](mac-support-kext.md) 疑难解答，了解如何解决此问题。

> [!NOTE]
> macOS 可能会请求在首次安装 Microsoft Defender for Endpoint 时重新启动设备。 在重新启动设备之前，实时保护将不可用。

## <a name="application-installation-macos-11-and-newer-versions"></a>macOS 11 (更高版本的应用程序安装) 

若要完成此过程，你必须在设备上拥有管理员权限。

1. 导航到 Finder 中下载的 wdav.pkg 并打开它。

    ![应用安装屏幕截图4](images/big-sur-install-1.png)

2. 选择 **"继续**"，同意许可条款，在系统提示时输入密码。

3. 在安装过程结束时，你将被提升为批准产品使用的系统扩展。 选择 **"打开安全首选项"。**

    ![系统扩展审批](images/big-sur-install-2.png)

4. 从"**安全&隐私"** 窗口中，选择"允许 **"。**

    ![系统扩展安全首选项1](images/big-sur-install-3.png)

5. 对随 Microsoft Defender for Endpoint for Mac 分发的所有系统扩展重复步骤 3 & 4。

6. 作为终结点检测和响应功能的一部分，Microsoft Defender for Mac 终结点会检查套接字流量，将此信息报告给 Microsoft Defender 安全中心门户。 当系统提示授予 Microsoft Defender 终结点权限以筛选网络流量时，请选择"允许 **"。**

    ![系统扩展安全首选项2](images/big-sur-install-4.png)

7. 打开 **"系统** 首选项&隐私"并导航到"隐私"选项卡。授予 Microsoft Defender ATP 和 Microsoft Defender ATP 终结点安全扩展的"完全磁盘  >  **访问权限"。**   

    ![完全磁盘访问](images/big-sur-install-5.png)

## <a name="client-configuration"></a>客户端配置

1. 将 wdav.pkg 和 MicrosoftDefenderATPOnboardingMacOs.py 复制到你部署适用于 macOS 的终结点的 Microsoft Defender 的设备。

    客户端设备不与 orgId 关联。 请注意 *，orgId* 属性为空。

    ```bash
    mdatp health --field org_id
    ```

2. 运行 Python 脚本以安装配置文件：

    ```bash
    /usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py
    ```

3. 验证设备现在是否与组织关联，并报告有效的 *orgId：*

    ```bash
    mdatp health --field org_id
    ```

安装后，你将在右上角的 macOS 状态栏中看到 Microsoft Defender 图标。

   ![状态栏中的 Microsoft Defender 图标屏幕截图](/windows/security/threat-protection/microsoft-defender-antivirus/images/mdatp-icon-bar)
   

## <a name="how-to-allow-full-disk-access"></a>如何：允许完全磁盘访问

> [!CAUTION]
> macOS 10.15 (Catalina) 新增了安全和隐私增强功能。 从此版本开始，默认情况下，应用程序无法访问磁盘上的某些位置 (如文档、下载、桌面等) 未经明确同意。 如果没有此同意，Microsoft Defender for Endpoint 将无法完全保护你的设备。

若要授予同意，请打开系统首选项 -> 安全&隐私 ->隐私 ->完全磁盘访问。 单击锁定图标以在 (对话框底部进行更改) 。 选择"适用于终结点的 Microsoft Defender"。

## <a name="logging-installation-issues"></a>记录安装问题

请参阅 [记录](mac-resources.md#logging-installation-issues) 安装问题，详细了解如何在发生错误时查找安装程序创建的自动生成的日志。

## <a name="uninstallation"></a>卸载

请参阅 [卸载](mac-resources.md#uninstalling) ，了解有关如何从客户端设备中删除适用于 macOS 的 Microsoft Defender for Endpoint 的详细信息。