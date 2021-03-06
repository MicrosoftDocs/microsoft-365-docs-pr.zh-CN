---
title: 打开"打开"功能时Microsoft 365 Defender
description: 获取有关授权、权限、初始设置以及其他与启用权限相关的产品和服务的最常见Microsoft 365 Defender
keywords: 常见问题， 常见问题， GCC， 入门， 启用 Microsoft 365 Defender， Microsoft 365 Defender， M365， 安全， 数据位置， 所需权限， 许可证资格， 设置页面
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 1ba049e9fe608ba8bd559180c5a30060b10ee9e0
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2021
ms.locfileid: "53285981"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>打开"打开"功能时Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**适用于：**
- Microsoft 365 Defender

阅读对有关打开 Microsoft 365 Defender 的最常见问题的回复，包括所需的许可证和权限[、](microsoft-365-defender.md)部署支持服务和初始设置。

有关如何打开服务的说明，请阅读打开[Microsoft 365 Defender。](m365d-enable.md)

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>我并没有许可证Microsoft 365 E5许可证。 我是否仍可以使用Microsoft 365 Defender？

具有以下非 E5 许可证的客户可以使用Microsoft 365 Defender：

- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Cloud App Security
- Defender for Office 365 (计划 2)

有关受支持的许可证的完整列表， [请阅读许可要求](prerequisites.md#licensing-requirements)。

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>是否需要安装或部署任何内容以开始使用Microsoft 365 Defender？

否，Microsoft 365 Defender已部署Microsoft 365安全服务的数据进行合并。 启用后，事件、自动化和搜寻体验将开始在已部署产品范围内工作。 如果未正确部署这些产品，Microsoft 365 Defender将不会显示任何数据，并且无法执行任何操作。

若要优化你的Microsoft 365 Defender体验，我们建议部署所有受支持的Microsoft 365[安全产品和服务](deploy-supported-services.md)。 

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>在哪里Microsoft 365 Defender和存储我的数据？

Microsoft 365 Defender为处理和存储合并数据的数据中心自动选择一个最佳位置。 如果你有适用于终结点的 Microsoft Defender，它将选择 Defender for Endpoint 所使用的相同位置。

>[!NOTE]
>Microsoft Defender for Endpoint 在通过 Azure Defender (欧盟) 数据中心自动设置。 Microsoft 365 Defender此方式预配 Microsoft Defender for Endpoint 的客户，系统将自动在同一欧盟数据中心进行预配。

数据中心位置显示在预配服务之前和之后，在 **Microsoft 365 Defender (设置 > Microsoft 365 Defender) 。** 如果你希望使用另一个数据中心位置，请选择安全中心Microsoft 365需要帮助？"，联系 Microsoft 支持人员。

## <a name="where-can-i-access-microsoft-365-defender"></a>在哪里可以访问Microsoft 365 Defender？

Microsoft 365 Defender安全Microsoft 365中提供。 若要转到安全中心，请浏览到 URL <https://security.microsoft.com> 。

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender-in-microsoft-365-security-center"></a>我需要在安全中心内访问Microsoft 365 Defender哪些Microsoft 365权限？

分配了以下 Azure AD Azure Active Directory (帐户) 可以访问Microsoft 365 Defender功能和数据：

- 全局管理员
- 安全管理员
- 安全操作员
- 全局读取者
- 安全读取者

> [!NOTE]
> Microsoft Defender for Endpoint 中基于角色的访问控制设置会影响对数据的访问。 有关详细信息，请阅读有关管理对 Microsoft 365 Defender[的访问权限](m365d-permissions.md)。

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>默认为Microsoft 365 Defender时区？

默认情况下，Microsoft 365 Defender UTC 时区显示时间信息。 你可以更改此设置以使用本地时区。 [了解如何设置时区](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>如何了解新的Microsoft 365 Defender和 UI 更新？

Microsoft 会定期通过各种渠道提供相关信息，包括：

- 邮件[中心](../../admin/manage/message-center.md)Microsoft 365 管理中心
- 安全与Microsoft 365[技术&博客文章](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

打开预览功能，获取最新公开 [可用体验](preview.md)。

## <a name="is-microsoft-365-defender-available-for-us-government-community-cloud-gcc-or-gcc-high"></a>此Microsoft 365 Defender是否适用于美国政府社区云 (GCC) 或GCC高？

目前不可用。

## <a name="related-topics"></a>相关主题

- [Microsoft 365 Defender概述](microsoft-365-defender.md)
- [打开"Microsoft 365 Defender"。](m365d-enable.md)
- [许可要求和其他先决条件](prerequisites.md)
- [部署支持的服务](deploy-supported-services.md)
- [启用预览功能](preview.md)
