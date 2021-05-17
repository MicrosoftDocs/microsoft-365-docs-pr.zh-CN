---
title: 高可用性联合身份验证阶段 5 为用户配置Microsoft 365
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
description: 摘要：配置 Azure AD 连接，以在 Microsoft 365 中Microsoft Azure。
ms.openlocfilehash: 2bca2b758486b85d185870e2e14b495b8f084cb7
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929404"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a><span data-ttu-id="c0755-103">高可用性联合身份验证阶段 5：为用户配置Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c0755-103">High availability federated authentication Phase 5: Configure federated authentication for Microsoft 365</span></span>

<span data-ttu-id="c0755-104">在 Azure 基础结构服务中为 Microsoft 365 部署高可用性联合身份验证的最后阶段，获取并安装公共证书颁发机构颁发的证书，验证配置，然后在目录同步服务器上安装和运行 Azure AD 连接。</span><span class="sxs-lookup"><span data-stu-id="c0755-104">In this final phase of deploying high availability federated authentication for Microsoft 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server.</span></span> <span data-ttu-id="c0755-105">Azure AD 连接配置 Microsoft 365 订阅和 Active Directory 联合身份验证服务 (AD FS) 和 Web 应用程序代理服务器进行联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="c0755-105">Azure AD Connect configures your Microsoft 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="c0755-106">请参阅[在 Azure 中为](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)Microsoft 365部署高可用性联合身份验证了解所有阶段。</span><span class="sxs-lookup"><span data-stu-id="c0755-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="c0755-107">获取公共证书并复制到目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="c0755-107">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="c0755-108">从具有以下属性的公共证书颁发机构获取数字证书：</span><span class="sxs-lookup"><span data-stu-id="c0755-108">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="c0755-109">适合于创建 SSL 连接的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="c0755-109">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="c0755-110">将使用者可选名称 (SAN) 扩展属性设置为联合身份验证服务 FQDN（示例：fs.contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="c0755-110">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="c0755-111">证书必须具有私钥并以 PFX 格式存储。</span><span class="sxs-lookup"><span data-stu-id="c0755-111">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="c0755-p102">此外，组织计算机和设备必须信任颁发数字证书的公共证书颁发机构。通过将公共证书颁发机构的一个根证书安装在计算机和设备上的受信任根证书颁发机构存储中来建立这种信任。运行 Microsoft Windows 的计算机通常会安装常用证书颁发机构颁发的这些类型的一系列证书。如果尚未安装公共证书颁发机构提供的根证书，则必须将该证书部署到组织的计算机和设备。</span><span class="sxs-lookup"><span data-stu-id="c0755-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="c0755-116">有关联合身份验证的证书要求的详细信息，请参阅[联合身份验证安装和配置的先决条件](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)。</span><span class="sxs-lookup"><span data-stu-id="c0755-116">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="c0755-117">收到证书后，将其复制到目录同步服务器的 C： 驱动器上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c0755-117">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server.</span></span> <span data-ttu-id="c0755-118">例如，将文件命名为 SSL.pfx，并存储到目录同步服务器上 C： \\ Certs 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c0755-118">For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="c0755-119">验证配置</span><span class="sxs-lookup"><span data-stu-id="c0755-119">Verify your configuration</span></span>

<span data-ttu-id="c0755-120">现在，你应准备好配置 Azure AD 连接和联合身份验证，Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="c0755-120">You should now be ready to configure Azure AD Connect and federated authentication for Microsoft 365.</span></span> <span data-ttu-id="c0755-121">为确保已就绪，请检查以下清单：</span><span class="sxs-lookup"><span data-stu-id="c0755-121">To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="c0755-122">你的组织的公共域将添加到你的Microsoft 365订阅。</span><span class="sxs-lookup"><span data-stu-id="c0755-122">Your organization's public domain is added to your Microsoft 365 subscription.</span></span>
    
- <span data-ttu-id="c0755-123">组织的 Microsoft 365用户帐户配置为组织的公共域名，可以成功登录。</span><span class="sxs-lookup"><span data-stu-id="c0755-123">Your organization's Microsoft 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="c0755-124">已基于公共域名确定联合身份验证服务 FQDN。</span><span class="sxs-lookup"><span data-stu-id="c0755-124">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="c0755-125">联合身份验证服务 FQDN 的公用 DNS A 记录指向用于 Web 应用程序代理服务器的面向 Internet 的 Azure 负载均衡器的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c0755-125">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="c0755-126">联合身份验证服务 FQDN 的专用 DNS A 记录指向用于 AD FS 服务器的内部 Azure 负载均衡器的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c0755-126">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="c0755-127">公共证书颁发机构颁发的数字证书适用于将 SAN 设置为联合身份验证服务 FQDN 的 SSL 连接，它是存储在目录同步服务器的 PFX 文件。</span><span class="sxs-lookup"><span data-stu-id="c0755-127">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="c0755-128">公共证书颁发机构的根证书安装在计算机和设备上受信任根证书颁发机构存储中。</span><span class="sxs-lookup"><span data-stu-id="c0755-128">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="c0755-129">下面是 Contoso 组织的一个示例：</span><span class="sxs-lookup"><span data-stu-id="c0755-129">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="c0755-130">**Azure 中高可用性联合身份验证基础结构的示例配置**</span><span class="sxs-lookup"><span data-stu-id="c0755-130">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中高可用性和联合Microsoft 365基础结构的示例配置](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="c0755-132">运行 Azure AD Connect 以配置联合身份验证</span><span class="sxs-lookup"><span data-stu-id="c0755-132">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="c0755-133">Azure AD 连接工具通过以下步骤配置 AD FS 服务器、Web 应用程序代理服务器Microsoft 365联合身份验证：</span><span class="sxs-lookup"><span data-stu-id="c0755-133">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Microsoft 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="c0755-134">使用具有本地管理员权限的域帐户创建到目录同步服务器的远程桌面连接。</span><span class="sxs-lookup"><span data-stu-id="c0755-134">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="c0755-135">在目录同步服务器的桌面上，打开Internet Explorer转到 [https://aka.ms/aadconnect](https://aka.ms/aadconnect) 。</span><span class="sxs-lookup"><span data-stu-id="c0755-135">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="c0755-136">在"Microsoft Azure Active Directory Connect"页上，单击"下载"，然后单击"运行"。</span><span class="sxs-lookup"><span data-stu-id="c0755-136">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="c0755-137">在"欢迎使用 Azure AD Connect"页上，请依次单击"我同意"、"继续"。</span><span class="sxs-lookup"><span data-stu-id="c0755-137">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="c0755-138">在"快速设置"页上，单击"自定义"。</span><span class="sxs-lookup"><span data-stu-id="c0755-138">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="c0755-139">在"安装所需的组件"页上，单击"安装"。</span><span class="sxs-lookup"><span data-stu-id="c0755-139">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="c0755-140">在"用户登录"页上，依次单击"使用 AD FS 进行联合身份验证"和"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-140">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c0755-141">在 **"连接 Azure AD"** 页上，键入你的 Microsoft 365 订阅的全局管理员帐户的名称和密码，然后单击"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="c0755-141">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Microsoft 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="c0755-142">在 **"连接** 目录"页上，确保在"林"中选择了本地 Active Directory 域服务 (AD DS) 林，键入域管理员帐户的名称和密码，单击"添加 **目录**"，然后单击"下一步 **"。**</span><span class="sxs-lookup"><span data-stu-id="c0755-142">On the **Connect your directories** page, ensure that your on-premises Active Directory Domain Services (AD DS) forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="c0755-143">在"Azure AD 登录配置"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-143">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="c0755-144">在"域和 OU 筛选"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-144">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="c0755-145">在"唯一标识用户"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-145">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="c0755-146">在"筛选用户和设备"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-146">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="c0755-147">在"可选功能"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-147">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="c0755-148">在"AD FS 场"页上，单击"配置新的 AD FS 场"。</span><span class="sxs-lookup"><span data-stu-id="c0755-148">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="c0755-149">单击"浏览"并指定公共证书颁发机构的 SSL 证书的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="c0755-149">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="c0755-150">出现提示时，键入证书密码，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="c0755-150">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="c0755-151">确认"使用者名称"和"联合身份验证服务名称"已设置为联合身份验证服务 FQDN，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-151">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c0755-152">在"AD FS 服务器"页上，键入第一个 AD FS 服务器的名称（表 M - 第 4 项 - 虚拟机名称列），然后单击"添加"。</span><span class="sxs-lookup"><span data-stu-id="c0755-152">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="c0755-153">键入第二个 AD FS 服务器的名称（表 M - 第 5 项 - 虚拟机名称列），依次单击"添加"、"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-153">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="c0755-154">在"Web 应用程序代理服务器"页上，键入第一个 Web 应用程序代理服务器的名称（表 M - 第 6 项 - 虚拟机名称列），然后单击"添加"。</span><span class="sxs-lookup"><span data-stu-id="c0755-154">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="c0755-155">键入第二个 Web 应用程序代理服务器的名称（表 M - 第 7 项 - 虚拟机名称列），依次单击"添加"、"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-155">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="c0755-156">在"域管理员凭据"页上，键入域管理员帐户的用户名和密码，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-156">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="c0755-157">在"AD FS 服务帐户"页上，键入企业管理员帐户的用户名和密码，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-157">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="c0755-158">在"Azure AD 域"页的"域"中，选择组织的 DNS 域名，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="c0755-158">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="c0755-159">在"准备配置"页上，单击"安装"。</span><span class="sxs-lookup"><span data-stu-id="c0755-159">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="c0755-p105">在"安装完成"页上，单击"验证"。应该可以看到两条指明 Intranet 和 Internet 配置均已成功验证的消息。</span><span class="sxs-lookup"><span data-stu-id="c0755-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="c0755-162">Intranet 消息应为 AD FS 服务器列出 Azure 内部负载均衡器的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c0755-162">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="c0755-163">Internet 消息应为 Web 应用程序代理服务器列出面向 Internet 的 Azure 负载均衡器的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c0755-163">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="c0755-164">在"安装完成"页上，单击"退出"。</span><span class="sxs-lookup"><span data-stu-id="c0755-164">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="c0755-165">下面是服务器具有占位符名称的最终配置。</span><span class="sxs-lookup"><span data-stu-id="c0755-165">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="c0755-166">**阶段 5：Azure 中高可用性联合身份验证基础结构的最终配置**</span><span class="sxs-lookup"><span data-stu-id="c0755-166">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中的高可用性和联合Microsoft 365基础结构的最终配置](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="c0755-168">Azure 中适用于 azure Microsoft 365的高可用性联合身份验证基础结构已完成。</span><span class="sxs-lookup"><span data-stu-id="c0755-168">Your high availability federated authentication infrastructure for Microsoft 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c0755-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0755-169">See Also</span></span>

[<span data-ttu-id="c0755-170">在 Azure 中为 Microsoft 365 部署高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="c0755-170">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[<span data-ttu-id="c0755-171">用于开发/测试Microsoft 365联合标识</span><span class="sxs-lookup"><span data-stu-id="c0755-171">Federated identity for your Microsoft 365 dev/test environment</span></span>](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[<span data-ttu-id="c0755-172">Microsoft 365 解决方案和体系结构中心</span><span class="sxs-lookup"><span data-stu-id="c0755-172">Microsoft 365 solution and architecture center</span></span>](../solutions/index.yml)

[<span data-ttu-id="c0755-173">联合身份验证Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c0755-173">Federated identity for Microsoft 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)