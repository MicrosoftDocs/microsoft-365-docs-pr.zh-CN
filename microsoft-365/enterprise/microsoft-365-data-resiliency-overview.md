---
title: Microsoft 365 中的数据复原能力
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 在本文中，了解在 Microsoft 365 中的数据恢复和恢复的设计和原则。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a0e6ca643fe9842a71102fbabd3c05324ba52b70
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2020
ms.locfileid: "46687777"
---
# <a name="data-resiliency-in-microsoft-365"></a>Microsoft 365 中的数据复原能力

考虑到云计算的复杂特性，Microsoft 注意，如果出现问题，则不是这样，而是不会出现什么情况。 我们设计云服务，以最大限度地提高可靠性并最大限度地减少客户发生错误时对客户造成的负面影响。 我们已经迁移到依赖复杂物理基础结构的传统策略之外，我们已直接在云服务中构建冗余。 我们使用的是不太复杂的物理基础结构和更智能软件的组合，可将数据弹性构建到服务中，并为我们的客户提供高可用性。 

## <a name="resiliency-and-recoverability-are-built-in"></a>恢复能力和可恢复性内置 

在恢复能力和恢复中，首先假定基础基础结构和过程将在某个时间点失败：硬件 (基础结构) 将失败，人类将产生错误，并且软件将产生错误。 虽然软件开发人员不会在云之前考虑这些问题，但在典型的 IT 实施中如何处理这些问题在云之前是非常不同的，这是不可能的：

- 首先，硬件和基础结构保护是非常重要的。 这意味着具有99.99% 可靠性的数据中心需要大量电源和网络冗余，并且服务器是使用基于硬件的群集、双电源、双网络接口等实现的。 
- 其次，流程非常重要。 操作团队维护了严格的过程，已雇用更改窗口，并且经常发生重大的项目管理开销。 
- 第三，部署采用 glacial 节奏进行。 在不拥有资源的情况下部署代码意味着要等待修补程序版本，主版本的版本涉及硬件更换和显著的资本 outlay。 此外，更正问题的唯一方法是回滚。 因此，大多数 IT 组织仅部署主要版本，以避免工作保持最新。 
- 最后，部署的系统的规模以及其 interconnectedness 的级别以前比现在更小。 

目前，客户预期来自 Microsoft 的连续创新不会降低质量，这也是 Microsoft 服务和软件以恢复和恢复为依据而构建的原因之一。 

## <a name="microsoft-365-data-resiliency-principles"></a>Microsoft 365 数据恢复原则

弹性是指基于云的服务经受某些类型的故障的能力，但从客户的角度来看功能完全正常。 数据恢复意味着无论在 Microsoft 365 中发生什么故障，关键客户数据保持不变且不受影响。 为此，Microsoft 365 服务在设计方面围绕了五种特定的恢复原则：

- 存在关键和非关键数据。 非关键数据 (例如，邮件是否已读) 可以在罕见故障场景中将其删除。 关键数据 (例如，应以极高的成本保护客户数据（如电子邮件) ）。 作为设计目标，已传递的邮件始终是关键的，例如邮件是否已被阅读是不重要的。 
- 客户数据的副本必须分为不同的故障区域或尽可能多的故障域 (例如，数据中心可通过单个凭据访问 (进程、服务器或操作员) # A3，以提供故障隔离。 
- 必须监视关键客户数据以使原子性、一致性、隔离、持续性 (ACID) 的任何部分失败。 
- 必须保护客户数据不受损坏。 必须主动扫描或监视、修复和恢复。 
- 大多数数据丢失结果来自客户操作，因此允许客户使用 GUI 自行恢复，使他们能够还原意外删除的项目。 
 
通过将我们的云服务与这些原则相结合，Microsoft 365 能够满足和超过客户的需求，同时确保平台能够进行持续的创新和改进。 

## <a name="related-links"></a>相关链接

- [处理数据损坏](microsoft-365-dealing-with-data-corruption.md)
- [恶意软件和勒索软件防护](microsoft-365-malware-and-ransomware-protection.md)
- [监视和自愈](microsoft-365-monitoring-and-self-healing.md)
- [Exchange 数据恢复能力](microsoft-365-exchange-data-resiliency.md)
