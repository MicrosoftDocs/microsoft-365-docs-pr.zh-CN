---
title: Microsoft 托管桌面的网络配置
description: 如何设置代理和必要的终结点
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
ms.openlocfilehash: 076d2fe17be8d557d55d432eda637e4ba74a0121
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339390"
---
#  <a name="network-configuration-for-microsoft-managed-desktop"></a>Microsoft 托管桌面的网络配置

<!--Proxy config -->


## <a name="proxy-configuration"></a>代理配置

Microsoft 托管桌面云托管服务。 有一组终结点Microsoft 托管桌面服务需要能够到达。 本节列出了需要为服务的各个方面允许的Microsoft 托管桌面。 

客户可以通过直接通过防火墙或代理Microsoft 365所有受信任的网络请求、绕过身份验证和所有其他数据包级检查或处理来优化其网络。 这样可减少延迟和外围容量要求。 

此外，为了优化Microsoft 托管桌面基于云的服务，这些终结点需要客户客户端浏览器及其边缘网络中设备进行特殊处理。 这些设备包括防火墙、SSL 中断和检查、数据包检查设备和数据丢失防护系统。

### <a name="proxy-requirement"></a>代理要求

代理或防火墙必须支持 TLS 1.2。 否则，您可能必须禁用协议检测。

### <a name="endpoints-allowed-that-are-necessary-for-microsoft-managed-desktop"></a>允许的终结点是Microsoft 托管桌面

Microsoft 托管桌面 Azure 门户托管其 Web 控制台。 以下 URL 必须位于代理和防火墙的允许列表中，以便Microsoft 托管桌面 Microsoft 服务进行通信。  

the Microsoft 托管桌面 URL is used for anything our service runs on the customer API. 必须确保此 URL 始终可在公司网络上访问。

Microsoft 服务  | 允许列表所需的 URL 
--- | ---
Microsoft 托管桌面 | prod-mwaas-services-customerapi.azurewebsites.net
获取帮助 | \*.support.services.microsoft.com  <br>inprod.support.services.microsoft.com  <br>supportchannels.services.microsoft.com  <br>graph.windows.net  <br>login.windows.net  <br>prod-mwaas-services-customerapi.azurewebsites.net  <br>concierge.live.com
快速助手 | remoteassistance.support.services.microsoft.com <br>relay.support.services.microsoft.com <br>channelwebsdks.azureedge.net  <br>web.vortex.data.microsoft.com  <br>gateway.channelservices.microsoft.com <br>\*.lync.com
Microsoft 支持和恢复助手 | \*.apibasic.diagnostics.office.com  <br>\*.api.diagnostics.office.com
 

### <a name="endpoints-allowed-used-by-other-microsoft-products"></a>其他 Microsoft 产品允许使用的终结点

允许列表中需要包含一些 Microsoft 产品的 URL，以便Microsoft 托管桌面这些 Microsoft 服务进行通信。 使用链接查看每个产品的完整列表。 

Microsoft 服务 | 文档
--- | ---
Windows 10 企业版包括 Windows Update for Business | [管理版本 1803 Windows 10连接终结点](/windows/privacy/manage-windows-1803-endpoints)<br><br>[管理连接终结点Windows 10 版本 1809](/windows/privacy/manage-windows-1809-endpoints)<br><br>[管理版本 1903 Windows 10连接终结点](/windows/privacy/manage-windows-1903-endpoints)<br><br>[管理 Windows 10 版本 2004 的连接终结点](/windows/privacy/manage-windows-2004-endpoints)
传递优化 | [配置传递优化以Windows 10更新](/windows/deployment/update/waas-delivery-optimization)
Microsoft 365 | [Microsoft 365URL 和 IP 地址范围](../../enterprise/urls-and-ip-address-ranges.md)
Azure Active Directory | [混合标识所需的端口和协议](/azure/active-directory/hybrid/reference-connect-ports) 以及 [Active Directory 和 Active Directory 域服务端口要求](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772723(v=ws.10)) 
Microsoft Intune | [Intune 网络配置要求](/intune/network-bandwidth-use)<br>[Microsoft Intune](/mem/intune/fundamentals/intune-endpoints)
Microsoft Defender for Endpoint | [适用于终结点的 Microsoft Defender 要求](/windows/security/threat-protection/windows-defender-atp/configure-proxy-internet-windows-defender-advanced-threat-protection#enable-access-to-windows-defender-atp-service-urls-in-the-proxy-server)
Windows Autopilot | [WindowsAutopilot 网络要求](/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements)

Microsoft 服务  | 允许列表所需的 URL | 文档源
--- | --- | ---
WindowsWUfB ()  | update.microsoft.com<br>\*.update.microsoft.com<br>download.windowsupdate.com<br>\*.download.windowsupdate.com<br>download.microsoft.com<br>\*.download.microsoft.com<br>windowsupdate.com<br>\*.windowsupdate.com<br>ntservicepack.microsoft.com<br>wustat.windows.com<br>login.live.com <br>mp.microsoft.com<br>\*.mp.microsoft.com | [Windows针对业务防火墙和代理要求的更新](https://support.microsoft.com/help/3084568/can-t-download-updates-from-windows-update-from-behind-a-firewall-or-p)
传递优化 | \*.do.dsp.mp.microsoft.com<br>\*.dl.delivery.mp.microsoft.com <br>\*.emdl.ws.microsoft.com<br>\*.download.windowsupdate.com <br>\*.windowsupdate.com   | [Windows更新代理要求](https://support.microsoft.com/help/3175743/proxy-requirements-for-windows-update)
适用于企业的 Microsoft Store | login.live.com <br>account.live.com <br>clientconfig.passport.net <br>wustat.windows.com <br>\*.windowsupdate.com <br>\*.wns.windows.com <br>\*.hotmail.com <br>\*.outlook.com <br>\*.microsoft.com <br>\*.msftncsi.com/ncsi.txt   | [Microsoft Store允许列表](https://support.microsoft.com/help/2778122/using-authenticated-proxy-servers-together-with-windows-8)
Microsoft 365 | \*.office365.com<br>\*.office.com<br>\*.office.net<br>\*.live.com<br>\*.portal.cloudappsecurity.com<br>\*.portal.cloudappsecurity.com<br>\*.us.portal.cloudappsecurity.com<br>\*.eu.portal.cloudappsecurity.com<br>\*.us2.portal.cloudappsecurity.com<br><tenant>.onmicrosoft.com<br>account.office.net<br>agent.office.net<br>apc.delve.office.com<br>aus.delve.office.com<br>can.delve.office.com<br>delve.office.com<br>eur.delve.office.com<br>gbr.delve.office.com<br>home.office.com<br>ind.delve.office.com<br>jpn.delve.office.com<br>kor.delve.office.com<br>lam.delve.office.com<br>nam.delve.office.com<br>admin.microsoft.com<br>outlook.office365.com<br>suite.office.net<br>webshell.suite.office.com<br>www.office.com<br>\*.aria.microsoft.com<br>browser.pipe.aria.microsoft.com<br>mobile.pipe.aria.microsoft.com<br>portal.microsoftonline.com<br>clientlog.admin.microsoft.com<br>nexus.officeapps.live.com<br>nexusrules.officeapps.live.com<br>amp.azure.net<br>\*.o365weve.com<br>auth.gfx.ms<br>appsforoffice.microsoft.com<br>assets.onestore.ms<br>az826701.vo.msecnd.net<br>c.microsoft.com<br>c1.microsoft.com<br>client.hip.live.com<br>contentstorage.osi.office.net<br>dgps.support.microsoft.com<br>docs.microsoft.com<br>groupsapi-<br>rod.outlookgroups.ms<br>groupsapi2-prod.outlookgroups.ms<br>groupsapi3-prod.outlookgroups.ms<br>groupsapi4-prod.outlookgroups.ms<br>msdn.microsoft.com<br>platform.linkedin.com<br>products.office.com<br>prod.msocdn.com<br>r1.res.office365.com<br>r4.res.office365.com<br>res.delve.office.com<br>shellprod.msocdn.com<br>support.content.office.net<br>support.microsoft.com<br>support.office.com<br>technet.microsoft.com<br>templates.office.com<br>video.osi.office.net<br>videocontent.osi.office.net<br>videoplayercdn.osi.office.net<br>\*.manage.office.com<br>\*.protection.office.com<br>manage.office.com<br>Protection.office.com<br>diagnostics.office.com | [Microsoft 365URL 和 IP 地址范围](../../enterprise/urls-and-ip-address-ranges.md)
Azure Active Directory | api.login.microsoftonline.com<br>api.passwordreset.microsoftonline.com<br>autologon.microsoftazuread-sso.com<br>becws.microsoftonline.com<br>clientconfig.microsoftonline-p.net <br>companymanager.microsoftonline.com <br>device.login.microsoftonline.com <br>hip.microsoftonline-p.net <br>hipservice.microsoftonline.com <br>login.microsoft.com<br>login.microsoftonline.com <br>logincert.microsoftonline.com <br>loginex.microsoftonline.com<br>login-us.microsoftonline.com <br>login.microsoftonline-p.com <br>login.windows.net <br>nexus.microsoftonline-p.com <br>passwordreset.microsoftonline.com <br>provisioningapi.microsoftonline.com<br>stamp2.login.microsoftonline.com<br>\*.msappproxy.net<br>ccs.login.microsoftonline.com<br>ccs-sdf.login.microsoftonline.com<br>accounts.accesscontrol.windows.net<br>secure.aadcdn.microsoftonline-p.com<br>\*.phonefactor.net<br>account.activedirectory.windowsazure.com<br>secure.aadcdn.microsoftonline-p.com<br>graph.microsoft.com | [混合标识所需的端口和协议](/azure/active-directory/connect/active-directory-aadconnect-ports) 以及 [Active Directory 和 Active Directory 域服务端口要求](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd772723(v=ws.10)) 
Microsoft Intune | login.microsoftonline.com<br>portal.manage.microsoft.com<br>m.manage.microsoft.com<br>sts.manage.microsoft.com<br>Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com<br>fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com<br>fef.msua01.manage.microsoft.com<br>fef.msua02.manage.microsoft.com<br>fef.msua04.manage.microsoft.com<br>fef.msua05.manage.microsoft.com<br>fef.msua06.manage.microsoft.com<br>fef.msua07.manage.microsoft.com<br>fef.msub01.manage.microsoft.com<br>fef.msub02.manage.microsoft.com<br>fef.msub03.manage.microsoft.com<br>fef.msub05.manage.microsoft.com<br>fef.msuc01.manage.microsoft.com<br>fef.msuc02.manage.microsoft.com<br>fef.msuc03.manage.microsoft.com<br>fef.msuc05.manage.microsoft.com |  [Intune 网络配置要求](/intune/network-bandwidth-use)
OneDrive for Business | onedrive.com <br> <br>\*.onedrive.com <br>onedrive.live.com <br>login.live.com <br>spoprod-a.akamaihd.net <br>\*.mesh.com <br>p.sfx.ms <br>\*.microsoft.com <br>fabric.io <br>\*.crashlytics.com <br>vortex.data.microsoft.com <br>https://posarprodcssservice.accesscontrol.windows.net <br>redemptionservices.accesscontrol.windows.net  <br>token.cp.microsoft.com/ <br>tokensit.cp.microsoft-tst.com/ <br>\*.office.com <br>\*.officeapps.live.com <br>\*.aria.microsoft.com <br>\*.mobileengagement.windows.net <br>\*.branch.io <br>\*.adjust.com <br>\*.servicebus.windows.net <br>vas.samsungapps.com <br>odc.officeapps.live.com <br>login.windows.net <br>login.microsoftonline.com <br>\*.files.1drv.com <br>\*.onedrive.live.com <br>\*.\*.onedrive.live.com <br>storage.live.com <br>\*.storage.live.com <br>\*.\*.storage.live.com <br>\*.groups.office.live.com <br>\*.groups.photos.live.com <br>\*.groups.skydrive.live.com <br>favorites.live.com <br>oauth.live.com <br>photos.live.com <br>skydrive.live.com <br>api.live.net <br>apis.live.net <br>docs.live.net <br>\*.docs.live.net <br>policies.live.net <br>\*.policies.live.net <br>settings.live.net <br>\*.settings.live.net <br>skyapi.live.net <br>snapi.live.net <br>\*.livefilestore.com <br>\*.\*.livefilestore.com <br>storage.msn.com <br>\*.storage.msn.com <br>\*.*.storage.msn.com | [所需的 URL 和端口用于OneDrive](/onedrive/required-urls-and-ports)
Microsoft Defender 高级威胁防护 (ATP) | \ *.oms.opinsights.azure.com <br>\*.blob.core.windows.net <br>\*.azure-automation.net <br>\*.ods.opinsights.azure.com <br>winatp-gw-cus.microsoft.com <br>winatp-gw-eus.microsoft.com <br>winatp-gw-neu.microsoft.com <br>winatp-gw-weu.microsoft.com <br>winatp-gw-uks.microsoft.com <br>winatp-gw-ukw.microsoft.com <br>winatp-gw-aus.microsoft.com <br>winatp-gw-aue.microsoft.com | [Windows DefenderATP 终结点](/windows/security/threat-protection/windows-defender-atp/configure-server-endpoints-windows-defender-advanced-threat-protection)
获取帮助 | \*.support.services.microsoft.com  <br>inprod.support.services.microsoft.com  <br>supportchannels.services.microsoft.com  <br>graph.windows.net  <br>login.windows.net  <br>prod-mwaas-services-customerapi.azurewebsites.net  <br>concierge.live.com <br>rave.office.net | 
快速助手 | remoteassistance.support.services.microsoft.com <br>relay.support.services.microsoft.com <br>channelwebsdks.azureedge.net  <br>web.vortex.data.microsoft.com  <br>gateway.channelservices.microsoft.com <br>\*.lync.com | 
SharePoint Online  | \*.sharepoint.com <br>\ *.svc.ms  <br>\<tenant\>.sharepoint.com  <br>\<tenant\>-my.sharepoint.com  <br>\<tenant\>-files.sharepoint.com  <br>\<tenant\>-myfiles.sharepoint.com <br>\*.sharepointonline.com  <br>cdn.sharepointonline.com  <br>static.sharepointonline.com  <br>spoprod-a.akamaihd.net  <br>publiccdn.sharepointonline.com  <br>privatecdn.sharepointonline.com | [Office 365 URL 和 IP 地址范围](/microsoft-365/enterprise/urls-and-ip-address-ranges)
OneDrive for Business | admin.onedrive.com  <br>officeclient.microsoft.com <br>odc.officeapps.live.com  <br>skydrive.wns.windows.com <br>g.live.com <br>oneclient.sfx.ms <br>\*.log.optimizely.com  <br>click.email.microsoftonline.com  <br>ssw.live.com  <br>storage.live.com |  [Office 365 URL 和 IP 地址范围](/microsoft-365/enterprise/urls-and-ip-address-ranges)
Microsoft Teams | \*.teams.skype.com  <br>\*.teams.microsoft.com  <br>teams.microsoft.com <br>\*.asm.skype.com <br>\ *.cc.skype.com  <br>\*.conv.skype.com  <br>\*.dc.trouter.io  <br>\*.msg.skype.com  <br>prod.registrar.skype.com  <br>prod.tpc.skype.com <br>\*.broker.skype.com <br>\*.config.skype.com  <br>\*.pipe.skype.com  <br>\*.pipe.aria.microsoft.com  <br>config.edge.skype.com  <br>pipe.skype.com  <br>s-0001.s-msedge.net  <br>s-0004.s-msedge.net  <br>scsinstrument-ss-us.trafficmanager.net  <br>scsquery-ss- <br>us.trafficmanager.net  <br>scsquery-ss-eu.trafficmanager.net  <br>scsquery-ss-asia.trafficmanager.net <br>\*.msedge.net <br>compass-ssl.microsoft.com  <br>feedback.skype.com <br>\*.secure.skypeassets.com  <br>mlccdnprod.azureedge.net  <br>videoplayercdn.osi.office.net <br>\*.mstea.ms | [Office 365 URL 和 IP 地址范围](/microsoft-365/enterprise/urls-and-ip-address-ranges)
Power BI | maxcdn.bootstrapcdn.com <br>ajax.aspnetcdn.com <br>netdna.bootstrapcdn.com <br>cdn.optimizely.com <br>google-analytics.com <br>\*.mktoresp.com <br>\*.aadcdn.microsoftonline-p.com <br>\*.msecnd.com <br>\*.localytics.com <br>ajax.aspnetcdn.com <br>\*.localytics.com <br>\*.virtualearth.net <br>platform.bing.com <br>powerbi.microsoft.com <br>c.microsoft.com <br>app.powerbi.com <br>\*.powerbi.com <br>dc.services.visualstudio.com <br>support.powerbi.com <br>powerbi.uservoice.com <br>go.microsoft.com <br>c1.microsoft.com <br>\*.azureedge.net |[Power BI &快速路由](/power-bi/service-admin-power-bi-expressroute) 
OneNote | apis.live.net <br>www.onedrive.com <br>login.microsoft.com  <br>www.onenote.com <br>\*.onenote.com <br>\*.msecnd.net <br>\*.microsoft.com <br>\*.office.net <br>cdn.onenote.net <br>site-cdn.onenote.net <br>cdn.optimizely.com <br>Ajax.aspnetcdn.com <br>officeapps.live.com <br>\\*.onenote.com <br>\*cdn.onenote.net <br>contentstorage.osi.office.net <br>\*onenote.officeapps.live.com <br>\*.microsoft.com | [Office 365 URL 和 IP 地址范围](/microsoft-365/enterprise/urls-and-ip-address-ranges)

## <a name="steps-to-get-ready"></a>准备步骤

1. Review [Prerequisites for Microsoft 托管桌面](prerequisites.md).
2. 使用 [准备情况评估工具](readiness-assessment-tool.md)。
3. [来宾帐户的先决条件](guest-accounts.md)
4. [Microsoft 托管桌面 (](network.md)网络配置 本文) 
5. [为 Microsoft 托管桌面准备证书和网络配置文件](certs-wifi-lan.md)
6. [为 Microsoft 托管桌面准备本地资源访问权限](authentication.md)
7. [Microsoft 托管桌面中的应用](apps.md)
8. [为 Microsoft 托管桌面准备映射的驱动器](mapped-drives.md)
9. [为 Microsoft 托管桌面准备打印资源](printing.md)
