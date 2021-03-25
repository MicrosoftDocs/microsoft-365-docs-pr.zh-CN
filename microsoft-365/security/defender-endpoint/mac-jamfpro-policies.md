---
title: 在 Jamf Pro 中设置适用于 macOS 的 Microsoft Defender ATP 策略
description: 了解如何在 Jamf Pro 中设置适用于 macOS 的 Microsoft Defender ATP 策略
keywords: 策略， microsoft， defender， atp， mac， 安装， 部署， 卸载， intune， jamfpro， macos， catalina， mojave， high sierra
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
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1559d8dca6b6909f22473c5a8f4d25d4bac501d1
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "51054956"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-for-macos-policies-in-jamf-pro"></a>在 Jamf Pro 中设置适用于 macOS 的 Microsoft Defender for Endpoint 策略

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**适用于：**

- [适用于 Mac 的终结点的 Defender](microsoft-defender-endpoint-mac.md)

此页面将指导你完成在 Jamf Pro 中设置 macOS 策略所需的步骤。

需要执行以下步骤：

1. [获取适用于终结点的 Microsoft Defender 载入程序包](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)

2. [使用载入程序包在 Jamf Pro 中创建配置文件](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)

3. [为终结点设置配置 Microsoft Defender](#step-3-configure-microsoft-defender-for-endpoint-settings)

4. [为终结点通知设置配置 Microsoft Defender](#step-4-configure-notifications-settings)

5. [配置 Microsoft AutoUpdate (MAU) ](#step-5-configure-microsoft-autoupdate-mau)

6. [授予对 Microsoft Defender for Endpoint 的完全磁盘访问权限](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)

7. [批准适用于终结点的 Microsoft Defender 内核扩展](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)

8. [批准适用于终结点的 Microsoft Defender 的系统扩展](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)

9. [配置网络扩展](#step-9-configure-network-extension)

10. [使用 Microsoft Defender for Endpoint for Mac 计划扫描](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)

11. [部署适用于 macOS 的 Microsoft Defender for Endpoint](#step-11-deploy-microsoft-defender-for-endpoint-for-macos)


## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>步骤 1：获取适用于终结点的 Microsoft Defender 载入程序包

1. 在 [Microsoft Defender 安全中心](https://securitycenter.microsoft.com )中，导航到">**载入"。** 

2. 选择 macOS 作为操作系统，选择移动设备管理/Microsoft Intune 作为部署方法。

    ![Microsoft Defender 安全中心的图像](images/onboarding-macos.png)

3. 选择 **下载载入程序包 (WindowsDefenderATPOnboardingPackage.zip) 。**

4. 提取 `WindowsDefenderATPOnboardingPackage.zip` 。

5. 将文件复制到首选位置。 例如，`C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`。


## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>步骤 2：使用载入程序包在 Jamf Pro 中创建配置文件

1. 找到上 `WindowsDefenderATPOnboarding.plist` 一部分中的文件。

   ![WindowsDefenderATPOnboarding 文件的图像](images/plist-onboarding-file.png)

 
2. 在 Jamf Pro 仪表板中，选择"新建 **"。**

    ![创建新的 Jamf Pro 仪表板的图像](images/jamf-pro-configure-profile.png)

3. 输入以下详细信息：

   **常规**
   - 名称：macOS 的 MDATP 载入
   - 说明：适用于 macOS 的 MDATP EDR 载入
   - 类别：无
   - 分发方法：自动安装
   - 级别：计算机级别

4. 在 **"应用程序&自定义设置"中选择**"配置 **"。**

    ![配置应用和自定义设置的图像](images/jamfpro-mac-profile.png)

5. 选择 **"将文件 (PLIST 文件**) ，然后在首选项 **域中输入** `com.microsoft.wdav.atp` ：。 

    ![jamfpro plist 上载文件的图像](images/jamfpro-plist-upload.png)

    ![上载文件属性列表文件的图像](images/jamfpro-plist-file.png)

7. 选择 **"** 打开"并选择载入文件。

    ![载入文件的图像](images/jamfpro-plist-file-onboard.png)

8. 选择 **"上载"。** 

    ![上传 plist 文件的图像](images/jamfpro-upload-plist.png)


9. 选择" **范围"** 选项卡。

    ![范围选项卡的图像](images/jamfpro-scope-tab.png)

10. 选择目标计算机。

    ![目标计算机的图像](images/jamfpro-target-computer.png)

    ![目标图像](images/jamfpro-targets.png) 

11. 选择“**保存**”。

    ![部署目标计算机的图像](images/jamfpro-deployment-target.png)

    ![选择的目标计算机的图像](images/jamfpro-target-selected.png)

12. 选择“**完成**”。

    ![目标组计算机的图像](images/jamfpro-target-group.png)

    ![配置文件列表](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>步骤 3：为终结点设置配置 Microsoft Defender

1.  使用以下 Microsoft Defender for Endpoint 配置设置：

    - enableRealTimeProtection
    - passiveMode
    
    >[!NOTE]
    >默认情况下未打开，如果计划运行适用于 macOS 的第三方 AV，请将其设置为 `true` 。

    - 排除项
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats
    
    >[!NOTE]
    >EICAR 位于示例中，如果你要通过概念证明，请删除它，尤其是在你测试 EICAR 时。
        
    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - tags
    - hideStatusMenuIcon
    
     有关信息，请参阅 [Jamf 配置文件的属性列表](mac-preferences.md#property-list-for-jamf-configuration-profile)。

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. 将文件另存为 `MDATP_MDAV_configuration_settings.plist` 。


3.  在 Jamf Pro 仪表板中，选择"常规 **"。**

    ![新 Jamf Pro 仪表板的图像](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. 输入以下详细信息：

    **常规**
    
    - 名称：MDATP MDAV 配置设置
    - 说明：\<blank\>
    - 类别：默认 (无) 
    - 分发方法：使用默认 (自动) 
    - 级别：计算机级别 (默认) 

    ![MDATP MDAV 配置设置的图像](images/3160906404bc5a2edf84d1d015894e3b.png)

5. 在 **"应用程序&自定义设置"中选择**"配置 **"。**

    ![应用和自定义设置的图像](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. 选择 **"将文件 (PLIST 文件) "。**

    ![配置设置 plist 文件的图像](images/6f85269276b2278eca4bce84f935f87b.png)

7. 在 **首选项域中，** 输入 `com.microsoft.wdav` ，然后选择上载  **PLIST 文件**。

    ![配置设置首选项域的图像](images/db15f147dd959e872a044184711d7d46.png)

8. 选择 **"选择文件"。**

    ![配置设置选择文件的图像](images/526e978761fc571cca06907da7b01fd6.png)

9. 选择 **"MDATP_MDAV_configuration_settings.plist"，** 然后选择"打开 **"。**

    ![mdatpmdav 配置设置的图像](images/98acea3750113b8dbab334296e833003.png)

10. 选择 **"上载"。**

    ![配置设置上载的图像](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![配置设置上载图像的图像](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    >[!NOTE]
    >如果你发生上载 Intune 文件的情况，你将看到以下错误：<br>
    >![配置设置 intune 文件上载的图像](images/8e69f867664668796a3b2904896f0436.png)


11. 选择“**保存**”。 

    ![配置设置的图像 保存映像](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. 文件已上载。

    ![配置文件上载图像的图像](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![已上载的配置设置文件的图像](images/a422e57fe8d45689227e784443e51bd1.png)

13. 选择" **范围"** 选项卡。

    ![配置设置作用域的图像](images/9fc17529e5577eefd773c658ec576a7d.png)

14. 选择 **Contoso 的机器组**。 

15. 选择 **"添加"，** 然后选择"**保存"。**

    ![配置设置的图像 addsav](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![配置设置保存添加的图像](images/6f093e42856753a3955cab7ee14f12d9.png)

16. 选择“**完成**”。 你将看到新的 **配置配置文件**。

    ![配置设置配置配置文件映像的图像](images/dd55405106da0dfc2f50f8d4525b01c8.png)


## <a name="step-4-configure-notifications-settings"></a>步骤 4：配置通知设置

这些步骤适用于加泰罗尼亚语或 (macOS 10.15) macOS 10.15。

1. 从 `notif.mobileconfig` [GitHub 存储库下载](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig)

2. 将其另存为 `MDATP_MDAV_notification_settings.plist` 。

3. 在 Jamf Pro 仪表板中，选择"常规 **"。** 
       
4. 输入以下详细信息：

    **常规** 
    
    - 名称：MDATP MDAV 通知设置
    - 说明：macOS 10.15 (加泰罗尼亚语) 或更高版本
    - 类别：默认 (无) 
    - 分发方法：使用默认 (自动) 
    - 级别：计算机级别 (默认) 

    ![配置设置 mdatpmdav 的图像](images/c9820a5ff84aaf21635c04a23a97ca93.png)


5. 选择 **"将文件 (PLIST 文件) "。**

    ![配置设置上载 plistfile 的图像](images/7f9138053dbcbf928e5182ee7b295ebe.png)
 

6. 选择 **"文件**  >  **MDATP_MDAV_Notification_Settings.plist"。**


    ![配置设置 mdatpmdav notsettings 的图像](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)


    ![配置设置 mdatpmdav notifsettings 的图像](images/20e33b98eb54447881dc6c89e58b890f.png)

7. 选择 **"打开**  >  **上载"。**

    ![配置设置 upl img 的图像](images/7697c33b9fd376ae5a8023d01f9d3857.png)


    ![配置设置 upl 映像的图像](images/2bda9244ec25d1526811da4ea91b1c86.png)

8. 选择"**范围"** 选项卡，然后选择"添加 **"。**

    ![配置设置范围添加的图像](images/441aa2ecd36abadcdd8aed03556080b5.png)


9. 选择 **Contoso 的机器组**。 

10. 选择 **"添加"，** 然后选择"**保存"。**
    
    ![配置设置的图像 contoso 计算机 grp 保存](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    
    ![配置设置添加保存的图像](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

11. 选择“**完成**”。 你将看到新的 **配置配置文件**。
    ![配置设置完成 img 的图像](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>步骤 5：配置 Microsoft AutoUpdate (MAU) 

1. 使用以下 Microsoft Defender for Endpoint 配置设置：

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
   </dict>
   </plist>
   ```

2. 将其另存为 `MDATP_MDAV_MAU_settings.plist` 。

3. 在 Jamf Pro 仪表板中，选择"常规 **"。** 

    ![配置设置常规映像的图像](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. 输入以下详细信息：

    **常规** 
    
    - 名称：MDATP MDAV MAU 设置
    - 说明：适用于 macOS 的 MDATP 的 Microsoft AutoUpdate 设置
    - 类别：默认 (无) 
    - 分发方法：使用默认 (自动) 
    - 级别：计算机级别 (默认) 

5. 在 **"应用程序&自定义设置"中选择**"配置 **"。**

    ![配置设置应用和自定义设置的图像](images/1f72e9c15eaafcabf1504397e99be311.png)

6. 选择 **"将文件 (PLIST 文件) "。**

    ![配置设置 plist 的图像](images/1213872db5833aa8be535da57653219f.png)  

7. In **Preference Domain** enter： ， then select Upload `com.microsoft.autoupdate2` **PLIST File**.

    ![配置设置 pref 域的图像](images/1213872db5833aa8be535da57653219f.png)

8. 选择 **"选择文件"。**

    ![配置设置 choosefile 的图像](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. 选择 **"MDATP_MDAV_MAU_settings.plist"。**

    ![配置设置 mdatpmdavmau 设置的图像](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. 选择 **"上载"。**
    ![配置设置设置的图像](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![配置设置设置的图像](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. 选择“**保存**”。

    ![配置设置 saveimg 的图像](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. 选择" **范围"** 选项卡。
   
     ![配置设置作用域tab的图像](images/10ab98358b2d602f3f67618735fa82fb.png)

13. 选择“**添加**”。
    
    ![配置设置 addimg1 的图像](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![配置设置 addimg2 的图像](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![配置设置 addimg3 的图像](images/321ba245f14743c1d5d51c15e99deecc.png)

14. 选择“**完成**”。
    
    ![配置设置完成映像的图像](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>步骤 6：向 Microsoft Defender for Endpoint 授予完全磁盘访问权限

1. 在 Jamf Pro 仪表板中，选择 **"配置文件"。**

    ![配置设置配置文件的图像](images/264493cd01e62c7085659d6fdc26dc91.png)

2. 选择 **+ 新建**。 

3. 输入以下详细信息：

    **常规** 
    - 名称：MDATP MDAV - 授予对 EDR 和 AV 的完全磁盘访问权限
    - 说明：在 macOS 加泰罗尼亚语或更高版本上，新的隐私首选项策略控制
    - 类别：无
    - 分发方法：自动安装
    - 级别：计算机级别


    ![配置设置常规的图像](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. 在 **"配置隐私首选项策略控制"中，选择**"**配置"。**

    ![配置隐私策略控制的图像](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. 在 **"隐私首选项策略控制"中**，输入以下详细信息：

    - 标识符： `com.microsoft.wdav`
    - 标识符类型：捆绑包 ID
    - 代码要求： `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`


    ![配置设置隐私首选项策略控制详细信息的图像](images/22cb439de958101c0a12f3038f905b27.png)

6. 选择“+ 添加”。

    ![配置设置的图像添加系统策略所有文件](images/bd93e78b74c2660a0541af4690dd9485.png)

    - 在"应用或服务：设置为 **SystemPolicyAllFiles" 下**

    - 在"访问"下：设置为 **"允许"**

7. 选择 **" (** 不是右下角的) 。

    ![配置设置保存图像的图像](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. 单击 `+` "应用访问" **旁边的** 符号添加新条目。

    ![配置设置应用访问的图像](images/tcc-add-entry.png)

9. 输入以下详细信息：

    - 标识符： `com.microsoft.wdav.epsext`
    - 标识符类型：捆绑包 ID
    - 代码要求： `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. 选择“+ 添加”。

    ![配置设置 tcc epsext 条目的图像](images/tcc-epsext-entry.png)

    - 在"应用或服务：设置为 **SystemPolicyAllFiles" 下**

    - 在"访问"下：设置为 **"允许"**

11. 选择 **" (** 不是右下角的) 。

    ![配置设置 tcc epsext 图像 2 的图像](images/tcc-epsext-entry2.png)

12. 选择" **范围"** 选项卡。

    ![配置设置作用域的图像](images/2c49b16cd112729b3719724f581e6882.png)

13. 选择“+ 添加”。

    ![配置设置 addimage 的图像](images/57cef926d1b9260fb74a5f460cee887a.png)

14. Select **Computer Groups** > under Group Name **>** select **Contoso's MachineGroup**. 

    ![配置设置 contoso machinegrp 的图像](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. 选择“**添加**”。 

16. 选择“**保存**”。 
    
17. 选择“**完成**”。
    
    ![配置设置的图像](images/809cef630281b64b8f07f20913b0039b.png)
    
    ![配置设置 donimg2 的图像](images/6c8b406ee224335a8c65d06953dc756e.png)


## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>步骤 7：批准适用于终结点的 Microsoft Defender 内核扩展

1. 在"**配置文件"中**，选择 **"+ 新建"。**

    ![自动生成的社交媒体文章描述的屏幕截图](images/6c8b406ee224335a8c65d06953dc756e.png)

2. 输入以下详细信息：

    **常规** 
    
    - 名称：MDATP MDAV 内核扩展
    - 说明：kext (MDATP 内核) 
    - 类别：无
    - 分发方法：自动安装
    - 级别：计算机级别

    ![配置设置 mdatpmdav 内核的图像](images/24e290f5fc309932cf41f3a280d22c14.png)

3. 在 **"配置批准的内核扩展"中，选择**"**配置"。**

    ![批准的内核扩展的配置设置的图像](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

   
4. 在 **"已批准内核扩展"** 中 输入以下详细信息：

    - 显示名称：Microsoft Corp.
    - 团队 ID：UBF8T346G9

    ![配置设置应用程序内核扩展的图像](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. 选择" **范围"** 选项卡。

    ![配置设置范围选项卡 img 的图像](images/0df36fc308ba569db204ee32db3fb40a.png)

6. 选择“+ 添加”。

7. Select **Computer Groups** > under Group Name **>** select **Contoso's Machine Group**.

8. 选择“+ 添加”。

    ![配置设置添加映像的图像](images/0dde8a4c41110dbc398c485433a81359.png)

9. 选择“**保存**”。

    ![配置设置保存映像](images/0add8019b85a453b47fa5c402c72761b.png)

10. 选择“**完成**”。

    ![配置设置完成映像的图像](images/1c9bd3f68db20b80193dac18f33c22d0.png)


## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>步骤 8：批准适用于终结点的 Microsoft Defender 的系统扩展

1. 在"**配置文件"中**，选择 **"+ 新建"。**

    ![自动生成的社交媒体文章描述的屏幕截图](images/6c8b406ee224335a8c65d06953dc756e.png)

2. 输入以下详细信息：

    **常规**
    
    - 名称：MDATP MDAV 系统扩展
    - 说明：MDATP 系统扩展
    - 类别：无
    - 分发方法：自动安装
    - 级别：计算机级别

    ![配置设置的图像 sysext new prof](images/sysext-new-profile.png)

3. 在 **"系统扩展"中，** 选择"**配置"。**

   ![配置设置 sysext 配置的图像](images/sysext-configure.png)

4. 在 **"系统扩展"** 中，输入以下详细信息：

   - 显示名称：Microsoft Corp. 系统扩展
   - 系统扩展类型：允许的系统扩展
   - 团队标识符：UBF8T346G9
   - 允许的系统扩展：
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![配置设置的图像 sysextconfig2](images/sysext-configure2.png)

5. 选择" **范围"** 选项卡。

    ![配置设置作用域映像的图像](images/0df36fc308ba569db204ee32db3fb40a.png)

6. 选择“+ 添加”。

7. Select **Computer Groups** > under Group Name **>** select **Contoso's Machine Group**.

8. 选择“+ 添加”。

   ![配置设置 addima 的图像](images/0dde8a4c41110dbc398c485433a81359.png)

9. 选择“**保存**”。

   ![配置设置 sysext 作用域的图像](images/sysext-scope.png)

10. 选择“**完成**”。

    ![配置设置的图像 sysext-final](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>步骤 9：配置网络扩展

作为终结点检测和响应功能的一部分，Microsoft Defender for Mac 终结点会检查套接字流量，将此信息报告给 Microsoft Defender 安全中心门户。 以下策略允许网络扩展执行此功能。

>[!NOTE]
>JAMF 没有对内容筛选策略的内置支持，这是启用 Microsoft Defender for Mac 终结点在设备上安装的网络扩展的先决条件。 此外，JAMF 有时会更改正在部署的策略的内容。
>因此，以下步骤提供了涉及对配置文件进行签名的解决方法。

1. 从 `netfilter.mobileconfig` [GitHub 存储库下载到](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) 设备并将其另存为 `com.microsoft.network-extension.mobileconfig`

2. 按照此页面上 [的说明使用](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) JAMF 的内置证书颁发机构创建签名证书

3. 创建证书并安装到设备后，从 macOS 设备从终端运行以下命令：

   ```bash
   $ security cms -S -N "<certificate name>" -i com.microsoft.network-extension.mobileconfig -o com.microsoft.network-extension.signed.mobileconfig
   ```

   ![具有用于创建已签名配置的命令的终端窗口](images/netext-create-profile.png)

4. 从 JAMF 门户中，导航到 **"配置文件"，** 然后单击" **上载"** 按钮。 

   ![上传窗口图像](images/netext-upload-file.png)

5. 选择 **"选择文件"，** 然后选择 `microsoft.network-extension.signed.mobileconfig` " "。

   ![上传窗口图像选择文件](images/netext-choose-file.png)

6. 选择 **"上载"。**

   ![上传窗口图像 netext 上载文件 2](images/netext-upload-file2.png)

7. 上载文件后，您将重定向到新页面以完成此配置文件的创建。

   ![新配置文件 netext 配置文件页的图像](images/netext-profile-page.png)

8. 选择" **范围"** 选项卡。

   ![配置设置标签页的图像](images/0df36fc308ba569db204ee32db3fb40a.png)

9. 选择“+ 添加”。

10. Select **Computer Groups** > under Group Name **>** select **Contoso's Machine Group**.

11. 选择“+ 添加”。

    ![配置设置 adim 的图像](images/0dde8a4c41110dbc398c485433a81359.png)

12. 选择“**保存**”。

    ![配置设置 savimg netextscop 的图像](images/netext-scope.png)

13. 选择“**完成**”。

    ![配置设置图像 netextfinal](images/netext-final.png)

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-for-mac"></a>步骤 10：使用 Microsoft Defender for Endpoint for Mac 计划扫描
按照使用 Microsoft Defender for Endpoint for Mac 计划 [扫描的说明进行操作](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)。

## <a name="step-11-deploy-microsoft-defender-for-endpoint-for-macos"></a>步骤 11：部署适用于 macOS 的终结点的 Microsoft Defender

1. 导航到保存的位置 `wdav.pkg` 。

    ![文件资源管理器 wdav pkg 的图像](images/8dde76b5463047423f8637c86b05c29d.png)

2. 将其重命名为 `wdav_MDM_Contoso_200329.pkg` 。

    ![文件资源管理器1 wdavmdmpkg 的图像](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. 打开 Jamf Pro 仪表板。

    ![配置设置 jamfpro 的图像](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. 选择您的计算机，然后单击顶部的齿轮图标，然后选择计算机 **管理**。

    ![配置设置 compmgmt 的图像](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. 在 **"程序包"** 中，选择 **"+ 新建"。** 
    ![包含鸟描述的图片自动生成程序包新建](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. 在 **"新建程序包"** 中 输入以下详细信息：

    **"常规"选项卡**
    - 显示名称：现在保留为空。 因为它将在你选择 pkg 时重置。
    - 类别：默认 (无) 
    - 文件名：选择"文件"

    ![配置设置常规选项卡的图像](images/21de3658bf58b1b767a17358a3f06341.png)

    打开 文件，并指向 `wdav.pkg` 或 `wdav_MDM_Contoso_200329.pkg` 。
    
    ![自动生成的计算机屏幕描述的屏幕截图](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. 选择 **“打开”**。 将显示 **名称设置为** **Microsoft Defender 高级威胁防护和 Microsoft Defender 防病毒**。

    **清单文件** 不是必需的。 Microsoft Defender 高级威胁防护在没有清单文件的情况下工作。
    
    **选项选项卡**<br> 保留默认值。

    **"限制"选项卡**<br> 保留默认值。
    
     ![配置设置限制选项卡的图像](images/56dac54634d13b2d3948ab50e8d3ef21.png)
   
8. 选择“**保存**”。 该程序包将上载到 Jamf Pro。 

   ![配置设置包 upl jamf pro 的图像](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   可能需要几分钟时间，程序包才能可用于部署。
   
   ![配置设置包 upl 的图像](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. 导航到" **策略"** 页。

    ![配置设置要求的图像](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. 选择 **+ 新建** 以创建新策略。

    ![配置设置新策略的图像](images/847b70e54ed04787e415f5180414b310.png)


11. 在 **"常规** "中 输入以下详细信息：

    - 显示名称：MDATP 载入 Contoso 200329 v100.86.92 或更高版本

    ![配置设置mdatponboard的图像 ](images/625ba6d19e8597f05e4907298a454d28.png)

12. 选择 **"定期签入"。** 
    
    ![配置设置重复签入的图像](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

  
13. 选择“**保存**”。 
 
14. 选择 **">配置"。**
 
    ![配置设置包配置的图像](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. 选择 Microsoft Defender **高级** 威胁防护和 Microsoft Defender 防病毒 旁边的 **"添加"按钮**。

    ![配置设置 MDATP 和 MDA 添加的图像](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. 选择“**保存**”。

    ![配置设置的图像avimg](images/9d6e5386e652e00715ff348af72671c6.png)

17. 选择" **范围"** 选项卡。  

    ![配置设置 scptab 的图像](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. 选择目标计算机。

    ![配置设置 tgtcomp 的图像](images/6eda18a64a660fa149575454e54e7156.png)

    **Scope**
    
    选择“**添加**”。
    
    ![配置设置 ad1img 的图像](images/1c08d097829863778d562c10c5f92b67.png)

    ![配置设置 ad2img 的图像](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **自助服务**
    
    ![配置设置自服务的图像](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. 选择“**完成**”。 

    ![配置设置 do1img 的图像](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![配置设置 do2img 的图像](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)



