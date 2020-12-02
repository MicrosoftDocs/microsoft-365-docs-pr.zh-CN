---
title: 准备不可路由域以进行目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: 如果您在与 Microsoft 365 同步之前拥有与本地用户关联的非 routale 域，请了解要执行的操作。
ms.openlocfilehash: f38f6143b6e26b2849c174f74c94d009ddea73cd
ms.sourcegitcommit: 4cbb4ec26f022f5f9d9481f55a8a6ee8406968d2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "49527717"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>准备不可路由域以进行目录同步
当您将本地目录与 Microsoft 365 同步时，您必须在 Azure Active Directory 中有一个经过验证的域 (Azure AD) 。 仅同步与本地域关联 (UPN) 的用户主体名称。 但是，任何包含非可路由域的 UPN （例如，本地 (如 billa@contoso 本地) ）将同步到 onmicrosoft.com 域 (，如 billa@contoso.onmicrosoft.com) 。 

如果您当前在 Active Directory 域服务 (AD DS 中为您的用户帐户使用了一个. 本地域) 建议您将其更改为使用经验证的域 (如 billa@contoso.com) ，以便正确地与 Microsoft 365 域同步。
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>如果我只有一个本地域，该怎么办？

你可用于将 AD DS 同步到 Azure AD 的最新工具称为 "Azure AD Connect"。 有关详细信息，请参阅 [将本地标识与 AZURE AD 集成](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。
  
Azure AD Connect 同步你的用户的 UPN 和密码，以便用户可以使用内部部署中使用的相同凭据登录。 但是，Azure AD Connect 仅将用户同步到 Microsoft 365 验证的域。 这意味着域也会由 Azure AD 验证，因为 Microsoft 365 身份由 Azure AD 管理。 换句话说，域必须是有效的 Internet 域 (例如 .com、. org、.net、. us 等 ) 。 如果内部 AD DS 仅使用不可路由的域 (例如，. local) ，这不会与 Microsoft 365 上已验证的域匹配。 您可以通过在本地 AD DS 中更改主要域，或通过添加一个或多个 UPN 后缀来修复此问题。
  
### <a name="change-your-primary-domain"></a>**更改你的主要域**

将您的主域更改为在 Microsoft 365 中验证的域（例如，contoso.com）。 然后，会将拥有域 contoso. 本地的每个用户更新为 contoso.com。 这是一个非常涉及的过程，但在下一节中介绍了更简单的解决方案。
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**添加 UPN 后缀并将你的用户更新到这些后缀**

您可以通过在 AD DS 中注册新的 UPN 后缀或后缀以匹配在 Microsoft 365 中验证的域 (或域) 解决本地问题。 注册新后缀后，使用新域名更新用户 Upn 以将局部变量替换为示例，以便用户帐户看起来像 billa@contoso.com。
  
将 Upn 更新为使用已验证的域后，即可将本地 AD DS 与 Microsoft 365 同步。
  
 **步骤1：添加新的 UPN 后缀**
  
1. 在 AD DS 域控制器上，在 "服务器管理器" 中选择 " **工具** \> **Active Directory 域和信任**"。
    
    **或者，如果您没有 Windows Server 2012**
    
    按 **Windows 键 + R** 以打开 " **运行** " 对话框，然后在 "services.msc" 中键入，然后选择 **"确定"**。
    
    ![选择 "Active Directory 域和信任"。](../media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. 在 " **Active Directory 域和信任** " 窗口中，右键单击 " **active Directory 域和信任关系**"，然后选择 " **属性**"。
    
    ![右键单击 "Active Directory 域和信任关系"，然后选择 "属性"](../media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. 在 " **UPN 后缀** " 选项卡上的 " **备用 upn 后缀** " 框中，键入新的 upn 后缀或后缀，然后选择 " **添加** \> **应用**"。
    
    ![添加新的 UPN 后缀](../media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    完成添加后缀后，选择 **"确定"** 。 
    
 **步骤2：更改现有用户的 UPN 后缀**
  
1. 在 AD DS 域控制器上，在 "服务器管理器" 中选择 " **工具**" " \> **Active Directory 用户和计算机**"。
    
    **或者，如果您没有 Windows Server 2012**
    
    按 **Windows 键 + R** 以打开 " **运行** " 对话框，然后在 "dsa.msc" 中键入，然后单击 **"确定"**
    
2. 选择一个用户，单击鼠标右键，然后选择 " **属性**"。
    
3. 在 " **帐户** " 选项卡上的 "UPN 后缀" 下拉列表中，选择新的 upn 后缀，然后选择 **"确定"**。
    
    ![为用户添加新的 UPN 后缀](../media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 为每个用户完成这些步骤。
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**您还可以使用 Windows PowerShell 为所有用户更改 UPN 后缀**

如果有大量用户要更新，则使用 Windows PowerShell 更为简单。 下面的示例使用 cmdlet [microsoft.rtc.management.adconnect.schema.aduser](https://go.microsoft.com/fwlink/p/?LinkId=624312) 和 [microsoft.rtc.management.adconnect.schema.aduser](https://go.microsoft.com/fwlink/p/?LinkId=624313) 将所有 contoso. 本地后缀更改为 contoso.com。 

例如，您可以运行以下 Windows PowerShell 命令将所有 contoso. 本地后缀更新为 contoso.com：
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

若要详细了解如何在 AD DS 中使用 Windows PowerShell，请参阅 [Active Directory Windows PowerShell 模块](https://go.microsoft.com/fwlink/p/?LinkId=624314) 。 

