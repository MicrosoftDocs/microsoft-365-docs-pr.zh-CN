---
title: 关于"AutoPilot 配置文件"设置
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: AutoPilot 配置文件可帮助你控制Windows安装用户设备。 配置文件包含默认和可选设置，如跳过 Cortana 安装。
ms.openlocfilehash: 86f8718131f0a0b93e18e65e39e02e7d65aded1a
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2021
ms.locfileid: "51578499"
---
# <a name="about-autopilot-profile-settings"></a>关于"AutoPilot 配置文件"设置

## <a name="autopilot-profile-settings"></a>AutoPilot 配置文件设置

可以使用 AutoPilot 配置文件来控制用户Windows安装方法。 配置文件包含以下设置。
  
 **AutoPilot 默认 (需要) 自动设置的功能：**
  
|**设置**|**说明**|
|:-----|:-----|
|跳过 Cortana、OneDrive 和 OEM 注册  <br/> |跳过 Cortana 和个人应用等消费者应用的OneDrive。 只要用户是设备的本地管理员，设备用户就可以稍后安装它们。 将跳过原始制造商注册，因为设备由 Microsoft 365 商业高级版。  <br/> |
|使用公司品牌登录体验  <br/> |如果你的公司有"将公司品牌添加到Microsoft 365[登录](../admin/setup/customize-sign-in-page.md)"页面，设备用户将在登录时获得该体验。  <br/> |
|使用已配置的 AAD 帐户自动注册 MDM。  <br/> |用户标识由用户Azure Active Directory，用户将登录到 Windows，Microsoft 365其Microsoft 365 商业高级版凭据。  <br/> |
   
 **可选设置：**
  
|**设置**|**说明**|
|:-----|:-----|
|默认情况下，跳过 ("关闭")   <br/> |如果此选项设置为 **"** 打开"，则设备用户将看不到设备的许可协议，Windows首次登录时将看不到该设备。  <br/> |
|不允许用户成为本地管理员  <br/> |如果此选项设置为 **"打开"，** 则设备用户将无法安装任何个人应用，例如 Cortana。<br/> |
