---
title: 在 SharePoint 管理中心设置信息权限管理 (IRM)
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
localization_priority: Normal
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: 了解如何通过 SHAREPOINT RmS Microsoft Azure Active Directory权限管理服务 (联机 IRM) SharePoint列表和文档库。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 68db84118ac8ccd7c734152aa28816db819198f7
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919398"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>在 SharePoint 管理中心设置信息权限管理 (IRM)

在 SharePoint Online 中，IRM 保护适用于列表和库级别的文件。 必须先设置权限管理，你的组织才能使用 IRM 保护。 IRM 依靠 Azure 信息保护的 Azure 权限管理服务来加密和分配使用限制。 某些Microsoft 365计划包括 Azure 权限管理，但不是全部。 若要了解更多信息，请参阅[Office服务如何支持 Azure 权限管理](/azure/information-protection/understand-explore/office-apps-services-support)。
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>使用管理中心打开 IRM SharePoint IRM 服务

在您的组织可以 IRM 保护SharePoint和库之前，您必须先为组织激活权限管理服务。 若要了解如何操作 [，请参阅激活 Azure 权限管理](/information-protection/deploy-use/activate-service)。 必须使用具有全局管理员权限的工作或学校帐户才能启用权限管理服务。 否则，将无法将 IRM 功能与 SharePoint Online 一同使用。
  
激活权限管理服务后，登录到管理SharePoint以打开 IRM。
  
1. 以全局管理员或全局管理员SharePoint登录。
    
2. 依次选择左上角的应用启动器图标 ![Office 365 中的应用启动器图标](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) 和“管理员”，以打开 Microsoft 365 管理中心。  (如果看不到"管理员"磁贴，则在你的组织中没有管理员权限。)  
    
3. 在左窗格中，选择"管理 **中心** \> **SharePoint"。**
    
4. 在左侧窗格中，选择 **"设置"，** 然后选择" **经典设置"页面**。
    
5. 在"**信息权限** 管理 (IRM) "部分，选择"使用配置中指定的 **IRM** 服务"，然后选择"刷新 **IRM 设置"。** 刷新 IRM 设置后，您组织成员可以开始在列表和文档库中SharePoint IRM。 但是，要这样做的选项可能需要一个小时，才显示在"库"设置和"列表设置"。
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>支持 IRM SharePoint文档库和列表
<a name="__toc220831191"> </a>

刷新 IRM 设置后，网站所有者可以 IRM SharePoint列表和文档库。 有关详细信息，请参阅将 [信息权限管理应用于列表或库](apply-irm-to-a-list-or-library.md)。
  
当网站所有者为列表或库启用 IRM 时，他们可以保护该列表或库中任何受支持的文件类型。 当为库启用 IRM 时，权限管理将应用于该库中的所有文件。 为列表启用 IRM 时，权限管理仅适用于附加到列表项的文件，而不是实际列表项。
  
当用户在启用 IRM 的列表或库中下载文件时，文件会进行加密，以便只有授权人员才能查看这些文件。 每个权限管理文件还包含对查看该文件的人施加限制的发布许可证。 典型限制包括使文件成为只读、禁用文本复制、阻止用户保存本地副本以及阻止用户打印文件。 可读取支持 IRM 的文件类型的客户端程序使用权限管理文件内的颁发许可证来强制执行这些限制。 这是权限管理文件即使在下载后仍保留其保护的方式。 若要对列表或库启用 IRM，请参阅将 [信息权限管理应用于列表或库](apply-irm-to-a-list-or-library.md)。
  
不能在启用 IRM 的库中使用浏览器Office文档。 相反，一个人一次可以下载和编辑 IRM 加密的文件。 使用签入和签出管理多个  *用户*  之间的共同创作或创作。 
  
从受 IRM 保护的库下载 PDF 文件时，Microsoft 365创建一个受保护的 PDF 文件。 文件的扩展名不会更改，但文件受保护。 若要查看此文件，你需要 Azure 信息保护查看器、完整的 Azure 信息保护客户端或其他支持查看受保护 PDF 文件的应用程序。 
  
SharePointOnline 支持对以下文件类型进行加密：
  
- PDF
    
- 以下程序 97-2003 文件格式Microsoft Office Word、Excel 和 PowerPoint
    
- 以下Office的 Open XML 格式Microsoft Office Word、Excel 和 PowerPoint
    
- XML 纸张规范 (XPS) 格式
 
> [!NOTE]
> IRM 保护无法应用于受保护文档 (如数字签名的 PDF) ，SharePoint需要在上载时打开文档。 

## <a name="next-steps"></a>后续步骤
<a name="__toc220831191"> </a>

为 SharePoint Online 启用 IRM 后，您可以开始对列表和库应用权限管理。 有关信息，请参阅 [将信息权限管理应用于列表或库](apply-irm-to-a-list-or-library.md)。
  
Windows 的新 OneDrive 同步客户端现在支持同步受 IRM 保护的 SharePoint 文档库和 OneDrive 位置 (只要库的 IRM 设置未设置为使文档访问权限) 过期。 有关详细信息，或者要开始部署新的同步客户端，请参阅部署适用于 OneDrive[的新同步Windows。](/onedrive/deploy-on-windows)
  
[页面顶部](set-up-irm-in-sp-admin-center.md)