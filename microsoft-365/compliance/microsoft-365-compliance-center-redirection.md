---
title: 将用户从 Office 365 安全与合规中心重定向到Microsoft 365 合规中心
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
localization_priority: Normal
description: 了解如何自动Office 365安全与合规中心用户重定向到Microsoft 365 合规中心。
ms.collection: M365-security-compliance
ms.openlocfilehash: 62fc302f9f065ac7bb0475a6e72dc240a56a1fe1
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339402"
---
# <a name="redirect-users-from-the-office-365-security-and-compliance-center-to-the-microsoft-365-compliance-center"></a>将用户从 Office 365 安全与合规中心重定向到Microsoft 365 合规中心

本文介绍了自动重定向如何适用于从安全与合规中心Office 365合规性解决方案 (protection.office.com) 到Microsoft 365 合规中心 (compliance.microsoft.com) 。

## <a name="what-to-expect"></a>预期结果

默认情况下，在安全与合规策略中访问以下合规性相关解决方案的所有用户Office 365自动 (protection.office.com) ：

- 数据丢失防护 (DLP)
- 分类
- 信息治理
- 记录管理
- 通信合规性 (以前是"监督") 

用户将自动路由到 Microsoft 365 合规中心 (compliance.microsoft.com) 中的相同合规性解决方案。

> [!NOTE]
> 对于安全与合规Office 365中包含的其他合规性解决方案，用户将继续在 Microsoft 365 合规中心 或 Office 365 安全与合规中心管理这些解决方案。 这些合规性解决方案的自动重定向即将推出。

此功能和相关控件不支持自动重定向 Microsoft Defender for Office 365。 若要启用安全功能重定向，请参阅将帐户从[Microsoft Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection) for Office 365重定向到 Microsoft 365 安全中心了解详细信息。

## <a name="can-i-go-back-to-using-the-former-portal"></a>我能否返回到使用以前的门户？

如果无法通过 Microsoft 365 合规中心 门户完成某些操作或无法完成某些操作，可以暂时禁用所有用户的自动重定向。

> [!IMPORTANT]
> The Microsoft 365 合规中心 is the replacement management portal for compliance solutions currently managed in the Office 365 Security and Compliance center. 所有Microsoft 365合规性解决方案将仅在 Microsoft 365 合规中心 中进行管理。 禁用重定向到Microsoft 365 合规中心应该是一个短期解决方案。

若要切换回Office 365安全与合规 (protection.microsoft.com) ，请完成以下步骤：

1. 以全局管理员[Microsoft 365 合规中心](https://compliance.microsoft.com)Azure Active directory 中具有合规性管理员权限的任何帐户登录帐户。
2. 导航到 **设置**  >  **合规中心重定向。**
3. 将"自动重定向"设置切换为 **"关"。**
4. 选择 **"关闭** "，在系统提示时共享反馈。

禁用后，用户将不再被路由到 compliance.microsoft.com 他们将被定向到 Office 365 安全与合规中心 (protection.microsoft.com) 。 全局管理员或合规性管理员可以随时再次启用此设置。

## <a name="related-information"></a>相关信息

- [Microsoft 365 合规中心概述](/microsoft-365/compliance/microsoft-365-compliance-center)
