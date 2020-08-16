---
title: 使用 PowerShell 连接 Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 使用 PowerShell for Microsoft 365 连接到 Microsoft 365 租户，从命令行执行管理中心任务。
ms.openlocfilehash: d1e347a13ca5c587fa544ef80a8e289a8dec0a59
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687940"
---
# <a name="connect-to-microsoft-365-with-powershell"></a><span data-ttu-id="0cd59-103">使用 PowerShell 连接 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0cd59-103">Connect to Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="0cd59-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="0cd59-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="0cd59-105">PowerShell for Microsoft 365 支持从命令行管理您的 Microsoft 365 设置。</span><span class="sxs-lookup"><span data-stu-id="0cd59-105">PowerShell for Microsoft 365 lets you manage your Microsoft 365 settings from the command line.</span></span> <span data-ttu-id="0cd59-106">连接到 PowerShell 是一个非常简单的过程：安装必需软件，然后连接到 Microsoft 365 组织。</span><span class="sxs-lookup"><span data-stu-id="0cd59-106">Connecting to PowerShell is a simple process where you install the required software and then connect to your Microsoft 365 organization.</span></span> 

<span data-ttu-id="0cd59-107">可以使用两种版本的 PowerShell 模块连接至 Microsoft 365 和管理员用户帐户、组和许可证：</span><span class="sxs-lookup"><span data-stu-id="0cd59-107">There are two versions of the PowerShell module that you use to connect to Microsoft 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="0cd59-108">Azure Active Directory PowerShell Graph（cmdlets 包括其名称中的 **AzureAD**）</span><span class="sxs-lookup"><span data-stu-id="0cd59-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="0cd59-109">用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块（cmdlets 包括其名称中的 **MSol**）</span><span class="sxs-lookup"><span data-stu-id="0cd59-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="0cd59-110">自本文发布之日起，对于用户、组和许可证管理，Azure Active Directory PowerShell Graph 模块不能完全替代用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块的 cmdlets 中的功能。</span><span class="sxs-lookup"><span data-stu-id="0cd59-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="0cd59-111">在某些情况下，需要同时使用两种版本。</span><span class="sxs-lookup"><span data-stu-id="0cd59-111">In some cases, you need to use both versions.</span></span> <span data-ttu-id="0cd59-112">可以在同一计算机上安全地安装两种版本。</span><span class="sxs-lookup"><span data-stu-id="0cd59-112">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="0cd59-113">开始前，需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="0cd59-113">What do you need to know before you begin?</span></span>

<span data-ttu-id="0cd59-114">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="0cd59-114">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="0cd59-115">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="0cd59-115">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="0cd59-116">Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="0cd59-116">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="0cd59-117">对于 Azure Active Directory PowerShell for Graph 模块，必须使用 PowerShell 版本 5.1 或以上版本。</span><span class="sxs-lookup"><span data-stu-id="0cd59-117">For the Azure Active Directory PowerShell for Graph module, you must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="0cd59-118">对于用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块，必须使用 PowerShell 版本 5.1 或以上版本（最高版本 6）。</span><span class="sxs-lookup"><span data-stu-id="0cd59-118">For the Microsoft Azure Active Directory Module for Windows PowerShell module, you must use PowerShell version 5.1 or later up to PowerShell version 6.</span></span> <span data-ttu-id="0cd59-119">你无法使用 PowerShell 版本 7。</span><span class="sxs-lookup"><span data-stu-id="0cd59-119">You cannot use PowerShell version 7.</span></span> <span data-ttu-id="0cd59-120">对于 Windows 8.1、Windows 8、Windows 7 Service Pack 1 (SP1)、Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2 SP1，请下载并安装 [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616)。</span><span class="sxs-lookup"><span data-stu-id="0cd59-120">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="0cd59-p104">请使用 64 位版 Windows。2014 年 10 月，用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块已不再支持 32 位版。</span><span class="sxs-lookup"><span data-stu-id="0cd59-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="0cd59-123">这些步骤适合于属于 Microsoft 365 管理员角色成员的用户。</span><span class="sxs-lookup"><span data-stu-id="0cd59-123">These procedures are intended for users who are members of a Microsoft 365 admin role.</span></span> <span data-ttu-id="0cd59-124">有关详细信息，请参阅[关于管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="0cd59-124">For more information, see [About admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="0cd59-125">连接到 Azure Active Directory PowerShell Graph 模块</span><span class="sxs-lookup"><span data-stu-id="0cd59-125">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="0cd59-126">Azure Active Directory PowerShell Graph 模块中的命令在其 cmdlet 名称中包含 **AzureAD**。</span><span class="sxs-lookup"><span data-stu-id="0cd59-126">Commands in the Azure Active Directory PowerShell for Graph module have **AzureAD** in their cmdlet name.</span></span> <span data-ttu-id="0cd59-127">可安装[Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 模块或 [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1)。</span><span class="sxs-lookup"><span data-stu-id="0cd59-127">You can install the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module or [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).</span></span>

<span data-ttu-id="0cd59-128">有关在 Azure Active Directory PowerShell Graph 模块中需要新 cmdlet 的过程，请使用以下步骤安装该模块并连接到 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="0cd59-128">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="0cd59-129">有关不同版本的 Microsoft Windows 的支持信息，请参阅 [Azure Active Directory PowerShell Graph 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。</span><span class="sxs-lookup"><span data-stu-id="0cd59-129">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="0cd59-130">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="0cd59-130">Step 1: Install required software</span></span>

<span data-ttu-id="0cd59-p107">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="0cd59-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="0cd59-133">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="0cd59-133">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="0cd59-134">在"管理员: Windows PowerShell"命令窗口中，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0cd59-134">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="0cd59-135">如果系统提示从不受信任的存储库安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="0cd59-135">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a><span data-ttu-id="0cd59-136">步骤 2：连接到 Microsoft 365 订阅的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="0cd59-136">Step 2: Connect to Azure AD for your Microsoft 365 subscription</span></span>

<span data-ttu-id="0cd59-137">若要使用帐户名称和密码或者多重身份验证 (MFA) 连接到 Microsoft 365 订阅的 Azure AD，请在 Windows PowerShell 命令提示符中运行这些命令之一（不必进行提升）。</span><span class="sxs-lookup"><span data-stu-id="0cd59-137">To connect to Azure AD for your Microsoft 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

| <span data-ttu-id="0cd59-138">Office 365 云</span><span class="sxs-lookup"><span data-stu-id="0cd59-138">Office 365 cloud</span></span> | <span data-ttu-id="0cd59-139">命令</span><span class="sxs-lookup"><span data-stu-id="0cd59-139">Command</span></span> |
|:-------|:-----|
| <span data-ttu-id="0cd59-140">Office 365 全球 (+GCC)</span><span class="sxs-lookup"><span data-stu-id="0cd59-140">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="0cd59-141">由世纪互联运营的 Office 365</span><span class="sxs-lookup"><span data-stu-id="0cd59-141">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="0cd59-142">Office 365 德国</span><span class="sxs-lookup"><span data-stu-id="0cd59-142">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="0cd59-143">Office 365 美国政府版 DoD 和 Office 365 美国政府版 GCC 高</span><span class="sxs-lookup"><span data-stu-id="0cd59-143">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="0cd59-144">在“**登录到你的帐户**”对话框中，键入 Microsoft 365 工作或学校帐户用户名和密码，再单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="0cd59-144">In the **Sign into your account** dialog box, type your Microsoft 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="0cd59-145">如果使用的是 MFA，请按照其他对话框中的说明提供更多身份验证信息，例如验证码。</span><span class="sxs-lookup"><span data-stu-id="0cd59-145">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="0cd59-146">连接后，可对 [Azure Active Directory PowerShell Graph 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0cd59-146">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="0cd59-147">与用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块连接</span><span class="sxs-lookup"><span data-stu-id="0cd59-147">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="0cd59-148">用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中的命令在其 cmdlet 名称中具有 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="0cd59-148">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

<span data-ttu-id="0cd59-149">PowerShell 版本 7 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="0cd59-149">PowerShell version 7 and later do not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0cd59-150">对于 PowerShell 版本 7 和更高版本，必须使用 Azure Active Directory PowerShell for Graph 模块或 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0cd59-150">For PowerShell version 7 and later, you must use the Azure Active Directory PowerShell for Graph module or Azure PowerShell.</span></span>

<span data-ttu-id="0cd59-151">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="0cd59-151">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0cd59-152">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="0cd59-152">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span> 
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="0cd59-153">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="0cd59-153">Step 1: Install required software</span></span>

<span data-ttu-id="0cd59-p110">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="0cd59-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="0cd59-156">如果您运行的不是 Windows 10，则请安装 64 位版 Microsoft Online Services 登录助手：[适用于 IT 专业人员 RTW 的 Microsoft Online Services 登录助手](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="0cd59-156">If you are not running Windows 10, install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="0cd59-157">安装用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，具体步骤如下：</span><span class="sxs-lookup"><span data-stu-id="0cd59-157">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="0cd59-158">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="0cd59-158">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="0cd59-159">运行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="0cd59-159">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="0cd59-160">如果系统提示安装 NuGet 提供程序，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="0cd59-160">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="0cd59-161">如果系统提示从 PSGallery 安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="0cd59-161">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a><span data-ttu-id="0cd59-162">步骤 2：连接到 Microsoft 365 订阅的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="0cd59-162">Step 2: Connect to Azure AD for your Microsoft 365 subscription</span></span>

<span data-ttu-id="0cd59-163">若要使用帐户名称和密码或者多重身份验证 (MFA) 连接到 Microsoft 365 订阅的 Azure AD，请在 Windows PowerShell 命令提示符中运行这些命令之一（不必进行提升）。</span><span class="sxs-lookup"><span data-stu-id="0cd59-163">To connect to Azure AD for your Microsoft 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

| <span data-ttu-id="0cd59-164">Office 365 云</span><span class="sxs-lookup"><span data-stu-id="0cd59-164">Office 365 cloud</span></span> | <span data-ttu-id="0cd59-165">命令</span><span class="sxs-lookup"><span data-stu-id="0cd59-165">Command</span></span> |
|:-------|:-----|
| <span data-ttu-id="0cd59-166">Office 365 全球 (+GCC)</span><span class="sxs-lookup"><span data-stu-id="0cd59-166">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="0cd59-167">由世纪互联运营的 Office 365</span><span class="sxs-lookup"><span data-stu-id="0cd59-167">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="0cd59-168">Office 365 德国</span><span class="sxs-lookup"><span data-stu-id="0cd59-168">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="0cd59-169">Office 365 美国政府版 DoD 和 Office 365 美国政府版 GCC 高</span><span class="sxs-lookup"><span data-stu-id="0cd59-169">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="0cd59-170">在“**登录到你的帐户**”对话框中，键入 Microsoft 365 工作或学校帐户用户名和密码，再单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="0cd59-170">In the **Sign into your account** dialog box, type your Microsoft 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="0cd59-171">如果使用的是 MFA，请按照其他对话框中的说明提供更多身份验证信息，例如验证码。</span><span class="sxs-lookup"><span data-stu-id="0cd59-171">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="0cd59-172">如何知道操作成功？</span><span class="sxs-lookup"><span data-stu-id="0cd59-172">How do you know this worked?</span></span>

<span data-ttu-id="0cd59-173">如果未收到任何错误，说明连接成功。</span><span class="sxs-lookup"><span data-stu-id="0cd59-173">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="0cd59-174">一个快速测试是运行 Microsoft 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="0cd59-174">A quick test is to run a Microsoft 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="0cd59-175">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="0cd59-175">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="0cd59-176">**常见问题是密码错误**。</span><span class="sxs-lookup"><span data-stu-id="0cd59-176">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="0cd59-177">重新运行步骤 2，</span><span class="sxs-lookup"><span data-stu-id="0cd59-177">Run Step 2 again.</span></span> <span data-ttu-id="0cd59-178">并仔细查看你输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="0cd59-178">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="0cd59-179">**用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块要求在计算机上启用 Microsoft .NET Framework 3.5.* x* 功能。很可能你的计算机已安装了较新的版本（例如 4 或 4.5.\* x\*），但可以启用或禁用与 .NET Framework 的早期版本的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="0cd59-179">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="0cd59-180">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="0cd59-180">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="0cd59-181">对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[使用“添加角色和功能”向导启用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="0cd59-181">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="0cd59-182">对于 Windows 7 或 Windows Server 2008 R2，请参阅[不能打开用于 Windows PowerShell 的 Azure Active Directory 模块](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="0cd59-182">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="0cd59-183">对于 Windows 10、Windows 8.1 和 Windows 8，请参阅[在 Windows 10、Windows 8.1 和 Windows 8 上安装 .NET Framework 3.5](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="0cd59-183">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="0cd59-184">**你的用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块版本可能已过期。**</span><span class="sxs-lookup"><span data-stu-id="0cd59-184">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.**</span></span> <span data-ttu-id="0cd59-185">若要进行检查，请在 PowerShell for Microsoft 365 或用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0cd59-185">To check, run the following command in PowerShell for Microsoft 365 or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="0cd59-186">如果返回的版本号低于值 1.0.8070.2，请卸载用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过上述第 1 步进行安装。</span><span class="sxs-lookup"><span data-stu-id="0cd59-186">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install from Step 1 above.</span></span>

- <span data-ttu-id="0cd59-187">**如果看到连接错误，请参阅以下主题：**[“Connect-MsolService：抛出类型异常”错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="0cd59-187">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
- <span data-ttu-id="0cd59-188">**如果收到“Get-Item：找不到路径”错误消息，请使用以下命令：**</span><span class="sxs-lookup"><span data-stu-id="0cd59-188">**If you receive a "Get-Item : Cannot find path" error, use this command:**</span></span> 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a><span data-ttu-id="0cd59-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cd59-189">See also</span></span>

- [<span data-ttu-id="0cd59-190">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0cd59-190">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
- [<span data-ttu-id="0cd59-191">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="0cd59-191">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)
- [<span data-ttu-id="0cd59-192">在单个 Windows PowerShell 窗口中连接所有 Microsoft 365 服务</span><span class="sxs-lookup"><span data-stu-id="0cd59-192">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
