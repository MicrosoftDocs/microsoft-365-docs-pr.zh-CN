---
title: Microsoft Defender for Office 365 中的安全文档
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: 了解保险箱文档Microsoft 365 E5或Microsoft 365 E5 安全性。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0e1bd2150a04e51e0d06c6cd1c17a71a032df1a5
ms.sourcegitcommit: ebb1c3b4d94058a58344317beb9475c8a2eae9a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "53108603"
---
# <a name="safe-documents-in-microsoft-365-e5"></a>Microsoft 365 E5 中的安全文档

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**适用对象**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

保险箱文档是 Microsoft 365 E5 或 Microsoft 365 E5 安全性 中的一项功能，该功能使用[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)扫描在受保护的[](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653)视图或应用程序防护中打开的文档[和文件Office。](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46)

## <a name="what-do-you-need-to-know-before-you-begin"></a>开始前，有必要了解什么？

- 保险箱文档仅对拥有 Microsoft 365 E5 *或**Microsoft 365 E5 安全性* 许可证的用户可用。 这些许可证不包含在 Microsoft Defender for Office 365计划中。

- 保险箱文档在以前称为Microsoft 365 企业应用版 (2004 或Office 365 专业增强版) 版本中受支持。

- 访问 <https://security.microsoft.com> 打开 Microsoft 365 Defender 门户。 若要直接转到"附件 **保险箱，** 请使用 <https://security.microsoft.com/safeattachmentv2> 。

- 若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)。

- 您需要在Exchange Online中的权限，然后才能执行本文中的过程：
  - 若要保险箱文档设置，您必须是组织管理或 **安全管理员角色组** 的成员。 
  - 若要对文档保险箱只读访问权限，您需要是全局读者或安全读者 **角色组的成员**。 

  有关详细信息，请参阅 [Exchange Online 中权限](/exchange/permissions-exo/permissions-exo)。

  > [!NOTE]
  >
  > - 在 Microsoft 365 管理中心将用户添加到相应的 Azure Active Directory 角色后，将为用户提供所需的权限 _和_ Microsoft 365 中其他功能的所需权限。 有关详细信息，请参阅 [关于管理员角色](../../admin/add-users/about-admin-roles.md)。
  >
  > - [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) 中的 **仅查看组织管理人员** 角色组也提供到该功能的只读访问。

### <a name="how-does-microsoft-handle-your-data"></a>Microsoft 如何处理你的数据？

若要保护你，保险箱文档将文件发送到[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)云进行分析。 有关 Microsoft Defender for Endpoint 如何处理你的数据的详细信息，请参阅 [：Microsoft Defender for Endpoint 数据存储和隐私](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)。

通常，保险箱文档发送的文件不会在 Defender 中保留超过分析 (，通常不超过 24 小时) 。

## <a name="use-the-microsoft-365-defender-to-configure-safe-documents"></a>使用Microsoft 365 Defender配置文档保险箱文档

1. 打开Microsoft 365 Defender门户，然后转到电子邮件&协作策略 \> **&规则** 威胁策略"页面"策略"部分保险箱 \>  \>  \> **附件"。**

2. 在 **"保险箱"页上**，单击"**全局设置"。**

3. 在出现的 **"全局** 设置"飞出中，配置以下设置：
   - **打开保险箱客户端Office** 文档：将切换开关向右移动，以打开功能： ![ 打开 ](../../media/scc-toggle-on.png) 。
   - 即使 **保险箱** 文档将文件标识为恶意文件，也允许用户单击"受保护的视图"：建议将此选项保持关闭状态 (将开关保留为左侧："关闭 ![) "。 ](../../media/scc-toggle-off.png)

   完成时，请单击“保存”。

   ![保险箱在"附件"页上选择"全局"保险箱文档设置。](../../media/safe-docs-global-settings.png)

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>使用 Exchange Online PowerShell 配置保险箱文档

使用以下语法：

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- _EnableSafeDocs_ 参数为保险箱启用或禁用文档。
- _AllowSafeDocsOpen_ 参数允许或阻止用户离开受保护的视图 (也就是说，如果文档被标识为恶意) 则打开文档。

本示例为保险箱启用文档，并阻止用户打开受保护视图中标识为恶意的文档。

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

有关语法和参数的详细信息，请参阅 [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365)。

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>载入 Microsoft Defender for Endpoint Service 以启用审核功能

若要部署 Microsoft Defender for Endpoint，你需要完成部署的各个阶段。 载入后，可以在企业门户中配置Microsoft 365 Defender功能。

若要了解更多信息，请参阅 [载入到 Microsoft Defender for Endpoint 服务](/microsoft-365/security/defender-endpoint/onboarding)。 如果你需要其他帮助，请参阅解决 [Microsoft Defender 终结点载入问题](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)。

### <a name="how-do-i-know-this-worked"></a>我如何知道这有效？

若要验证是否已启用和配置保险箱文档，请执行下列任一步骤：

- 在 Microsoft 365 Defender 门户中，转到电子邮件 **& 协作** 策略 & 规则威胁策略页面策略部分 保险箱 附件全局设置，并验证启用 Office 客户端的 保险箱 文档和允许用户通过受保护的视图单击，即使 \>  \>  \>  \>  \> **保险箱 文档** 将该文件标识为恶意设置。

- 在 PowerShell 中Exchange Online以下命令并验证属性值：

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- 以下文件可用于测试文档保险箱保护。 这些文档类似于EICAR.TXT反恶意软件和防病毒解决方案的文档文件。 这些文件不有害的，但它们将触发保险箱文档保护。

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
