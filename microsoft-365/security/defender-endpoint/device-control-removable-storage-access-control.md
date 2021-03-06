---
title: Microsoft Defender for Endpoint 设备控件可移动存储访问控制
description: 有关 Microsoft Defender for Endpoint 的演练
keywords: 可移动存储媒体
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0b0f7c5a4a75fdc80509dbc02a43d28f7c93fd7c
ms.sourcegitcommit: 53aebd492a4b998805c70c8e06a2cfa5d453905c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2021
ms.locfileid: "53327043"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Microsoft Defender for Endpoint 设备控件可移动存储访问控制

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender for Endpoint 设备控制可移动存储访问控制使你能够执行以下任务：

- 审核，允许或阻止对可移动存储进行读取、写入或执行访问（带排除或不排除）

|Privilege |权限  |
|---------|---------|
|Access    |  读取、写入、执行       |
|操作模式    |    审核、允许、阻止     |
|云解决方案提供商支持   |   是      |
|GPO 支持    |   是      |
|基于用户的支持     |   是      |
|基于计算机的支持    |    是     |

## <a name="prepare-your-endpoints"></a>准备终结点

在存储 **4.18.2103.3** 或更高版本的 Windows 10 设备上部署可移动访问控制。

- **4.18.2104 或更高版本**：添加 SerialNumberId、VID_PID、基于 filepath 的 GPO 支持、ComputerSid

- **4.18.2105** 或更高版本：添加对 HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId 的通配符支持、特定计算机上特定用户的组合、可删除的 SSD (SanDisk 极性 SSD) /USB 附加 SCSI (UAS) 支持

- **4.18.2107 或** 更高版本：添加 Windows 可移植设备 (WPD) 支持 (移动设备（如平板电脑或) 

:::image type="content" source="images/powershell.png" alt-text="PowerShell 接口":::

> [!NOTE]
> 任何Windows 安全中心组件都不需要处于活动状态，您可以运行"可移动存储访问控制"，而不受Windows 安全中心状态。

## <a name="policy-properties"></a>策略属性

可以使用以下属性创建可移动存储组：

**属性名称：组 ID**

1. 说明 [：GUID](https://en.wikipedia.org/wiki/Universally_unique_identifier)是一个唯一 ID，表示组，将在策略中使用。

**属性名称：DescriptorIdList**

2. 说明：列出你想要在组中覆盖的设备属性。
有关每个设备属性的详细信息， **请参阅上面的设备** 属性部分。

3. 选项：
    - PrimaryId
        - RemovableMediaDevices
        - CdRomDevices
        - WpdDevices
    - DeviceId
    - HardwareId
    - InstancePathId：InstancePathId 是一个唯一标识系统中设备的字符串，例如 USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0。 末尾的号码 (例如 0&**0**) 表示可用插槽，并且可能会从设备更改为设备。 为获得最佳结果，请结尾使用通配符。 例如，USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*
    - FriendlyNameId
    - SerialNumberId
    - VID
    - PID
    - VID_PID
        - 0751_55E0：匹配此精确的 VID/PID 对
        - _55E0：将任何媒体与 PID=55E0 匹配
        - 0751_：将任何媒体与 VID=0751 匹配
        
**属性名称：MatchType** 

1. 说明：当 DescriptorIDList 中使用多个设备属性时，MatchType 定义关系。

2. 选项：

    - MatchAll：DescriptorIdList 下的任何属性将为 **And** 关系;例如，如果管理员将 DeviceID 和 InstancePathID 放在每个连接的 USB 上，系统将检查 USB 是否同时满足这两个值。
    - MatchAny：DescriptorIdList 下的属性将为 **Or** 关系;例如，如果管理员将 DeviceID 和 InstancePathID 放在每个连接的 USB 上，只要 USB 具有相同的 **DeviceID** 或 **InstanceID** 值，系统就会执行强制操作。

以下是访问控制策略属性：

**属性名称：PolicyRuleId**

1. 说明 [：GUID](https://en.wikipedia.org/wiki/Universally_unique_identifier)是一个唯一 ID，表示策略，将用于报告和疑难解答。

**属性名称：IncludedIdList**

1. 说明： (策略) 的组。 如果添加了多个组，该策略将应用于所有这些组的任何媒体。

2. 选项：必须在此实例使用组 ID/GUID。

以下示例显示 GroupID 的用法：

`<IncludedIdList> <GroupId>{EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>`

**属性名称：ExcludedIDList**

说明： (策略) 的组。

选项：必须在此实例使用组 ID/GUID。

**属性名称：条目 ID**

1. 说明：一个 PolicyRule 可以有多个条目;每个具有唯一 GUID 的条目告知设备控件一个限制。

**属性名称：Type**

1. 说明：定义 IncludedIDList 中可移动存储组的操作。
    - 强制：允许或拒绝
    - 审核：AuditAllowed 或 AuditDenied 

2. 选项：

    - 允许
    - 拒绝
    - AuditAllowed：定义允许访问时的通知和事件
    - AuditDenied：定义拒绝访问时的通知和事件;必须配合拒绝 **条目** 一起工作。

当同一媒体存在冲突类型时，系统将应用策略中的第一个冲突类型。 冲突类型的一个示例是 **"允许"和**"**拒绝"。**

**属性名称：Sid**

说明：本地计算机 Sid 或 AD 对象的 Sid 定义是否对特定用户或用户组应用此策略;一个条目最多可具有一个 Sid 和一个不带任何 Sid 的条目，这意味着在计算机中应用策略。

**属性名称：ComputerSid**

说明：本地计算机 Sid 或 AD 对象的 Sid 定义是否对特定计算机或计算机组应用此策略;一个条目最多可具有一个 ComputerSid，而一个条目没有任何 ComputerSid 意味着将策略应用到计算机。 如果要将条目应用于特定用户和特定计算机，请同时将 Sid 和 ComputerSid 添加到同一条目中。

**属性名称：Options**

说明：定义是否显示通知。

   :::image type="content" source="images/device-status.png" alt-text="可在其中查看设备状态的屏幕":::

选项：0-4。 选择"类型允许"或"拒绝"时：

   - 0：无
   - 4：对此条目 **禁用 AuditAllowed** **和 AuditDenied。** 即使 **发生阻止** 且已配置 **AuditDenied** 设置，系统也将不会显示通知。

   选择" **类型 AuditAllowed"** 或 **"AuditDenied"** 时：

   - 0：无
   - 1：显示通知
   - 2：发送事件
   - 3：显示通知和发送事件

**属性名称：AccessMask**

说明：定义访问权限。

选项 1-7：
  - 1：读取
  - 2：写入
  - 3：读取和写入
  - 4：执行
  - 5：读取和执行
  - 6：写入和执行
  - 7：读取、写入和执行

## <a name="common-removable-storage-access-control-scenarios"></a>常见的可移动存储访问控制方案

为了帮助你熟悉 Microsoft Defender for Endpoint Removable 存储访问控制，我们将一些常见方案放在一起供你遵循。

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>方案 1：阻止对全部 USB 执行写入和执行访问，但允许特定批准的 USB

1. 创建组

    1. 组 1：任何可移动存储和 CD/DVD。 可移动存储和 CD/DVD 的一个示例是：示例 Any [Removable 存储 and CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) file中的组 **9b28fae8-72f7-4267-a1a5-685f747a7146。**
    
    2. 组 2：基于设备属性批准的 USB。 此用例的一个示例是：示例已批准 [USB Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)文件中的实例 ID – 组 **65fa649a-a111-4912-9294-fb6337a25038。**

    > [!NOTE]
    > 您必须在 值 `&` 中 `&amp;` 将 替换为 。

2. 创建策略

    1. 策略 1：阻止写入和执行访问，但允许批准的 USB。 此用例的一个示例是：示例方案 [1](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)阻止写入和执行访问但允许批准的 USBs.xml文件中的 PolicyRule **c544a991-5786-4402-949e-a032cb790d0e。**
    
    2. 策略 2：审核对允许的 USB 的写入和执行访问权限。 此用例的一个示例是：对批准的 [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)文件进行审核写入和执行访问示例中的 PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c。**

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>方案 2：审核对全部（但阻止特定未批准的 USB）的写入和执行访问权限

1. 创建组

    1. 组 1：任何可移动存储和 CD/DVD。 此用例的一个示例是：示例 Any [Removable 存储 and CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) file中的 Group **9b28fae8-72f7-4267-a1a5-685f747a7146。**
    
    2. 组 2：基于设备属性（例如，供应商 ID/产品 ID、友好名称 – 组 **65fa649a-a111-4912-9294-fb6337a25038）** 的未批准 USB Group.xml文件中未批准的 [USB。](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) 

    > [!NOTE]
    > 您必须在 值 `&` 中 `&amp;` 将 替换为 。

2. 创建策略

    1. 策略 1：阻止对全部（但阻止特定未批准的 USB）的写入和执行访问。 此用例的一个示例是：示例方案 2 审核写入和执行对除阻止特定未批准的 [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)文件的访问中的 PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98。**
    
    2. 策略 2：审核写入和执行对他人的访问。 此用例的一个示例是：对 [others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)文件进行审核写入和执行访问示例中的 PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48。**

## <a name="deploying-and-managing-policy-via-group-policy"></a>通过组策略部署和管理策略

通过"存储访问控制"功能，可以通过组策略将策略应用于用户或设备，或同时应用于两者。

### <a name="licensing"></a>许可

在开始使用"可移动存储访问控制"之前，必须确认Microsoft 365 [订阅](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2)。 若要访问和使用可移动存储访问控制，您必须具有Microsoft 365 E3或Microsoft 365 E5。

### <a name="deploying-policy-via-group-policy"></a>通过组策略部署策略

1. 将所有组组合到 `<Groups>` `</Groups>` 一个 xml 文件中。 

    下图演示了方案 [1：](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs)阻止对全部 USB 进行写入和执行访问，但允许特定批准的 USB 的示例。
    
    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="显示允许在设备上允许特定批准的 USB 的配置设置的屏幕":::
    
2. 将所有规则合并到 `<PolicyRules>` `</PolicyRules>` 一个 xml 文件中。 

    如果要限制特定用户，请使用 Entry 中的 SID 属性。 如果策略条目中没有任何 SID，则条目将应用于计算机的每一个登录实例。
    
    下图演示了 SID 属性的用法，以及方案 [1：](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs)阻止对全部但允许特定批准的 USB 的写入和执行访问的示例。
    
    :::image type="content" source="images/usage-sid-property.png" alt-text="显示指示 SID 属性属性使用情况的代码的屏幕":::

3. 在网络共享文件夹中保存规则和组 XML 文件，将网络共享文件夹路径放入组策略设置：**计算机配置 -> 管理模板 -> Windows 组件 -> Microsoft Defender 防病毒 -> 设备控制："定义设备** 控制策略组"和"定义设备控制策略规则"。

    - 目标计算机必须能够访问网络共享才能拥有策略。 但是，读取策略后，不再需要网络连接，即使在计算机重新启动后也不例外。

    :::image type="content" source="images/device-control.png" alt-text="设备控制屏幕":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>通过 Intune OMA-URI 部署和管理策略

通过可移动存储访问控制功能，你可以将策略通过 OMA-URI 应用到用户或设备，或同时应用到两者。

### <a name="licensing"></a>许可

在开始使用"可移动存储访问控制"之前，必须确认Microsoft 365 [订阅](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2)。 若要访问和使用可移动存储访问控制，您必须具有Microsoft 365 E3或Microsoft 365 E5。

### <a name="permission"></a>权限

对于 Intune 中的策略部署，该帐户必须具有创建、编辑、更新或删除设备配置文件的权限。 可以创建自定义角色或使用具有这些权限的任何内置角色。

- 策略和配置文件管理器角色
- 为设备配置文件启用"创建/编辑/更新/读取/删除/查看报告"权限的自定义角色
- 全局管理员

### <a name="deploying-policy-via-oma-uri"></a>通过 OMA-URI 部署策略

**Microsoft Endpoint Manager管理中心 (https://endpoint.microsoft.com/) -> Devices -> Configuration profiles -> Create profile -> Platform： Windows 10 and later & Profile： Custom**

1. 对于每个组，创建 OMA-URI 规则：
    - OMA-URI： 

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b **GroupGUID**%7d/GroupData

      例如，对于 **示例中的任何可移动存储和 CD/DVD** 组，该链接必须为：

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData

    - 数据类型：String (XML 文件) 
    
      :::image type="content" source="images/xml-data-type-string.png" alt-text="STRING 文件的 xml 数据类型":::

2. 对于每个策略，还要创建 OMA-URI：

    - OMA-URI： 

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bFA6BE102-0784-4A2A-B010-A0BEBEBF68E1%7d/RuleData

      例如，对于示例中 **的"阻止写入和执行访问但允许批准的 USB"** 规则，该链接必须是： 

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData。

    - 数据类型：String (XML 文件) 

      :::image type="content" source="images/xml-data-type-string-2.png" lightbox="images/xml-data-type-string-2.png" alt-text="STRING 文件的 XML 文件的数据类型":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>使用 Intune 用户界面部署和管理策略

此功能 (Microsoft Endpoint Manager 管理中心 (> 设备 > 配置文件 > 创建配置文件 https://endpoint.microsoft.com/) > 平台：Windows 10 及更高版本 & 配置文件：设备控制) 尚不可用。 

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>在 Microsoft Defender for Endpoint 存储设备控件可移动访问控件数据

安全Microsoft 365门户显示受设备控件可移动控件和访问控制存储的可移动存储。 若要访问Microsoft 365安全性，您必须具有以下订阅：

- Microsoft 365 E5 报告

```kusto
//events triggered by RemovableStoragePolicyTriggered
DeviceEvents
| where ActionType == &quot;RemovableStoragePolicyTriggered&quot; 
| extend parsed=parse_json(AdditionalFields) 
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess)  
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict)  
| extend MediaBusType = tostring(parsed.BusType)  
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId) 
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId) 
| extend MediaName = tostring(parsed.MediaName) 
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy)  
| extend MediaProductId = tostring(parsed.ProductId)  
| extend MediaVendorId = tostring(parsed.VendorId)  
| extend MediaSerialNumber = tostring(parsed.SerialNumber)  
| extend MediaVolume = tostring(parsed.Volume)  
| project Timestamp, DeviceId, DeviceName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber, MediaVolume 
| order by Timestamp desc
```

:::image type="content" source="images/block-removable-storage.png" alt-text="描述可移动存储被阻止的屏幕":::

## <a name="frequently-asked-questions"></a>常见问题解答

**最大 USB 数量的可移动存储媒体限制是什么？**

我们已验证一个具有 100，000 个媒体的 USB 组 - 大小最高为 7 MB。 该策略在 Intune 和 GPO 中均有效，而未发生性能问题。

**为什么策略不起作用？**

最常见的原因是不需要反 [恶意软件客户端版本](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints)。

另一个原因是 XML 文件格式不正确，例如，未对 XML 文件中"&"字符使用正确的 markdown 格式，或者文本编辑器可能在文件的开头添加字节顺序标记 (BOM) 0xEF 0xBB 0xBF，这会导致 XML 分析不起作用。 一个简单的解决方案是下载示例文件 [， ("](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)**原始**"，**然后选择"另** 存为) 然后更新。

如果有值并且策略通过组策略进行管理，请检查客户端设备是否可以访问策略 XML 路径。

**如何知道哪个计算机正在使用组织中过期的反恶意软件客户端版本？**

可以使用以下查询在安全门户上获取反恶意软件Microsoft 365版本：
```kusto
//check the antimalware client version
DeviceFileEvents
| where FileName == "MsMpEng.exe"
| where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
| extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//| project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
| summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
| order by PlatformVersion desc
```
