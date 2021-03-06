---
title: 调查 Microsoft Defender for Endpoint 中的用户帐户
description: 调查用户帐户以在调查期间潜在泄露的凭据或透视关联的用户帐户。
keywords: 调查， 帐户， 用户， 用户实体， 警报， Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: e98142e4076c5e695f16eb06c062bc69d3d7dd55
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935061"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>调查 Microsoft Defender for Endpoint 中的用户帐户

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>想要体验适用于终结点的 Defender？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigatgeuser-abovefoldlink)

## <a name="investigate-user-account-entities"></a>调查用户帐户实体

识别在仪表板上显示为"处于风险中的用户" (最活跃警报的用户帐户) 调查凭据可能遭到入侵的情况，或在调查警报或设备时透视关联的用户帐户，以确定具有该用户帐户的设备之间可能的横向移动。

您可以在以下视图中找到用户帐户信息：

- 仪表板
- 警报队列
- 设备详细信息页面

这些视图中提供了一个可单击的用户帐户链接，可让你访问显示有关用户帐户的更多详细信息的用户帐户详细信息页面。

调查用户帐户实体时，你将看到：

- 用户帐户详细信息、Microsoft Defender 标识警报以及登录的设备、角色、登录类型和其他详细信息
- 事件和用户设备概述
- 与此用户相关的警报
- 在组织中观测 (登录到) 

![用户帐户实体详细信息页面的图像](images/atp-user-details-view.png)

### <a name="user-details"></a>用户详细信息

左侧的用户详细信息窗格提供有关用户的信息，例如相关的打开事件、活动警报、SAM 名称、SID、Microsoft Defender for Identity 警报、用户登录的设备数、首次看到和最后一次看到用户时、角色和登录类型。 根据你已启用的集成功能，你将看到其他详细信息。 例如，如果你启用 Skype 企业集成，你将能够从门户联系用户。 Azure **ATP** 警报部分包含一个链接，如果你已启用 Microsoft Defender for Identity 功能，并且存在与用户相关的警报，该链接将你指向 Microsoft Defender for Identity 页面。 Microsoft Defender for Identity 页面将提供有关警报详细信息。

>[!NOTE]
>你需要在 Microsoft Defender for Identity 和 Defender for Endpoint 上启用集成才能使用此功能。 在 Defender for Endpoint 中，可以在高级功能中启用此功能。 若要详细了解如何启用高级功能，请参阅 [启用高级功能](advanced-features.md)。

组织中"概述"、"警报"和"观测到"是显示有关用户帐户的各种属性的不同选项卡。

### <a name="overview"></a>概述

" **概述** "选项卡显示事件详细信息以及用户已登录的设备列表。 你可以展开它们以查看每个设备的登录事件的详细信息。

### <a name="alerts"></a>警报

" **警报** "选项卡提供与用户帐户关联的警报列表。 此列表是警报队列的筛选视图，它[](alerts-queue.md)显示用户上下文为所选用户帐户的警报、检测到最后一个活动的日期、警报的简短描述、与警报关联的设备、警报的严重性、队列中警报的状态以及分配了警报的用户。

### <a name="observed-in-organization"></a>在组织中观测到

通过"在组织中观测到"选项卡，你可以指定一个日期范围，以查看观测到此用户登录的设备列表、其中每台设备的登录频率最多和登录频率最少的用户帐户，以及每台设备上观测到的用户总数。

选择"组织中观测到的项目"表上的项目将展开该项目，显示有关设备的更多详细信息。 直接选择项目内的链接将发送给相应的页面。

## <a name="search-for-specific-user-accounts"></a>搜索特定用户帐户

1. 从 **搜索** 栏 **下拉菜单中选择** 用户。
2. 在"搜索"字段中 **输入** 用户帐户。
3. 单击搜索图标或按 **Enter。**

将显示与查询文本匹配的用户列表。 你将看到用户帐户的域和名称、上次看到用户帐户的时间，以及过去 30 天内观测到它登录到的设备总数。

可以按以下时间段筛选结果：

- 1 天
- 3 天
- 7 天
- 30 天
- 6 个月

## <a name="related-topics"></a>相关主题

- [查看和组织 Microsoft Defender 终结点警报队列](alerts-queue.md)
- [管理 Microsoft Defender for Endpoint 警报](manage-alerts.md)
- [调查 Microsoft Defender for Endpoint 警报](investigate-alerts.md)
- [调查与 Defender for Endpoint 警报关联的文件](investigate-files.md)
- [调查 Defender for Endpoint Devices 列表中的设备](investigate-machines.md)
- [调查与 Defender for Endpoint 警报关联的 IP 地址](investigate-ip.md)
- [调查与 Defender for Endpoint 警报关联的域](investigate-domain.md)
