---
title: 创建安全的来宾共享环境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-security-compliance
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- seo-marvel-apr2020
localization_priority: Priority
f1.keywords: NOCSH
description: 在本文中，你将了解在 Microsoft 365 中安全的客户共享环境的可用选项。
ms.openlocfilehash: 227c609329ae3cca4cc38e65984f1036bfe41068
ms.sourcegitcommit: 6501e01a9ab131205a3eef910e6cea7f65b3f010
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2020
ms.locfileid: "46527926"
---
# <a name="create-a-secure-guest-sharing-environment"></a><span data-ttu-id="c4e82-103">创建安全的来宾共享环境</span><span class="sxs-lookup"><span data-stu-id="c4e82-103">Create a secure guest sharing environment</span></span>

<span data-ttu-id="c4e82-104">在本文中，我们将介绍多种在 Microsoft 365 中创建安全来宾共享环境的选项。</span><span class="sxs-lookup"><span data-stu-id="c4e82-104">In this article, we'll walk through a variety of options for creating a secure guest sharing environment in Microsoft 365.</span></span> <span data-ttu-id="c4e82-105">这是一个示例方案，可让你大致了解可用选项。</span><span class="sxs-lookup"><span data-stu-id="c4e82-105">This is an example scenario to give you an idea of the options available.</span></span> <span data-ttu-id="c4e82-106">你可以在不同的组合中使用这些过程，以满足组织的安全性和合规性需求。</span><span class="sxs-lookup"><span data-stu-id="c4e82-106">You can use these procedures in different combinations to meet the security and compliance needs of your organization.</span></span> <span data-ttu-id="c4e82-107">在本文末尾，我们将演练一个测试案例，介绍其中的一些选项如何协同工作。</span><span class="sxs-lookup"><span data-stu-id="c4e82-107">At the end of the article, we'll walk through a test case to see how some of these options work together.</span></span>

<span data-ttu-id="c4e82-108">此方案包括：</span><span class="sxs-lookup"><span data-stu-id="c4e82-108">This scenario includes:</span></span>

- <span data-ttu-id="c4e82-109">为来宾设置多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="c4e82-109">Setting up multi-factor authentication for guests.</span></span>
- <span data-ttu-id="c4e82-110">设置来宾的使用条款。</span><span class="sxs-lookup"><span data-stu-id="c4e82-110">Setting up a terms of use for guests.</span></span>
- <span data-ttu-id="c4e82-111">设置每季度来宾访问评审，以定期验证来宾是否继续需要团队和站点的权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-111">Setting up quarterly guest access reviews to periodically validate whether guests continue to need permissions to teams and sites.</span></span>
- <span data-ttu-id="c4e82-112">限制来宾仅对非托管设备进行仅 Web 访问。</span><span class="sxs-lookup"><span data-stu-id="c4e82-112">Restricting guests to web-only access for unmanaged devices.</span></span>
- <span data-ttu-id="c4e82-113">配置会话超时策略，确保来宾每天进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c4e82-113">Configuring a session timeout policy to ensure guests authenticate daily.</span></span>
- <span data-ttu-id="c4e82-114">创建和发布敏感度标签以对内容进行分类。</span><span class="sxs-lookup"><span data-stu-id="c4e82-114">Creating and publishing sensitivity labels to classify content.</span></span>
- <span data-ttu-id="c4e82-115">为高度敏感的项目创建敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="c4e82-115">Creating a sensitive information type for a highly sensitive project.</span></span>
- <span data-ttu-id="c4e82-116">自动为包含敏感信息类型的文档分配“*高度敏感*”标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-116">Automatically assigning a *highly sensitive* label to documents that contain the sensitive information type.</span></span>
- <span data-ttu-id="c4e82-117">自动从标记为“*高度敏感*”的文件中删除来宾访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-117">Automatically removing guest access from files labeled as *highly sensitive*.</span></span>

<span data-ttu-id="c4e82-118">本文中所述的某些选项要求来宾在 Azure Active Directory 中具有帐户。</span><span class="sxs-lookup"><span data-stu-id="c4e82-118">Some of the options discussed in this article require guests to have an account in Azure Active Directory.</span></span> <span data-ttu-id="c4e82-119">若要确保在与来宾共享文件和文件夹时在目录中包含这些来宾，请使用[与 Azure AD B2B 预览版的 SharePoint 和 OneDrive 集成](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)。</span><span class="sxs-lookup"><span data-stu-id="c4e82-119">To ensure that guests are included in the directory when you share files and folders with them, use the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).</span></span>

<span data-ttu-id="c4e82-120">请注意，我们不在本文中讨论如何启用来宾共享设置。</span><span class="sxs-lookup"><span data-stu-id="c4e82-120">Note that we won't discuss enabling guest sharing settings in this article.</span></span> <span data-ttu-id="c4e82-121">有关为不同方案启用来宾共享的详细信息，请参阅[与组织外部人员进行协作](collaborate-with-people-outside-your-organization.md)。</span><span class="sxs-lookup"><span data-stu-id="c4e82-121">See [Collaborating with people outside your organization](collaborate-with-people-outside-your-organization.md) for details about enabling guest sharing for different scenarios.</span></span>

## <a name="set-up-multi-factor-authentication-for-guests"></a><span data-ttu-id="c4e82-122">为来宾设置多重身份验证</span><span class="sxs-lookup"><span data-stu-id="c4e82-122">Set up multi-factor authentication for guests</span></span>

<span data-ttu-id="c4e82-123">多重身份验证可显著降低帐户被盗的机率。</span><span class="sxs-lookup"><span data-stu-id="c4e82-123">Multi-factor authentication greatly reduces the chances of an account being compromised.</span></span> <span data-ttu-id="c4e82-124">由于来宾用户对个人电子邮件帐户的使用可能不符合任何管理策略或最佳做法，因此要求对来宾进行多重身份验证尤为重要。</span><span class="sxs-lookup"><span data-stu-id="c4e82-124">Since guest users may be using personal email accounts that don't adhere to any governance policies or best practices, it's especially important to require multi-factor authentication for guests.</span></span> <span data-ttu-id="c4e82-125">如果来宾用户的用户名和密码被盗，则要求进行双重身份验证可显著降低未知方获得对网站和文件的访问权限的机率。</span><span class="sxs-lookup"><span data-stu-id="c4e82-125">If a guest user's username and password is stolen, requiring a second factor of authentication greatly reduces the chances of unknown parties gaining access to your sites and files.</span></span>

<span data-ttu-id="c4e82-126">在此示例中，我们将使用 Azure Active Directory 中的条件访问策略为来宾设置多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="c4e82-126">In this example, we'll set up multi-factor authentication for guests by using a conditional access policy in Azure Active Directory.</span></span>

<span data-ttu-id="c4e82-127">为来宾设置多重身份验证</span><span class="sxs-lookup"><span data-stu-id="c4e82-127">To set up multi-factor authentication for guests</span></span>
1. <span data-ttu-id="c4e82-128">在 Microsoft Azure 中，搜索“*条件访问*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-128">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="c4e82-129">在“**条件访问 - 策略**”边栏选项卡上，单击“**新建策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-129">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="c4e82-130">在“**名称**”字段中，键入“*来宾 MFA*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-130">In the **Name** field, type *Guest MFA*.</span></span>
4. <span data-ttu-id="c4e82-131">在“**分配**”下，单击“**用户和组**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-131">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="c4e82-132">在“**用户和组**”边栏选项卡上，选择“**选择用户和组**”，然后选中“**所有来宾和外部用户**”复选框。</span><span class="sxs-lookup"><span data-stu-id="c4e82-132">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box.</span></span>
6. <span data-ttu-id="c4e82-133">在“**分配**”下，单击“**云应用或操作**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-133">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="c4e82-134">在“**云应用或操作**”边栏选项卡中，选择“**包含**”选项卡上的“**所有云应用**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-134">On the **Cloud apps or actions** blade, select **All cloud apps** on the **Include** tab.</span></span>
8. <span data-ttu-id="c4e82-135">在“**访问控制**”下，单击“**授予**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-135">Under **Access controls**, click **Grant**.</span></span>
9. <span data-ttu-id="c4e82-136">在“**授予**”边栏选项卡上，选中“**要求多重身份验证**”复选框，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-136">On the **Grant** blade, select the **Require multi-factor authentication** check box, and then click **Select**.</span></span>
10. <span data-ttu-id="c4e82-137">在“**新建**”边栏选项卡中的“**启用策略**”下面，单击“**打开**”，然后单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-137">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

<span data-ttu-id="c4e82-138">现在，来宾需要在多重身份验证中进行注册，然后才能访问共享内容、网站或团队。</span><span class="sxs-lookup"><span data-stu-id="c4e82-138">Now, guest will be required to enroll in multi-factor authentication before they can access shared content, sites, or teams.</span></span>

### <a name="more-information"></a><span data-ttu-id="c4e82-139">更多信息</span><span class="sxs-lookup"><span data-stu-id="c4e82-139">More information</span></span>

[<span data-ttu-id="c4e82-140">规划基于云的 Azure 多重身份验证部署</span><span class="sxs-lookup"><span data-stu-id="c4e82-140">Planning a cloud-based Azure Multi-Factor Authentication deployment</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a><span data-ttu-id="c4e82-141">设置来宾的使用条款</span><span class="sxs-lookup"><span data-stu-id="c4e82-141">Set up a terms of use for guests</span></span>

<span data-ttu-id="c4e82-142">通常，来宾用户可能未与贵组织签署保密协议或其他法律协议。</span><span class="sxs-lookup"><span data-stu-id="c4e82-142">Often times guest users may not have signed non-disclosure agreements or other legal agreements with your organization.</span></span> <span data-ttu-id="c4e82-143">你可以要求来宾在访问与之共享的文件之前同意使用条款。</span><span class="sxs-lookup"><span data-stu-id="c4e82-143">You can require guests to agree to a terms of use before accessing files that are shared with them.</span></span> <span data-ttu-id="c4e82-144">可在他们首次尝试访问共享文件或网站时显示使用条款。</span><span class="sxs-lookup"><span data-stu-id="c4e82-144">The terms of use can be displayed the first time they attempt to access a shared file or site.</span></span>

<span data-ttu-id="c4e82-145">若要创建使用条款，首先需要在 Word 或其他创作程序中创建文档，然后将其另存为 pdf 文件。</span><span class="sxs-lookup"><span data-stu-id="c4e82-145">To create a terms of use, you first need to create the document in Word or another authoring program, and then save it as a .pdf file.</span></span> <span data-ttu-id="c4e82-146">然后，可将该文件上传到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="c4e82-146">This file can then be uploaded to Azure AD.</span></span>

<span data-ttu-id="c4e82-147">创建 Azure AD 使用条款</span><span class="sxs-lookup"><span data-stu-id="c4e82-147">To create an Azure AD terms of use</span></span>
1. <span data-ttu-id="c4e82-148">以全局管理员、安全管理员或条件访问管理员的身份登录到 Azure。</span><span class="sxs-lookup"><span data-stu-id="c4e82-148">Sign in to Azure as a Global Administrator, Security Administrator, or Conditional Access Administrator.</span></span>
2. <span data-ttu-id="c4e82-149">导航到“[使用条款](https://aka.ms/catou)”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-149">Navigate to [Terms of use](https://aka.ms/catou).</span></span>
3. <span data-ttu-id="c4e82-150">单击“**新建条款**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-150">Click **New terms**.</span></span></br>
   <span data-ttu-id="c4e82-151">![Azure AD 新使用条款设置的屏幕截图](../media/azure-ad-guest-terms-of-use.png)</span><span class="sxs-lookup"><span data-stu-id="c4e82-151">![Screenshot of Azure AD new terms of use settings](../media/azure-ad-guest-terms-of-use.png)</span></span>
4. <span data-ttu-id="c4e82-152">在“**名称**”和“**显示名称**”框中，键入“*来宾使用条款*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-152">In the **Name** and **Display name** boxes, type *Guest terms of use*.</span></span>
6. <span data-ttu-id="c4e82-153">对于“**使用条款文档**”，浏览至你创建的 pdf 文件并选择它。</span><span class="sxs-lookup"><span data-stu-id="c4e82-153">For **Terms of use document**, browse to the pdf file that you created and select it.</span></span>
7. <span data-ttu-id="c4e82-154">选择使用条款文档的语言。</span><span class="sxs-lookup"><span data-stu-id="c4e82-154">Select the language for your terms of use document.</span></span>
8. <span data-ttu-id="c4e82-155">将“**要求用户展开使用条款**”设置为“**打开**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-155">Set **Require users to expand the terms of use** to **On**.</span></span>
9. <span data-ttu-id="c4e82-156">在“**条件访问**”下的“**强制实施条件访问策略模板**”列表中，选择“**稍后创建条件访问策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-156">Under **Conditional Access**, in the **Enforce with Conditional Access policy template** list choose **Create conditional access policy later**.</span></span>
10. <span data-ttu-id="c4e82-157">单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-157">Click **Create**.</span></span>

<span data-ttu-id="c4e82-158">创建使用条款后，下一步是创建用于显示来宾用户的使用条款的条件访问策略。</span><span class="sxs-lookup"><span data-stu-id="c4e82-158">Once you've created the terms of use, the next step is to create a conditional access policy that displays the terms of use to guest users.</span></span>

<span data-ttu-id="c4e82-159">创建条件访问策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-159">To create a conditional access policy</span></span>
1. <span data-ttu-id="c4e82-160">在 Microsoft Azure 中，搜索“*条件访问*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-160">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="c4e82-161">在“**条件访问 - 策略**”边栏选项卡上，单击“**新建策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-161">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="c4e82-162">在“**名称**”框中，键入“*来宾用户使用条款策略*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-162">In the **Name** box, type *Guest user terms of use policy*.</span></span>
4. <span data-ttu-id="c4e82-163">在“**分配**”下，单击“**用户和组**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-163">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="c4e82-164">在“**用户和组**”边栏选项卡上，选择“**选择用户和组**”，选中“**所有来宾和外部用户**”复选框，然后单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-164">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="c4e82-165">在“**分配**”下，单击“**云应用或操作**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-165">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="c4e82-166">在“**包括**”选项卡上，选择“**选择应用**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-166">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="c4e82-167">在“**选择**”边栏选项卡上，选择“**Microsoft Teams**”、“**Office 365 SharePoint Online**”和“**Outlook Groups**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-167">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="c4e82-168">在“**云应用或操作**”边栏选项卡上，单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-168">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="c4e82-169">在“**访问控制**”下，单击“**授予**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-169">Under **Access controls**, click **Grant**.</span></span>
11. <span data-ttu-id="c4e82-170">在“**授予**”边栏选项卡上，选择“**来宾使用条款**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-170">On the **Grant** blade, select **Guest terms of use**, and then click **Select**.</span></span>
12. <span data-ttu-id="c4e82-171">在“**新建**”边栏选项卡中的“**启用策略**”下面，单击“**打开**”，然后单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-171">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

<span data-ttu-id="c4e82-172">现在，当来宾用户首次尝试访问组织中的内容、团队或网站时，必须接受使用条款。</span><span class="sxs-lookup"><span data-stu-id="c4e82-172">Now, the first time a guest user attempts to access content or a team or site in your organization, they will be required to accept the terms of use.</span></span>

> [!NOTE]
> <span data-ttu-id="c4e82-173">使用条件访问需要 Azure AD Premium P1 许可证。</span><span class="sxs-lookup"><span data-stu-id="c4e82-173">Using Conditional Access requires an Azure AD Premium P1 license.</span></span> <span data-ttu-id="c4e82-174">有关详细信息，请参阅[什么是条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)。</span><span class="sxs-lookup"><span data-stu-id="c4e82-174">For more information, see [What is Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).</span></span>

### <a name="more-information"></a><span data-ttu-id="c4e82-175">更多信息</span><span class="sxs-lookup"><span data-stu-id="c4e82-175">More information</span></span>
[<span data-ttu-id="c4e82-176">Azure Active Directory 使用条款</span><span class="sxs-lookup"><span data-stu-id="c4e82-176">Azure Active Directory terms of use</span></span>](https://docs.microsoft.com/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a><span data-ttu-id="c4e82-177">设置来宾访问评审</span><span class="sxs-lookup"><span data-stu-id="c4e82-177">Set up guest access reviews</span></span>

<span data-ttu-id="c4e82-178">借助 Azure AD 中的访问评审功能，可以自动定期评审用户对各个团队和组的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-178">With access reviews in Azure AD, you can automate a periodic review of user access to various teams and groups.</span></span> <span data-ttu-id="c4e82-179">通过特别要求对来宾进行访问评审，可帮助确保来宾用户在规定时间内拥有对组织敏感信息的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-179">By requiring an access review for guests specifically, you can help ensure guest users do not retain access to your organization's sensitive information for longer than is necessary.</span></span>

<span data-ttu-id="c4e82-180">访问评审可以组织成计划。</span><span class="sxs-lookup"><span data-stu-id="c4e82-180">Access reviews can be organized into programs.</span></span> <span data-ttu-id="c4e82-181">计划是一组类似的访问评审，可用于组织访问评审以进行报告和审核。</span><span class="sxs-lookup"><span data-stu-id="c4e82-181">A program is a grouping of similar access reviews that can be used to organize access reviews for reporting and auditing purposes.</span></span>

<span data-ttu-id="c4e82-182">在此示例中，我们将创建一个用于来宾访问评审的计划。</span><span class="sxs-lookup"><span data-stu-id="c4e82-182">In this example, we'll create a program for guest access reviews.</span></span>

<span data-ttu-id="c4e82-183">创建计划</span><span class="sxs-lookup"><span data-stu-id="c4e82-183">To create a program</span></span>
1. <span data-ttu-id="c4e82-184">登录到 Azure 门户并打开 [Identity Governance](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) 页面。</span><span class="sxs-lookup"><span data-stu-id="c4e82-184">Sign in to the Azure portal and open the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade).</span></span>
2. <span data-ttu-id="c4e82-185">在左侧菜单中，单击“**计划**”</span><span class="sxs-lookup"><span data-stu-id="c4e82-185">In the left menu, click **Programs**</span></span>
3. <span data-ttu-id="c4e82-186">单击“**新建计划**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-186">Click **New program**.</span></span>
4. <span data-ttu-id="c4e82-187">在“**名称**”框中，键入“*来宾访问评审计划*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-187">In the **Name** box, type *Guest access review program*.</span></span>
5. <span data-ttu-id="c4e82-188">在“**说明**”框中，键入“*来宾访问评审的计划*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-188">In the **Description** box, type *Program for guest access reviews*.</span></span>
6. <span data-ttu-id="c4e82-189">单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-189">Click **Create**.</span></span>

<span data-ttu-id="c4e82-190">创建计划后，即可创建来宾访问评审并将其与计划关联。</span><span class="sxs-lookup"><span data-stu-id="c4e82-190">Once the program has been created, we can create a guest access review and associate it with the program.</span></span>

<span data-ttu-id="c4e82-191">设置来宾用户访问评审</span><span class="sxs-lookup"><span data-stu-id="c4e82-191">To set up a guest user access review</span></span>
1. <span data-ttu-id="c4e82-192">在 [Identity Governance](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) 页面上的左侧菜单中，单击“**访问评审**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-192">On the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade), in the left menu, click **Access reviews**.</span></span>
2. <span data-ttu-id="c4e82-193">单击“**新建访问评审**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-193">Click **New access review**.</span></span></br>
   <span data-ttu-id="c4e82-194">![Azure AD 访问评审设置的屏幕截图](../media/azure-ad-create-access-review.png)</span><span class="sxs-lookup"><span data-stu-id="c4e82-194">![Screenshot of Azure AD access review settings](../media/azure-ad-create-access-review.png)</span></span>
3. <span data-ttu-id="c4e82-195">在“**名称**”框中，键入“*每季度来宾访问评审*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-195">In the **Name** box, type *Quarterly guest access review*.</span></span>
4. <span data-ttu-id="c4e82-196">对于“**频率**”，选择“**每季度**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-196">For **Frequency**, choose **Quarterly**.</span></span>
5. <span data-ttu-id="c4e82-197">对于“**结束**”，选择“**从不**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-197">For **End**, choose **Never**.</span></span>
6. <span data-ttu-id="c4e82-198">对于“**范围**”，选择“**仅限来宾用户**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-198">For **Scope**, choose **Guest users only**.</span></span>
7. <span data-ttu-id="c4e82-199">单击“**组**”，选择要包括在访问评审中的组，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-199">Click **Group**, select the groups that you want to include in the access review, and then click **Select**.</span></span>
8. <span data-ttu-id="c4e82-200">在“**计划**”下，单击“**链接到计划**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-200">Under **Programs**, click **Link to program**.</span></span>
9. <span data-ttu-id="c4e82-201">在“**选择计划**”边栏选项卡上，选择“**来宾访问评审计划**”</span><span class="sxs-lookup"><span data-stu-id="c4e82-201">On the **Select a program** blade, choose **Guest access review program**</span></span>
10. <span data-ttu-id="c4e82-202">单击“**开始**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-202">Click **Start**.</span></span>

<span data-ttu-id="c4e82-203">将为你指定的每个组创建一个单独的访问评审。</span><span class="sxs-lookup"><span data-stu-id="c4e82-203">A separate access review is created for each group that you specify.</span></span> <span data-ttu-id="c4e82-204">每个组的组所有者将在每季度收到一封电子邮件，用于批准或拒绝来宾访问其组。</span><span class="sxs-lookup"><span data-stu-id="c4e82-204">Group owners of each groups will be emailed quarterly to approve or deny guest access to their groups.</span></span>

<span data-ttu-id="c4e82-205">请务必注意，可以向来宾授予对团队或组的访问权限，也可以授予对各个文件和文件夹的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-205">It's important to note that guests can be given access to teams or groups, or to individual files and folders.</span></span> <span data-ttu-id="c4e82-206">授予对文件和文件夹的访问权限时，可能不会将来宾添加到任何特定组。</span><span class="sxs-lookup"><span data-stu-id="c4e82-206">When given access to files and folders, guests may not be added to any particular group.</span></span> <span data-ttu-id="c4e82-207">如果想要对不属于团队或组的来宾用户执行访问评审，可在 Azure AD 中创建一个动态组，以包含所有来宾并为该组创建访问评审。</span><span class="sxs-lookup"><span data-stu-id="c4e82-207">If you want to do access reviews on guest users who don't belong to a team or group, you can create a dynamic group in Azure AD to contain all guests and then create an access review for that group.</span></span>

### <a name="more-information"></a><span data-ttu-id="c4e82-208">更多信息</span><span class="sxs-lookup"><span data-stu-id="c4e82-208">More information</span></span>
[<span data-ttu-id="c4e82-209">使用 Azure AD 访问评审管理来宾访问权限</span><span class="sxs-lookup"><span data-stu-id="c4e82-209">Manage guest access with Azure AD access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[<span data-ttu-id="c4e82-210">在 Azure AD 访问评审中针对组或应用程序创建访问评审</span><span class="sxs-lookup"><span data-stu-id="c4e82-210">Create an access review of groups or applications in Azure AD access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guest-users"></a><span data-ttu-id="c4e82-211">为来宾用户设置仅 Web 访问权限</span><span class="sxs-lookup"><span data-stu-id="c4e82-211">Set up web-only access for guest users</span></span>

<span data-ttu-id="c4e82-212">通过要求来宾用户仅使用 Web 浏览器来访问团队、网站和文件，可以减少攻击面并简化管理。</span><span class="sxs-lookup"><span data-stu-id="c4e82-212">You can reduce your attack surface and ease administration by requiring guest users to access your teams, sites, and files by using a web browser only.</span></span> <span data-ttu-id="c4e82-213">这是通过 Azure AD 条件访问策略完成的。</span><span class="sxs-lookup"><span data-stu-id="c4e82-213">This is done with an Azure AD conditional access policy.</span></span>

<span data-ttu-id="c4e82-214">限制来宾进行仅 Web 访问</span><span class="sxs-lookup"><span data-stu-id="c4e82-214">To restrict guests to web-ony access</span></span>
1. <span data-ttu-id="c4e82-215">在 Microsoft Azure 中，搜索“*条件访问*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-215">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="c4e82-216">在“**条件访问 - 策略**”边栏选项卡上，单击“**新建策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-216">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="c4e82-217">在“**名称**”框中，键入“*来宾用户浏览器访问*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-217">In the **Name** box, type *Guest user browser access*.</span></span>
4. <span data-ttu-id="c4e82-218">在“**分配**”下，单击“**用户和组**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-218">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="c4e82-219">在“**用户和组**”边栏选项卡上，选择“**选择用户和组**”，选中“**所有来宾和外部用户**”复选框，然后单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-219">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="c4e82-220">在“**分配**”下，单击“**云应用或操作**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-220">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="c4e82-221">在“**包括**”选项卡上，选择“**选择应用**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-221">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="c4e82-222">在“**选择**”边栏选项卡上，选择“**Microsoft Teams**”、“**Office 365 SharePoint Online**”和“**Outlook Groups**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-222">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="c4e82-223">在“**云应用或操作**”边栏选项卡上，单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-223">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="c4e82-224">在“**分配**”下，单击“**条件**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-224">Under **Assignments**, click **Conditions**.</span></span>
11. <span data-ttu-id="c4e82-225">在“**条件**”边栏选项卡上，单击“**客户端应用**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-225">On the **Conditions** blade, click **Client apps**.</span></span>
12. <span data-ttu-id="c4e82-226">在“**客户端应用**”边栏选项卡上，为“**配置**”单击“**是**”，然后选择“**移动应用和桌面客户端**”和“**新式身份验证客户端**”设置。</span><span class="sxs-lookup"><span data-stu-id="c4e82-226">On the **Client apps** blade, click **Yes** for **Configure**, and then select the **Mobile apps and desktop clients** and **Modern authentication clients** settings.</span></span></br>
    <span data-ttu-id="c4e82-227">![Azure AD 条件访问客户端应用设置的屏幕截图](../media/azure-ad-conditional-access-client-mobile.png)</span><span class="sxs-lookup"><span data-stu-id="c4e82-227">![Screenshot of Azure AD conditional access client apps settings](../media/azure-ad-conditional-access-client-mobile.png)</span></span>
13. <span data-ttu-id="c4e82-228">单击“**完成**”，然后在“**条件**”边栏选项卡上，再次单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-228">Click **Done**, and then on the **Conditions** blade, click **Done** again.</span></span>
14. <span data-ttu-id="c4e82-229">在“**访问控制**”下，单击“**授予**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-229">Under **Access controls**, click **Grant**.</span></span>
15. <span data-ttu-id="c4e82-230">在“**授予**”边栏选项卡上，选择“**需要标记为兼容的设备**”和“**需要加入混合 Azure AD 的设备**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-230">On the **Grant** blade, select **Require device to be marked as compliant** and **Require Hybrid Azure AD joined device**.</span></span>
16. <span data-ttu-id="c4e82-231">在“**对于多个控件**”，选择“**需要某一已选控件**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-231">Under **For multiple controls**, select **Require one of the selected controls**, and then click **Select**.</span></span>
17. <span data-ttu-id="c4e82-232">在“**新建**”边栏选项卡中的“**启用策略**”下面，单击“**打开**”，然后单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-232">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

## <a name="configure-a-session-timeout-for-guest-users"></a><span data-ttu-id="c4e82-233">为来宾用户配置会话超时</span><span class="sxs-lookup"><span data-stu-id="c4e82-233">Configure a session timeout for guest users</span></span>

<span data-ttu-id="c4e82-234">如果来宾用户的设备不安全，则定期要求来宾进行身份验证可以降低未知用户访问组织内容的可能性。</span><span class="sxs-lookup"><span data-stu-id="c4e82-234">Requiring guests to authenticate on a regular basis can reduce the possibility of unknown users accessing your organization's content if a guest user's device isn't kept secure.</span></span> <span data-ttu-id="c4e82-235">可以在 Azure AD 中为来宾用户配置会话超时条件访问策略。</span><span class="sxs-lookup"><span data-stu-id="c4e82-235">You can configure a session timeout conditional access policy for guest users in Azure AD.</span></span>

<span data-ttu-id="c4e82-236">配置来宾会话超时策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-236">To configure a guest session timeout policy</span></span>
1. <span data-ttu-id="c4e82-237">在 Microsoft Azure 中，搜索“*条件访问*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-237">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="c4e82-238">在“**条件访问 - 策略**”边栏选项卡上，单击“**新建策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-238">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="c4e82-239">在“**名称**”框中，键入“*来宾会话超时*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-239">In the **Name** box, type *Guest session timeout*.</span></span>
4. <span data-ttu-id="c4e82-240">在“**分配**”下，单击“**用户和组**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-240">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="c4e82-241">在“**用户和组**”边栏选项卡上，选择“**选择用户和组**”，选中“**所有来宾和外部用户**”复选框，然后单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-241">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="c4e82-242">在“**分配**”下，单击“**云应用或操作**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-242">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="c4e82-243">在“**包括**”选项卡上，选择“**选择应用**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-243">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="c4e82-244">在“**选择**”边栏选项卡上，选择“**Microsoft Teams**”、“**Office 365 SharePoint Online**”和“**Outlook Groups**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-244">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="c4e82-245">在“**云应用或操作**”边栏选项卡上，单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-245">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="c4e82-246">在“**访问控制**”下，单击“**会话**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-246">Under **Access controls**, click **Session**.</span></span>
11. <span data-ttu-id="c4e82-247">在“**会话**”边栏选项卡上，选择“**登录频率**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-247">On the **Session** blade, select **Sign-in frequency**.</span></span>
12. <span data-ttu-id="c4e82-248">为时间段选择 **1** 和“**天**”，然后单击“**选择**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-248">Select **1** and **Days** for the time period, and then click **Select**.</span></span>
13. <span data-ttu-id="c4e82-249">在“**新建**”边栏选项卡中的“**启用策略**”下面，单击“**打开**”，然后单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-249">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

## <a name="create-sensitivity-labels"></a><span data-ttu-id="c4e82-250">创建敏感度标签</span><span class="sxs-lookup"><span data-stu-id="c4e82-250">Create sensitivity labels</span></span>

<span data-ttu-id="c4e82-251">可通过多种方式使用敏感度标签来分类和保护组织的信息。</span><span class="sxs-lookup"><span data-stu-id="c4e82-251">Sensitivity labels can be used in a variety of ways to classify and protect your organization's information.</span></span> <span data-ttu-id="c4e82-252">在此示例中，我们将介绍如何使用标签来帮助管理来宾对共享文件和文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="c4e82-252">In this example, we'll look at how labels can be used to help you manage guest access to shared files and folders.</span></span>

<span data-ttu-id="c4e82-253">首先，我们将在 Microsoft 365 合规中心创建三个敏感度标签：</span><span class="sxs-lookup"><span data-stu-id="c4e82-253">First, we'll create three sensitivity labels in the Microsoft 365 Compliance Center:</span></span>

- <span data-ttu-id="c4e82-254">常规</span><span class="sxs-lookup"><span data-stu-id="c4e82-254">General</span></span>
- <span data-ttu-id="c4e82-255">敏感</span><span class="sxs-lookup"><span data-stu-id="c4e82-255">sensitive</span></span>
- <span data-ttu-id="c4e82-256">高度敏感</span><span class="sxs-lookup"><span data-stu-id="c4e82-256">Highly sensitive</span></span>

<span data-ttu-id="c4e82-257">请按下列步骤创建“*常规*”和“*敏感*”标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-257">Use the following procedure to create the *General* and *sensitive* labels.</span></span>

<span data-ttu-id="c4e82-258">创建分类标签（常规和敏感）</span><span class="sxs-lookup"><span data-stu-id="c4e82-258">To create a classification label (General and sensitive)</span></span>
1. <span data-ttu-id="c4e82-259">在 [Microsoft 365 合规中心](https://compliance.microsoft.com)的左侧导航中，展开“**分类**”，然后单击“**敏感度标签**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-259">In the [Microsoft 365 Compliance Center](https://compliance.microsoft.com), in the left navigation, expand **Classification**, and then click **Sensitivity labels**.</span></span>
2. <span data-ttu-id="c4e82-260">单击“**创建标签**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-260">Click **Create a label**.</span></span>
3. <span data-ttu-id="c4e82-261">在“**标签名称**”中，键入“*常规*”或“*敏感*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-261">In **Label name**, type *General* or *sensitive*.</span></span>
4. <span data-ttu-id="c4e82-262">在“**工具提示**”中，键入“*可与员工、来宾和合作伙伴共享的常规信息*”或“*仅与员工和授权来宾共享的敏感信息*”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-262">In **Tooltip**, type *General information that can be shared with employees, guests, and partners* or *sensitive information. Share only with employees and authorized guests*, and then click **Next**.</span></span>
5. <span data-ttu-id="c4e82-263">让加密保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-263">Leave encryption **Off** and click **Next**.</span></span>
6. <span data-ttu-id="c4e82-264">让内容标记保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-264">Leave content marking **Off** and click **Next**.</span></span>
7. <span data-ttu-id="c4e82-265">让终结点数据丢失防护保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-265">Leave endpoint data loss prevention **Off** and click **Next**.</span></span>
8. <span data-ttu-id="c4e82-266">让自动标记保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-266">Leave auto labeling **Off** and click **Next**.</span></span>
9. <span data-ttu-id="c4e82-267">单击“创建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4e82-267">Click **Create**.</span></span>

<span data-ttu-id="c4e82-268">使用“*高度敏感*”标签，为带有标签的文档自动添加水印。</span><span class="sxs-lookup"><span data-stu-id="c4e82-268">With the *Highly sensitive* label, we'll add automatic watermarking of documents with the label.</span></span>

<span data-ttu-id="c4e82-269">创建分类标签（高度敏感）</span><span class="sxs-lookup"><span data-stu-id="c4e82-269">To create a classification label (Highly sensitive)</span></span>
1. <span data-ttu-id="c4e82-270">单击“**创建标签**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-270">Click **Create a label**.</span></span>
2. <span data-ttu-id="c4e82-271">在“**标签名称**”中，键入“*高度敏感*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-271">In **Label name**, type *Highly sensitive*.</span></span>
3. <span data-ttu-id="c4e82-272">在“**工具提示**”中，键入“*高度敏感信息。不要与来宾共享*”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-272">In **Tooltip**, type *Highly sensitive information. Do not share with guests*, and then click **Next**.</span></span>
4. <span data-ttu-id="c4e82-273">让加密保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-273">Leave encryption **Off** and click **Next**.</span></span>
5. <span data-ttu-id="c4e82-274">将内容标记设为“**打开**”，选中“**添加页眉**”复选框，然后单击“**自定义文本**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-274">Turn content marking **On**, select the **Add a header** check box, and then click **Customize text**.</span></span>
6. <span data-ttu-id="c4e82-275">为页眉文本键入“*高度敏感*”，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-275">Type *Highly sensitive* for the header text and click **Save**.</span></span>
7. <span data-ttu-id="c4e82-276">在“**内容标记**”页面上，将内容标记设为“**打开**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-276">On the **Content marking** page, turn content marking **On**.</span></span>
8. <span data-ttu-id="c4e82-277">选中“**添加水印**”复选框，然后单击“**自定义文本**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-277">Select the **Add a watermark** check box, and then click **Customize text**.</span></span>
9. <span data-ttu-id="c4e82-278">对于“**水印文本**”，请键入“*高度敏感*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-278">For **Watermark text**, type *Highly sensitive*.</span></span>
10. <span data-ttu-id="c4e82-279">为“**字号**”键入 *24*，然后单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-279">Type *24* for **Font size**, and then click **Save**.</span></span>
11. <span data-ttu-id="c4e82-280">在“**内容标记**”页面上，单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-280">On the **Content marking** page, click **Next**.</span></span>
12. <span data-ttu-id="c4e82-281">让终结点数据丢失防护保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-281">Leave endpoint data loss prevention **Off** and click **Next**.</span></span>
13. <span data-ttu-id="c4e82-282">让自动标记保持“**关闭**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-282">Leave auto labeling **Off** and click **Next**.</span></span>
14. <span data-ttu-id="c4e82-283">单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-283">Click **Create**.</span></span>

![Microsoft 365 合规中心内的敏感度标签的屏幕截图](../media/microsoft-365-sharing-sensitivity-labels.png)

<span data-ttu-id="c4e82-285">创建标签后，下一步是发布它们。</span><span class="sxs-lookup"><span data-stu-id="c4e82-285">Once you've created the labels, the next step is to publish them.</span></span> 

<span data-ttu-id="c4e82-286">发布标签</span><span class="sxs-lookup"><span data-stu-id="c4e82-286">To publish labels</span></span>
1. <span data-ttu-id="c4e82-287">在“**敏感度标签**”页面上，单击“**发布标签**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-287">On the **Sensitivity labels** page, click **Publish labels**.</span></span>
2. <span data-ttu-id="c4e82-288">单击“**选择要发布的标签**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-288">Click **Choose labels to publish**.</span></span>
3. <span data-ttu-id="c4e82-289">单击“**添加**”，选择创建的标签，然后单击“**添加**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-289">Click **Add**, select the labels that you created, and then click **Add**.</span></span>
4. <span data-ttu-id="c4e82-290">单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-290">Click **Done**.</span></span>
5. <span data-ttu-id="c4e82-291">单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-291">Click **Next**.</span></span>
6. <span data-ttu-id="c4e82-292">将用户和组设置保留为“**全部**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-292">Leave the users and groups set to **All** and click **Next**.</span></span>
7. <span data-ttu-id="c4e82-293">在“**默认将此标签应用于文档和电子邮件**”列表中，选择“**常规**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-293">In the **Apply this label by default to documents and email** list, choose **General**, and then click **Next**.</span></span>
8. <span data-ttu-id="c4e82-294">在“**策略设置**”页面上，为名称键入“*文档敏感度*”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-294">On the **Policy settings** page, type *Document sensitivity* for the name, and then click **Next**.</span></span>
9. <span data-ttu-id="c4e82-295">单击“**发布**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-295">Click **Publish**.</span></span>

<span data-ttu-id="c4e82-296">发布标签后，Office 桌面应用的用户就可以使用它们。</span><span class="sxs-lookup"><span data-stu-id="c4e82-296">With the labels published, they're available to users of Office desktop apps.</span></span> <span data-ttu-id="c4e82-297">当用户应用“**高度敏感**”标签时，水印会自动添加到文档中。</span><span class="sxs-lookup"><span data-stu-id="c4e82-297">When users apply the **Highly sensitive** label, a watermark is automatically added to the document.</span></span>

### <a name="more-information"></a><span data-ttu-id="c4e82-298">更多信息</span><span class="sxs-lookup"><span data-stu-id="c4e82-298">More information</span></span>
[<span data-ttu-id="c4e82-299">敏感度标签概述</span><span class="sxs-lookup"><span data-stu-id="c4e82-299">Overview of sensitivity labels</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a><span data-ttu-id="c4e82-300">为高度敏感的项目创建敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="c4e82-300">Create a sensitive information type for a highly sensitive project</span></span>

<span data-ttu-id="c4e82-301">敏感信息类型是预定义的字符串，可以在策略工作流中使用这些字符串来强制执行合规性要求。</span><span class="sxs-lookup"><span data-stu-id="c4e82-301">Sensitive information types are predefined strings that can be used in policy workflows to enforce compliance requirements.</span></span> <span data-ttu-id="c4e82-302">Microsoft 365 合规中心提供一百多种敏感信息类型，包括驾驶执照号码、信用卡号、银行帐号等。</span><span class="sxs-lookup"><span data-stu-id="c4e82-302">The Microsoft 365 Compliance Center comes with over one hundred sensitive information types, including driver's license numbers, credit card numbers, bank account numbers, etc.</span></span>

<span data-ttu-id="c4e82-303">你可以创建自定义敏感信息类型，以帮助管理特定于组织的内容。</span><span class="sxs-lookup"><span data-stu-id="c4e82-303">You can create custom sensitive information types to help manage content specific to your organization.</span></span> <span data-ttu-id="c4e82-304">在此示例中，我们将为高度敏感项目创建自定义敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="c4e82-304">In this example, we'll create a custom sensitive information type for a highly sensitive project.</span></span> <span data-ttu-id="c4e82-305">然后，可使用此敏感信息类型自动应用分类标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-305">We can then use this sensitive information type to automatically apply a classification label.</span></span>

<span data-ttu-id="c4e82-306">创建敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="c4e82-306">To create a sensitive information type</span></span>
1. <span data-ttu-id="c4e82-307">在 [Microsoft 365 合规中心](https://compliance.microsoft.com)的左侧导航中，展开“**分类**”，然后单击“**敏感信息类型**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-307">In the [Microsoft 365 Compliance Center](https://compliance.microsoft.com), in the left navigation, expand **Classification**, and then click **Sensitive info types**.</span></span>
2. <span data-ttu-id="c4e82-308">单击“**创建**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-308">Click **Create**.</span></span>
3. <span data-ttu-id="c4e82-309">对于“**名称**”和“**说明**”，键入“**土星项目**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-309">For **Name** and **Description**, type **Project Saturn**, and then click **Next**.</span></span>
4. <span data-ttu-id="c4e82-310">单击“**添加元素**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-310">Click **Add an element**.</span></span>
5. <span data-ttu-id="c4e82-311">在“**检测内容包含**”列表上，选择“**关键字**”，然后在“关键字”框中键入“*土星项目*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-311">On the **Detect content containing** list, select **Keywords**, and then type *Project Saturn* in the keyword box.</span></span>
6. <span data-ttu-id="c4e82-312">单击“**下一步**”，再单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-312">Click **Next**, and then click **Finish**.</span></span>
7. <span data-ttu-id="c4e82-313">如果系统询问你是否要测试敏感信息类型，请单击“**否**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-313">If asked if you would like to test the sensitive information type, click **No**.</span></span>

### <a name="more-information"></a><span data-ttu-id="c4e82-314">更多信息</span><span class="sxs-lookup"><span data-stu-id="c4e82-314">More information</span></span>
[<span data-ttu-id="c4e82-315">自定义敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="c4e82-315">Custom sensitive information types</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-a-policy-to-assign-a-label-based-on-a-sensitive-information-type"></a><span data-ttu-id="c4e82-316">创建根据敏感信息类型分配标签的策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-316">Create a policy to assign a label based on a sensitive information type</span></span>

<span data-ttu-id="c4e82-317">创建敏感信息类型后，可以在 Microsoft Cloud App Security 中创建文件策略，以将“*高度敏感*”标签自动应用于包含“*土星项目*”字符串的文档。</span><span class="sxs-lookup"><span data-stu-id="c4e82-317">Once the sensitive information type is created, we can create a file policy in Microsoft Cloud App Security to apply the *Highly sensitive* label to documents that contain the *Project Saturn* string automatically.</span></span>

> [!NOTE]
> <span data-ttu-id="c4e82-318">可通过复制过程在 Cloud App Security 中使用敏感度标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-318">There is a replication process that makes sensitivity labels available in Cloud App Security.</span></span> <span data-ttu-id="c4e82-319">你可能无法立即看到可用于某一策略的标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-319">You may not see the label available for a policy right away.</span></span>

<span data-ttu-id="c4e82-320">创建基于敏感信息类型的文件策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-320">To create a sensitive information type-based file policy</span></span>
1. <span data-ttu-id="c4e82-321">打开 [Microsoft Cloud App Security](https://portal.cloudappsecurity.com)。</span><span class="sxs-lookup"><span data-stu-id="c4e82-321">Open [Microsoft Cloud App Security](https://portal.cloudappsecurity.com).</span></span>
2. <span data-ttu-id="c4e82-322">在左侧导航中，展开“**控制**”，然后单击“**策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-322">In the left navigation, expand **Control**, and then click **Policies**.</span></span>
3. <span data-ttu-id="c4e82-323">单击“**创建策略**”，然后选择“**文件策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-323">Click **Create policy**, and then choose **File policy**.</span></span>
4. <span data-ttu-id="c4e82-324">对于“**策略名称**”，键入“*土星项目标记*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-324">For **Policy name**, type *Project Saturn labeling*.</span></span>
5. <span data-ttu-id="c4e82-325">在“**创建一个筛选器，筛选出即将应用此策略的文件**”下，单击 X 两次以删除默认筛选器。</span><span class="sxs-lookup"><span data-stu-id="c4e82-325">Under **Create a filter for the files this policy will act on**, click X twice to delete the default filters.</span></span>
7. <span data-ttu-id="c4e82-326">在“**选择筛选器**”列表中选择“**应用**”，然后从“**选择应用...**”列表中选择 **Microsoft SharePoint Online**。</span><span class="sxs-lookup"><span data-stu-id="c4e82-326">In the **Select a filter** list, choose **App**, and then select **Microsoft SharePoint Online** from the **Select apps...** list.</span></span>
8. <span data-ttu-id="c4e82-327">在“**检查方法**”下，选择“**数据分类服务**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-327">Under **Inspection method**, choose **Data classification service**.</span></span>
9. <span data-ttu-id="c4e82-328">在“**选择检查类型**”列表上，选择“**敏感信息类型**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-328">On the **Choose inspection type** list, choose **Sensitive information type**.</span></span>
10. <span data-ttu-id="c4e82-329">搜索并选择“*土星项目*”敏感度标签，然后单击“**完成**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-329">Search for and select the *Project Saturn* sensitivity label, and then click **Done**.</span></span></br>
   <span data-ttu-id="c4e82-330">![Cloud App Security 检查方法设置的屏幕截图](../media/mcas-sensitive-info-type-project-saturn.png)</span><span class="sxs-lookup"><span data-stu-id="c4e82-330">![Screenshot of Cloud App Security inspection method settings](../media/mcas-sensitive-info-type-project-saturn.png)</span></span>
11. <span data-ttu-id="c4e82-331">在“**治理**”下，展开 **Microsoft SharePoint Online**。</span><span class="sxs-lookup"><span data-stu-id="c4e82-331">Under **Governance**, expand **Microsoft SharePoint Online**.</span></span>
12. <span data-ttu-id="c4e82-332">选中“**应用分类标签**”复选框，然后选择“**高度敏感**”标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-332">Select the **Apply classification label** check box and select the **Highly sensitive** label.</span></span>
13. <span data-ttu-id="c4e82-333">单击“创建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4e82-333">Click **Create**.</span></span>

<span data-ttu-id="c4e82-334">实施策略后，当用户在文档中键入“土星项目”时，Cloud App Security 在扫描文件时将自动应用“*高度敏感*”标签。</span><span class="sxs-lookup"><span data-stu-id="c4e82-334">With the policy in place, when a user types "Project Saturn" into a document, Cloud App Security will automatically apply the *Highly sensitive* label when it scans the file.</span></span>

### <a name="more-information"></a><span data-ttu-id="c4e82-335">更多信息</span><span class="sxs-lookup"><span data-stu-id="c4e82-335">More information</span></span>
[<span data-ttu-id="c4e82-336">文件策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-336">File policies</span></span>](https://docs.microsoft.com/cloud-app-security/data-protection-policies)

## <a name="create-a-policy-to-remove-guest-access-to-highly-sensitive-files"></a><span data-ttu-id="c4e82-337">创建用于删除来宾对高度敏感文件的访问权限的策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-337">Create a policy to remove guest access to highly sensitive files</span></span>

<span data-ttu-id="c4e82-338">在本文的示例中，不应将带有“*高度敏感*”标签的文件与来宾共享。</span><span class="sxs-lookup"><span data-stu-id="c4e82-338">In the example in this article, files with the *Highly sensitive* label shouldn't be shared with guests.</span></span> <span data-ttu-id="c4e82-339">可以在 Cloud App Security 中创建一个文件策略，该策略会自动从带有该标签的文件中删除来宾访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-339">We can create a file policy in Cloud App Security that automatically removes guest access from files with that label.</span></span>

<span data-ttu-id="c4e82-340">请注意，这不会阻止用户共享或重新共享这些文件。</span><span class="sxs-lookup"><span data-stu-id="c4e82-340">Note that this doesn't prevent users from sharing or re-sharing these files.</span></span> <span data-ttu-id="c4e82-341">对于存储在允许来宾共享的网站中的文件，仍依靠用户来执行你的治理策略。</span><span class="sxs-lookup"><span data-stu-id="c4e82-341">You're still reliant on your users to follow your governance policies for files that are stored in sites that allow guest sharing.</span></span> <span data-ttu-id="c4e82-342">但是，这是一个有用的工具，可用于从与来宾共享后添加了敏感信息的文件中删除来宾访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-342">However, this can be a useful tool for removing guest access from files that had sensitive information added to them after they were shared with guests.</span></span>

<span data-ttu-id="c4e82-343">创建基于标签的文件策略</span><span class="sxs-lookup"><span data-stu-id="c4e82-343">To create a label-based file policy</span></span>
1. <span data-ttu-id="c4e82-344">打开 [Microsoft Cloud App Security](https://portal.cloudappsecurity.com)。</span><span class="sxs-lookup"><span data-stu-id="c4e82-344">Open [Microsoft Cloud App Security](https://portal.cloudappsecurity.com).</span></span>
2. <span data-ttu-id="c4e82-345">在左侧导航中，展开“**控制**”，然后单击“**策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-345">In the left navigation, expand **Control**, and then click **Policies**.</span></span>
3. <span data-ttu-id="c4e82-346">单击“**创建策略**”，然后选择“**文件策略**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-346">Click **Create policy**, and then choose **File policy**.</span></span>
4. <span data-ttu-id="c4e82-347">对于“**策略名称**”，键入“*土星项目 - 删除来宾访问权限*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-347">For **Policy name**, type *Project Saturn - remove guest access*.</span></span>
5. <span data-ttu-id="c4e82-348">在“**创建一个筛选器，筛选出即将应用此策略的文件**”下，单击 X 两次以删除默认筛选器。</span><span class="sxs-lookup"><span data-stu-id="c4e82-348">Under **Create a filter for the files this policy will act on**, click X twice to delete the default filters.</span></span>
6. <span data-ttu-id="c4e82-349">在“**选择筛选器**”列表中选择“**应用**”，然后从“**选择应用...**”列表中选择 **Microsoft SharePoint Online**。</span><span class="sxs-lookup"><span data-stu-id="c4e82-349">In the **Select a filter** list, choose **App**, and then select **Microsoft SharePoint Online** from the **Select apps...** list.</span></span>
7. <span data-ttu-id="c4e82-350">单击“**添加筛选器**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-350">Click **Add a filter**.</span></span>
8. <span data-ttu-id="c4e82-351">在“**选择筛选器**”列表中，选择“**分类标签**”，然后从“**选择筛选器...**”列表中选择“**Azure 信息保护**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-351">In the **Select a filter** list, choose **Classification label**, and then select **Azure Information Protection** from the **Select filter...** list.</span></span>
9. <span data-ttu-id="c4e82-352">在“**选择分类标签**”列表中，选择“**高度敏感**”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-352">In the **Select classification label** list, select **Highly sensitive**.</span></span></br>
   <span data-ttu-id="c4e82-353">![Cloud App Security 策略筛选器设置的屏幕截图](../media/mcas-sharepoint-confidential-label-filter.png)</span><span class="sxs-lookup"><span data-stu-id="c4e82-353">![Screenshot of Cloud App Security policy filter settings](../media/mcas-sharepoint-confidential-label-filter.png)</span></span>
10. <span data-ttu-id="c4e82-354">在“**治理**”下，展开 **Microsoft SharePoint Online**。</span><span class="sxs-lookup"><span data-stu-id="c4e82-354">Under **Governance**, expand **Microsoft SharePoint Online**.</span></span>
11. <span data-ttu-id="c4e82-355">选中“**向文件所有者发送策略匹配摘要**”和“**删除外部用户**”复选框。</span><span class="sxs-lookup"><span data-stu-id="c4e82-355">Select the **Send policy-match digest to file owner** and **Remove external users** check boxes.</span></span>
12. <span data-ttu-id="c4e82-356">对于自定义通知消息，请键入“*此文件是高度敏感文件。公司策略禁止与来宾共享该文件*”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-356">For the custom notification message, type *This file is highly sensitive. Company policy prohibits sharing it with guests*.</span></span>
13. <span data-ttu-id="c4e82-357">单击“创建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c4e82-357">Click **Create**.</span></span>

<span data-ttu-id="c4e82-358">请务必注意，该策略将删除使用*特定人员*链接共享的文件的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-358">It's important to note, that this policy removes access for files shared using a *Specific people* link.</span></span> <span data-ttu-id="c4e82-359">它不会从未认证（*任何人*）链接中删除访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-359">It doesn't remove access from unauthenticated (*Anyone*) links.</span></span> <span data-ttu-id="c4e82-360">如果来宾是整个网站或团队的成员，也不会删除其访问权限。</span><span class="sxs-lookup"><span data-stu-id="c4e82-360">It also doesn't remove access if the guest is a member of the site or team as a whole.</span></span> <span data-ttu-id="c4e82-361">如果计划将网站或团队中的高度机密文档与来宾成员进行共享，请考虑使用 [Teams 中的专用频道](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9)并仅允许组织成员在专用频道中共享。</span><span class="sxs-lookup"><span data-stu-id="c4e82-361">If you plan to have highly sensitive documents in a site or team with guest members, consider using [private channels in Teams](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9) and only allowing members of your organization in the private channels.</span></span>

## <a name="test-the-solution"></a><span data-ttu-id="c4e82-362">测试解决方案</span><span class="sxs-lookup"><span data-stu-id="c4e82-362">Test the solution</span></span>

<span data-ttu-id="c4e82-363">若要测试本文中所述的解决方案，请创建一个 Word 文档并将其保存到文档库。</span><span class="sxs-lookup"><span data-stu-id="c4e82-363">To test the solution described in this article, create a Word document and save it to a document library.</span></span> <span data-ttu-id="c4e82-364">与来宾用户共享文件。</span><span class="sxs-lookup"><span data-stu-id="c4e82-364">Share the file with a guest user.</span></span> <span data-ttu-id="c4e82-365">当来宾尝试访问该文档时，应要求他们在多重身份验证中注册，然后接受使用条款。</span><span class="sxs-lookup"><span data-stu-id="c4e82-365">When the guest attempts to access the document, they should be required to enroll in multi-factor authentication, and then accept the terms of use.</span></span>

<span data-ttu-id="c4e82-366">一旦来宾有权访问文档，请在文档中键入“*土星项目*”并进行保存。</span><span class="sxs-lookup"><span data-stu-id="c4e82-366">Once the guest has access to the document, type *Project Saturn* in the document and save it.</span></span> <span data-ttu-id="c4e82-367">Cloud App Security 扫描文档后，应该应用“*高度敏感*”标签，并且来宾用户将不再有权访问它。</span><span class="sxs-lookup"><span data-stu-id="c4e82-367">Once Cloud App Security scans the document, the *Highly sensitive* label should be applied and the guest user should no longer have access to it.</span></span>

<span data-ttu-id="c4e82-368">可使用本文中所述的各种组合工具，帮助为组织创建高效而安全的来宾共享环境。</span><span class="sxs-lookup"><span data-stu-id="c4e82-368">You can use the tools described in this article in various combinations to help create a productive but safe guest sharing environment for your organization.</span></span>

## <a name="additional-options"></a><span data-ttu-id="c4e82-369">其他选项</span><span class="sxs-lookup"><span data-stu-id="c4e82-369">Additional options</span></span>

<span data-ttu-id="c4e82-370">Microsoft 365 和 Azure Active Directory 中提供部分选项，可帮助保护来宾共享环境的安全。</span><span class="sxs-lookup"><span data-stu-id="c4e82-370">There are some additional options in Microsoft 365 and Azure Active Directory that can help secure your guest sharing environment.</span></span>

- <span data-ttu-id="c4e82-371">可创建允许或拒绝的共享域的列表，限制用户可以与之共享的人员。</span><span class="sxs-lookup"><span data-stu-id="c4e82-371">You can create a list of allowed or denied sharing domains to limit who users can share with.</span></span> <span data-ttu-id="c4e82-372">有关详细信息，请参见“[按域限制共享 SharePoint 和 OneDrive 内容”](https://docs.microsoft.com/sharepoint/restricted-domains-sharing)和“[允许或组织邀请指定组织的 B2B 用户](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-372">See [Restrict sharing of SharePoint and OneDrive content by domain](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) and [Allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list) for more information.</span></span>
- <span data-ttu-id="c4e82-373">可限制用户连接至的其他 Azure Active Directory 租户。</span><span class="sxs-lookup"><span data-stu-id="c4e82-373">You can limit which other Azure Active Directory tenants your users can connect to.</span></span> <span data-ttu-id="c4e82-374">参见“[使用租户限制管理对 SaaS 云应用程序的访问权限](https://docs.microsoft.com/azure/active-directory/manage-apps/tenant-restrictions)”了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="c4e82-374">See [Use tenant restrictions to manage access to SaaS cloud applications](https://docs.microsoft.com/azure/active-directory/manage-apps/tenant-restrictions) for information.</span></span>
- <span data-ttu-id="c4e82-375">可创建合作伙伴能够帮助管理访客用户的托管环境。</span><span class="sxs-lookup"><span data-stu-id="c4e82-375">You can create a managed environment where partners can help manage guest accounts.</span></span> <span data-ttu-id="c4e82-376">有关信息，请参见“[创建有访客用户的 B2B 外联网](https://docs.microsoft.com/Office365/Enterprise/b2b-extranet)”。</span><span class="sxs-lookup"><span data-stu-id="c4e82-376">See [Create a B2B extranet with managed guests](https://docs.microsoft.com/Office365/Enterprise/b2b-extranet) for information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4e82-377">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4e82-377">See Also</span></span>

[<span data-ttu-id="c4e82-378">与来宾共享时限制文件意外曝光</span><span class="sxs-lookup"><span data-stu-id="c4e82-378">Limit accidental exposure to files when sharing with guests</span></span>](share-limit-accidental-exposure.md)

[<span data-ttu-id="c4e82-379">有关与未经认证用户共享文件和文件夹的最佳做法</span><span class="sxs-lookup"><span data-stu-id="c4e82-379">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="c4e82-380">创建托管有来宾的 B2B 外联网</span><span class="sxs-lookup"><span data-stu-id="c4e82-380">Create a B2B extranet with managed guests</span></span>](b2b-extranet.md)
