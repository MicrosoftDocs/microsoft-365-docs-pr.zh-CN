---
title: 诊断日志
description: 在疑难解答期间可能从设备收集的日志及其存储方式
keywords: Microsoft 托管桌面, Microsoft 365, 服务, 文档
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: ef7d19fef989610c10323c2a9820a5314d5e1641
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "52272885"
---
# <a name="diagnostic-logs"></a><span data-ttu-id="1d075-104">诊断日志</span><span class="sxs-lookup"><span data-stu-id="1d075-104">Diagnostic logs</span></span>

<span data-ttu-id="1d075-105">当我们在由 Microsoft 托管桌面 管理的设备上解决问题时，无论你已报告问题还是由服务识别的问题，我们可能需要从设备中收集某些诊断日志，而无需用户干预。</span><span class="sxs-lookup"><span data-stu-id="1d075-105">When we troubleshoot an issue on a device managed by Microsoft Managed Desktop, whether one you've reported or one identified by our service, we might have to collect certain diagnostic logs from the device without intervention from the user.</span></span> <span data-ttu-id="1d075-106">我们不会从用户目录中收集任何用户生成的内容或信息。</span><span class="sxs-lookup"><span data-stu-id="1d075-106">We don't collect any user-generated content or information from user directories.</span></span> <span data-ttu-id="1d075-107">我们仅收集与设备运行状况和状态有关诊断和日志数据。</span><span class="sxs-lookup"><span data-stu-id="1d075-107">We only collect diagnostic and log data that concerns device health and status.</span></span>

<span data-ttu-id="1d075-108">我们将收集的任何日志存储 28 天，然后将其删除。</span><span class="sxs-lookup"><span data-stu-id="1d075-108">We store any collected logs for 28 days, and then delete them.</span></span> <span data-ttu-id="1d075-109">我们将按照数据处理标准处理从设备 [收集的任何日志](privacy-personal-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1d075-109">We process any logs collected from a device following our [data handling standards](privacy-personal-data.md).</span></span>

## <a name="data-collected"></a><span data-ttu-id="1d075-110">收集的数据</span><span class="sxs-lookup"><span data-stu-id="1d075-110">Data collected</span></span>

<span data-ttu-id="1d075-111">此列表包括所有文件夹、事件日志、可执行文件或注册表位置，Microsoft 托管桌面收集诊断日志。</span><span class="sxs-lookup"><span data-stu-id="1d075-111">This list includes all the folders, event logs, executables, or registry locations that Microsoft Managed Desktop might collect diagnostic logs from.</span></span> <span data-ttu-id="1d075-112">收集的实际数据将是此列表的子集，具体取决于已识别的问题。</span><span class="sxs-lookup"><span data-stu-id="1d075-112">The actual data collected will be a subset of this list and depends on the identified issue.</span></span>

### <a name="registry-keys"></a><span data-ttu-id="1d075-113">注册表项</span><span class="sxs-lookup"><span data-stu-id="1d075-113">Registry keys</span></span>

- <span data-ttu-id="1d075-114">HKLM \\ SYSTEM \\ CurrentControlSet \\ Services</span><span class="sxs-lookup"><span data-stu-id="1d075-114">HKLM\\SYSTEM\\CurrentControlSet\\Services</span></span>
- <span data-ttu-id="1d075-115">HKLM \\ 软件 \\ Microsoft \\ Surface</span><span class="sxs-lookup"><span data-stu-id="1d075-115">HKLM\\SOFTWARE\\Microsoft\\Surface</span></span>
- <span data-ttu-id="1d075-116">HKLM \\ SOFTWARE Policies Microsoft Windows \\ \\ \\ \\ WindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="1d075-116">HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows\\WindowsUpdate</span></span>
- <span data-ttu-id="1d075-117">HKLM \\ SYSTEM \\ CurrentControlSet \\ 控件 \\ MUI \\ UILanguages</span><span class="sxs-lookup"><span data-stu-id="1d075-117">HKLM\\SYSTEM\\CurrentControlSet\\Control\\MUI\\UILanguages</span></span>
- <span data-ttu-id="1d075-118">HKLM \\ 软件 \\ 策略 Microsoft \\ \\ WindowsStore</span><span class="sxs-lookup"><span data-stu-id="1d075-118">HKLM\\Software\\Policies\\Microsoft\\WindowsStore</span></span>
- <span data-ttu-id="1d075-119">HKLM \\ 软件 Microsoft Windows \\ \\ \\ CurrentVersion \\ WindowsStore \\ WindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="1d075-119">HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\WindowsStore\\WindowsUpdate</span></span>
- <span data-ttu-id="1d075-120">HKLM \\ SOFTWARE Microsoft Windows NT \\ \\ \\ CurrentVersion</span><span class="sxs-lookup"><span data-stu-id="1d075-120">HKLM\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion</span></span>
- <span data-ttu-id="1d075-121">HKLM \\ SOFTWARE Microsoft Windows NT \\ \\ \\ CurrentVersion</span><span class="sxs-lookup"><span data-stu-id="1d075-121">HKLM\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion</span></span>
- <span data-ttu-id="1d075-122">HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ \\ CurrentVersion AppModel</span><span class="sxs-lookup"><span data-stu-id="1d075-122">HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\AppModel</span></span>
- <span data-ttu-id="1d075-123">HKLM \\ SYSTEM \\ CurrentControlSet \\ 控件 \\ FirmwareResources</span><span class="sxs-lookup"><span data-stu-id="1d075-123">HKLM\\SYSTEM\\CurrentControlSet\\Control\\FirmwareResources</span></span>
- <span data-ttu-id="1d075-124">HKLM \\ SOFTWARE \\ Microsoft \\ WindowsSelfhost</span><span class="sxs-lookup"><span data-stu-id="1d075-124">HKLM\\SOFTWARE\\Microsoft\\WindowsSelfhost</span></span>
- <span data-ttu-id="1d075-125">HKLM \\ SOFTWARE \\ Microsoft \\ WindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="1d075-125">HKLM\\SOFTWARE\\Microsoft\\WindowsUpdate</span></span>
- <span data-ttu-id="1d075-126">HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion \\ Appx</span><span class="sxs-lookup"><span data-stu-id="1d075-126">HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Appx</span></span>
- <span data-ttu-id="1d075-127">HKLM \\ SOFTWARE Microsoft Windows NT \\ \\ \\ CurrentVersion \\ Superfetch</span><span class="sxs-lookup"><span data-stu-id="1d075-127">HKLM\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Superfetch</span></span>
- <span data-ttu-id="1d075-128">HKLM \\ 系统 \\ 设置</span><span class="sxs-lookup"><span data-stu-id="1d075-128">HKLM\\SYSTEM\\Setup</span></span>
- <span data-ttu-id="1d075-129">HKLM \\ 软件 \\ Microsoft \\ IntuneManagementExtension</span><span class="sxs-lookup"><span data-stu-id="1d075-129">HKLM\\Software\\Microsoft\\IntuneManagementExtension</span></span>
- <span data-ttu-id="1d075-130">HKLM \\ 软件 \\ Microsoft \\ SystemCertificates \\ AuthRoot</span><span class="sxs-lookup"><span data-stu-id="1d075-130">HKLM\\SOFTWARE\\Microsoft\\SystemCertificates\\AuthRoot</span></span>
- <span data-ttu-id="1d075-131">HKLM \\ SOFTWARE Microsoft Windows \\ \\ 高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="1d075-131">HKLM\\SOFTWARE\\Microsoft\\Windows Advanced Threat Protection</span></span>
- <span data-ttu-id="1d075-132">HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion Authentication \\ \\ LogonUI</span><span class="sxs-lookup"><span data-stu-id="1d075-132">HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Authentication\\LogonUI</span></span>
- <span data-ttu-id="1d075-133">HKLM \\ SOFTWARE Microsoft Windows \\ \\ \\ CurrentVersion Internet \\ 设置</span><span class="sxs-lookup"><span data-stu-id="1d075-133">HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet Settings</span></span>
- <span data-ttu-id="1d075-134">HKLM \\ 软件 Microsoft Windows \\ \\ \\ CurrentVersion \\ 卸载</span><span class="sxs-lookup"><span data-stu-id="1d075-134">HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall</span></span>
- <span data-ttu-id="1d075-135">HKLM \\ 软件 \\ 策略</span><span class="sxs-lookup"><span data-stu-id="1d075-135">HKLM\\Software\\Policies</span></span>
- <span data-ttu-id="1d075-136">HKLM \\ 软件 \\ 策略 Microsoft \\ \\ 加密配置 \\ \\ SSL</span><span class="sxs-lookup"><span data-stu-id="1d075-136">HKLM\\SOFTWARE\\Policies\\Microsoft\\Cryptography\\Configuration\\SSL</span></span>
- <span data-ttu-id="1d075-137">HKLM \\ 软件 \\ 策略 Microsoft \\ \\ Windows高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="1d075-137">HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows Advanced Threat Protection</span></span>
- <span data-ttu-id="1d075-138">HKLM \\ 软件 \\ WOW6432Node \\ Microsoft Windows \\ \\ CurrentVersion \\ 卸载</span><span class="sxs-lookup"><span data-stu-id="1d075-138">HKLM\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall</span></span>
- <span data-ttu-id="1d075-139">HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ SecurityProviders \\ SCHANNEL</span><span class="sxs-lookup"><span data-stu-id="1d075-139">HKLM\\SYSTEM\\CurrentControlSet\\Control\\SecurityProviders\\SCHANNEL</span></span>

### <a name="commands"></a><span data-ttu-id="1d075-140">命令</span><span class="sxs-lookup"><span data-stu-id="1d075-140">Commands</span></span>

- <span data-ttu-id="1d075-141">%programfiles% \\ windows defendermpcmdrun.exe \\ -GetFiles</span><span class="sxs-lookup"><span data-stu-id="1d075-141">%programfiles%\\windows defender\\mpcmdrun.exe -GetFiles</span></span>
- <span data-ttu-id="1d075-142">%windir% \\ system32 \\certutil.exe -store</span><span class="sxs-lookup"><span data-stu-id="1d075-142">%windir%\\system32\\certutil.exe -store</span></span>
- <span data-ttu-id="1d075-143">%windir% \\ system32 \\certutil.exe -store -user my</span><span class="sxs-lookup"><span data-stu-id="1d075-143">%windir%\\system32\\certutil.exe -store -user my</span></span>
- <span data-ttu-id="1d075-144">%windir% \\ system32 \\Dsregcmd.exe /status</span><span class="sxs-lookup"><span data-stu-id="1d075-144">%windir%\\system32\\Dsregcmd.exe /status</span></span>
- <span data-ttu-id="1d075-145">%windir% \\ system32 \\ipconfig.exe /all</span><span class="sxs-lookup"><span data-stu-id="1d075-145">%windir%\\system32\\ipconfig.exe /all</span></span>
- <span data-ttu-id="1d075-146">%windir% \\ system32 \\ipconfig.exe /displaydns</span><span class="sxs-lookup"><span data-stu-id="1d075-146">%windir%\\system32\\ipconfig.exe /displaydns</span></span>
- <span data-ttu-id="1d075-147">%windir% \\ system32 \\mdmdiagnosticstool.exe</span><span class="sxs-lookup"><span data-stu-id="1d075-147">%windir%\\system32\\mdmdiagnosticstool.exe</span></span>
- <span data-ttu-id="1d075-148">%windir% \\ system32 \\msinfo32.exe /report %temp% \\ MDMDiagnostics \\ msinfo32.log</span><span class="sxs-lookup"><span data-stu-id="1d075-148">%windir%\\system32\\msinfo32.exe /report %temp%\\MDMDiagnostics\\msinfo32.log</span></span>
- <span data-ttu-id="1d075-149">%windir% \\ system32 \\netsh.exe advfirewall 显示所有文件</span><span class="sxs-lookup"><span data-stu-id="1d075-149">%windir%\\system32\\netsh.exe advfirewall show allprofiles</span></span>
- <span data-ttu-id="1d075-150">%windir% \\ system32 \\netsh.exe advfirewall 显示全局</span><span class="sxs-lookup"><span data-stu-id="1d075-150">%windir%\\system32\\netsh.exe advfirewall show global</span></span>
- <span data-ttu-id="1d075-151">%windir% \\ system32 \\netsh.exe lan 显示配置文件</span><span class="sxs-lookup"><span data-stu-id="1d075-151">%windir%\\system32\\netsh.exe lan show profiles</span></span>
- <span data-ttu-id="1d075-152">%windir% \\ system32 \\netsh.exe winhttp 显示代理</span><span class="sxs-lookup"><span data-stu-id="1d075-152">%windir%\\system32\\netsh.exe winhttp show proxy</span></span>
- <span data-ttu-id="1d075-153">%windir% \\ system32 \\netsh.exe wlan 显示配置文件</span><span class="sxs-lookup"><span data-stu-id="1d075-153">%windir%\\system32\\netsh.exe wlan show profiles</span></span>
- <span data-ttu-id="1d075-154">%windir% \\ system32 \\netsh.exe wlan 显示 wlanreport</span><span class="sxs-lookup"><span data-stu-id="1d075-154">%windir%\\system32\\netsh.exe wlan show wlanreport</span></span>
- <span data-ttu-id="1d075-155">%windir% \\ system32 \\ping.exe -n 50 localhost</span><span class="sxs-lookup"><span data-stu-id="1d075-155">%windir%\\system32\\ping.exe -n 50 localhost</span></span>
- <span data-ttu-id="1d075-156">%windir% \\ system32 \\powercfg.exe /batteryreport /output %temp% \\ MDMDiagnostics \\battery-report.html</span><span class="sxs-lookup"><span data-stu-id="1d075-156">%windir%\\system32\\powercfg.exe /batteryreport /output %temp%\\MDMDiagnostics\\battery-report.html</span></span>
- <span data-ttu-id="1d075-157">%windir% \\ system32 \\powercfg.exe /energy /output %temp% \\ MDMDiagnostics \\energy-report.html</span><span class="sxs-lookup"><span data-stu-id="1d075-157">%windir%\\system32\\powercfg.exe /energy /output %temp%\\MDMDiagnostics\\energy-report.html</span></span>
- <span data-ttu-id="1d075-158">bitsadmin /list /allusers /verbose</span><span class="sxs-lookup"><span data-stu-id="1d075-158">bitsadmin /list /allusers /verbose</span></span>
- <span data-ttu-id="1d075-159">fltMC.exe</span><span class="sxs-lookup"><span data-stu-id="1d075-159">fltMC.exe</span></span>
- <span data-ttu-id="1d075-160">bcdedit /enum all /v</span><span class="sxs-lookup"><span data-stu-id="1d075-160">bcdedit /enum all /v</span></span>
- <span data-ttu-id="1d075-161">manage-bde -protectors -get</span><span class="sxs-lookup"><span data-stu-id="1d075-161">manage-bde -protectors -get</span></span>
- <span data-ttu-id="1d075-162">Windows PowerShell命令：</span><span class="sxs-lookup"><span data-stu-id="1d075-162">Windows PowerShell commands:</span></span>
    - <span data-ttu-id="1d075-163">Get-appxpackage -allusers</span><span class="sxs-lookup"><span data-stu-id="1d075-163">Get-appxpackage -allusers</span></span>
    - <span data-ttu-id="1d075-164">Get-appxpackage -packagetype bundle</span><span class="sxs-lookup"><span data-stu-id="1d075-164">Get-appxpackage -packagetype bundle</span></span>
    - <span data-ttu-id="1d075-165">Get-Service wuauserv</span><span class="sxs-lookup"><span data-stu-id="1d075-165">Get-Service wuauserv</span></span>
    - <span data-ttu-id="1d075-166">Get-NetFirewallRule</span><span class="sxs-lookup"><span data-stu-id="1d075-166">Get-NetFirewallRule</span></span>
    - <span data-ttu-id="1d075-167">Get-WmiObject -Class win32 \_ 产品</span><span class="sxs-lookup"><span data-stu-id="1d075-167">Get-WmiObject -Class win32\_product</span></span>
    - <span data-ttu-id="1d075-168">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="1d075-168">Get-ComputerInfo</span></span>
    - <span data-ttu-id="1d075-169">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1d075-169">Get-Service</span></span>
    - <span data-ttu-id="1d075-170">Get-Process</span><span class="sxs-lookup"><span data-stu-id="1d075-170">Get-Process</span></span>
    - <span data-ttu-id="1d075-171">Get-WmiObject Win32 \_ PnPSignedDriver</span><span class="sxs-lookup"><span data-stu-id="1d075-171">Get-WmiObject Win32\_PnPSignedDriver</span></span>

### <a name="event-logs"></a><span data-ttu-id="1d075-172">事件日志</span><span class="sxs-lookup"><span data-stu-id="1d075-172">Event logs</span></span>

- <span data-ttu-id="1d075-173">应用程序</span><span class="sxs-lookup"><span data-stu-id="1d075-173">Application</span></span>
- <span data-ttu-id="1d075-174">Microsoft-Windows-AppLocker/EXE 和 DLL</span><span class="sxs-lookup"><span data-stu-id="1d075-174">Microsoft-Windows-AppLocker/EXE and DLL</span></span>
- <span data-ttu-id="1d075-175">Microsoft-Windows-AppLocker/MSI 和脚本</span><span class="sxs-lookup"><span data-stu-id="1d075-175">Microsoft-Windows-AppLocker/MSI and Script</span></span>
- <span data-ttu-id="1d075-176">Microsoft-Windows-AppLocker/封装应用部署</span><span class="sxs-lookup"><span data-stu-id="1d075-176">Microsoft-Windows-AppLocker/Packaged app-Deployment</span></span>
- <span data-ttu-id="1d075-177">Microsoft-Windows-AppLocker/封装应用执行</span><span class="sxs-lookup"><span data-stu-id="1d075-177">Microsoft-Windows-AppLocker/Packaged app-Execution</span></span>
- <span data-ttu-id="1d075-178">Microsoft-Windows-Bitlocker/Bitlocker Management</span><span class="sxs-lookup"><span data-stu-id="1d075-178">Microsoft-Windows-Bitlocker/Bitlocker Management</span></span>
- <span data-ttu-id="1d075-179">Microsoft-Windows-SENSE/Operational</span><span class="sxs-lookup"><span data-stu-id="1d075-179">Microsoft-Windows-SENSE/Operational</span></span>
- <span data-ttu-id="1d075-180">Microsoft-Windows-SenseIR/Operational</span><span class="sxs-lookup"><span data-stu-id="1d075-180">Microsoft-Windows-SenseIR/Operational</span></span>
- <span data-ttu-id="1d075-181">设置</span><span class="sxs-lookup"><span data-stu-id="1d075-181">Setup</span></span>
- <span data-ttu-id="1d075-182">系统警报</span><span class="sxs-lookup"><span data-stu-id="1d075-182">System</span></span>

### <a name="files"></a><span data-ttu-id="1d075-183">文件</span><span class="sxs-lookup"><span data-stu-id="1d075-183">Files</span></span>

- <span data-ttu-id="1d075-184">%ProgramData% \\ Microsoft \\ DiagnosticLogCSP \\ Collectors \\ \* .etl</span><span class="sxs-lookup"><span data-stu-id="1d075-184">%ProgramData%\\Microsoft\\DiagnosticLogCSP\\Collectors\\\*.etl</span></span>
- <span data-ttu-id="1d075-185">%ProgramData% \\ Microsoft \\ IntuneManagementExtension \\ Logs \\ \* .\*</span><span class="sxs-lookup"><span data-stu-id="1d075-185">%ProgramData%\\Microsoft\\IntuneManagementExtension\\Logs\\\*.\*</span></span>
- <span data-ttu-id="1d075-186">%ProgramData% \\ Microsoft Windows Defender Support \\ \\ \\MpSupportFiles.cab</span><span class="sxs-lookup"><span data-stu-id="1d075-186">%ProgramData%\\Microsoft\\Windows Defender\\Support\\MpSupportFiles.cab</span></span>
- <span data-ttu-id="1d075-187">%ProgramData% \\ Microsoft \\ Windows \\ WlanReport \\wlan-report-latest.html</span><span class="sxs-lookup"><span data-stu-id="1d075-187">%ProgramData%\\Microsoft\\Windows\\WlanReport\\wlan-report-latest.html</span></span>
- <span data-ttu-id="1d075-188">%ProgramData% \\ Microsoft \\ Windows \\ WlanReport -SourceFileName wlan-report-latest.html</span><span class="sxs-lookup"><span data-stu-id="1d075-188">%ProgramData%\\Microsoft\\Windows\\WlanReport -SourceFileName wlan-report-latest.html</span></span>
- <span data-ttu-id="1d075-189">%windir% \\ ccm \\ logs \* .log</span><span class="sxs-lookup"><span data-stu-id="1d075-189">%windir%\\ccm\\logs\*.log</span></span>
- <span data-ttu-id="1d075-190">%windir% \\ ccmsetup \\ logs \* .log</span><span class="sxs-lookup"><span data-stu-id="1d075-190">%windir%\\ccmsetup\\logs\*.log</span></span>
- <span data-ttu-id="1d075-191">%windir% \\ logs \\ CBS \\ cbs.log</span><span class="sxs-lookup"><span data-stu-id="1d075-191">%windir%\\logs\\CBS\\cbs.log</span></span>
- <span data-ttu-id="1d075-192">%windir% \\ logs \\ measuredboot \* .\*</span><span class="sxs-lookup"><span data-stu-id="1d075-192">%windir%\\logs\\measuredboot\*.\*</span></span>
- <span data-ttu-id="1d075-193">%windir% \\ Logs \\ WindowsUpdate \* .etl</span><span class="sxs-lookup"><span data-stu-id="1d075-193">%windir%\\Logs\\WindowsUpdate\*.etl</span></span>
- <span data-ttu-id="1d075-194">%windir% \\ inf \\ \* .log</span><span class="sxs-lookup"><span data-stu-id="1d075-194">%windir%\\inf\\\*.log</span></span>
- <span data-ttu-id="1d075-195">%windir% \\ \\ 服务会话 \\ActionList.xml</span><span class="sxs-lookup"><span data-stu-id="1d075-195">%windir%\\servicing\\sessions\\ActionList.xml</span></span>
- <span data-ttu-id="1d075-196">%windir% \\ \\ 服务会话 \\Sessions.xml</span><span class="sxs-lookup"><span data-stu-id="1d075-196">%windir%\\servicing\\sessions\\Sessions.xml</span></span>
- <span data-ttu-id="1d075-197">%windir% \\ SoftwareDistribution \\ DataStore \\ Logs \\ edb.log</span><span class="sxs-lookup"><span data-stu-id="1d075-197">%windir%\\SoftwareDistribution\\DataStore\\Logs\\edb.log</span></span>
- <span data-ttu-id="1d075-198">%windir% \\ SoftwareDistribution \\ DataStore \\ DataStore.edb</span><span class="sxs-lookup"><span data-stu-id="1d075-198">%windir%\\SoftwareDistribution\\DataStore\\DataStore.edb</span></span>
- <span data-ttu-id="1d075-199">%windir% \\ logs \\ dism \\ dism.log</span><span class="sxs-lookup"><span data-stu-id="1d075-199">%windir%\\logs\\dism\\dism.log</span></span>
- <span data-ttu-id="1d075-200">%SystemRoot% \\ System32 \\ Winevt \\ 日志</span><span class="sxs-lookup"><span data-stu-id="1d075-200">%SystemRoot%\\System32\\Winevt\\Logs</span></span>\\
- <span data-ttu-id="1d075-201">%appdata% \\ Microsoft \\ Teams \\ media-stack \\ \* .blog</span><span class="sxs-lookup"><span data-stu-id="1d075-201">%appdata%\\Microsoft\\Teams\\media-stack\\\*.blog</span></span>
- <span data-ttu-id="1d075-202">%appdata% \\ Microsoft \\ Teams \\ skylib \\ \* .blog</span><span class="sxs-lookup"><span data-stu-id="1d075-202">%appdata%\\Microsoft\\Teams\\skylib\\\*.blog</span></span>
- <span data-ttu-id="1d075-203">%appdata% \\ Microsoft \\ Teams \\ media-stack \\ \* .etl</span><span class="sxs-lookup"><span data-stu-id="1d075-203">%appdata%\\Microsoft\\Teams\\media-stack\\\*.etl</span></span>
- <span data-ttu-id="1d075-204">%appdata% \\ Microsoft \\ Teams \\logs.txt</span><span class="sxs-lookup"><span data-stu-id="1d075-204">%appdata%\\Microsoft\\Teams\\logs.txt</span></span>
- <span data-ttu-id="1d075-205">%windir% \\ Windows \\ System32 \\ winevt \\ \* 。\*</span><span class="sxs-lookup"><span data-stu-id="1d075-205">%windir%\\Windows\\System32\\winevt\\\*.\*</span></span>