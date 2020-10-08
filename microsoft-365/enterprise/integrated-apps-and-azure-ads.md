---
title: 适用于 Microsoft 365 管理员的集成应用和 Azure AD
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: 了解如何在 Azure AD 中注册和管理 Office 365 集成的应用程序，从而允许全局管理员级别的应用程序授权。
ms.openlocfilehash: 1e84b5e6f82848bf1d100004bcd2711ad2e9ed39
ms.sourcegitcommit: 11d1044c6600b1f568b6dc8a53db9b07f2f0ad1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2020
ms.locfileid: "48384898"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>适用于 Microsoft 365 管理员的集成应用和 Azure AD

除了 [管理用户对应用的同意](https://docs.microsoft.com/microsoft-365/admin/misc/integrated-apps)之外，还有更多的管理集成的应用程序。 随着 Microsoft 365 REST Api 的出现，用户可以向应用授予对其 Microsoft 365 数据（如邮件、日历、联系人、用户、组、文件和文件夹）的访问权限。 默认情况下，用户需要单独向每个应用授予权限。 

但是，如果您希望在全局管理员级别对应用程序进行授权，并通过应用启动器将其部署到整个组织，则无法很好地进行扩展。 为此，必须在 Azure Active Directory (Azure AD) 中注册应用程序。 在 Azure AD 中注册应用程序之前需要执行一些步骤，以及你应该知道哪些可帮助你管理 Microsoft 365 组织中的应用程序的背景信息。
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>适用于 Microsoft 365 管理员的 Azure AD 资源

必须先执行以下两项任务，然后才能在 Azure AD 中管理 Microsoft 365 应用。
  
|先决条件|备注|
|:-----|:-----|
|[使用免费的 Azure AD 订阅](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |对 Microsoft 365 的每个付费订阅都提供了 Azure AD 的免费订阅。 您可以使用 Azure AD 管理您的应用程序，并创建和管理用户和组帐户。 若要使用 Azure AD，请转到 Azure 门户， [https://portal.azure.com](https://portal.azure.com) 并使用 Microsoft 365 帐户进行登录。  <br/> |
|[管理用户同意应用程序](https://docs.microsoft.com/microsoft-365/admin/misc/integrated-apps) <br/> |您必须对应用程序的用户同意进行管理，以允许第三方应用访问用户 Microsoft 365 信息，并让您在 Azure AD 中注册应用程序。 例如，当某用户使用第三方应用时，该应用可能会请求权限来访问其日历和编辑 OneDrive 文件夹中的文件。  <br/> |
   
管理 Microsoft 365 应用程序需要你了解 Azure AD 中的应用程序。 使用这些文章可为你提供所需的背景。
  
|文章|备注|
|:-----|:-----|
|[满足 Microsoft 365 应用启动器](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |如果你不熟悉应用启动器，你可能会想知道它是什么以及如何使用它。 应用启动器旨在帮助你从 Microsoft 365 中的任何位置访问你的应用程序。  <br/> |
|[Office 365 管理 Api 概述](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |Microsoft 365 管理 Api 允许你提供对 Microsoft 365 数据的访问权限，包括他们最关心的事情—他们的邮件、日历、联系人、用户和组、文件和文件夹。 <br/> |
|[在 Azure AD 中集成应用程序](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | 了解与 Azure AD 集成的应用程序，以及如何注册您的应用程序，了解已注册应用程序背后的概念，并了解多租户应用程序的品牌指南。  <br/> |
|[将自定义磁贴添加到应用启动器](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |Microsoft 365 中的应用启动器使用户能够更轻松地查找和访问其应用程序。 本文介绍了您作为开发人员可以在用户的应用程序启动器中显示您的应用程序的方法，同时还为他们提供了使用其 Microsoft 365 凭据的单一登录 (SSO) 体验。  <br/> |
|[Azure AD 集成教程](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |这些教程的目标是向您介绍如何为第三方 SaaS 应用程序配置 Azure AD SSO。  <br/> |
|[Azure AD 的身份验证场景](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD 通过提供标识作为一项服务来简化对开发人员的身份验证，并支持对行业标准协议（如 OAuth 2.0 和 OpenID Connect）以及针对不同平台的开放源库，以帮助您快速开始编码。 本文档可帮助您了解 Azure AD 支持的各种方案，并说明如何开始。  <br/> |
|[应用程序访问](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |通过 Azure AD，可以轻松地将当今流行软件的许多与服务 (SaaS) 应用程序集成在一起。 它提供了标识和访问管理，并为用户提供了一个访问面板，用户可在其中发现他们拥有的应用程序访问权限以及它们可以使用 SSO 访问其应用程序的位置。 本文为您提供了相关资源的链接，这些资源使您能够详细了解 Azure AD 的应用程序访问增强功能，以及如何参与这些增强。  <br/> |
|[个性化设置 Office 365 体验](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |您可以通过在 Microsoft 365 应用启动器中添加或删除应用程序，快速访问您每天使用的应用程序。  <br/> |

