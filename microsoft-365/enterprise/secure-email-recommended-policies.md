---
title: 保护电子邮件的推荐策略 - Microsoft 365 企业版 | Microsoft Docs
description: 介绍针对有关如何应用电子邮件策略和配置的 Microsoft 建议的策略。
author: brendacarter
manager: laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.author: bcarter
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.openlocfilehash: dd1504ac11f0e2eefa56572af24de14b5f87830e
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "26865409"
---
# <a name="policy-recommendations-for-securing-email"></a><span data-ttu-id="d1374-103">用于保护电子邮件的策略建议</span><span class="sxs-lookup"><span data-stu-id="d1374-103">Policy recommendations for securing email</span></span>
<span data-ttu-id="d1374-p101">本文介绍如何实现建议的标识和设备访问策略以保护组织的电子邮件和电子邮件客户端支持现代身份验证和条件的访问。本指南基于[公用标识和设备访问策略](identity-access-policies.md)，其中也包括几个其他建议。</span><span class="sxs-lookup"><span data-stu-id="d1374-p101">This article describes how to implement the recommended identity and device access policies to protect organizational email and email clients that support Modern Authentication and Conditional Access. This guidance builds on the [Common identity and device access policies](identity-access-policies.md) and also includes a few additional recommendations.</span></span>


<span data-ttu-id="d1374-p102">这些建议基于三个不同级别的安全和保护可以应用基于您的需求的粒度：**基线**、**敏感**和**高度管控**。您可以了解有关这些安全层及推荐客户端的操作系统，引用中[建议的安全策略和配置介绍](microsoft-365-policies-configurations.md)这些建议的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1374-p102">These recommendations are based on three different tiers of security and protection that can be applied based on the granularity of your needs: **baseline**, **sensitive**, and **highly regulated**. You can learn more about these security tiers, and the recommended client operating systems, referenced by these recommendations in the [recommended security policies and configurations introduction](microsoft-365-policies-configurations.md).</span></span>

<span data-ttu-id="d1374-p103">这些建议需要您使用现代的电子邮件客户端，包括适用于 iOS 的 Outlook 和 Android 移动设备上的用户。Outlook 开发 iOS 和 Android 为 Office 365 的最佳功能提供支持。这些移动 Outlook 应用程序也被构建安全功能支持移动的使用和结合使用其他 Microsoft 云安全功能。有关详细信息，请参阅[Outlook for iOS 和 Android 常见问题](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq)。</span><span class="sxs-lookup"><span data-stu-id="d1374-p103">These recommendations require your users to use modern email clients, including Outlook for iOS and Android on mobile devices. Outlook for iOS and Android provide support for the best features of Office 365. These mobile Outlook apps are also architected with security capabilities that support mobile use and work together with other Microsoft cloud security capabilities. For more information, see [Outlook for iOS and Android FAQ](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).</span></span>

## <a name="updating-common-policies-to-include-email"></a><span data-ttu-id="d1374-112">更新常见的策略，以包含电子邮件</span><span class="sxs-lookup"><span data-stu-id="d1374-112">Updating common policies to include email</span></span>
<span data-ttu-id="d1374-p104">下图说明了常见的标识和设备访问策略，指示哪些策略需要更新，以保护电子邮件。请注意的 Exchange Online 以阻止 ActiveSync 客户端的新规则。这样会强制 Outlook 使用移动。</span><span class="sxs-lookup"><span data-stu-id="d1374-p104">The following diagram illustrates the common identity and device access policies and indicates which policies need to be updated to protect email. Note the addition of a new rule for Exchange Online to block ActiveSync clients. This forces the use of Outlook mobile.</span></span>

![用于保护电子邮件的策略更新的摘要](../images/identity-access-ruleset-mail.png)

<span data-ttu-id="d1374-p105">如果您 Exchange Online 和 Outlook 中包含的策略的范围在您将这些设置时，您只需创建新的策略，以阻止 ActiveSync 客户端。查看下表中列出的策略并之一进行的建议的增加，或确认这些已包含。每个规则链接到[常见的标识和设备访问策略](identity-access-policies.md)一文中的关联的配置说明。</span><span class="sxs-lookup"><span data-stu-id="d1374-p105">If you included Exchange Online and Outlook in the scope of the policies when you set them up, you only need to create the new policy to block ActiveSync clients. Review the policies listed in the following table and either make the recommended additions, or confirm that these are already included. Each rule links to the associated configuration instructions in the [Common identity and device access policies](identity-access-policies.md) article.</span></span> 

|<span data-ttu-id="d1374-120">保护级别</span><span class="sxs-lookup"><span data-stu-id="d1374-120">Protection level</span></span>|<span data-ttu-id="d1374-121">Policies</span><span class="sxs-lookup"><span data-stu-id="d1374-121">Policies</span></span>|<span data-ttu-id="d1374-122">更多信息</span><span class="sxs-lookup"><span data-stu-id="d1374-122">More information</span></span>|
|:---------------|:-------|:----------------|
|<span data-ttu-id="d1374-123">**基线**</span><span class="sxs-lookup"><span data-stu-id="d1374-123">**Baseline**</span></span>|[<span data-ttu-id="d1374-124">*中等*或*高*风险登录时需要 MFA</span><span class="sxs-lookup"><span data-stu-id="d1374-124">Require MFA when sign-in risk is *medium* or *high*</span></span>](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|<span data-ttu-id="d1374-125">包括 Exchange Online 中的云应用程序的分配。</span><span class="sxs-lookup"><span data-stu-id="d1374-125">Include Exchange Online in the assignments of cloud apps.</span></span>|
|        |[<span data-ttu-id="d1374-126">阻止客户端不支持现代身份验证</span><span class="sxs-lookup"><span data-stu-id="d1374-126">Block clients that don't support modern authentication</span></span>](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|<span data-ttu-id="d1374-127">包括 Exchange Online 中的云应用程序的分配。</span><span class="sxs-lookup"><span data-stu-id="d1374-127">Include Exchange Online in the assignments of cloud apps.</span></span>|
|        |[<span data-ttu-id="d1374-128">定义应用程序保护策略</span><span class="sxs-lookup"><span data-stu-id="d1374-128">Define app protection policies</span></span>](identity-access-policies.md#high-risk-users-must-change-password)|<span data-ttu-id="d1374-p106">确保 Outlook 包含在列表中的应用程序。请务必更新为每个平台 (iOS，Android、 Windows) 策略。</span><span class="sxs-lookup"><span data-stu-id="d1374-p106">Be sure Outlook is included in the list of apps. Be sure to update the policy for each platform (iOS, Android, Windows).</span></span>|
|        |[<span data-ttu-id="d1374-131">需要已批准应用程序</span><span class="sxs-lookup"><span data-stu-id="d1374-131">Require approved apps</span></span>](identity-access-policies.md#require-approved-apps)|<span data-ttu-id="d1374-132">包括的云应用程序列表中的 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="d1374-132">Include Exchange Online in the list of cloud apps.</span></span>|
|        |[<span data-ttu-id="d1374-133">需要符合标准的 Pc</span><span class="sxs-lookup"><span data-stu-id="d1374-133">Require compliant PCs</span></span>](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|<span data-ttu-id="d1374-134">包括 Exchange Online 中的云应用程序的列表。</span><span class="sxs-lookup"><span data-stu-id="d1374-134">Include Exchange Online in list of cloud apps.</span></span>|
|        |[<span data-ttu-id="d1374-135">阻止 ActiveSync 客户端</span><span class="sxs-lookup"><span data-stu-id="d1374-135">Block ActiveSync clients</span></span>](#block-activesync)|<span data-ttu-id="d1374-136">添加此新策略。</span><span class="sxs-lookup"><span data-stu-id="d1374-136">Add this new policy.</span></span> 
|<span data-ttu-id="d1374-137">**敏感**</span><span class="sxs-lookup"><span data-stu-id="d1374-137">**Sensitive**</span></span>|[<span data-ttu-id="d1374-138">*低*、*中*或*高*风险登录时需要 MFA</span><span class="sxs-lookup"><span data-stu-id="d1374-138">Require MFA when sign-in risk is *low*, *medium* or *high*</span></span>](identity-access-policies.md#require-mfa-based-on-sign-in-risk)| <span data-ttu-id="d1374-139">包括 Exchange Online 中的云应用程序的分配。</span><span class="sxs-lookup"><span data-stu-id="d1374-139">Include Exchange Online in the assignments of cloud apps.</span></span>|
|         |[<span data-ttu-id="d1374-140">需要符合标准的 Pc*和*移动设备</span><span class="sxs-lookup"><span data-stu-id="d1374-140">Require compliant PCs *and* mobile devices</span></span>](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|<span data-ttu-id="d1374-141">包括的云应用程序列表中的 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="d1374-141">Include Exchange Online in the list of cloud apps.</span></span>|
|<span data-ttu-id="d1374-142">**高度管控**</span><span class="sxs-lookup"><span data-stu-id="d1374-142">**Highly regulated**</span></span>|[<span data-ttu-id="d1374-143">*始终*需要 MFA</span><span class="sxs-lookup"><span data-stu-id="d1374-143">*Always* require MFA</span></span>](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|<span data-ttu-id="d1374-144">包括 Exchange Online 中的云应用程序的分配</span><span class="sxs-lookup"><span data-stu-id="d1374-144">Include Exchange Online in the assignments of cloud apps</span></span> |

## <a name="block-activesync-clients"></a><span data-ttu-id="d1374-145">阻止 ActiveSync 客户端</span><span class="sxs-lookup"><span data-stu-id="d1374-145">Block ActiveSync clients</span></span>
<span data-ttu-id="d1374-p107">此策略阻止 ActiveSync 客户端绕过其他条件访问规则。规则配置仅适用于 ActiveSync 客户端。通过选择**需要批准客户端应用程序**，此策略阻止 ActiveSync 客户端。配置此策略：</span><span class="sxs-lookup"><span data-stu-id="d1374-p107">This policy prevents ActiveSync clients from bypassing other conditional access rules. The rule configuration applies only to ActiveSync clients. By selecting **Require approved client app**, this policy blocks ActiveSync clients. To configure this policy:</span></span>

1. <span data-ttu-id="d1374-p108">转到 [Azure 门户](https://portal.azure.com)，然后使用你的凭据登录。 成功登录后，会看到 Azure 仪表板。</span><span class="sxs-lookup"><span data-stu-id="d1374-p108">Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials. After you've successfully signed in, you see the Azure Dashboard.</span></span>

2. <span data-ttu-id="d1374-152">从左侧菜单中选择“Azure Active Directory”。</span><span class="sxs-lookup"><span data-stu-id="d1374-152">Choose **Azure Active Directory** from the left menu.</span></span>

3. <span data-ttu-id="d1374-153">在“安全”部分之下，选择“条件访问”。</span><span class="sxs-lookup"><span data-stu-id="d1374-153">Under the **Security** section, choose **Conditional access**.</span></span>

4. <span data-ttu-id="d1374-154">选择“新策略”。</span><span class="sxs-lookup"><span data-stu-id="d1374-154">Choose **New policy**.</span></span>

5. <span data-ttu-id="d1374-155">输入策略名称，然后选择要应用策略的“用户和组”。</span><span class="sxs-lookup"><span data-stu-id="d1374-155">Enter a policy name, then choose the **Users and groups** you want to apply the policy for.</span></span>

6. <span data-ttu-id="d1374-156">选择“云应用”。</span><span class="sxs-lookup"><span data-stu-id="d1374-156">Choose **Cloud apps**.</span></span>

7. <span data-ttu-id="d1374-p109">选择**应用程序**中，选择 Office 365 Exchange Online。单击**选择**并**完成**。</span><span class="sxs-lookup"><span data-stu-id="d1374-p109">Choose **Select apps**, select Office 365 Exchange Online. Click **Select** and **Done**.</span></span>
8. <span data-ttu-id="d1374-159">选择**条件**，然后选择**客户端应用程序**。</span><span class="sxs-lookup"><span data-stu-id="d1374-159">Choose **Conditions**, and then choose **Client apps**.</span></span>
9. <span data-ttu-id="d1374-p110">有关**配置**，请选择**是**。检查只有以下：**移动应用程序和桌面客户端**和**Exchange ActiveSync 客户端**。单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="d1374-p110">For **Configure**, select **Yes**. Check only the following: **Mobile apps and desktop clients** and **Exchange ActiveSync clients**. Click **Done**.</span></span>

10. <span data-ttu-id="d1374-163">从“访问控制”部分选择“授予”。</span><span class="sxs-lookup"><span data-stu-id="d1374-163">Choose **Grant** from the **Access controls** section.</span></span>

11. <span data-ttu-id="d1374-p111">选择**授予访问**，选择**需要批准客户端应用程序**。 为多个控件中，选择**需要选定的控件**，然后选择**选择**。</span><span class="sxs-lookup"><span data-stu-id="d1374-p111">Choose **Grant access**, select **Require approved client app**.  For multiple controls, select **Require the selected controls**, then choose **Select**.</span></span> 

12. <span data-ttu-id="d1374-166">单击“创建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1374-166">Click **Create**.</span></span>

## <a name="setup-office-365-message-encryption"></a><span data-ttu-id="d1374-167">安装 Office 365 邮件加密</span><span class="sxs-lookup"><span data-stu-id="d1374-167">Setup Office 365 message encryption</span></span>
<span data-ttu-id="d1374-p112">使用新的 Office 365 邮件加密 (OME) 功能，利用 Azure Information Protection 中的保护功能，您的组织可以轻松地共享受保护的电子邮件与任何设备上的任何人。用户可以发送和接收与其他 Office 365 组织以及非 Office 365 客户使用 Outlook.com、 Gmail 和其他电子邮件服务的受保护的邮件。</span><span class="sxs-lookup"><span data-stu-id="d1374-p112">With the new Office 365 Message Encryption (OME) capabilities, which leverage the protection features in Azure Information Protection, your organization can easily share protected email with anyone on any device. Users can send and receive protected messages with other Office 365 organizations as well as non-Office 365 customers using Outlook.com, Gmail, and other email services.</span></span>

<span data-ttu-id="d1374-170">有关详细信息，请参阅[设置新的 Office 365 邮件加密功能](https://support.office.com/article/set-up-new-office-365-message-encryption-capabilities-7ff0c040-b25c-4378-9904-b1b50210d00e)。</span><span class="sxs-lookup"><span data-stu-id="d1374-170">For more information, see [Set up new Office 365 Message Encryption capabilities](https://support.office.com/article/set-up-new-office-365-message-encryption-capabilities-7ff0c040-b25c-4378-9904-b1b50210d00e).</span></span> 

<!---
This article describes recommended policies to help you secure organizational email and email clients that support Modern Authentication and Conditional Access. These recommendations are in addition to the [common identity and access policy recommendations](identity-access-policies.md).

The following recommendations are based on three different layers of security and protection for your email that can be applied based on the granularity of your needs:

- **Baseline**: Microsoft recommends you establish a minimum standard for protecting data, as well as the identities and devices that access your data. Microsoft provides strong default protection that meets the needs of many organizations. Some organizations require additional capabilities to meet their baseline requirements.
- **Sensitive**: Some customers have a subset of data that must be protected at higher levels. You can apply increased protection to specific data sets in your Office 365 environment. Microsoft recommends protecting identities and devices that access sensitive data with comparable levels of security. 
- **Highly regulated**: Some organizations may have a very small amount of data that is highly classified, trade secret, or regulated data. Microsoft provides capabilities to help organizations meet these requirements, including added protection for identities and devices.

See the [recommended security policies and configurations introduction](microsoft-365-policies-configurations.md) topic for more details.

> [!IMPORTANT]
> All security groups created as part of these recommendations must be created with Office features enabled. This is specifically important for the deployment of Azure Information Protection (AIP) when securing documents in SharePoint Online.
>
>![Office features enabled for security groups](./media/security-group.png)
>

## Baseline
To create a new conditional access policy: 

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials. After you've successfully signed in, you see the Azure Dashboard.

2. Choose **Azure Active Directory** from the left menu.

3. Under the **Security** section, choose **Conditional access**.

4. Choose **New policy** as shown in the screen-shot below:

![Baseline CA policy](./media/secure-email/CA-EXO-policy-1.png)

The following tables describe the appropriate settings necessary to express the policies required for each level of protection.

### Medium and above risk requires MFA

The following tables describes the conditional access policy settings to implement for this policy.

**Assignments**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Users and groups|Include|Select users and groups – Select specific security group containing targeted users|Start with security group including pilot users.|
||Exclude|Exception security group; service accounts (app identities)|Membership modified on an as needed temporary basis|
|Cloud apps|Include|Select apps -  Select Office 365 Exchange Online||
|Conditions|Configured|Yes|Configure specific to your environment and needs|
|Sign-in risk|Risk level|High, medium|Check both|

**Access controls**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Grant|Grant access|True|Selected|
||Require MFA|True|Check|
||Require compliant devices|False||
||Require domain joined devices|False||
||Require all the selected controls|True|Selected|

> [!NOTE]
> Be sure to enable this policy, by clicking **On**. Also consider using the [What if](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) tool to test the policy

### Require a compliant or domain joined device

To create a conditional access policy for Exchange Online:

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials. After you've successfully signed in, you see the Azure Dashboard.

2. Choose **Azure Active Directory** from the left menu.

3. Under the **Security** section, choose **Conditional access**.

4. Choose **New policy**.

5. Enter a policy name, then choose the **Users and groups** you want to apply the policy for.

6. Choose **Cloud apps**.

7. Choose **Select apps**, select **Office 365 Exchange Online** from the **Cloud apps** list, click on **Select**. Once the **Office 365 Exchange Online** app is selected, click **Done**.

8. Choose **Grant** from the **Access controls** section.

9. Choose **Grant access**, select both **Require device to be marked as compliant** and **Require domain joined (Hybrid Azure AD)**, then choose **Select**.

10. Click **Create** to create the Exchange Online conditional access policy.

    > [!NOTE]
    > Beginning with Intune on Azure, you have to create all conditional access policies in the Azure Active Directory workload. Intune provides a link to Azure AD conditional access policies workload from its portal  for convenience.

    > [!IMPORTANT]
    > If you need assistance on migrating conditional access policies previously created in the Intune classic portal to the Intune on Azure portal, see the [reassign conditional access policies from Intune classic portal to the Azure portal](https://docs.microsoft.com/intune/conditional-access-intune-reassign) topic. 

### App-based conditional access for Exchange Online

You can add one more security layer by setting up an app-based conditional access policy for Exchange Online in the Intune on Azure portal. When you apply an app-based conditional access for Exchange Online you require users to use a specific app (E.g. Microsoft Outlook app) to access corporate e-mail.

To add an app-based conditional access policy:

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your Intune credentials. After you've successfully signed in, you see the Azure Dashboard.

2. Choose **More services** from the left menu, then type: "**Intune**".

3. Choose **Intune App Protection**.

4. On the **Intune mobile application management** blade choose **All Settings**.

5. Choose **Exchange Online** under the **Conditional access** section.

6. Select **Allow apps that support Intune app policies**, then choose the app (E.g. Microsoft Outlook).

7. Choose **Restricted user groups**, click **Select groups**, select the user or group you want to apply the policy for, then click **Select**.

## Sensitive

### Low and above risk requires MFA
The following tables describes the conditional access policy settings to implement for low- and above-risk policies.

**Assignments**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Users and groups|Include|Select users and groups – Select specific security group containing targeted users|Start with security group including pilot users|
||Exclude|Exception security group; service accounts (app identities)|Membership modified on an as needed temporary basis|
|Cloud apps|Include|Select apps -  Select Office 365 Exchange Online||
|Conditions|Configured|Yes|Configure specific to your environment and needs|
|Sign-in risk|Configured|Yes|Configure specific to your environment and needs|
||Risk level|Low, medium, high|Check all three|

**Access controls**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
||Grant|Grant access|True|Selected|
||Require MFA|True|Check|
||Require compliant devices|False||
||Require domain joined device|False||
||Require all the selected controls|True|Selected|

> [!NOTE]
> Be sure to enable this policy, by clicking **On**. Also consider using the [What if](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) tool to test the policy

### Require a compliant or domain joined device
(See baseline instructions)

### App-based conditional access for Exchange online

(See baseline instructions)

#### Apply to

Once the pilot project has been completed, these policies should be applied to users in your organization who require access to email considered sensitive.

## Highly regulated
### MFA required

The following tables describes the conditional access policy settings to implement for the highly regulated policy.

**Assignments**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Users and groups|Include|Select users and groups – Select specific security group containing targeted users|Start with security group including pilot users|
||Exclude|Exception security group; service accounts (app identities)|Membership modified on an as needed temporary basis|
|Cloud apps|Include|Select apps -  Select Office 365 Exchange Online||

**Access controls**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Grant|Grant access|True|Selected|
||Require MFA|True|Check|
||Require complaint devices|False|Check|
||Require domain joined device|False||
||Require all the selected controls|True|Selected|

> [!NOTE]
> Be sure to enable this policy, by clicking **On**. Also consider using the [What if](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) tool to test the policy

### Require a compliant or domain joined device
(See baseline instructions)
### App-based conditional access for Exchange online
(See baseline instructions)
#### Apply to
Once the pilot project has been completed, these policies should be applied to users in your organization who require access to email considered highly regulated.

### High risk users policy
To ensure that all high-risk users compromised accounts are forced to perform a password change when signing-in, you must apply the following policy.

Log in to the [Microsoft Azure portal (http://portal.azure.com)](http://portal.azure.com/) with your administrator credentials, and then navigate to **Azure AD Identity Protection > User Risk Policy**.

**Assignments**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Users|Include|All users|Selected|
||Exclude|None||
|Conditions|User risk|High|Selected|

**Controls**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
||Access|Allow access|True|Selected|
||Access|Require password change|True|Check|

**Review:** not applicable

> [!NOTE]
> Be sure to enable this policy, by clicking **On**. Also consider using the [What if](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) tool to test the policy

## Additional configurations
In addition to the above policies, you must configure the following Mobile Application and Device Management settings discussed in this section.

### Intune mobile application management

To ensure email is protected by the policy recommendations stated earlier for each security and data protection tier, you must create Intune app protection policies from within the Azure portal.

To create a new app protection policy, log in to the Microsoft Azure portal with your administer credentials, and then navigate to **Intune App Protection > App policy**.

Add a new policy (+Add) as shown in the following screen shot:

![Intune mobile application management](./media/secure-email/CA-EXO-policy-2.png)

>[!NOTE]
>There are slight differences in the app protection policy options between iOS and Android. The below policy is specifically for Android.
>

The following tables describe the recommended Intune app protection policy settings:

**General**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Email|Name|Secure email policy for Android|Enter a policy name|
||Description||Enter text that describes the policy|
||Platform|Android|There are slight differences in the app protection policy options between iOS and Android; this policy is specifically for Android|

**Apps**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Applications|Apps|Outlook|Selected (list)|

**Settings**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Data relocation|Prevent Android backup|Yes|On iOS this will specifically call out iTunes and iCloud|
|||Allow app to transfer data to other apps|Policy managed apps||
||Allow app to receive data to other apps|Policy managed apps||
||Prevent "Save As"|Yes||
||Restrict cut, copy, and paste with other apps|Policy managed apps||
||Restrict web content to display in the managed browser|No||
||Encrypt app data|Yes|On iOS select option: When device is locked|
||Disable contacts sync|No||
|Access|Require PIN for access|Yes||
||Number of attempts before PIN reset|3||
||Allow simple PIN|No||
||PIN length|6||
||Allow fingerprint instead of PIN|Yes||
||Require Corporate credentials for access|No||
||Block managed apps from running on jailbroken or rooted devices|Yes||
||Recheck the access requirement after (minutes)|30||
||Offline grace period|720||
||Offline interval (days) before app data is wiped|90||
||Block screen capture and Android assistant|No|On iOS this is not an available option|

When complete, remember to click "Create". Repeat the above steps and replace the selected platform (dropdown) with iOS. This creates two app policies, so once you create the policy, then assign groups to the policy and deploy it.

- See [how to create and assign app protection policies](https://docs.microsoft.com/intune/app-protection-policies) for more details.

### Intune mobile device management
You create the following device configuration profiles and device compliance policies by logging into the [Intune on Azure portal](https://portal.azure.com) with your Intune credentials.

#### iOS email profile
In the [Intune on Azure portal](https://portal.azure.com), you can create the following device configuration profiles at **Device configuration > Profiles > Create Profile > Platform (iOS) > Profile type (E-mail)**.

**Email profile**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Exchange Active Sync|Host (#)|Outlook.office365.com||
||Account Name (#)|SecureEmailAccount|Admini choice|
||Username|User principal name|Selected – Drop down|
||Email address|Primary SMTP address|Selected – Drop down|
||Authentication method|Username and password|Selected – Drop down|
||Use S/MIME|False||
|Synchronization settings|Number of days of email to synchronize|Two weeks|Selected – Drop down|
||Use SSL|True|Check|
||Allow messages to be moved to other email accounts|False||
||Allow email to be sent from third party applications|True||
||Synchronize recently used email addresses|True|Check|

#### Android email profile
In the [Intune on Azure portal](https://portal.azure.com), you can create the following device configuration profiles at **Device configuration > Profiles > Create Profile > Platform (Android) > Profile type (E-mail)**.

**Email profile**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Exchange Active Sync|Host (#)| Outlook.office365.com|
||Account Name (#)|SecureEmailAccount|Admini choice|
||Username|User principal name|Selected – Drop down|
||Email address|Primary SMTP address|Selected – Drop down|
||Authentication method|Username and password|Selected – Drop down|
||Use S/MIME|False||
|Synchronization settings|Number of days of email to synchronize|Two weeks|Selected – Drop down|
||Sync schedule|Not configured|Selected – Drop down|
||Use SSL|True|Check|
||Content type to synchronize|||
||Email|True|Check (locked)|
||Contacts|True|Check|
||Calenadr|True|Check|
||Tasks|True|Check|
||Notes|True|Check|

#### Android for work email profile
In the [Intune on Azure portal](https://portal.azure.com), you can create the following device configuration profiles at **Device configuration > Profiles > Create Profile > Platform (Android for Work) > Profile type (E-mail)**.

**Email profile**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Exchange Active Sync|Host(#)| Outlook.office365.com|
||Account Name(#)|SecureEmailAccount|Admini choice|
||Username|User principal name|Selected – Drop down|
||Email address|Primary SMTP address|Selected – Drop down|
||Authentication method|Username and password|Selected – Drop down|
|Synchronization settings|Number of days of email to synchronize|Two weeks|Selected – Drop down|
||Use SSL|True|Check|

#### Device compliance policy
In the [Intune on Azure portal](https://portal.azure.com), you can create the following device compliance policies at **Device compliance > Policies > Create Policy > Platform (iOS, Android or others) > Settings**.

**System security**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Password|Require a password to unlock mobile devices (...)|Yes|Selected – Drop down|
||Allow simple passwords (...)|No|Selected – Drop down|
||Minimum password length (...)|6|Selected – List|
|Advanced password settings|All|Not configured||
|Encryption|Require encryption on mobile device (...)|Yes|Selected – Drop down|
|Email profiles|Email account must be managed by Intune (iOS 8.0+)|Yes| Selected  – Drop down|
||Select (#)||Must select Email Configuration Policy for iOS: iOS Email Policy (see configuration policies above)|

**Device health**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Windows decide health attestation|Require devices to be reported as healthy (Windows 10 Desktop and Mobile and later)|Yes||
|Device security settings|All|Not configured||
|Device threat protection|All|Not configured||
|Jailbreak|Device must not be jailbroken or rooted (iOS 8.0+, Android 4.0+)|Yes||

**Device properties**
|Type|Properties|Values|Notes|
|:---|:---------|:-----|:----|
|Operating system version|All|Not configured||

For all the above policies to be considered deployed, they must be targeted at user groups. You can do this by creating the policy (on Save) or later by selecting Manage Deployment in the Policy section (same level as Add).

## Remediating medium or high risk access events
If a user reports that they are now expected to perform MFA when this was previously not required, support can review their status from a risk perspective.  

Users within the organization with a Global Administrator or Security Administrator role can use Azure AD Identity Protection to review the risky events that contributed to the calculated risk score. If they identify some events that were flagged as suspicious, but are confirmed to be valid (such as a login from an unfamiliar location when an employee is on vacation), the administrator can resolve the event so it no longer contributes to the risk score.
--->

## <a name="next-steps"></a><span data-ttu-id="d1374-171">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d1374-171">Next steps</span></span>

[<span data-ttu-id="d1374-172">了解用于保护 SharePoint 网站和文件的策略建议</span><span class="sxs-lookup"><span data-stu-id="d1374-172">Learn about policy recommendations for securing SharePoint Sites and files</span></span>](sharepoint-file-access-policies.md)
