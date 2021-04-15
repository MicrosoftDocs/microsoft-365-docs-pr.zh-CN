---
title: 了解设备配置文件
description: 管理员可以分配给设备的各种配置文件
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: e6b0c96d4e145a2e5df7c7555e262aefe891e483
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "51689992"
---
# <a name="device-profiles"></a>设备配置文件

你可以为设备分配不同的 ("设备配置文件) 配置，每个配置都针对特定类型的用户的需求进行了优化。 有三个设备配置文件可用：

- 标准
- 敏感数据
- Power user

你可以将设备配置文件视为设备配置选项层次结构的一部分。

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="显示为棱锥的设备配置。说明如下":::

从根本上说，每个 Microsoft 托管桌面设备都有一个基础，其中包括标准安全基线、合规性策略、Windows 更新设置和组。 若要使用 Microsoft 托管桌面，每个设备必须包含所有这些元素，管理员如果不请求 Microsoft 托管桌面，则无法更改这些元素。

设备配置文件显示在下一个较高级别。 每个 Microsoft 托管桌面设备必须分配一 (一个) 配置文件。 管理员可以选择已分配设备的配置文件。

更高级别的是其他 [自定义](customizing.md)项。 每台设备可以具有一个或多个自定义 (或) 自定义。 它们可以修改设备配置文件中的 (层或基础配置) ，或者作为一个全新请求，在标准配置的基础上分层。

最上面是你自己的修改，如网络详细信息或应用程序。 设备可以有任意数目的这些修改，但 Microsoft 托管桌面不会管理或阻止这些修改。


## <a name="device-profile-details"></a>设备配置文件详细信息

下表总结了设备配置文件配置的每个设置的设置及其默认值。  (使用 Microsoft Endpoint Manager.OMA-URIs中的自定义配置文件在后台使用自定义配置文件配置这些设置) 

| 功能 | 敏感数据 | Power User | 标准 |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|------------------------|-----------------------|
| **阻止外部存储**                                                                                                                               | 是                       | 是                   | 否                   |
| **[云块级别](https://docs.microsoft.com/graph/api/resources/intune-deviceconfig-defendercloudblockleveltype)** | 高                      | 高                  | 高                 |
| **禁用 Microsoft 帐户**                                                                                                                           | 是                       | 是                   | 否                   |
| **禁用个人 OneDrive**                                                                                                                            | 是                       | 是                   | 否                   |
| **切换到安全桌面进行提升**                                                                                                               | 否                        | 是                   | 否                   |
| **适用于终结点设备标记的 Microsoft Defender**                                                                                                           | M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
| **设备上管理员？**                                                                                                                                 | 否                        | 是                   | 否                   |
| **Autopilot 配置文件**                                                                                                                                     | MMD Standard               | MMD Power User         | MMD Standard          |
| **AppLocker**                                                                                                                                            | 是                       | 否                    | 否                   |
| **阻止公共存储**                                                                                                                                   | 是                       | 是                   | 否                   |

每个设备配置文件也涉及以下项：

- 动态成员身份 Azure Active Directory (AAD) 设备组
- 静态成员资格 AAD 设备组
- Microsoft Endpoint Manager 配置文件

> [!IMPORTANT]
> 不要直接修改这些组的成员身份。 使用重新分配配置文件 [中所述的接口](../working-with-managed-desktop/change-device-profile.md)。

## <a name="limitations"></a>限制

你可以像对任何其他策略一样请求设备配置文件及其详细信息的例外。 请记住，你的 Azure Active Directory 组织只能有一个设备配置文件 ("租户") 。 例如，你无法请求敏感数据设备配置文件仅对部分用户禁用 AppLocker。 所有具有敏感数据配置文件的设备都必须具有相同的配置。

每台设备只能有一个配置文件。 如果给定设备由多个用户使用，则该设备上的所有用户都将具有相同的配置。