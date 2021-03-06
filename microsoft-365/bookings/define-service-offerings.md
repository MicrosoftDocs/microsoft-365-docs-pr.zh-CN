---
title: 在 Bookings 中定义服务产品
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: 有关输入服务产品/服务信息的说明，包括服务名称、说明、位置、持续时间和定价。 还可以标记有资格提供服务的员工。
ms.openlocfilehash: 095188546c01149a793a478a3cbd5ac9fbeb5524
ms.sourcegitcommit: 7c0873d2a804f17697844fb13f1a100fabce86c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "47962533"
---
# <a name="define-your-service-offerings-in-bookings"></a>在 Bookings 中定义服务产品

在 Microsoft Bookings 中定义服务产品/服务时，你可以设置服务名称、说明、位置 (选择是希望自己开会还是参加联机会议) 、持续时间、向客户和员工发送的默认提醒、有关服务的内部说明以及定价。 还可以标记有资格提供服务的员工。 然后，当客户到您的业务网站预订约会时，他们可以看到确切可用的约会类型、选择要提供服务的人及其服务成本。

您还可以将自定义信息和 URL 添加到你在某人通过你的预订页面预订服务时发送的电子邮件确认和提醒。

## <a name="create-the-service-details"></a>创建服务详细信息

1. 转到"[管理服务"页，](https://outlook.office.com/bookings/services)然后选择"**添加服务"。**

2. **服务** 名称：输入服务的名称。 这是将在"日历"页上的下拉菜单中显示的名称。 当任何人在日历页面上手动添加约会时，此名称也会显示，并且它将在自助服务页面上显示为磁贴。

3. **说明**：输入的说明是当用户单击"自助服务"页面上的信息图标时将显示的内容。

4. **默认位置**：此位置将在员工和客户确认和提醒电子邮件中显示，并且将显示在为预订创建的日历事件上。

5. **添加联机** 会议：此设置启用或禁用每个约会（通过 Teams 或 Skype）的联机会议，具体取决于您将哪一个配置为员工成员的默认客户端。

    - 已启用：

        - 指向会议Teams或 Skype 会议的链接（对于预订是唯一的）将添加到员工和客户日历上的日历事件，以及拨入信息。
        - 用于加入会议的链接将添加到所有确认和提醒电子邮件中，如以下示例所示：

        :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="在 Bookings 中Teams会议的链接示例":::

        > [!NOTE]
        > Teams，可以通过 Teams 移动应用、桌面Teams、Web 浏览器或电话拨入加入会议。 我们强烈建议将 Teams启用为租户的默认联机会议服务，以获得最佳预订虚拟约会体验。

    - 已禁用：
        - 约会将不包含会议选项，并且启用"添加联机会议"时显示的所有与会议相关的字段将不会显示。

6. **默认持续时间**：这是所有会议的预定时间。 从开始时间（在预订期间选择）开始阻止时间。 将阻止员工日历上的完全约会时间。

7. **客户无法预订的** 缓冲时间：启用此设置后，每次预订约会时，都会向员工日历添加额外时间。

    将在员工的日历上阻止该时间，并影响忙/闲信息。 这意味着，如果约会在下午 3：00 结束，并且会议结束时添加了 10 分钟的缓冲区时间，则员工日历将显示为忙碌且不可预订，直到下午 3：10。 如果员工在会议前需要时间进行准备（例如审阅患者图表的顾问或准备相关帐户信息的财务顾问）可能很有用。 在会议后（例如，当某人需要时间前往另一个位置时）它也可能很有用。

8. **允许客户管理其** 预订：此设置确定客户是否可以修改或取消其预订（如果预订是通过 Bookings Web 应用上的"日历"选项卡预订的）。

    - 已启用：

        客户 **确认** 电子邮件中将显示"管理预订"按钮。 当客户选择此按钮时，将显示三个选项：
        - **重新计划** 选择此选项将用户带到特定于服务的 Self-Service 页面，在此页面中，用户可以从原始预订中选择相同服务和相同员工的新时间和/或日期。 请注意，即使默认情况下原始员工附加到重新安排的预订，用户也具有更改员工成员的选项。
        - **取消预订** 这将取消预订，并从员工日历中删除它。
        - **新预订** 此选项将用户带到"Self-Service"页面，并列出所有服务和员工，以计划新的预订。

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bookings 中的&quot;管理预订&quot;按钮":::

        只有在你熟悉客户访问该页面时，才建议Self-Service此设置。

    - 已禁用：

        当用户通过 Bookings Web 应用的"日历"选项卡进行预订时，将不能重新安排或取消预定。 但是，当通过 Self-Service 页面进行预订时，即使禁用此设置，客户仍将拥有"管理预订"按钮及其所有选项。

        如果希望限制对页面页面的访问，建议Self-Service此设置。 此外，我们建议将文本添加到你的确认和提醒电子邮件中，告知客户如何通过其他方式更改其预订，例如通过致电办公室或通过电子邮件发送技术支持。

9. **每个事件的最大参与者数** 此设置允许你创建需要多个人能够预订同一约会时间和相同员工预约的服务 (如健身课程) 。 所选服务的约会时间段、员工和时间将可供预订，直到达到指定的最大与会者数。 可以在 Bookings Web 应用的"日历"选项卡中查看当前约会容量和与会者。

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="在 Bookings 中设置最大与会者数的示例":::

10. **默认价格**  这是将在"价格"页上Self-Service的价格。 如果选择 **"未设置** 价格"，将不会显示任何价格或对成本或定价的引用。

11. **备注** 此字段显示在预订员工的预订事件以及 Bookings Web 应用中"日历"选项卡上显示的事件中。

12. **自定义域** 如果客户需要回答任何问题才能成功预订，此部分允许添加或删除问题。

    - 客户电子邮件、电话号码、地址和注释都是不可删除的字段，但您可以通过在每个字段旁边取消选择"必需"来使其可选。 

    - 通过选择"添加问题"，可以添加多个选择或文本 **响应问题**。

        每次预订特定约会时收集所需信息时，自定义字段可能很有用。 示例包括的访问前保险提供商、贷款类型、学院咨询服务的主要研究或候选人面试的候选人 ID。

13. **提醒和确认** 这两种类型的电子邮件在约会前的指定时段发送给客户、员工或两者。 根据你的偏好，可以针对每个约会创建多个邮件。

    - 默认确认和提醒电子邮件包括有关约会的基本信息，例如客户/客户名称、员工姓名、已预订的服务或约会以及约会的时间。 对于联机会议，还将包含加入链接。 如果启用此设置，还可以包括管理预订 (如步骤 8 中所述) 。

        :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="来自 Bookings 的确认电子邮件":::

    - （可选）你可以在此处添加任何要添加的文本，例如有关日程安排或客户应为约会带来哪些信息。 下面是添加到原始确认电子邮件的自定义文本示例，如"电子邮件确认的其他信息" **字段** 所示：

        :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Bookings 电子邮件中的附加信息":::

14. **为客户启用短信通知** 如果选中短信，则只会在用户选择加入时，才将邮件发送给客户。

    - 手动预订和预订页面上的"选择加入Self-Service框：

        :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Bookings 中的选择加入框":::

    - 短信通知将如下所示， (请注意短信目前仅在北美地区提供) ：

        :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="来自 Bookings 的文本通知":::

15. **发布选项** 选择是让此服务显示为可预订Self-Service页上，还是使该服务仅在 Bookings Web 应用程序的"日历"选项卡上可预订。

16. **计划策略** 此设置确定如何查看约会时间，以及可以预订或取消的时间段。

17. **电子邮件通知** 设置电子邮件何时发送给组织员工以及客户或客户。

18. **员工** 选中此复选框，客户或客户可以选择特定的员工进行约会。

    - 已启用：

        客户在"约会"页面上进行预订时，可以从分配给约会的所有Self-Service选择。 选择"任何人 **"** 选项将允许 Bookings 随机选择一个可用的员工，以分配给该约会。

    - 已禁用：

        客户通过"Self-Service"页面预订可以选择服务和时间和日期。 将随机预订可用员工。 请注意，通过 Bookings Web 应用中的"日历"选项卡预订时，仍可选择特定员工。

19. **可用性** 以下选项确定何时可以预订服务：

    - **员工空闲时可预订** 该服务根据员工在工作时间内空闲的时间保持可用性，没有额外的时间限制。

    - **每周 (自定义小时数)** 该服务具有一个额外的可用性层，除了 (工作时间或员工工作时间限制外，还可以进一步限制) 。 如果只能在特定时间提供或执行服务，请使用此选项。

    - **为日期范围设置不同的可用性** 此设置会影响特定时间点的可用性，而不是定期影响可用性。 例如，当服务所需的计算机暂时提供服务和不可用时，或者组织因假日而关闭时，就可以使用此功能。

20. **分配员工** 选择员工 (，只要你已将员工添加到"员工"选项卡) 该特定服务可预订的人员。 选择任何单个员工将导致所有员工都分配到该服务。