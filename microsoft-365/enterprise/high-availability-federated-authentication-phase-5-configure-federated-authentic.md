---
title: 高可用性联合身份验证阶段5为 Microsoft 365 配置联合身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 摘要：为 microsoft Azure 中的 Microsoft 365 的高可用性联合身份验证配置 Azure AD Connect。
ms.openlocfilehash: f00763487261b62940ac5def38d35158db77a699
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687970"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>高可用性联合身份验证阶段5：为 Microsoft 365 配置联合身份验证

在 Azure 基础结构服务中为 Microsoft 365 部署高可用性联合身份验证的最后一阶段，您将获取并安装由公共证书颁发机构颁发的证书，验证您的配置，然后在目录同步服务器上安装并运行 Azure AD Connect。 Azure AD Connect 将 Microsoft 365 订阅和 Active Directory 联合身份验证服务 (AD FS) 和 web 应用程序代理服务器配置为进行联合身份验证。
  
有关所有阶段，请参阅 [在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) 。
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>获取公共证书并将其复制到目录同步服务器

从具有以下属性的公共证书颁发机构获取数字证书：
  
- 适合于创建 SSL 连接的 X.509 证书。
    
- 将使用者可选名称 (SAN) 扩展属性设置为联合身份验证服务 FQDN（示例：fs.contoso.com）。
    
- 证书必须具有私钥并以 PFX 格式存储。
    
此外，组织计算机和设备必须信任颁发数字证书的公共证书颁发机构。通过将公共证书颁发机构的一个根证书安装在计算机和设备上的受信任根证书颁发机构存储中来建立这种信任。运行 Microsoft Windows 的计算机通常会安装常用证书颁发机构颁发的这些类型的一系列证书。如果尚未安装公共证书颁发机构提供的根证书，则必须将该证书部署到组织的计算机和设备。
  
有关联合身份验证的证书要求的详细信息，请参阅[联合身份验证安装和配置的先决条件](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)。
  
收到证书后，将其复制到目录同步服务器的 C：驱动器上的文件夹中。 例如，将文件命名为 SSL，并将其存储在 \\ 目录同步服务器上的 C：证书文件夹中。
  
## <a name="verify-your-configuration"></a>验证配置

现在，你应该已准备好为 Microsoft 365 配置 Azure AD Connect 和联合身份验证。 为确保已就绪，请检查以下清单：
  
- 您的组织的公共域已添加到 Microsoft 365 订阅中。
    
- 您的组织的 Microsoft 365 用户帐户配置为您的组织的公共域名，并且可以成功登录。
    
- 已基于公共域名确定联合身份验证服务 FQDN。
    
- 联合身份验证服务 FQDN 的公用 DNS A 记录指向用于 Web 应用程序代理服务器的面向 Internet 的 Azure 负载均衡器的公用 IP 地址。
    
- 联合身份验证服务 FQDN 的专用 DNS A 记录指向用于 AD FS 服务器的内部 Azure 负载均衡器的专用 IP 地址。
    
- 适用于将 SAN 设置为联合身份验证服务 FQDN 的 SSL 连接的公共证书颁发机构-isssued 数字证书是存储在目录同步服务器上的 PFX 文件。
    
- 公共证书颁发机构的根证书安装在计算机和设备上受信任根证书颁发机构存储中。
    
下面是 Contoso 组织的一个示例：
  
**Azure 中高可用性联合身份验证基础结构的示例配置**

![Azure 中高可用性 Microsoft 365 联合身份验证基础结构的示例配置](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>运行 Azure AD Connect 以配置联合身份验证

Azure AD Connect 工具使用以下步骤配置 AD FS 服务器、web 应用程序代理服务器和 Microsoft 365 以进行联合身份验证：
  
1. 使用具有本地管理员特权的域帐户创建到目录同步服务器的远程桌面连接。
    
2. 从目录同步服务器的桌面，打开 "Internet Explorer"，然后转到 [https://aka.ms/aadconnect](https://aka.ms/aadconnect) 。
    
3. 在"Microsoft Azure Active Directory Connect"页上，单击"下载"，然后单击"运行"。
    
4. 在"欢迎使用 Azure AD Connect"页上，请依次单击"我同意"、"继续"。
    
5. 在"快速设置"页上，单击"自定义"。
    
6. 在"安装所需的组件"页上，单击"安装"。
    
7. 在"用户登录"页上，依次单击"使用 AD FS 进行联合身份验证"和"下一步"。
    
8. 在 " **连接到 AZURE AD** " 页上，键入 Microsoft 365 订阅的全局管理员帐户的名称和密码，然后单击 " **下一步**"。
    
9. 在 " **连接目录** " 页上，确保在 " **林**" 中选择了 "本地 Active DIRECTORY 域服务 (AD DS) 林"，键入域管理员帐户的名称和密码，单击 " **添加目录**"，然后单击 " **下一步**"。
    
10. 在"Azure AD 登录配置"页上，单击"下一步"。
    
11. 在"域和 OU 筛选"页上，单击"下一步"。
    
12. 在"唯一标识用户"页上，单击"下一步"。
    
13. 在"筛选用户和设备"页上，单击"下一步"。
    
14. 在"可选功能"页上，单击"下一步"。
    
15. 在"AD FS 场"页上，单击"配置新的 AD FS 场"。
    
16. 单击"浏览"并指定公共证书颁发机构的 SSL 证书的位置和名称。
    
17. 出现提示时，键入证书密码，然后单击"确定"。
    
18. 确认"使用者名称"和"联合身份验证服务名称"已设置为联合身份验证服务 FQDN，然后单击"下一步"。
    
19. 在"AD FS 服务器"页上，键入第一个 AD FS 服务器的名称（表 M - 第 4 项 - 虚拟机名称列），然后单击"添加"。
    
20. 键入第二个 AD FS 服务器的名称（表 M - 第 5 项 - 虚拟机名称列），依次单击"添加"、"下一步"。
    
21. 在"Web 应用程序代理服务器"页上，键入第一个 Web 应用程序代理服务器的名称（表 M - 第 6 项 - 虚拟机名称列），然后单击"添加"。
    
22. 键入第二个 Web 应用程序代理服务器的名称（表 M - 第 7 项 - 虚拟机名称列），依次单击"添加"、"下一步"。
    
23. 在"域管理员凭据"页上，键入域管理员帐户的用户名和密码，然后单击"下一步"。
    
24. 在"AD FS 服务帐户"页上，键入企业管理员帐户的用户名和密码，然后单击"下一步"。
    
25. 在"Azure AD 域"页的"域"中，选择组织的 DNS 域名，然后单击"下一步"。
    
26. 在"准备配置"页上，单击"安装"。
    
27. 在"安装完成"页上，单击"验证"。应该可以看到两条指明 Intranet 和 Internet 配置均已成功验证的消息。
    
  - Intranet 消息应为 AD FS 服务器列出 Azure 内部负载均衡器的专用 IP 地址。
    
  - Internet 消息应为 Web 应用程序代理服务器列出面向 Internet 的 Azure 负载均衡器的公用 IP 地址。
    
28. 在"安装完成"页上，单击"退出"。
    
下面是服务器具有占位符名称的最终配置。
  
**阶段 5：Azure 中高可用性联合身份验证基础结构的最终配置**

![Azure 中高可用性 Microsoft 365 联合身份验证基础结构的最终配置](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Microsoft 365 在 Azure 中的高可用性联合身份验证基础结构已完成。
  
## <a name="see-also"></a>另请参阅

[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365 开发/测试环境的联合身份](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 解决方案和体系结构中心](../solutions/solution-architecture-center.md)

[适用于 Microsoft 365 的联合身份](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


