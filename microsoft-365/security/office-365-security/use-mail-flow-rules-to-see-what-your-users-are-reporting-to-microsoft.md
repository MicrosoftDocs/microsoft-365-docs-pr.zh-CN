---
title: 使用邮件流规则来查看用户向 Microsoft 报告的内容
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 8401f520-8e7c-467b-9e06-4a9fdb2ba548
ms.collection:
- M365-security-compliance
description: 管理员可以了解如何使用邮件流规则（也称为传输规则）接收用户向 Microsoft 报告的邮件的副本。
ms.openlocfilehash: 2b1e82ece936551c48e5617955f546cf851a8913
ms.sourcegitcommit: c7f11d851073ef14a69669f6c8b7e0c11e4bb7a1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "43939495"
---
# <a name="use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft"></a><span data-ttu-id="54881-103">使用邮件流规则来查看用户向 Microsoft 报告的内容</span><span class="sxs-lookup"><span data-stu-id="54881-103">Use mail flow rules to see what your users are reporting to Microsoft</span></span>

<span data-ttu-id="54881-104">用户可通过多种方式将邮件报告给 Microsoft 进行分析，如[报告消息和文件到 microsoft](report-junk-email-messages-to-microsoft.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="54881-104">There are multiple ways for users to report messages to Microsoft for analysis as described in [Report messages and files to Microsoft](report-junk-email-messages-to-microsoft.md).</span></span>

<span data-ttu-id="54881-105">您可以创建邮件流规则（也称为传输规则），查找用户向 Microsoft 报告的邮件，并且您可以配置密件抄送收件人以接收这些报告的邮件的副本。</span><span class="sxs-lookup"><span data-stu-id="54881-105">You can create a mail flow rule (also known as a transport rule) that looks for messages that users report to Microsoft, and you can configure Bcc recipients to receive copies of these reported messages.</span></span>

<span data-ttu-id="54881-106">您可以在 Exchange 管理中心（EAC）和 PowerShell （Exchange Online PowerShell for Microsoft 365 客户中创建邮件流规则;适用于独立 EOP 客户的 Exchange Online Protection PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="54881-106">You can create the mail flow rule in the Exchange admin center (EAC) and PowerShell (Exchange Online PowerShell for Microsoft 365 customers; Exchange Online Protection PowerShell for standalone EOP customers).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="54881-107">开始前，有必要了解什么？</span><span class="sxs-lookup"><span data-stu-id="54881-107">What do you need to know before you begin?</span></span>

- <span data-ttu-id="54881-108">您需要在 Exchange Online 或 EOP 中分配权限，然后才能执行这些过程。</span><span class="sxs-lookup"><span data-stu-id="54881-108">You need to be assigned permissions in Exchange Online or EOP before you can do these procedures.</span></span> <span data-ttu-id="54881-109">具体来说，您需要分配 "**传输规则**" 角色，默认情况下会将其分配给 "**组织管理**"、"**合规性管理**" 和 "**记录管理**" 角色。</span><span class="sxs-lookup"><span data-stu-id="54881-109">Specifically, you need to be assigned the **Transport Rules** role, which is assigned to the **Organization Management**, **Compliance Management**, and **Records Management** roles by default.</span></span> <span data-ttu-id="54881-110">有关详细信息，请参阅[在 Exchange Online 中管理角色组](https://docs.microsoft.com/Exchange/permissions-exo/role-groups)。</span><span class="sxs-lookup"><span data-stu-id="54881-110">For more information, see [Manage role groups in Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/role-groups).</span></span>

- <span data-ttu-id="54881-111">若要打开 EAC，请参阅 exchange [online 中的 exchange 管理中心](https://docs.microsoft.com/Exchange/exchange-admin-center)或 Exchange [online Protection 中的 exchange 管理中心](exchange-admin-center-in-exchange-online-protection-eop.md)。</span><span class="sxs-lookup"><span data-stu-id="54881-111">To open the EAC, see [Exchange admin center in Exchange Online](https://docs.microsoft.com/Exchange/exchange-admin-center) or [Exchange admin center in Exchange Online Protection](exchange-admin-center-in-exchange-online-protection-eop.md).</span></span>

- <span data-ttu-id="54881-112">若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="54881-112">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> <span data-ttu-id="54881-113">若要连接到独立 Exchange Online Protection，请参阅[连接到 Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell)。</span><span class="sxs-lookup"><span data-stu-id="54881-113">To connect to standalone Exchange Online Protection PowerShell, see [Connect to Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).</span></span>

- <span data-ttu-id="54881-114">有关 Exchange Online 和独立 EOP 中的邮件流规则的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="54881-114">For more information about mail flow rules in Exchange Online and standalone EOP, see the following topics:</span></span>

  - [<span data-ttu-id="54881-115">Exchange Online 中的邮件流规则（传输规则）</span><span class="sxs-lookup"><span data-stu-id="54881-115">Mail flow rules (transport rules) in Exchange Online</span></span>](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

  - [<span data-ttu-id="54881-116">Exchange Online 中的邮件流规则条件和例外（谓词）</span><span class="sxs-lookup"><span data-stu-id="54881-116">Mail flow rule conditions and exceptions (predicates) in Exchange Online</span></span>](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [<span data-ttu-id="54881-117">Exchange Online 中的邮件流规则操作</span><span class="sxs-lookup"><span data-stu-id="54881-117">Mail flow rule actions in Exchange Online</span></span>](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

## <a name="use-the-eac-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a><span data-ttu-id="54881-118">使用 EAC 创建邮件流规则以接收报告的邮件的副本</span><span class="sxs-lookup"><span data-stu-id="54881-118">Use the EAC to create a mail flow rule to receive copies of reported messages</span></span>

1. <span data-ttu-id="54881-119">In the EAC, go to **Mail flow** \> **Rules**.</span><span class="sxs-lookup"><span data-stu-id="54881-119">In the EAC, go to **Mail flow** \> **Rules**.</span></span>

2. <span data-ttu-id="54881-120">单击 "**添加** !["](../../media/ITPro-EAC-AddIcon.png) "添加" 图标，然后选择 "**创建新规则**"。</span><span class="sxs-lookup"><span data-stu-id="54881-120">Click **Add** ![Add icon](../../media/ITPro-EAC-AddIcon.png) and then select **Create a new rule**.</span></span>

3. <span data-ttu-id="54881-121">在打开的" **新规则**"窗口中，配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="54881-121">In the **New rule** page that opens, configure the following settings:</span></span>

   - <span data-ttu-id="54881-122">**名称**：输入规则的唯一描述性名称。</span><span class="sxs-lookup"><span data-stu-id="54881-122">**Name**: Enter a unique, descriptive name for the rule.</span></span> <span data-ttu-id="54881-123">例如，向 Microsoft 报告的密件抄送邮件。</span><span class="sxs-lookup"><span data-stu-id="54881-123">For example, Bcc Messages Reported to Microsoft.</span></span>

   - <span data-ttu-id="54881-124">单击“其他选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="54881-124">Click **More Options**.</span></span>

   - <span data-ttu-id="54881-125">**在以下情况下应用此规则**：选择**收件人** \> **地址包括以下任何词语**：在显示的 "**指定字词或短语**" 对话框中，输入以下值之一， **Add** ![单击 "添加](../../media/ITPro-EAC-AddIcon.png)" "添加" 图标，然后重复此步骤，直到您输入所有值为止。</span><span class="sxs-lookup"><span data-stu-id="54881-125">**Apply this rule if**: Select **The recipient** \> **address includes any of these words**: In the **Specify words or phrases** dialog that appears, enter one of the following values, click **Add** ![Add Icon](../../media/ITPro-EAC-AddIcon.png), and repeat until you've entered all the values.</span></span>

     - `junk@office365.microsoft.com`
     - `abuse@messaging.microsoft.com`
     - `phish@office365.microsoft.com`
     - `false_positive@messaging.microsoft.com`

     <span data-ttu-id="54881-126">若要编辑条目，请选择该条目**Edit** ![，然后单击](../../media/ITPro-EAC-EditIcon.png)"编辑" "编辑" 图标。</span><span class="sxs-lookup"><span data-stu-id="54881-126">To edit an entry, select it and click **Edit** ![Edit icon](../../media/ITPro-EAC-EditIcon.png).</span></span> <span data-ttu-id="54881-127">若要删除条目，请将其选中**Remove** ![，然后单击](../../media/ITPro-EAC-DeleteIcon.png)"删除删除图标"。</span><span class="sxs-lookup"><span data-stu-id="54881-127">To remove an entry, select it and click **Remove** ![Remove icon](../../media/ITPro-EAC-DeleteIcon.png).</span></span>

     <span data-ttu-id="54881-128">完成后，请单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="54881-128">When you're finished, click **OK**.</span></span>

   - <span data-ttu-id="54881-129">**执行下列**操作：选择 "**将收件人** \>添加**到密件抄送" 框**。</span><span class="sxs-lookup"><span data-stu-id="54881-129">**Do the following**: Select **Add recipients** \> **to the Bcc box**.</span></span> <span data-ttu-id="54881-130">在出现的对话框中，查找并选择要添加的收件人。</span><span class="sxs-lookup"><span data-stu-id="54881-130">In the dialog that appears, find and select the recipients that you want to add.</span></span> <span data-ttu-id="54881-131">完成后，请单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="54881-131">When you're finished, click **OK**.</span></span>

4. <span data-ttu-id="54881-132">您可以进行其他选择来审核规则、测试规则、在特定时间段内激活规则，以及其他设置。</span><span class="sxs-lookup"><span data-stu-id="54881-132">You can make additional selections to audit the rule, test the rule, activate the rule during a specific time period, and other settings.</span></span> <span data-ttu-id="54881-133">建议在强制执行规则之前对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="54881-133">We recommend testing the rule before you enforce it.</span></span>

5. <span data-ttu-id="54881-134">完成后，单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="54881-134">When you're finished, click **Save**.</span></span>

## <a name="use-powershell-to-create-a-mail-flow-rule-to-receive-copies-of-reported-messages"></a><span data-ttu-id="54881-135">使用 PowerShell 创建邮件流规则以接收报告的邮件的副本</span><span class="sxs-lookup"><span data-stu-id="54881-135">Use PowerShell to create a mail flow rule to receive copies of reported messages</span></span>

<span data-ttu-id="54881-136">本示例将新建一个名为 "密件抄送给 Microsoft" 的邮件流规则，该规则将查找通过使用本主题中所述方法报告给 Microsoft 的电子邮件，并将用户 laura@contoso.com 和 julia@contoso.com 添加为密件抄送收件人。</span><span class="sxs-lookup"><span data-stu-id="54881-136">This example creates a new mail flow rule named Bcc Messages Reported to Microsoft that looks for email messages that are reported to Microsoft by using the methods described in this topic, and adds the users laura@contoso.com and julia@contoso.com as Bcc recipients.</span></span>

```powershell
New-TransportRule -Name "Bcc Messages Reported to Microsoft" -RecipientAddressContainsWords "junk@office365.microsoft.com","abuse@messaging.microsoft.com","phish@office365.microsoft.com","false_positive@messaging.microsoft.com" -BlindCopyTo "laura@contoso.com","julia@contoso.com".
```

<span data-ttu-id="54881-137">有关语法和参数的详细信息，请参阅 [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-transportrule)。</span><span class="sxs-lookup"><span data-stu-id="54881-137">For detailed syntax and parameter information, see [New-TransportRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-transportrule).</span></span>

## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="54881-138">如何判断是否生效？</span><span class="sxs-lookup"><span data-stu-id="54881-138">How do you know this worked?</span></span>

<span data-ttu-id="54881-139">若要验证是否已将邮件流规则配置为接收报告的邮件的副本，请执行以下任一步骤：</span><span class="sxs-lookup"><span data-stu-id="54881-139">To verify that you've configured a mail flow rules to receive copies of reported messages, do any of the following steps:</span></span>

- <span data-ttu-id="54881-140">在 EAC 中，转到 **"邮件流** \> **规则** \> "。 \>选择该规则，](../../media/ITPro-EAC-EditIcon.png)然后单击 "**编辑** ![编辑" 图标，并验证设置。</span><span class="sxs-lookup"><span data-stu-id="54881-140">In the EAC, go to **Mail flow** \> **Rules** \> select the rule \> click **Edit** ![Edit icon](../../media/ITPro-EAC-EditIcon.png), and verify the settings.</span></span>

- <span data-ttu-id="54881-141">在 PowerShell 中，运行以下命令来验证设置：</span><span class="sxs-lookup"><span data-stu-id="54881-141">In PowerShell, run the following command to verify the settings:</span></span>

  ```powershell
  Get-TransportRule -Identity "Bcc Messages Reported to Microsoft" | Format-List
  ```

- <span data-ttu-id="54881-142">将测试邮件发送到其中一个报告电子邮件地址，并验证结果。</span><span class="sxs-lookup"><span data-stu-id="54881-142">Send a test messages to one of the reporting email addresses and verify the results.</span></span>