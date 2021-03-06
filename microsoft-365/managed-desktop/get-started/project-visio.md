---
title: 在Microsoft Project设备上Visio安装 Microsoft 托管桌面 或 Microsoft Microsoft 托管桌面
description: 有关在 Microsoft Project 设备上Visio Microsoft Microsoft 托管桌面的信息
keywords: Microsoft 托管桌面、Microsoft 365、Microsoft Project、Microsoft Visio
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: normal
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: 9fd46410877012d92e847ba7ff8b60cd5acceb1e
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925535"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>在Microsoft Project设备上Visio安装 Microsoft 托管桌面 或 Microsoft Microsoft 托管桌面

Microsoft Project和 Microsoft Visio需要在设备上安装特定Microsoft 托管桌面步骤。 本主题介绍这些应用程序的先决条件和安装过程。

## <a name="prerequisites"></a>先决条件

管理员应验证他们满足以下先决条件：
- **许可证数量**- 用户Microsoft Project Microsoft Visio许可证的正确数量。 Microsoft 托管桌面当前仅支持这些应用程序的 64 位版本。 
- **许可证名称** - 这些应用程序的适当许可证名称为：
    - **Microsoft Project** - Project Online Professional 或 Project Online 高级版
    - **Microsoft Visio** - Visio Online 计划 2
- **公司门户**- 公司门户必须在租户中提供，以便用户安装这些应用程序。 如果公司门户未在租户中部署[，请参阅](company-portal.md)公司门户。

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>为Project Visio部署 Microsoft 托管桌面 和 Microsoft 托管桌面
Microsoft 托管桌面中，Microsoft Project Microsoft Visio 添加为两个 Win32 Microsoft Intune。 我们还将在应用程序内创建Azure Active Directory组，这两个组将分配给具有"可用"意图的相应应用程序。 

**部署Project和Visio** 将用户添加到相应的组，应用程序将在相应的公司门户。 可能需要几分钟才能同步，但随后你的用户可以从 公司门户。 

Azure AD 组名称 | 要分配哪些用户？   
 --- | ---
现代 Workplace-Office-Project_Install | 需要用户Project
现代 Workplace-Office-Visio_Install | 需要用户Visio

## <a name="communicate-changes"></a>传达更改
IT 管理员必须让用户了解如何安装Project Visio。 这包括： 
- 在这些应用程序可供用户使用时通知用户。 
- 有关如何从客户端安装这些应用程序的公司门户。
