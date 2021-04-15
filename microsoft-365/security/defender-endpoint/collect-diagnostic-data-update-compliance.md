---
title: 收集 Microsoft Defender 防病毒更新合规性Windows Defender诊断数据
description: 使用工具收集数据，解决使用 Microsoft Defender 防病毒评估加载项时的更新合规性问题
keywords: 疑难解答， 错误， 修复， 更新合规性， oms， 监视器， 报告， Microsoft Defender AV
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
ms.openlocfilehash: 3975a18c2986ac7766664194a6d4b80ee1a503b1
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "51689958"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-av-assessment"></a>收集 Microsoft Defender AV 评估的更新合规性诊断数据

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

本文介绍如何收集诊断数据，Microsoft 支持和工程团队可以使用这些数据来帮助解决在使用更新合规性外接程序中的 Microsoft Defender AV 评估部分时可能遇到的问题。

在尝试此过程之前，请确保你已阅读 Microsoft [Defender 防病毒](troubleshoot-reporting.md)报告疑难解答，满足所有先决条件，并采取了任何其他建议的疑难解答步骤。

在至少两台未在更新合规性中报告或显示的设备上，通过执行以下步骤获取 .cab 诊断文件：

1. 打开命令提示符的管理员级别版本，如下所示：
        
    a. 打开" **开始"** 菜单。

    b. 类型 **cmd**。 右键单击命令 **提示符，** 然后单击 **以管理员角色运行**。

    c. 输入管理员凭据或批准提示。
        
2. 导航到Windows Defender目录。 默认情况下，此操作为 `C:\Program Files\Windows Defender`。

3. 键入以下命令，然后按 **Enter**
        
    ```Dos
    mpcmdrun -getfiles
    ```
    
4. 将生成包含各种诊断日志的 .cab 文件。 将在命令提示符的输出中指定文件的位置。 默认情况下，位置为 `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab` 。

5. 将这些 .cab 文件复制到 Microsoft 支持人员可以访问的位置。 例如，可以与我们共享受密码保护的 OneDrive 文件夹。

6. 使用更新一致性支持 <a href="mailto:ucsupport@microsoft.com?subject=WDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">电子邮件模板发送电子邮件</a>，并填写包含以下信息的模板：
  
    ```
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:
    
    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>另请参阅

- [Microsoft Windows Defender防病毒报告疑难解答](troubleshoot-reporting.md)