---
title: 在设备上安装 Intune 公司门户
description: 有关在 Microsoft 托管桌面设备上安装公司门户应用的信息
keywords: Microsoft 托管桌面，Microsoft 365，公司门户
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: f9f36d6ca14be610ce9374380349264439282a6a
ms.sourcegitcommit: 1206319a5d3fed8d52a2581b8beafc34ab064b1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2021
ms.locfileid: "52086681"
---
# <a name="install-intune-company-portal-on-devices"></a>在设备上安装 Intune 公司门户

Microsoft 托管桌面要求 IT 管理员使用 Microsoft 托管桌面设备为用户安装 Intune 公司门户。 以下是组织的一些好处：
- 用户有一个浏览和安装可用应用程序的位置。 
- IT 管理员可以按用户类别组织应用程序。  
- 某些应用程序 (Microsoft Project 和 Microsoft Visio) 需要公司门户与 Microsoft 托管桌面一起部署。
- IT 管理员可以为组织自定义公司门户。 这包括品牌映像、添加本地支持联系人等。 有关详细信息，请参阅 [如何配置 Microsoft Intune 公司门户应用](/intune/company-portal-app)。   

本主题介绍将 Intune 公司门户部署到 Microsoft 托管桌面用户的过程。 整个过程如下所示：
1. 从适用于企业 Microsoft Store 购买公司门户，并同步到 Intune
2. 将公司门户分配给用户
3. 向用户传达更改

## <a name="step-1---purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>步骤 1 - 从适用于 Business 的 Microsoft Store 购买公司门户，并同步到 Intune
若要了解如何购买应用和与 Intune 同步，请参阅将应用部署到 *Microsoft 托管* 桌面设备中的 [适用于企业](deploy-apps.md#msfb-apps)应用的 Microsoft Store 应用。

本主题提供如何： 
- 从适用于企业 Microsoft Store 购买公司门户 
- 在 Intune 和适用于 Business 的 Microsoft Store 之间强制同步
- 验证 Intune 和适用于 Business 的 Microsoft Store 之间的活动同步 

## <a name="step-2---assign-company-portal-to-your-users"></a>步骤 2 - 将公司门户分配给用户
注册 Microsoft 托管桌面后，我们将自动将公司门户部署到租户，并在你的组织的 Microsoft 托管桌面设备上安装该应用。

## <a name="step-3---communicate-change-to-your-users"></a>步骤 3 - 将更改传达给用户
作为组织的 IT 管理员，让用户了解如何在组织中使用公司门户非常重要。 Microsoft 托管桌面建议：
- 从公司门户安装应用程序的步骤。 有关详细信息，请参阅在设备上 [安装和共享应用](/intune-user-help/install-apps-cpapp-windows)。
- 如何向 IT 管理员发送当前不可用的应用程序的请求。 有关详细信息，请参阅请求 [工作或学校应用](/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school)。  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft 托管桌面入门步骤

1. [在管理门户中添加和验证管理员联系人](add-admin-contacts.md)
2. [调整条件访问](conditional-access.md)
3. [分配许可证](assign-licenses.md)
4. 部署 Intune 公司门户 (本主题) 
5. [启用企业状态漫游](enterprise-state-roaming.md)
6. [设置设备](set-up-devices.md)
7. [让用户做好使用设备的准备](get-started-devices.md)
8. [部署应用](deploy-apps.md)
