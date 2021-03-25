---
title: 配置 Microsoft Cloud App Security 集成
ms.reviewer: ''
description: 了解如何启用设置以启用 Microsoft Defender 终结点与 Microsoft Cloud App Security 集成。
keywords: 云， 应用， 安全性， 设置， 集成， 发现， 报告
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ddf32b26191826ab6ecbad6b9d047ac7bbb6276a
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056526"
---
# <a name="configure-microsoft-cloud-app-security-in-microsoft-defender-for-endpoint"></a>在 Microsoft Defender for Endpoint 中配置 Microsoft Cloud App Security

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**适用于：**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> 想要体验 Microsoft Defender for Endpoint？ [注册免费试用版。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


若要从适用于 Endpoint 的 Microsoft Defender 云应用发现信号中获益，请启用 Microsoft Cloud App Security 集成。

>[!NOTE]
>此功能将在运行 Windows 10 版本 1709 (OS 内部版本 16299.1085（具有[KB4493441](https://support.microsoft.com/help/4493441)版本）的设备上提供企业移动性[+](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)安全性的 E5) ， Windows 10 版本 1803 (OS 内部版本 17134.704（带[KB4493464](https://support.microsoft.com/help/4493464)) 、Windows 10 版本 1809 (操作系统版本 17763.379，具有[KB4489899](https://support.microsoft.com/help/4489899)) 或更高版本的 Windows 10 版本）。

> 有关 Microsoft Defender for Endpoint 与 [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/mde-integration) 的详细集成，请参阅 Microsoft Defender for Endpoint integration with Microsoft Cloud App Security。 

## <a name="enable-microsoft-cloud-app-security-in-microsoft-defender-for-endpoint"></a>在 Microsoft Defender for Endpoint 中启用 Microsoft Cloud App Security

1. 在导航窗格中，选择 **首选项设置**  >  **高级功能**。
2. 选择 **"Microsoft Cloud App Security"，** 将开关切换到 **"开"。**
3. 单击 **保存首选项**。

激活后，Microsoft Defender for Endpoint 将立即开始将发现信号转发到 Cloud App Security。

## <a name="view-the-data-collected"></a>查看收集的数据

若要查看和访问 Microsoft Cloud Apps Security 中的 Microsoft Defender for Endpoint 数据，请参阅调查 [Cloud App Security 中的设备](https://docs.microsoft.com/cloud-app-security/mde-integration#investigate-devices-in-cloud-app-security)。


有关云发现详细信息，请参阅 [使用发现的应用](https://docs.microsoft.com/cloud-app-security/discovered-apps)。

如果你对试用 Microsoft Cloud App Security 感兴趣，请参阅 [Microsoft Cloud App Security 试用版](https://signup.microsoft.com/Signup?OfferId=757c4c34-d589-46e4-9579-120bba5c92ed&ali=1)。

## <a name="related-topic"></a>相关主题
- [Microsoft Cloud App Security 集成](microsoft-cloud-app-security-integration.md)