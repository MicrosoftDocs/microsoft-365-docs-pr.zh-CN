---
title: 为 Microsoft 托管桌面准备本地资源访问权限
description: 确保 Azure AD 可以与本地 AD 进行通信以提供身份验证的重要步骤
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 6df23e0d7e3ea0ecd7ebacd96f00cb47b9e0aa84
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2021
ms.locfileid: "51574591"
---
#  <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>为 Microsoft 托管桌面准备本地资源访问权限

在 Microsoft 托管桌面中，设备会自动加入到 Azure AD (Azure Active Directory) 。 因此，如果你使用的是本地 Active Directory，必须检查一些内容，以确保加入 Azure AD 的设备可以与本地 Active Directory 通信。 

> [!NOTE]  
> *混合* Microsoft 托管桌面不支持加入 Azure AD。

Azure Active Directory 允许你的用户利用单一 Sign-On (SSO) ，这意味着他们通常不需要每次使用资源时都提供凭据。

有关加入 Azure Active Directory 的信息，请参阅 [如何：规划 Azure AD 加入实现](/azure/active-directory/devices/azureadjoin-plan)。 有关加入 Azure AD 的Sign-On (SSO) ，请参阅 SSO 到本地资源在 [加入 Azure AD](/azure/active-directory/devices/azuread-join-sso#how-it-works)的设备上的工作原理。


本文介绍了需要检查哪些内容，以确保依赖于本地 Active Directory 连接的应用和其他资源能够顺利使用 Microsoft 托管桌面。


## <a name="single-sign-on-for-on-premises-resources"></a>用于Sign-On资源的单个资源

默认情况下Sign-On (Microsoft 托管桌面) 启用使用 UPN 和密码的单一 SSO 设置。 但是，你的用户也可以使用 Windows Hello 企业应用，这需要一些额外的设置步骤。 

### <a name="single-sign-on-by-using-upn-and-password"></a>单Sign-On UPN 和密码进行加密

在大多数组织中，用户将能够使用 SSO 通过 UPN 进行身份验证，并使用 Microsoft 托管桌面设备上的密码进行身份验证。 但是，若要确保此函数正常工作，应仔细检查以下内容：

- 确认已设置 Azure AD Connect 并使用运行 Windows Server 2008 R2 或更高版本的本地 Active Directory 服务器。
- 确认 Azure AD Connect 正在运行受支持的版本，并设置为与 Azure AD 同步这三个属性： 
    - 用户所在的本地 Active Directory (DNS 域名) 
    - 用户所在的本地 Active Directory (的 NetBIOS) 
    - 用户的 SAM 帐户名


### <a name="single-sign-on-by-using-windows-hello-for-business"></a>使用 windows hello 企业Sign-On单一应用

Microsoft 托管桌面设备还通过使用 Windows Hello 企业版为用户提供快速、无密码的体验。 若要确保 Windows Hello 企业版本在用户无需提供各自的 UPN 和密码的情况下工作，请访问为本地 Single-Sign 配置 [加入 Azure AD](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) 的设备。使用 Windows Hello 企业版本检查要求，然后按照那里提供的步骤操作。


## <a name="apps-and-resources-that-use-authentication"></a>使用身份验证的应用和资源

有关 [设置应用以使用](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) Azure Active Directory 的完整指南，请参阅了解 Azure 内容集内应用程序和资源注意事项。 摘要：


- 如果你使用 **基于云的应用**（例如添加到 Azure AD 应用库的应用），则大多数应用无需进一步准备，以使用 Microsoft 托管桌面。 但是，任何不使用 Web 帐户管理器或 WAM (Win32) 可能仍提示用户进行身份验证。

- 对于在本地 **托管的应用，** 请确保将这些应用添加到浏览器的受信任站点列表。 此步骤将使 Windows 身份验证无缝工作，而不会提示用户提供凭据。 若要添加应用，请参阅可 [配置设置](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) 参考 [中的受信任的站点](../working-with-managed-desktop/config-setting-ref.md)。

- 如果使用的是 Active Directory 联合服务，则使用使用 AD FS 验证和管理单一登录中的步骤检查 [SSO 是否已启用](/previous-versions/azure/azure-services/jj151809(v=azure.100))。 

- 对于 **本地和使用旧** 协议的应用，无需额外设置，只要设备有权访问本地域控制器进行身份验证。 但是，若要为这些应用程序提供安全访问，应部署 Azure AD 应用程序代理。 有关详细信息，请参阅通过 [Azure Active Directory](/azure/active-directory/manage-apps/application-proxy)的应用程序代理远程访问本地应用程序。

- 不支持 **在本地运行并依赖** 计算机身份验证的应用，因此应考虑将它们替换为较新版本。

### <a name="network-shares-that-use-authentication"></a>使用身份验证的网络共享

只要设备能够使用 UNC 路径访问本地域控制器，用户就无需进行额外的设置，即访问网络共享。

### <a name="printers"></a>打印机

Microsoft 托管桌面设备无法连接到发布到本地 Active Directory 的打印机，除非已配置 [混合云打印](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy)。

虽然无法自动在仅云环境中发现打印机，但只要设备可以访问本地域控制器，用户就可以使用打印机路径或打印机队列路径来使用本地打印机。

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready"></a>准备步骤

1. 查看 [Microsoft 托管桌面的先决条件](prerequisites.md)。
2. 使用 [准备情况评估工具](readiness-assessment-tool.md)。
3. [来宾帐户的先决条件](guest-accounts.md)
4. [Microsoft 托管桌面的网络配置](network.md)
5. [为 Microsoft 托管桌面准备证书和网络配置文件](certs-wifi-lan.md)
6. [Prepare on-premises resources access for Microsoft Managed Desktop](authentication.md) (This article) 
7. [Microsoft 托管桌面中的应用](apps.md)
8. [为 Microsoft 托管桌面准备映射的驱动器](mapped-drives.md)
9. [为 Microsoft 托管桌面准备打印资源](printing.md)
