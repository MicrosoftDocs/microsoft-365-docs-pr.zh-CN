---
title: 测试包指南
description: 查看有关测试包的指南
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
localization_priority: Normal
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: b6842f793627bddeab842bbd9570c9c3481699a6
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322514"
---
# <a name="test-package-guidelines"></a>测试包指南

## <a name="1---script-referencing"></a>1. 脚本引用

当您将.zip文件上载到门户时，我们会将该文件的所有内容解压缩到根文件夹中。 无需编写任何代码来执行此初始解压缩操作。 您还可以通过使用相对于上载的 zip 文件.zip文件内的任何文件。

在下面的示例中，我们显示了如何从"任务"选项卡的输入字段引用二进制文件/脚本。应该将蓝色文本输入到" **脚本路径** "字段中 **，而不使用引号。**

在上载 zip 文件之前，了解其中的内容非常重要。 通常，压缩文件夹时，本地计算机将在 zip 文件下创建主文件夹。 在这种情况下，引用将如下所示 **，以粗体** 显示：

 **Contoso_App_Folder.zip**
~~~ 
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│        ├── file3.exe

│        ├── script.ps1
~~~

  - ScriptX.ps1 – **"Contoso_App_Folder/ScriptX.ps1"**
  - Script.ps1 - **"Contoso_App_Folder/folder1/script.ps1"**

其他时候，zip 文件可能正下方有文件或内容，即没有 2nd 级文件夹：

 **Zip_file_uploaded.zip**
~~~ 
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - ScriptX.ps1 – **"ScriptX.ps1"**
  - Script.ps1 - **"folder1/script.ps1"**
  
## <a name="2---script-execution"></a>2. 脚本执行

**Out-of-Box 测试：** 应用程序包至少需要包含三个 PowerShell 脚本，这些脚本将执行无人参与安装、启动和关闭应用程序及其依赖项。 每个脚本都应检查自己的必备组件，验证成功，并在必要时 (清理) 。

**功能测试：** 应用程序包至少需要包含一个 PowerShell 脚本。 如果提供了多个脚本，脚本将按上载顺序运行，并且特定脚本中的失败将阻止后续脚本执行。

### <a name="script-requirements"></a>脚本要求

• PowerShell 版本 5.1 及以上     

• 无人参与执行    

• 错误返回代码               

• 验证成功            

• 记录以编写特定日志文件夹的脚本

每个脚本都需要完全无人参与运行，以在测试管道中成功执行。

> [!Note]
> 脚本应在成功完成时返回"0"，如果在执行期间发生任何错误，则返回非零错误代码。

每个脚本应验证其是否成功运行。 例如， 安装程序二进制文件执行完成后，安装脚本应检查系统上是否存在某些二进制文件和/或注册表项，以确保在合理的置信度下安装成功。 

这是正确诊断在测试运行期间发生错误（例如，无法成功安装应用程序与无法启动应用程序）所必需的。

> [!Important]
> **避免以下事项：** 脚本不应重新启动计算机，如果需要重新启动，请在上载脚本期间指定此参数。

## <a name="3---log-collection"></a>3. 日志集合

每个脚本都应将生成的任何日志输出到名为 的文件夹中 ```logs``` 。 将复制目录中名为 的所有文件夹， ```logs``` 并呈现在页面上进行 ```Test Results``` 下载。

例如，可能位于 **App/scripts/install** 目录) 中的安装脚本 (可以将其日志输出到 **：logs/install.log，** 这样最终日志将位于 **：Apps/scripts/install/logs/install.log**

系统将选取文件以及其他文件夹中的其他文件， ```install.log``` ```logs``` 并整理该文件进行下载。


## <a name="4---application-binaries"></a>4. 应用程序二进制文件

任何二进制文件和依赖项都应包含在单个 zip 文件中。 

这些应包括安装应用程序所需的一切 (，例如应用程序安装程序) ;如果应用程序依赖任何框架（如 .NET Core/Standard 或 .NET Framework），则这些文件应包含在文件中，并正确引用提供的脚本。


> [!Note]
> 上载的 zip 文件的名称中不能包含任何空格或特殊字符

## <a name="next-steps"></a>后续步骤

前进到下一篇文章以查看一些常见问题 (**常见问题)**
> [!div class="nextstepaction"]
> [后续步骤](faq.md)
