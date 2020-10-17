---
title: 使用 PowerShell 管理 Skype for Business Online 策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要：使用 PowerShell 通过策略管理 Skype for Business Online 用户帐户属性。
ms.openlocfilehash: 20a75fa1c131f693fcf30d20477af5c9ee7aed35
ms.sourcegitcommit: 22755cebfbfa2c4dc3f8b4f54ccb23636a211ee5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2020
ms.locfileid: "48477037"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>使用 PowerShell 管理 Skype for Business Online 策略

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

若要管理用于 Skype for Business Online 的用户帐户的许多属性，必须使用适用于 Microsoft 365 的 PowerShell 将它们指定为策略的属性。
  
## <a name="before-you-begin"></a>准备工作

使用以下说明设置运行命令 (跳过已完成的步骤) ：

  > [!Note]
  > Skype for Business Online 连接器当前是最新团队 PowerShell 模块的一部分。 如果您使用的是最新的团队 PowerShell 公开发布，则无需安装 Skype for Business Online 连接器。

1. 安装 [团队 PowerShell 模块](https://docs.microsoft.com/microsoftteams/teams-powershell-install)。
    
2. 开启 Windows PowerShell 命令提示符并运行以下命令： 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

   出现提示时，请输入你的 Skype for Business Online 管理员帐户名称和密码。
    
## <a name="manage-user-account-policies"></a>管理用户帐户策略

许多 Skype for Business Online 用户帐户属性都是通过使用策略配置的。 策略只是可应用于一个或多个用户的设置集合。 若要了解如何配置策略，可以对 FederationAndPICDefault 策略运行此示例命令：
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

反过来，您应返回类似于以下的内容：
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

在此示例中，此策略中的值确定在与联合用户通信时可使用的功能或无法执行的操作。 例如，EnableOutsideAccess 属性必须设置为 True，用户才能够与组织外部的人员进行通信。 请注意，此属性不会显示在 Microsoft 365 管理中心中。 相反，该属性将根据您所做的其他选择自动设置为 True 或 False。 其他两个感兴趣的属性为：
  
- **EnableFederationAccess** 指示用户是否可以与联合域的用户通信。
    
- **EnablePublicCloudAccess** 指示用户是否可以与 Windows Live 用户通信。
    
因此，不会直接更改用户帐户的与联合相关的属性 (例如 **get-csuser-EnableFederationAccess $True**) 。 而是为帐户分配一个预先配置的所需属性值的外部访问策略。 如果我们希望用户能够与联合用户和 Windows Live 用户通信，则必须为该用户帐户分配允许这些类型的通信的策略。
  
如果您希望知道某人是否可以与组织外部的用户进行通信，则必须执行以下操作：
  
- 确定为此用户分配的是哪种外部访问策略。
    
- 确定此策略允许的许可范围。
    
例如，您可以通过使用以下命令来执行此操作：
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

此命令可查找分配给用户的策略，然后查找该策略中启用或禁用的功能。
  
若要使用 PowerShell 管理 Skype for Business Online 策略，请参阅以下 cmdlet：

- [客户端策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [会议策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [移动策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [联机语音邮件策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [语音路由策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Skype for Business Online 拨号计划是除了名称之外的每个方面的策略。 已选择名称 "拨号计划"，而不是 "拨号策略"，以便提供与 Office 通信服务器和 Exchange 的向后兼容性。 
  
例如，若要查看所有可供使用的语音策略，请运行以下命令：
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> 将返回所有可用的语音策略的列表。 但请记住，并非所有策略都可以分配给所有用户。 这是由于涉及许可和地理位置的各种限制导致的。  (所谓的 "[使用位置](https://msdn.microsoft.com/library/azure/dn194136.aspx)"。) 如果您想知道可分配给特定用户的外部访问策略和会议策略，请使用与以下命令类似的命令： 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo 参数可将返回的数据限制为可分配到特定用户的策略（例如，Alex Darrow）。根据不同的授权和使用位置限制，可能会代表所有可用策略的子集。 
  
在某些情况下，不会将策略的属性与 Microsoft 365 一起使用，而有些则只能由 Microsoft 支持人员管理。 
  
使用 Skype for Business Online，用户必须由某种类型的策略进行管理。 如果与策略相关的有效属性为空，则表示有问题的用户将由全局策略管理，这是一个策略，该策略将自动应用于用户，除非专门为其分配了每用户策略。 由于我们看不到为用户帐户列出的客户端策略，因此它由全局策略管理。 您可以使用此命令确定全局客户端策略：
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>另请参阅

[使用 PowerShell 管理 Skype for Business Online](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[使用 PowerShell 管理 Microsoft 365](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[PowerShell for Microsoft 365 入门](getting-started-with-microsoft-365-powershell.md)

