---
title: Windows 10 位置服务
description: 如何为设备打开 Windows 定位服务
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 210356dd21b36efbb27d8faa4f8616145584159c
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929461"
---
# <a name="windows-10-location-service"></a><span data-ttu-id="ec81f-104">Windows 10 位置服务</span><span class="sxs-lookup"><span data-stu-id="ec81f-104">Windows 10 location service</span></span>

<span data-ttu-id="ec81f-105">Microsoft 托管桌面中的设备是使用 Windows Autopilot 注册的。</span><span class="sxs-lookup"><span data-stu-id="ec81f-105">Devices in Microsoft Managed Desktop are registered by using Windows Autopilot.</span></span> <span data-ttu-id="ec81f-106">此过程允许我们使用 Azure Active Directory 和 Microsoft Intune 管理它们。</span><span class="sxs-lookup"><span data-stu-id="ec81f-106">This process lets us manage them with Azure Active Directory and Microsoft Intune.</span></span> <span data-ttu-id="ec81f-107">默认情况下，当设备首次打开时，Windows 10 位置服务处于禁用状态，除非在"开箱即用体验"期间的隐私设置中启用了此功能。</span><span class="sxs-lookup"><span data-stu-id="ec81f-107">By default, the Windows 10 location service is disabled when a device is turned on for the first time unless this feature is enabled in the Privacy settings during the "out of box experience."</span></span> <span data-ttu-id="ec81f-108">这些设置在 Microsoft 托管桌面的 Autopilot 注册过程中隐藏。</span><span class="sxs-lookup"><span data-stu-id="ec81f-108">These settings are hidden during Autopilot enrollment in Microsoft Managed Desktop.</span></span> <span data-ttu-id="ec81f-109">For more information about how Autopilot is set up， see [First-run experience with Autopilot and the Enrollment Status Page](esp-first-run.md).</span><span class="sxs-lookup"><span data-stu-id="ec81f-109">For more information about how Autopilot is set up, see [First-run experience with Autopilot and the Enrollment Status Page](esp-first-run.md).</span></span>

<span data-ttu-id="ec81f-110">因此，Microsoft 托管桌面设备无法获取其设备位置，这将限制多个 Windows 功能（如时区）的功能。</span><span class="sxs-lookup"><span data-stu-id="ec81f-110">For this reason, Microsoft Managed Desktop devices can't obtain their device location, which limits the functionality of several Windows features, such as time zones.</span></span> <span data-ttu-id="ec81f-111">有关 Windows 10 位置服务详细信息，请参阅 [Windows 10 位置服务和隐私](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)。</span><span class="sxs-lookup"><span data-stu-id="ec81f-111">For more information about the Windows 10 location service, see [Windows 10 location service and privacy](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).</span></span>

<span data-ttu-id="ec81f-112">你不必使用定位服务才能参与 Microsoft 托管桌面，但用户体验将受到限制。</span><span class="sxs-lookup"><span data-stu-id="ec81f-112">You don't have to use the location service in order to participate in Microsoft Managed Desktop, but the user experience will be restricted.</span></span> <span data-ttu-id="ec81f-113">例如，当用户在不同的时区工作时，设备将无法自动确定它们所在的时区。</span><span class="sxs-lookup"><span data-stu-id="ec81f-113">For example, devices won't be able to automatically determine the time zone they're in when your users work in a different time zone.</span></span>

## <a name="enable-the-location-service"></a><span data-ttu-id="ec81f-114">启用定位服务</span><span class="sxs-lookup"><span data-stu-id="ec81f-114">Enable the location service</span></span>

<span data-ttu-id="ec81f-115">在将设备注册到 Microsoft 托管桌面服务时，可以选择使用定位服务，也可以注册后打开或关闭该服务。</span><span class="sxs-lookup"><span data-stu-id="ec81f-115">You can either opt in to using the location service when you enroll devices into the Microsoft Managed Desktop service or you can turn the service on or off after enrollment.</span></span>

### <a name="opt-in-during-enrollment"></a><span data-ttu-id="ec81f-116">在注册期间选择加入</span><span class="sxs-lookup"><span data-stu-id="ec81f-116">Opt in during enrollment</span></span>

<span data-ttu-id="ec81f-117">您可以让 Microsoft 托管桌面服务启用定位服务。</span><span class="sxs-lookup"><span data-stu-id="ec81f-117">You can have the Microsoft Managed Desktop service enable the location service.</span></span> <span data-ttu-id="ec81f-118">在注册序列中，将要求你选择是否要允许在设备上启用 Windows 10 定位服务。</span><span class="sxs-lookup"><span data-stu-id="ec81f-118">During the enrollment sequence, you'll be asked to select whether you want to allow the Windows 10 location service to be enabled on devices.</span></span>

### <a name="control-the-location-service-after-enrollment"></a><span data-ttu-id="ec81f-119">注册后控制定位服务</span><span class="sxs-lookup"><span data-stu-id="ec81f-119">Control the location service after enrollment</span></span>

<span data-ttu-id="ec81f-120">通过管理门户提交支持 (，) 定位服务处于打开状态或[关闭状态](access-admin-portal.md)。 [](../working-with-managed-desktop/admin-support.md)</span><span class="sxs-lookup"><span data-stu-id="ec81f-120">You can have the location service turned on (or off) at any time by submitting a [support request](../working-with-managed-desktop/admin-support.md) through the [Admin portal](access-admin-portal.md).</span></span>

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a><span data-ttu-id="ec81f-121">Microsoft 托管桌面如何配置 Windows 10 定位服务</span><span class="sxs-lookup"><span data-stu-id="ec81f-121">How Microsoft Managed Desktop configures the Windows 10 location service</span></span>

<span data-ttu-id="ec81f-122">如果你选择使用定位服务，我们将使用所需的最低设置，而不会影响用户的隐私。</span><span class="sxs-lookup"><span data-stu-id="ec81f-122">If you opt in to using the location service, we use the minimum settings necessary without affecting users' privacy.</span></span> <span data-ttu-id="ec81f-123">有关详细信息，请参阅 [Windows 10 位置服务和隐私](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)。</span><span class="sxs-lookup"><span data-stu-id="ec81f-123">For more information, see [Windows 10 location service and privacy](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).</span></span>

<span data-ttu-id="ec81f-124">Microsoft 托管桌面将 Windows 设置 **中的**"位置隐私"**设置** 启用为 **"允许访问此设备上的位置"。**</span><span class="sxs-lookup"><span data-stu-id="ec81f-124">Microsoft Managed Desktop enables the **Location privacy** setting in **Windows settings** to **Allow access to location on this device**.</span></span> <span data-ttu-id="ec81f-125">用户界面如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec81f-125">The user interface looks like this:</span></span>

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="Windows 设置中的位置设置":::

> [!NOTE]
> <span data-ttu-id="ec81f-127">如果你选择使用位置服务，这仅适用于 Windows 操作系统本身。</span><span class="sxs-lookup"><span data-stu-id="ec81f-127">If you opt in to using the location service, this applies only to the Windows operating system itself.</span></span> <span data-ttu-id="ec81f-128">不允许应用使用位置服务。</span><span class="sxs-lookup"><span data-stu-id="ec81f-128">Apps are not allowed to use location services.</span></span> <span data-ttu-id="ec81f-129">每个用户都可以选择是否允许应用访问其位置。</span><span class="sxs-lookup"><span data-stu-id="ec81f-129">Each user can choose whether to allow apps to access their location.</span></span>