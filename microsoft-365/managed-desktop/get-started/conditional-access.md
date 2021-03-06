---
title: 注册后调整设置
description: 如何排除某些 Microsoft 帐户
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 760fcb94ec6d84a55fe4b8c3cb3540ae29994ae3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50918438"
---
# <a name="adjust-settings-after-enrollment"></a>注册后调整设置

在 Microsoft 托管桌面中完成注册后，可能需要调整一些管理设置。 若要检查并根据需要进行调整，请按照以下步骤操作：

1. 查看下一节中介绍的 Microsoft Intune 和 Azure Active Directory 设置。
2. 如果任何项目适用于您的环境，请进行所述的调整。
3. 如果要仔细检查所有设置是否正确，可以重新运行准备情况评估工具，以确保与 Microsoft[](https://aka.ms/mmdart)托管桌面没有任何冲突。

> [!NOTE]
> 由于操作将在几个月后继续，如果在 Microsoft Intune、Azure Active Directory 或 Microsoft 365 中注册影响 Microsoft 托管桌面的策略后进行更改，Microsoft 托管桌面可能会停止正常运行。 若要避免服务问题，请在更改就绪情况评估工具发现的问题[](../get-ready/readiness-assessment-fix.md)前检查修复工具发现的问题中描述的特定设置，然后再更改它中列出的策略。 您还可以随时重新运行准备情况评估工具。


## <a name="microsoft-intune-settings"></a>Microsoft Intune 设置

- Autopilot 部署配置文件：如果你使用任意 Autopilot 策略，请更新每个策略以排除 **现代工作区设备 -所有** Azure AD 组。 若要更新它们，请在"分配"下的"排除的组"部分中，选择在 Microsoft 托管桌面注册期间创建的"现代工作区设备 **-** 所有 Azure AD"组。 Microsoft 托管桌面还将创建 Autopilot 配置文件，其名称将为"新式工作区 (**新式工作区配置文件**) 。 更新你自己的 Autopilot 配置文件时，请确保不要从Microsoft 托管桌面创建的现代 **工作区 Autopilot** 配置文件中排除现代工作区设备 **-** 所有 Azure AD 组。

- 条件访问策略：如果你在 Microsoft 托管桌面注册后创建与 Azure AD、Microsoft Intune 或 Microsoft Defender for Endpoint 相关的任何新条件访问策略，则从它们中排除现代 **工作区服务帐户** Azure AD 组。 有关步骤，请参阅条件 [访问：用户和组](/azure/active-directory/conditional-access/concept-conditional-access-users-groups)。 Microsoft 托管桌面维护单独的条件访问策略来限制访问这些帐户。 若要查看 Microsoft 托管桌面条件访问策略 (**现代工作区 –** 安全工作站) ，请转到 Microsoft Endpoint Manager 并导航到 Endpoint **Security****中的条件** 访问。 不要修改 Microsoft 托管桌面创建的任何 Azure AD 条件访问策略，这些策略的名称为"现代工作区"。

- 多重身份验证：如果你在 Microsoft 托管桌面注册后在与 Azure AD、Intune 或 Microsoft Defender for Endpoint 相关的条件访问策略中创建了任何新的多重身份验证要求，则从它们中排除现代 **工作区** 服务帐户 Azure AD 组。 有关步骤，请参阅条件 [访问：用户和组](/azure/active-directory/conditional-access/concept-conditional-access-users-groups)。 Microsoft 托管桌面维护单独的条件访问策略，以限制对此组的成员的访问。 若要查看 Microsoft 托管桌面条件访问策略 (**现代工作区 -**) ，请转到 Microsoft Endpoint Manager 并 **导航到** Endpoint **Security** 中的条件访问。 

- Windows 10 更新圈：对于你创建的任何 Windows 10 更新圈策略，从每个策略中排除 **现代工作区设备 -所有** Azure AD 组。 有关步骤，请参阅 [创建和分配更新圈](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings)。 Microsoft 托管桌面还将创建一些更新圈策略，其中所有策略的名称为 (例如现代工作区更新策略 **[广泛]、** 现代工作场所更新策略 **[快速]、** 现代工作区更新策略 **[第一]** 和现代工作区更新策略 **[测试]**) 。 更新自己的策略时，请确保不要将现代工作区设备 **-** 所有 Azure AD 组从 Microsoft 托管桌面创建的组排除。


## <a name="azure-active-directory-settings"></a>Azure Active Directory 设置

自助服务密码重置：如果使用所有用户的自助密码重置，请调整分配以排除 Microsoft 托管桌面服务帐户。 若要调整此分配，请为除 *Microsoft* 托管桌面服务帐户以外的所有用户创建 Azure AD 动态组，然后将该组用于分配，而不是"所有用户"。

为了帮助您查找和排除服务帐户，下面是可以使用的动态查询的示例：

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

在此查询中，将 @TENANT替换为租户域名。



## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft 托管桌面入门步骤

1. [在管理门户中添加和验证管理员联系人](add-admin-contacts.md)
2. 在注册后调整 (本文) 
3. [分配许可证](assign-licenses.md)
4. [部署 Intune 公司门户](company-portal.md)
5. [启用企业状态漫游](enterprise-state-roaming.md)
6. [设置设备](set-up-devices.md)
7. [让用户做好使用设备的准备](get-started-devices.md)
8. [部署应用](deploy-apps.md)