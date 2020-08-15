---
title: 如何配置本地 Skype for Business 以使用混合新式验证
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 了解如何将 Skype for Business 本地配置为使用混合新式身份验证 (HMA) ，从而为您提供更安全的用户身份验证和授权。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 74c8e3e0514fbfd8779c2f65e9c541c33b281c59
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46695002"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>如何配置本地 Skype for Business 以使用混合新式验证

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

新式身份验证是一种提供更安全的用户身份验证和授权的身份管理方法，适用于本地 Skype for business server 和 Exchange server 本地以及拆分域 Skype for Business 混合。
  
 **重要说明** 您想了解有关新式验证 (MA) 的详细信息，以及您为什么希望在贵公司或组织中使用它？ 查看 [此文档](hybrid-modern-auth-overview.md) 以了解概述。 如果需要了解 MA 支持的 Skype for Business 拓扑，此处对此进行了介绍！
  
 **在开始之前**，我使用以下术语：
  
- 新式验证 (MA) 

- 混合新式身份验证 (HMA) 

- Exchange 本地 (EXCH) 

- Exchange Online (EXO) 

- Skype for Business 本地 (SFB) 

- Skype for Business Online (SFBO) 

此外，如果本文中的图形有一个灰显或变暗的对象，表示在 MA 特定的配置中 **不** 包含以灰色显示的元素。
  
## <a name="read-the-summary"></a>阅读摘要

此摘要将流程分解为在执行过程中可能会丢失的步骤，并适用于整个清单，以跟踪您在进程中所处的位置。
  
1. 首先，请确保满足所有先决条件。

1. 由于许多 **先决条件** 对于 Skype for Business 和 Exchange 都是常见的， [请参阅预先申请清单的概述文章](hybrid-modern-auth-overview.md)。 在开始本文中的任何步骤  *之前*  ，请执行此操作。

1. 收集您在文件或 OneNote 中需要的 HMA 特定信息。

1. 如果尚未打开) ，请为 EXO (打开新式验证。

1. 如果尚未打开) ，请为 SFBO (打开新式验证。

1. 为本地 Exchange 启用混合新式身份验证。

1. 启用本地 Skype for business 的混合新式身份验证。

这些步骤为 SFB、SFBO、EXCH 和 EXO 启用了 MA-也就是说，可以参与 HMA 和 (SFB 的 SFBO 配置的所有产品，包括对 EXCH/EXO) 的依赖项。 换句话说，如果用户驻留在混合 (EXO + SFBO、EXO + SFB、EXCH + SFBO 或 EXCH + SFB) 的任何部分中，则您的最终产品将如下所示：
  
![混合的6个 Skype for business HMA 拓扑在所有四个可能的位置都有 MA。](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
正如您所看到的，有四个不同的位置可以打开 MA！ 为获得最佳用户体验，我们建议你在所有四个位置都打开 MA。 如果无法在所有这些位置启用 MA，请调整步骤，以便仅在环境所需的位置启用 MA。
  
有关支持的拓扑，请参阅 [Skype for](https://technet.microsoft.com/library/mt803262.aspx) business 的可支持性主题（MA 为 MA）。
  
 **重要说明** 在开始之前，请仔细检查是否满足所有先决条件。 你将发现 [混合新式验证概述和先决条件](hybrid-modern-auth-overview.md)中的信息。
  
## <a name="collect-all-hma-specific-info-youll-need"></a>收集您需要的所有 HMA 特定信息

在仔细检查您是否符合使用新式验证的 [先决条件](hybrid-modern-auth-overview.md) 后 (。请参阅上面的注释) ，应创建一个文件，以保存在前面步骤中配置 HMA 所需的信息。 本文中使用的示例：
  
- **SIP/SMTP 域**

  - Ex. contoso.com (与 Office 365) 联合使用

- **租户 ID**

  - 在 contoso.onmicrosoft.com) 登录时表示 Office 365 租户 (的 GUID。

- **SFB 2015 CU5 Web 服务 Url**

你将需要部署的所有 SfB 2015 池的内部和外部 web 服务 Url。 若要获取这些内容，请从 Skype for Business 命令行管理程序运行以下命令：
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Ex. 里面 https://lyncwebint01.contoso.com

- Ex. 对外 https://lyncwebext01.contoso.com

如果使用的是 Standard Edition server，则内部 URL 将为空。 在这种情况下，请使用内部 URL 的池 fqdn。
  
## <a name="turn-on-modern-authentication-for-exo"></a>打开 EXO 的新式验证

请按照以下说明操作： [Exchange Online：如何为你的租户启用新式验证。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>打开 SFBO 的新式验证

请按照以下说明操作： [Skype For Business Online：为你的租户启用新式验证](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>启用本地 Exchange 的混合新式身份验证

请按照以下说明操作： [如何将 Exchange Server 本地配置为使用混合新式身份验证](configure-exchange-server-for-hybrid-modern-authentication.md)。
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>启用本地 Skype for business 的混合新式身份验证

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>在 Azure Active Directory 中将本地 web 服务 Url 添加为 Spn

现在，您需要运行命令，以添加作为 SFBO 中的服务主体 (之前收集) 的 Url。
  
 **注释** 服务主体名称 (Spn) 标识 web 服务并将它们与安全 (主体（如帐户名称或组) ）相关联，以便服务可以代表授权的用户执行操作。 对服务器进行身份验证的客户端使用 Spn 中包含的信息。
  
1. 首先，使用 [以下说明](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)连接到 Azure Active Directory (azure AD) 。

2. 运行此命令（本地）以获取 SFB web 服务 Url 的列表。

   请注意，AppPrincipalId 以开头 `00000004` 。 这对应于 Skype for Business Online。

   记下 (和屏幕截图，以便稍后比较) 此命令的输出，其中包括 SE 和 WS URL，但主要由以开头的 Spn 组成 `00000004-0000-0ff1-ce00-000000000000/` 。

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. 如果内部 **或** 外部 SFB url 来自内部部署，则 (例如， https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) 我们需要将这些特定记录添加到此列表中。

    请务必将下面  *的示例 url* 替换为在 Add 命令中使用的实际 url！
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. 再次运行步骤2中的 **new-msolserviceprincipal** 命令，并查看输出，以验证新记录是否已添加。 将列表或屏幕截图从早到新的 Spn 列表进行比较。 您还可能会为记录提供新的列表屏幕截图。 如果成功，您将在列表中看到两个新的 Url。 根据我们的示例，Spn 列表现在将包含特定的 Url https://lyncwebint01.contoso.com 和 https://lyncwebext01.contoso.com/ 。

### <a name="create-the-evosts-auth-server-object"></a>创建 EvoSTS Auth Server 对象

在 Skype for Business 命令行管理程序中运行以下命令。
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>启用混合新式身份验证

这是实际打开 MA 的步骤。 前面的所有步骤都可以提前运行，而无需更改客户端身份验证流。 当您准备好更改身份验证流时，请在 Skype for Business 命令行管理程序中运行此命令。

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Verify

启用 HMA 后，客户端的下一次登录将使用新的身份验证流。 请注意，仅打开 HMA 不会对任何客户端触发重新身份验证。 客户端根据身份验证令牌和/或证书具有的有效期进行身份验证。
  
若要测试 HMA 在启用后是否正常工作，请注销测试 SFB Windows 客户端，并确保单击 "删除我的凭据"。 重新登录。 客户端现在应使用新式的身份验证流，并且您的登录现在将包含 **Office 365** 提示 "工作或学校" 帐户，在客户端与服务器联系并登录之前，请立即看到该帐户。
  
您还应检查 "OAuth 颁发机构" 的 Skype for business 客户端的 "配置信息"。 若要在客户端计算机上执行此操作，请按住 CTRL 键，同时右键单击 Windows 通知托盘中的 "Skype for Business" 图标。 在出现的菜单中单击 " **配置信息** "。 在将出现在桌面上的 "Skype for Business 配置信息" 窗口中，查找以下内容：
  
![使用新式验证的 Skype for business 客户端的配置信息显示了的 Lync 和 EWS OAUTH 授权 URL https://login.windows.net/common/oauth2/authorize 。](../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
您还应按住 CTRL 键，同时右键单击 Outlook 客户端的图标 (也在 Windows 通知托盘) 中，然后单击 "连接状态"。 针对身份验证类型的 "载荷" 查找客户端的 SMTP 地址 \* ，该类型表示在 OAuth 中使用的持有者令牌。
  
## <a name="related-articles"></a>相关文章

[链接回新式验证概述](hybrid-modern-auth-overview.md)。
  
您是否需要了解如何对您的 Skype for business 客户端使用新式验证 (ADAL) ？ 我们 [在此处](https://technet.microsoft.com/library/mt710548.aspx)获取了一些步骤。
