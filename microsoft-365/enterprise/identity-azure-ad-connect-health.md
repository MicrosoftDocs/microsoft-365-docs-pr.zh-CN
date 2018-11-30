---
title: 第 8 步：监视同步运行状况
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/13/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: 理解并配置 Azure AD Connect Health。
ms.openlocfilehash: 21cfd88617bccab3f0a2bdb51c0d320cd4568a56
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/28/2018
ms.locfileid: "26865821"
---
# <a name="step-8-monitor-synchronization-health"></a><span data-ttu-id="2a2c3-103">第 8 步：监视同步运行状况</span><span class="sxs-lookup"><span data-stu-id="2a2c3-103">Step 8: Monitor synchronization health</span></span>

<span data-ttu-id="2a2c3-104">\*\* 此步骤是可选的，适用于 Microsoft 365 企业版的 E3 和 E5 版本</span><span class="sxs-lookup"><span data-stu-id="2a2c3-104">*This step is optional and applies to both the E3 and E5 versions of Microsoft 365 Enterprise*</span></span>

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

<span data-ttu-id="2a2c3-p101">在此步骤中，将在每个本地标识服务器上安装 Azure AD Connect Health 代理，以监控由 Azure AD Connect 提供的身份基础结构和同步服务。Azure AD Connect Health 门户提供了监控信息，可以从中查看警报、性能监控、使用情况分析和其他信息。</span><span class="sxs-lookup"><span data-stu-id="2a2c3-p101">In Step 4, you'll install an Azure AD Connect Health agent on each of your on-premises identity servers to monitor your identity infrastructure and the synchronization services provided by Azure AD Connect. The monitoring information is made available in an Azure AD Connect Health portal, where you can view alerts, performance monitoring, usage analytics, and other information.</span></span>

![Azure AD Connect Health 组件](./media/identity-azure-ad-connect-health/identity-azure-ad-connect-health.png)

<span data-ttu-id="2a2c3-108">如何使用 Azure AD Connect Health 的关键设计决策是基于使用 Azure AD Connect 的方式：</span><span class="sxs-lookup"><span data-stu-id="2a2c3-108">The key design decision of how to use Azure AD Connect Health is based on how you are using Azure AD Connect:</span></span>

- <span data-ttu-id="2a2c3-109">如果你使用的是\*\*\*\*“托管身份验证”选项，请从[使用用于同步的 Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) 开始，以理解并配置 Azure AD Connect Health。</span><span class="sxs-lookup"><span data-stu-id="2a2c3-109">If you’re using the **managed authentication** option, start with [Using Azure AD Connect Health with sync](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) to understand and configure Azure AD Connect Health.</span></span>
- <span data-ttu-id="2a2c3-110">如果仅使用\*\*\*\*“联合身份验证”将帐户和组的名称与 Active Directory 联合身份验证服务 (AD FS) 同步，请从[在 AD FS 中使用 Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) 开始，以理解并配置 Azure AD Connect Health。</span><span class="sxs-lookup"><span data-stu-id="2a2c3-110">If you're synchronizing just the names of the accounts and groups using **federated authentication** with Active Directory Federation Services (AD FS), start with [Using Azure AD Connect Health with AD FS](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) to understand and configure Azure AD Connect Health.</span></span>

<span data-ttu-id="2a2c3-111">完成这一步后，将具有：</span><span class="sxs-lookup"><span data-stu-id="2a2c3-111">When you complete this step, you’ll have:</span></span>

- <span data-ttu-id="2a2c3-112">在本地标识提供者服务器上安装的 Azure AD Connect Health 代理。</span><span class="sxs-lookup"><span data-stu-id="2a2c3-112">The Azure AD Connect Health agent installed on your on-premises identity provider servers.</span></span>
- <span data-ttu-id="2a2c3-113">显示本地基础结构的当前状态，以及与 Office 365 和 EMS 订阅的 Azure AD 租户同步活动的 Azure AD Connect Health 门户。</span><span class="sxs-lookup"><span data-stu-id="2a2c3-113">The Azure AD Connect Health portal displaying the current state of your on-premises infrastructure and synchronization activities with the Azure AD tenant for your Office 365 and EMS subscriptions.</span></span>

<span data-ttu-id="2a2c3-114">作为临时检查点，请查看对应于此步骤的[退出条件](identity-exit-criteria.md#crit-identity-sync-health)。</span><span class="sxs-lookup"><span data-stu-id="2a2c3-114">As an interim checkpoint, you can see the [exit criteria](identity-exit-criteria.md#crit-identity-sync-health) for this step.</span></span>


## <a name="next-step"></a><span data-ttu-id="2a2c3-115">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2a2c3-115">Next step</span></span>

|||
|:-------|:-----|
|![](./media/stepnumbers/Step9.png)| [<span data-ttu-id="2a2c3-116">简化密码更新</span><span class="sxs-lookup"><span data-stu-id="2a2c3-116">Simplify password updates</span></span>](identity-password-writeback.md) |

