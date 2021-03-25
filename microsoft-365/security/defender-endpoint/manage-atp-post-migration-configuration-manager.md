---
title: 使用 Configuration Manager 管理 Microsoft Defender for Endpoint
description: 了解如何使用 Configuration Manager 管理 Microsoft Defender for Endpoint
keywords: 迁移后， 管理， 操作， 维护， 利用率， Configuration Manager， windows defender 高级威胁防护， atp， edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 09/22/2020
ms.reviewer: chventou
ms.openlocfilehash: 36599d830ac737b112df9f7c948e65829d6a7ce6
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056102"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>使用 Configuration Manager 管理 Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


我们建议使用 [Microsoft Endpoint Manager，](https://docs.microsoft.com/mem)其中包括 [Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) (Intune) 和 [Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/understand/introduction) (Configuration Manager) 来管理组织针对设备的威胁防护功能 (也称为终结点) 。 
- [详细了解终结点管理器](https://docs.microsoft.com/mem/endpoint-manager-overview)
- [使用 Configuration Manager 和 Intune 在 Windows 10 设备上共同管理 Microsoft Defender for Endpoint](manage-atp-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>使用 Configuration Manager 配置 Microsoft Defender for Endpoint

|任务  |了解详细信息的资源  |
|---------|---------|
|**安装 Configuration Manager** 控制台（如果尚未安装）<br/><br/>*如果你还没有配置管理器控制台，请使用这些资源获取位并安装它。* |[获取安装媒体](https://docs.microsoft.com/mem/configmgr/core/servers/deploy/install/get-install-media)<br/><br/>[安装 Configuration Manager 控制台](https://docs.microsoft.com/mem/configmgr/core/servers/deploy/install/install-consoles)  |
|**使用 Configuration Manager 将设备载入** 到 Microsoft Defender for Endpoint <br/><br/> *如果你的设备已 (或) 尚未载入到 Microsoft Defender for Endpoint，可以使用 Configuration Manager 完成这一操作。*   |[使用 Configuration Manager 载入到 Microsoft Defender for Endpoint](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)      |
|**管理客户端计算机和终结点** 的反恶意软件策略 (Windows 防火墙) <br/><br/>*配置终结点保护功能，包括适用于终结点的 Microsoft Defender、Exploit Protection、应用程序控制、反恶意软件、防火墙设置等。*  |[Configuration Manager：Endpoint Protection](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/endpoint-protection)       |
|**选择在组织设备上更新** 反恶意软件更新的方法 <br/><br/>*借助 Configuration Manager 中的 Endpoint Protection，可以从多种方法中选择，使反恶意软件定义在组织设备上保持最新。* |[配置 Endpoint Protection 的定义更新](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/>[使用 Configuration Manager 提供定义更新](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr) |
|**启用网络** 保护以帮助防止员工使用 Internet 上恶意内容的应用 <br/><br/>*我们建议在 [测试环境中首先](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/evaluate-network-protection) 使用审核模式进行网络保护，以查看在推出之前哪些应用将被阻止。* |[使用 Configuration Manager 打开网络保护](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)  |
|**配置受控文件夹访问权限** 以防范勒索软件 <br/><br/>*受控文件夹访问权限也称为反反somware保护。*   |[终结点保护：受控文件夹访问权限](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/>[在 Microsoft Endpoint Configuration Manage 中启用受控文件夹访问权限](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager) |

## <a name="configure-your-microsoft-defender-security-center"></a>配置 Microsoft Defender 安全中心

如果尚未配置，请配置 Microsoft **Defender** 安全中心 () 以查看警报、配置威胁防护功能以及查看有关组织整体安全状况 [https://securitycenter.windows.com](https://securitycenter.windows.com) 的详细信息。 

还可以配置最终用户是否可以在 Microsoft Defender 安全中心看到的功能以及这些功能。

- [Microsoft Defender 安全中心概述](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/use)

- [终结点保护：Microsoft Defender 安全中心](https://docs.microsoft.com/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>后续步骤

- [获取威胁和漏洞管理的概述](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [访问 Microsoft Defender 安全中心安全操作仪表板](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [使用 Intune 管理 Microsoft Defender for Endpoint](manage-atp-post-migration-intune.md)