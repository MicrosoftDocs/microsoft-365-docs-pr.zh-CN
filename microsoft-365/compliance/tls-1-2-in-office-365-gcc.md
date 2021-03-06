---
title: 在 Microsoft 365 GCC High 和 DoD 中禁用 TLS 1.0 和 1.1
description: 讨论 Microsoft 如何禁用对 GCC High 和 DoD 环境中 TLS 1.1 和 1.0 Microsoft 365。
author: kccross
manager: laurawi
localization_priority: Normal
search.appverid:
- MET150
audience: ITPro
ms.collection: M365-security-compliance
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 16a02985107c5f578d6d6c21bf2efc6e80297951
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919338"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>在 Microsoft 365 GCC High 和 DoD 中禁用 TLS 1.0 和 1.1

## <a name="summary"></a>摘要

为了符合联邦风险与授权管理计划 (FedRAMP) 的最新合规性标准，我们针对 Microsoft 365 高和 DoD 环境禁用 Microsoft 365 中的传输层安全性 (TLS) 版本 1.1 和 GCC 1.0。 此更改之前通过 Microsoft 支持在准备在 Office 365 中强制使用[TLS 1.2 中公布](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)。

数据的安全性非常重要，我们承诺就可能影响服务使用的更改透明化。

尽管 [Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) 实施没有已知的安全漏洞，但我们仍致力于遵守 FedRAMP 合规性标准。 因此，我们在 Microsoft 365 High 和 DoD GCC 2020 年 1 月 15 日禁用了 Microsoft 365 中的 TLS 1.1 和 1.0。 若要了解如何删除 TLS 1.1 和 1.0 依赖项，请参阅以下白皮书：

[解决 TLS 1.0 问题](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>详细信息

从 2020 年 1 月 15 Microsoft 365，GCC高和 DoD 环境中将禁用 TLS 1.1 和 1.0。

到 2020 年 1 月 15 日，客户端服务器和浏览器服务器的所有组合都应使用 TLS 版本 1.2 (或更高版本) 以确保可以建立所有连接，而不会与 Microsoft 365 发生问题。 这可能需要更新客户端服务器和浏览器服务器的某些组合。

对于SharePoint和OneDrive，需要更新和配置 .NET 以支持 TLS 1.2。 有关信息，请参阅[如何在客户端上启用 TLS 1.2。](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client)

您必须更新客户端计算机，以确保保持对 Office 365 GCC 高和 DoD 的不间断访问。

你需要更新通过 TLS 1.0 或 TLS 1.1 调用 Microsoft 365 API 的应用程序，以使用 TLS 1.2。 .NET 4.5 默认为 TLS 1.1。 若要更新 .NET 配置，请参阅如何在客户端上启用传输层安全性[ (TLS) 1.2。](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client) 有关详细信息，请参阅在 Office 365 中准备强制使用[TLS 1.2。](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)

我们知道以下客户端应用程序无法使用 TLS 1.2：

- Android 4.3 和更低的版本
- Firefox 版本 5.0 及更低版本
- Internet Explorer 8 7 和早期版本Windows 10
- Internet Explorer 10 8.0 Windows Phone上
- Safari 6.0.4/OS X 10.8.4 及更早版本

虽然当前对 Microsoft Online 服务连接的分析表明，大多数服务和终结点几乎看不到 TLS 1.1 和 1.0 的使用情况，但我们提供了此更改的通知，以便你能够在必要时更新任何受影响的客户端或服务器，然后再结束对 TLS 1.1 和 1.0 的支持。 如果要将任何本地基础结构用于混合方案或 Active Directory 联合身份验证服务 (AD FS) ，请确保该基础结构可以支持使用 TLS 1.2 (或更高版本) 的入站和出站连接。

除了使用无法使用 TLS 1.2 的列出的客户端时可能会遇到的中断之外，删除 TLS 1.1 和 1.0 将阻止你使用以下 Microsoft 产品：

- Lync 电话

## <a name="references"></a>参考

有关帮助确保客户端使用 TLS 1.2 的指导和参考，请参阅 Office 365 中的准备强制[使用 TLS 1.2。](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)