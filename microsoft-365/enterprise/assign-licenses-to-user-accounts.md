---
title: 将 Microsoft 365 许可证分配给用户帐户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何将 Microsoft 365 许可证单独或基于组成员身份分配给用户帐户。
ms.openlocfilehash: 60936e52bffa58d50419f771e670848ee76271fd
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687633"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>将 Microsoft 365 许可证分配给用户帐户

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

对于仅限云的标识模型，可以根据创建的方式将 Microsoft 365 许可证分配给用户帐户，具体取决于您的创建方式。

对于混合标识模型，如果 Active Directory 域服务 (AD DS) 用户帐户首次同步，则不会自动为其分配 Microsoft 365 许可证。 必须先使用用户位置配置每个用户帐户。

在这两种情况下，都必须将许可证分配给用户帐户，以便您的用户可以访问 Microsoft 365 服务，例如电子邮件和 Microsoft 团队。

您可以通过组成员身份单独或自动将许可证分配给用户帐户。

若要将 Microsoft 365 许可证分配给单个用户帐户，您可以使用：

- [Microsoft 365 管理员中心](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [PowerShell for Microsoft 365](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)

有关自动许可证分配，请参阅 [AZURE AD 中的基于组的许可](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。

## <a name="next-steps"></a>后续步骤

使用已分配了许可证的完整用户帐户集，您现在可以：

- [实施安全性](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [部署客户端软件，例如 Microsoft 365 应用程序](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [在 Microsoft 365 中设置移动设备管理](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [配置服务和应用程序](configure-services-and-applications.md)
