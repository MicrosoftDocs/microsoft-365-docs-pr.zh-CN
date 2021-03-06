---
title: 解决 Microsoft Defender for Endpoint 实时响应问题
description: 解决在 Microsoft Defender for Endpoint 中使用实时响应时可能出现的问题
keywords: 实时响应， 实时， 响应， 锁定， 文件
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 99a52188dd5f6eca2f8368aa3c114d0bfb950b10
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2021
ms.locfileid: "52844150"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>解决 Microsoft Defender for Endpoint 实时响应问题

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 

此页面提供解决实时响应问题的详细步骤。

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>在实时响应会话期间无法访问文件
如果在实时响应会话期间尝试采取操作时，您遇到一条错误消息，指出无法访问该文件，您需要使用以下步骤来解决此问题。

1. 复制以下脚本代码段并将其另存为 PS1 文件：

    ```
    $copied_file_path=$args[0] 
    $action=Copy-Item $copied_file_path -Destination $env:TEMP -PassThru -ErrorAction silentlyContinue
        
    if ($action){
         Write-Host "You copied the file specified in $copied_file_path to $env:TEMP Succesfully"
    }
    
    else{
        Write-Output "Error occoured while trying to copy a file, details:"
        Write-Output  $error[0].exception.message
 
    }
    ```


2. 将脚本添加到实时响应库。
3. 使用一个参数运行脚本：要复制的文件的文件路径。
4. 导航到 TEMP 文件夹。
5. 对复制的文件运行要执行的操作。

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>初始连接期间实时响应会话慢或延迟
实时响应利用 Defender for Endpoint 传感器注册和 WNS 服务在 Windows。 如果实时响应的连接问题，请确认以下详细信息：
1. `notify.windows.com` 不会在你的环境中被阻止。 有关详细信息，请参阅配置 [设备代理和 Internet 连接设置](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)。
2. 未 (Windows WpnService) 推送通知系统服务。

请参阅以下文章，以完全了解 WpnService 服务行为和要求：
- [Windows推送通知服务 (WNS) 概述](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [Enterprise支持 WNS 流量的防火墙和代理配置](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [Microsoft 推送通知服务 (MPNS) 公共 IP 范围](https://www.microsoft.com/en-us/download/details.aspx?id=44535)

