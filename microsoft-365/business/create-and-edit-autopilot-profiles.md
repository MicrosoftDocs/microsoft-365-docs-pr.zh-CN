---
title: 创建和编辑 AutoPilot 配置文件
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: 了解如何创建 AutoPilot 配置文件，并应用到设备，以及编辑或删除配置文件或者从设备中删除配置文件。
ms.openlocfilehash: 414243da88fb6f39f8e6067d19d49ffe955f725f
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2021
ms.locfileid: "51580246"
---
# <a name="create-and-edit-autopilot-profiles"></a>创建和编辑 AutoPilot 配置文件

## <a name="create-a-profile"></a>创建配置文件

配置文件适用于单个设备或一组设备，
  
1. In the Microsoft 365 admin center， choose **Devices** \> **AutoPilot**.
  
2. 在 **AutoPilot 页面上** ，选择 **配置文件** 选项卡 \> **创建配置文件**。
    
3. 在 **"创建配置文件** "页上，输入可帮助您标识该配置文件的名称，例如 Marketing。 打开您想要的设置，然后选择"保存 **"。** 有关 AutoPilot 配置文件设置详细信息，请参阅关于 [AutoPilot 配置文件设置](autopilot-profile-settings.md)。
    
    ![Enter name and turn on settings in the Create profile panel.](../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>对设备应用配置文件

创建配置文件后，你可以将配置文件应用于设备或一组设备。 可以在分步指南中选取现有配置文件[](add-autopilot-devices-and-profile.md)并将其应用到新设备，或者替换设备或设备组的现有配置文件。 
  
1. 在" **准备 Windows**"页面上，选择" **设备**"选项卡。 
    
2. 选中设备名称旁边的复选框，在"设备"面板中，从"分配配置文件"下拉列表"保存"中选择 \> **配置文件**。
    
    ![In the Device panel, select an Assigned profile to apply it.](../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>编辑、删除或移除配置文件

将配置文件分配给一个设备后，便可以更新该文件，即使已将该设备提供给一个用户。如果设备连接了 internet，系统会在设置过程中下载最新版本的配置文件。如果用户将其设备恢复为出厂默认设置，设备将再次下载配置文件的最新更新。 
  
### <a name="edit-a-profile"></a>编辑配置文件

1. 在" **准备 Windows**"页面上，选择" **配置文件**"选项卡。 
    
2. 选中设备名称旁边的复选框，在配置文件面板中更新任何可用的设置保存 \> 。
    
    如果在用户将设备连接到 internet 之前执行此操作，配置文件会应用于设置过程。
    
### <a name="delete-a-profile"></a>删除配置文件

1. 在" **准备 Windows**"页面上，选择" **配置文件**"选项卡。 
    
2. 选中设备名称旁边的复选框，在"配置文件"面板 **中，选择**"删除配置文件""**保存** \> **"。**
    
    如果删除了配置文件，该文件会从之前分配到的一个或一组设备中移除。
    
### <a name="remove-a-profile"></a>移除配置文件

1. 在" **准备 Windows**"页面上，选择" **设备**"选项卡。 
    
2. 选中设备名称旁边的复选框，在"设备"面板中，从"已分配配置文件"下拉列表"保存"中选择"无 \> **"。**
    
