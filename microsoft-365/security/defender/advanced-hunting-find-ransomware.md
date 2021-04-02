---
title: 使用高级搜寻查找勒索软件
description: 使用高级搜寻查找受勒索软件潜在影响的设备。
keywords: 高级搜寻， 勒索软件， 威胁搜寻， 网络威胁搜寻， 搜索， 查询， 遥测， Microsoft 365， Microsoft 威胁防护， Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 97f2174f74e7866f75b901cd1609341548a1a7c5
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2021
ms.locfileid: "51498219"
---
# <a name="hunt-for-ransomware"></a><span data-ttu-id="478d6-104">查寻勒索软件</span><span class="sxs-lookup"><span data-stu-id="478d6-104">Hunt for ransomware</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

<span data-ttu-id="478d6-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="478d6-105">**Applies to:**</span></span>
- <span data-ttu-id="478d6-106">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="478d6-106">Microsoft 365 Defender</span></span>

<span data-ttu-id="478d6-107">勒索软件已从影响单个计算机用户的简单商品恶意软件快速演变为严重影响行业和政府机构的企业威胁。</span><span class="sxs-lookup"><span data-stu-id="478d6-107">Ransomware has rapidly evolved from being simple commodity malware affecting individual computer users to an enterprise threat that is severely impacting industries and government institutions.</span></span> <span data-ttu-id="478d6-108">[虽然 Microsoft 365 Defender](microsoft-365-defender.md)提供了许多检测和阻止勒索软件和相关入侵活动的功能，但主动检查泄露的迹象有助于保护你的网络。</span><span class="sxs-lookup"><span data-stu-id="478d6-108">While [Microsoft 365 Defender](microsoft-365-defender.md) provides many capabilities that detect and block ransomware and associated intrusion activities, performing proactive checks for signs of compromise can help keep your network protected.</span></span>

> [<span data-ttu-id="478d6-109">阅读有关人工操作的勒索软件</span><span class="sxs-lookup"><span data-stu-id="478d6-109">Read about human-operated ransomware</span></span>](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

<span data-ttu-id="478d6-110">借助[](advanced-hunting-overview.md) Microsoft 365 Defender 中的高级搜寻功能，你可以创建查询，以查找与勒索软件活动关联的单个项目。</span><span class="sxs-lookup"><span data-stu-id="478d6-110">With [advanced hunting](advanced-hunting-overview.md) in Microsoft 365 Defender, you can create queries that locate individual artifacts associated with ransomware activity.</span></span> <span data-ttu-id="478d6-111">还可以运行更复杂的查询，以查找活动的迹象并权衡这些符号以查找需要立即关注的设备。</span><span class="sxs-lookup"><span data-stu-id="478d6-111">You can also run more sophisticated queries that can look for signs of activity and weigh those signs to find devices that require immediate attention.</span></span>

## <a name="signs-of-ransomware-activity"></a><span data-ttu-id="478d6-112">勒索软件活动的迹象</span><span class="sxs-lookup"><span data-stu-id="478d6-112">Signs of ransomware activity</span></span>
<span data-ttu-id="478d6-113">Microsoft 安全研究人员在由复杂的恶意软件启动的许多勒索软件活动中观察到各种常见但很细微的项目。</span><span class="sxs-lookup"><span data-stu-id="478d6-113">Microsoft security researchers have observed various common yet subtle artifacts in many ransomware campaigns launched by sophisticated intruders.</span></span> <span data-ttu-id="478d6-114">这些符号主要涉及使用系统工具准备加密、阻止检测和清除取证证据。</span><span class="sxs-lookup"><span data-stu-id="478d6-114">These signs mostly involve use of system tools to prepare for encryption, prevent detection, and clear forensic evidence.</span></span>

| <span data-ttu-id="478d6-115">勒索软件活动</span><span class="sxs-lookup"><span data-stu-id="478d6-115">Ransomware activity</span></span> | <span data-ttu-id="478d6-116">常用工具</span><span class="sxs-lookup"><span data-stu-id="478d6-116">Common tools</span></span> | <span data-ttu-id="478d6-117">Intent</span><span class="sxs-lookup"><span data-stu-id="478d6-117">Intent</span></span> |
|--|--|--|
| <span data-ttu-id="478d6-118">停止进程</span><span class="sxs-lookup"><span data-stu-id="478d6-118">Stop processes</span></span> | <span data-ttu-id="478d6-119">_taskkill.exe_ _、net stop_</span><span class="sxs-lookup"><span data-stu-id="478d6-119">_taskkill.exe_, _net stop_</span></span> | <span data-ttu-id="478d6-120">确保各种应用程序不会锁定针对加密的文件。</span><span class="sxs-lookup"><span data-stu-id="478d6-120">Ensure files targeted for encryption are not locked by various applications.</span></span> |
| <span data-ttu-id="478d6-121">关闭服务</span><span class="sxs-lookup"><span data-stu-id="478d6-121">Turn off services</span></span> | <span data-ttu-id="478d6-122">_sc.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-122">_sc.exe_</span></span> | <span data-ttu-id="478d6-123">- 确保各种应用程序不会锁定针对加密的文件。</span><span class="sxs-lookup"><span data-stu-id="478d6-123">- Ensure files targeted for encryption are not locked by various applications.</span></span><br><span data-ttu-id="478d6-124">- 阻止安全软件中断加密和其他勒索软件活动。</span><span class="sxs-lookup"><span data-stu-id="478d6-124">- Prevent security software from disrupting encryption and other ransomware activity.</span></span><br><span data-ttu-id="478d6-125">- 停止备份软件创建可恢复副本。</span><span class="sxs-lookup"><span data-stu-id="478d6-125">- Stop backup software from creating recoverable copies.</span></span>  |
| <span data-ttu-id="478d6-126">删除日志和文件</span><span class="sxs-lookup"><span data-stu-id="478d6-126">Delete logs and files</span></span> | <span data-ttu-id="478d6-127">_cipher.exe_ _、wevtutil_ _、fsutil.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-127">_cipher.exe_, _wevtutil_, _fsutil.exe_</span></span> | <span data-ttu-id="478d6-128">删除取证证据。</span><span class="sxs-lookup"><span data-stu-id="478d6-128">Remove forensic evidence.</span></span> |
| <span data-ttu-id="478d6-129">删除卷影副本</span><span class="sxs-lookup"><span data-stu-id="478d6-129">Delete shadow copies</span></span>  | <span data-ttu-id="478d6-130">_vsadmin.exe_ _、wmic.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-130">_vsadmin.exe_, _wmic.exe_</span></span> | <span data-ttu-id="478d6-131">删除可用于恢复加密文件的驱动器卷影副本。</span><span class="sxs-lookup"><span data-stu-id="478d6-131">Remove drive shadow copies that can be used to recover encrypted files.</span></span> |
| <span data-ttu-id="478d6-132">删除和停止备份</span><span class="sxs-lookup"><span data-stu-id="478d6-132">Delete and stop backups</span></span> | <span data-ttu-id="478d6-133">_wbadmin.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-133">_wbadmin.exe_</span></span> | <span data-ttu-id="478d6-134">删除现有备份并停止计划的备份任务，以防止加密后恢复。</span><span class="sxs-lookup"><span data-stu-id="478d6-134">Delete existing backups and stop scheduled backup tasks, preventing recovery after encryption.</span></span> |
| <span data-ttu-id="478d6-135">修改启动设置</span><span class="sxs-lookup"><span data-stu-id="478d6-135">Modify boot settings</span></span> | <span data-ttu-id="478d6-136">_bcdedit.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-136">_bcdedit.exe_</span></span> | <span data-ttu-id="478d6-137">在由加密过程导致的启动失败后关闭警告和自动修复。</span><span class="sxs-lookup"><span data-stu-id="478d6-137">Turn off warnings and automatic repairs after boot failures that can be caused by the encryption process.</span></span> |
| <span data-ttu-id="478d6-138">关闭恢复工具</span><span class="sxs-lookup"><span data-stu-id="478d6-138">Turn off recovery tools</span></span> | <span data-ttu-id="478d6-139">_schtasks.exe_ _、regedit.exe_、</span><span class="sxs-lookup"><span data-stu-id="478d6-139">_schtasks.exe_, _regedit.exe_,</span></span> | <span data-ttu-id="478d6-140">关闭系统还原和其他系统恢复选项。</span><span class="sxs-lookup"><span data-stu-id="478d6-140">Turn off System Restore and other system recovery options.</span></span> |

## <a name="check-for-individual-signs-of-ransomware-activity"></a><span data-ttu-id="478d6-141">检查勒索软件活动的个别标志</span><span class="sxs-lookup"><span data-stu-id="478d6-141">Check for individual signs of ransomware activity</span></span>
<span data-ttu-id="478d6-142">许多构成勒索软件行为的活动（包括上一节中所述的活动）可能是恶意的。</span><span class="sxs-lookup"><span data-stu-id="478d6-142">Many activities that constitute ransomware behavior, including the activities described in the preceding section, can be benign.</span></span> <span data-ttu-id="478d6-143">When using the following queries to locate ransomware， run more than one query to check whether the same devices are exhibiting various signs of possible ransomware activity.</span><span class="sxs-lookup"><span data-stu-id="478d6-143">When using the following queries to locate ransomware, run more than one query to check whether the same devices are exhibiting various signs of possible ransomware activity.</span></span>

### <a name="stopping-multiple-processes-using-_taskkillexe_"></a><span data-ttu-id="478d6-144">使用工具停止多个 _taskkill.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-144">Stopping multiple processes using _taskkill.exe_</span></span>
<span data-ttu-id="478d6-145">此查询会检查是否尝试使用taskkill.exe停止至少 10 _个单独的_ 进程。</span><span class="sxs-lookup"><span data-stu-id="478d6-145">This query checks for attempts to stop at least 10 separate processes using the _taskkill.exe_ utility.</span></span> [<span data-ttu-id="478d6-146">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-146">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RS2vCUBCFz7rgfwiuIkit3eumVSgtpYvuS9SLDTY2eLUvxN_eb8YHKlFkyNzJzDkn505aailRX7mmGlFlmhNBhUrOSGeuT3L0s6QqNaMagolEcMyCbApjx2e8TYhcH8Q1mB-emq50z_lF39gvBzo9-gEF-6Yhlyh9653ejCfRK6zCsaZfuJOu-x2jkqqN-0Yls-8-gp6dZ52OVuT6Sad1plulyN0KIkMt15_zt7zHDe8OBwv3btoJToa7Tnp0T8Ou9WzfT761gPOm3_FQ16Zxp2qcCdg33_rlyokG-iXv7_4BRNMnhkortmvTW6rqnZ7bgP2Vtm70D3d9wcFaAgAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using taskkill.exe
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10
```
  
### <a name="stopping-processes-using-_net-stop_"></a><span data-ttu-id="478d6-147">使用网络停止 _停止进程_</span><span class="sxs-lookup"><span data-stu-id="478d6-147">Stopping processes using _net stop_</span></span>
<span data-ttu-id="478d6-148">此查询使用 net stop 命令检查是否尝试停止至少 10 _个单独的_ 进程。</span><span class="sxs-lookup"><span data-stu-id="478d6-148">This query checks for attempts to stop at least 10 separate processes using the _net stop_ command.</span></span> [<span data-ttu-id="478d6-149">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-149">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2RQUvDUBCE5yz0P4ScUijWereXVkGQIti7aA1pqakhL7VVxN_ebzc1NBChPLJv2Z2ZN5sdaqhId1ppozeyF1WcVLkK7kCl0gcx-F2QFSrJFmACJ3XMlmgKGfmGWnXC6OlCU2qfIIz12OLfUk_h2FuG_IG505JayRdpDit3bIW33B2M3WeGSqIRrvudTJvpnWzmPKvc6JcYHx1eEvd8savV07e9TchzTt198AlNZ0kluNLfjHHjIPAvak4J_tvx9XtPR6ypbn1icxShvGgqyVkO-hrAm7VUrRcaTWOs6T_7hs7XjfSqL-Lpvu5BDLxjqKRjI9a9Juvew__T2x5HutIB3T1qt4QCAAA&runQuery=true&timeRangeId=week)

```kusto
// Find attempts to stop processes using net stop
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10
```
### <a name="deletion-of-data-on-multiple-drives-using-_cipherexe_"></a><span data-ttu-id="478d6-150">使用数据删除多个驱动器上 _cipher.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-150">Deletion of data on multiple drives using _cipher.exe_</span></span>
<span data-ttu-id="478d6-151">此查询将检查是否尝试使用cipher.exe删除 _多个驱动器上的数据_。</span><span class="sxs-lookup"><span data-stu-id="478d6-151">This query checks for attempts to delete data on multiple drives using _cipher.exe_.</span></span> <span data-ttu-id="478d6-152">此活动通常由勒索软件执行，以防止在加密后恢复数据。</span><span class="sxs-lookup"><span data-stu-id="478d6-152">This activity is typically done by ransomware to prevent recovery of data after encryption.</span></span> [<span data-ttu-id="478d6-153">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-153">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI1SXUvDQBCcZ8H_cOQpgWLoD7AvVUEo4oPvElO1pblUcmn9QPztzk6TEuEsIdzdZndndm73cuRwWGDLb0PrhWfDs8Qab1jhmX8X3D-4HJbcK66W0Rqv8hT8K4RsiPW0PHbMasVQdbiGf3vaAec4wxWtPT0lz3vhSsUCrpVVE33I_Cb6vdNhTA9EeeVaVc8KDjOugmq2SDFlrSyKvCHS1NwJZ55L_HBPondNGDGWXP2JdyMnv927UnXHWwf6l4MunupXTOPfXszVT8_smriFOCxrRU-QclOQDLgCNRwQ1u8vZc8H2o1xp-7a7U1NefSko6pnmKjakNVi4chpiA39j-rGeF6HJ3xyH76NW2ZMFLGsNDJ9i05pZSPmVdDfq-jncfqtOuU5zSuQz6Zq92w7Hfbm-9cUm-d_vZ9J9S81O2KIfAMAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for cipher.exe deleting data from multiple drives
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine),
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1
```

### <a name="clearing-of-forensic-evidence-from-event-logs-using-_wevtutil_"></a><span data-ttu-id="478d6-154">使用 _wevtutil_ 从事件日志中清除取证证据</span><span class="sxs-lookup"><span data-stu-id="478d6-154">Clearing of forensic evidence from event logs using _wevtutil_</span></span>
<span data-ttu-id="478d6-155">此查询使用 wevtutil 检查从事件日志中清除至少 10 个 _日志条目的尝试_。</span><span class="sxs-lookup"><span data-stu-id="478d6-155">This query checks for attempts to clear at least 10 log entries from event logs using _wevtutil_.</span></span> [<span data-ttu-id="478d6-156">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-156">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWRTU_CQBCG37OJ_2HDqSQkwMGjXgoHEg4cUI-m2hUaqGu6BaPxx_vsEFCTxmA225nOvB_tzFBDOc0VOBuyZ2JD3CnKEwMVpzfyPbVWlba8t9Sdnsi9CsPXdLfWf7Wq4xm0QuVSF5oYv4LhtQAfLIucKXWvF5gH5Ke5rak1prKEVRu2xalG3emGW6AdlGmsUv1O5m-fnLzmFHiV_G9FTKg1lUjs6Z5vucPvljsD0TOXhP6_Vm7841dFZnPAN2A_DDu36eSnCSbNnc3B6Zpb4nasZGf59zWA963orZdcEiKelBNvQ_fBNny-utOj3nn-3OUMxMA6CZV1bCt1r8i6d_TXFNKWxxrpC48hm8miAgAA&runQuery=true&timeRangeId=week)

```kusto
// Look for use of wevtutil to clear multiple logs
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10
```

### <a name="turning-off-services-using-_scexe_"></a><span data-ttu-id="478d6-157">使用应用程序关闭 _sc.exe_</span><span class="sxs-lookup"><span data-stu-id="478d6-157">Turning off services using _sc.exe_</span></span>
<span data-ttu-id="478d6-158">此查询将检查是否尝试使用sc.exe关闭至少 10 _个现有服务_。</span><span class="sxs-lookup"><span data-stu-id="478d6-158">This query checks for attempts to turn off at least 10 existing services using _sc.exe_.</span></span> [<span data-ttu-id="478d6-159">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-159">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAKWST2vCQBDF31nodwg5RZCqhx7bi3ooeCjovaQxraIxxfU_fvj-ZoiiEIqlhM3Ozrz3ZnZm22or0lAl3xzrk33FHpTpUbn2rEgTzfCk-tACa6kvR-Qgt5wzrKAHNdTHOnveiJZVLGiAP4e5rpAnFHaauoZlGMMqHLsmT6FvfC-slFylEnWpoVnLvM3Twy74UnJNuJdVa6gpnsAe-81iVzbE3_kZiCV9mlHZf3Sue5pzii-3C9pU3BWYo_NGKPdvGJZh4x2N9Owzyi6e5K5qmmrVKg_9dNY11hzvu0_8fu0ItQP_6zfxCqLlEUMlNVO36BNW_ax_74K9l646-gFts39I1AIAAA&runQuery=true&timeRangeId=week)

```kusto
// Look for sc.exe disabling services
DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10
```

### <a name="turning-off-system-restore"></a><span data-ttu-id="478d6-160">关闭系统还原</span><span class="sxs-lookup"><span data-stu-id="478d6-160">Turning off System Restore</span></span>
<span data-ttu-id="478d6-161">此查询标识了尝试停止系统还原并阻止系统创建还原点，还原点可用于恢复通过勒索软件加密的数据。</span><span class="sxs-lookup"><span data-stu-id="478d6-161">This query identifies attempts to stop System Restore and prevent the system from creating restore points, which can be used to recover data encrypted by ransomware.</span></span> [<span data-ttu-id="478d6-162">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-162">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAK2S3UrDQBCFz7XgO6y9id4o6HWvrIVCkaJPENOYFNumZGO1ID673w4xJA1isbJMZnZ-zpzM7EiptlooQc9UqjDLc-7wp1qrwj7Via44MzK35FTotTI5PXMr0aVe8cy15NzoGo-zqg_0m3KQSsRpQtbC6uMGpdt3jHeJfU_GymqG-uQb9XpcEn1HIuvmGpZT0Aq99Dim4G3ousNO8K04sSE6EEN22kL6jvzO-LaDNW2QzqxLmGBsPo9vUMt_oA8Na3DQv3vwcmPiifpmds48jkhut8T2FLikxm_T4bI_m_6uQt-wrXO28lPPSBcdziOqPFlP9RYy47tDKtuZM07hVtSvaJ_HYRPL63-NyMgtmtWv5684jy2WDx2O0ZEM562ZBLQvURxur6gDAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
//Pivoting for rundll32  
| where InitiatingProcessFileName =~ 'rundll32.exe'   
//Looking for empty command line   
and InitiatingProcessCommandLine !contains " " and InitiatingProcessCommandLine != ""  
//Looking for schtasks.exe as the created process  
and FileName in~ ('schtasks.exe')  
//Disabling system restore   
and ProcessCommandLine has 'Change' and ProcessCommandLine has 'SystemRestore' 
and ProcessCommandLine has 'disable'
```

### <a name="backup-deletion"></a><span data-ttu-id="478d6-163">备份删除</span><span class="sxs-lookup"><span data-stu-id="478d6-163">Backup deletion</span></span>
<span data-ttu-id="478d6-164">此查询标识加密 _wmic.exe_ 删除卷影副本快照的使用。</span><span class="sxs-lookup"><span data-stu-id="478d6-164">This query identifies use of _wmic.exe_ to delete shadow copy snapshots prior to encryption.</span></span> [<span data-ttu-id="478d6-165">运行查询</span><span class="sxs-lookup"><span data-stu-id="478d6-165">Run query</span></span>](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAJWS2wqCQBCG_-ugd5CupTfoqgMIEV70AqFLGp5QyYLo2fsavEjxwlhWZ7-df2Z2dndyuitVxD9UrdKshrGHOxVqsZda6CVPnRJYzfR0QJVhnXRRbmSjN98VXrlFXEMfzNWkfphti50zLmSMdURfmFcCaSxqY3aMX4eqVKUn1OsV_8eLWX_rbwcVVhblBovY8bT76U-AxoedWeeWp7WzV0YDMqSQFNZavuuopnHH_Iku-lbJnLPMyxnYDTp4bZ5P9M5uNpsZIWSn7l_CuNoPSggb4z4CAAA&runQuery=true&timeRangeId=week)

```kusto
DeviceProcessEvents
| where FileName =~ "wmic.exe"
| where ProcessCommandLine has "shadowcopy" and ProcessCommandLine has "delete"
| project DeviceId, Timestamp, InitiatingProcessFileName, FileName,
ProcessCommandLine, InitiatingProcessIntegrityLevel, InitiatingProcessParentFileName
```

## <a name="check-for-multiple-signs-of-ransomware-activity"></a><span data-ttu-id="478d6-166">检查勒索软件活动的多个标志</span><span class="sxs-lookup"><span data-stu-id="478d6-166">Check for multiple signs of ransomware activity</span></span>
<span data-ttu-id="478d6-167">除了单独运行多个查询外，您还可以使用全面的查询来检查勒索软件活动的多个标志，以标识受影响的设备。</span><span class="sxs-lookup"><span data-stu-id="478d6-167">Instead of running several queries separately, you can also use a comprehensive query that checks for multiple signs of ransomware activity to identify affected devices.</span></span> <span data-ttu-id="478d6-168">以下合并查询：</span><span class="sxs-lookup"><span data-stu-id="478d6-168">The following consolidated  query:</span></span>
- <span data-ttu-id="478d6-169">查找勒索软件活动的相对具体和细微的标志</span><span class="sxs-lookup"><span data-stu-id="478d6-169">Looks for both relatively concrete and subtle signs of ransomware activity</span></span>
- <span data-ttu-id="478d6-170">权衡是否存在这些符号</span><span class="sxs-lookup"><span data-stu-id="478d6-170">Weighs the presence of these signs</span></span>
- <span data-ttu-id="478d6-171">标识具有较高机会成为勒索软件目标的设备</span><span class="sxs-lookup"><span data-stu-id="478d6-171">Identifies devices with a higher chance of being targets of ransomware</span></span> 

<span data-ttu-id="478d6-172">运行时，此合并查询将返回已呈现多个攻击信号的设备列表。</span><span class="sxs-lookup"><span data-stu-id="478d6-172">When run, this consolidated query returns a list of devices that have exhibited multiple signs of attack.</span></span> <span data-ttu-id="478d6-173">还显示了每种类型的勒索软件活动的计数。</span><span class="sxs-lookup"><span data-stu-id="478d6-173">The count of each type of ransomware activity is also shown.</span></span> <span data-ttu-id="478d6-174">若要运行此合并查询，请直接将其复制到[高级搜寻查询编辑器 。](https://security.microsoft.com/advanced-hunting)</span><span class="sxs-lookup"><span data-stu-id="478d6-174">To run this consolidated query, copy it directly to the [advanced hunting query editor](https://security.microsoft.com/advanced-hunting).</span></span> 

```kusto
// Find attempts to stop processes using taskkill.exe
let taskKill = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "taskkill.exe" 
| summarize taskKillCount = dcount(ProcessCommandLine), TaskKillList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where taskKillCount > 10;
// Find attempts to stop processes using net stop
let netStop = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "net.exe" and ProcessCommandLine has "stop"
| summarize netStopCount = dcount(ProcessCommandLine), NetStopList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 2m)
| where netStopCount > 10;
// Look for cipher.exe deleting data from multiple drives
let cipher = DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "cipher.exe" 
// cipher.exe /w flag used for deleting data 
| where ProcessCommandLine has "/w" 
| summarize CipherCount = dcount(ProcessCommandLine), 
CipherList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 1m) 
// cipher.exe accessing multiple drives in a short timeframe 
| where CipherCount > 1;
// Look for use of wevtutil to clear multiple logs
let wevtutilClear = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "WEVTUTIL" and ProcessCommandLine has "CL"
| summarize LogClearCount = dcount(ProcessCommandLine), ClearedLogList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where LogClearCount > 10;
// Look for sc.exe disabling services
let scDisable = DeviceProcessEvents
| where Timestamp > ago(1d)
| where ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled"
| summarize ScDisableCount = dcount(ProcessCommandLine), ScDisableList = make_set(ProcessCommandLine) by DeviceId, bin(Timestamp, 5m)
| where ScDisableCount > 10;
// Main query for counting and aggregating evidence
DeviceProcessEvents
| where Timestamp > ago(1d)
| where FileName =~ "vssadmin.exe" and ProcessCommandLine has_any("list shadows", "delete shadows")
or FileName =~ "fsutil.exe" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal"
or ProcessCommandLine has("bcdedit") and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures")
or ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup")
or (ProcessCommandLine has "wevtutil" and ProcessCommandLine has "cl") 
or (ProcessCommandLine has "wmic" and ProcessCommandLine has "shadowcopy delete")
or (ProcessCommandLine has "sc" and ProcessCommandLine has "config" and ProcessCommandLine has "disabled")
| extend Bcdedit = iff(ProcessCommandLine has "bcdedit" and ProcessCommandLine has_any("recoveryenabled no", "bootstatuspolicy ignoreallfailures"), 1, 0)
| extend ShadowCopyDelete = iff (ProcessCommandLine has "shadowcopy delete", 1, 0)
| extend VssAdminShadows = iff(ProcessCommandLine has "vssadmin" and ProcessCommandLine has_any("list shadows", "delete shadows"), 1, 0)
| extend Wbadmin = iff(ProcessCommandLine has "wbadmin" and ProcessCommandLine has "delete" and ProcessCommandLine has_any("backup", "catalog", "systemstatebackup"), 1,0)
| extend Fsutil = iff(ProcessCommandLine has "fsutil" and ProcessCommandLine has "usn" and ProcessCommandLine has "deletejournal", 1, 0)
| summarize FirstActivity = min(Timestamp), ReportId = any(ReportId), Commands = make_set(ProcessCommandLine) by DeviceId, Fsutil, Wbadmin, ShadowCopyDelete, Bcdedit, VssAdminShadows, bin(Timestamp, 6h)
// Joining extra evidence
| join kind=leftouter (wevtutilClear) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (cipher) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (netStop) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (taskKill) on $left.DeviceId == $right.DeviceId
| join kind=leftouter (scDisable) on $left.DeviceId == $right.DeviceId
| extend WevtutilUse = iff(LogClearCount > 10, 1, 0)
| extend CipherUse = iff(CipherCount > 1, 1, 0)
| extend NetStopUse = iff(netStopCount > 10, 1, 0)
| extend TaskkillUse = iff(taskKillCount > 10, 1, 0)
| extend ScDisableUse = iff(ScDisableCount > 10, 1, 0)
// Adding up all evidence
| mv-expand CommandList = NetStopList, TaskKillList, ClearedLogList, CipherList, Commands, ScDisableList
// Format results
| summarize BcdEdit = iff(make_set(Bcdedit) contains "1" , 1, 0), NetStop10PlusCommands = iff(make_set(NetStopUse) contains "1", 1, 0), Wevtutil10PlusLogsCleared = iff(make_set(WevtutilUse) contains "1", 1, 0),
CipherMultipleDrives = iff(make_set(CipherUse) contains "1", 1, 0), Fsutil = iff(make_set(Fsutil) contains "1", 1, 0), ShadowCopyDelete = iff(make_set(ShadowCopyDelete) contains "1", 1, 0),
Wbadmin = iff(make_set(Wbadmin) contains "1", 1, 0), TaskKill10PlusCommand = iff(make_set(TaskkillUse) contains "1", 1, 0), VssAdminShadow = iff(make_set(VssAdminShadows) contains "1", 1, 0), 
ScDisable = iff(make_set(ScDisableUse) contains "1", 1, 0), TotalEvidenceCount = count(CommandList), EvidenceList = make_set(Commands), StartofBehavior = min(FirstActivity) by DeviceId, bin(Timestamp, 1d)
| extend UniqueEvidenceCount = BcdEdit + NetStop10PlusCommands + Wevtutil10PlusLogsCleared + CipherMultipleDrives + Wbadmin + Fsutil + TaskKill10PlusCommand + VssAdminShadow + ScDisable + ShadowCopyDelete
| where UniqueEvidenceCount > 2
```
### <a name="understand-and-tweak-the-query-results"></a><span data-ttu-id="478d6-175">了解并调整查询结果</span><span class="sxs-lookup"><span data-stu-id="478d6-175">Understand and tweak the query results</span></span>
<span data-ttu-id="478d6-176">合并查询将返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="478d6-176">The consolidated query returns the following results:</span></span>

- <span data-ttu-id="478d6-177">**DeviceId** 标识受影响的设备</span><span class="sxs-lookup"><span data-stu-id="478d6-177">**DeviceId**—identifies the affected device</span></span> 
- <span data-ttu-id="478d6-178">**TimeStamp**- 第一次在设备上观察到任何勒索软件活动的符号时</span><span class="sxs-lookup"><span data-stu-id="478d6-178">**TimeStamp**—first time any sign of ransomware activity was observed on the device</span></span>
- <span data-ttu-id="478d6-179">**特定活动标志**- 显示在多个列中的每个符号的计数，如 _BcdEdit_ 或 _FsUtil_</span><span class="sxs-lookup"><span data-stu-id="478d6-179">**Specific signs of activity**—the count for each sign shown in multiple columns, such as _BcdEdit_ or _FsUtil_</span></span>
- <span data-ttu-id="478d6-180">**TotalEvidenceCount** 观测到的符号数</span><span class="sxs-lookup"><span data-stu-id="478d6-180">**TotalEvidenceCount**—number of observed signs</span></span>
- <span data-ttu-id="478d6-181">**UniqueEvidenceCount** 观测到的符号类型的数量</span><span class="sxs-lookup"><span data-stu-id="478d6-181">**UniqueEvidenceCount**—number of types of observed signs</span></span>

![勒索软件活动的查询结果的图像](../../media/advanced-hunting-ransomware-query.png)

<span data-ttu-id="478d6-183">*显示受影响的设备和各种勒索软件活动标志计数的查询结果*</span><span class="sxs-lookup"><span data-stu-id="478d6-183">*Query results showing affected devices and counts of various signs of ransomware activity*</span></span>

<span data-ttu-id="478d6-184">默认情况下，查询结果仅列出具有两种以上类型的勒索软件活动的设备。</span><span class="sxs-lookup"><span data-stu-id="478d6-184">By default, the query result lists only devices that have more than two types of ransomware activity.</span></span> <span data-ttu-id="478d6-185">To see all devices with any sign of ransomware activity， modify the following `where` operator and set the number to zero (0) .</span><span class="sxs-lookup"><span data-stu-id="478d6-185">To see all devices with any sign of ransomware activity, modify the following `where` operator and set the number to zero (0).</span></span> <span data-ttu-id="478d6-186">若要查看较少的设备，请设置一个更高的数量。</span><span class="sxs-lookup"><span data-stu-id="478d6-186">To see fewer devices, set a higher number.</span></span> 

```kusto
| where UniqueEvidenceCount > 2
```

## <a name="related-topics"></a><span data-ttu-id="478d6-187">相关主题</span><span class="sxs-lookup"><span data-stu-id="478d6-187">Related topics</span></span>
- [<span data-ttu-id="478d6-188">高级搜寻概述</span><span class="sxs-lookup"><span data-stu-id="478d6-188">Advanced hunting overview</span></span>](advanced-hunting-overview.md)
- [<span data-ttu-id="478d6-189">了解查询语言</span><span class="sxs-lookup"><span data-stu-id="478d6-189">Learn the query language</span></span>](advanced-hunting-query-language.md)
- [<span data-ttu-id="478d6-190">处理查询结果</span><span class="sxs-lookup"><span data-stu-id="478d6-190">Work with query results</span></span>](advanced-hunting-query-results.md)
- [<span data-ttu-id="478d6-191">使用共享查询</span><span class="sxs-lookup"><span data-stu-id="478d6-191">Use shared queries</span></span>](advanced-hunting-shared-queries.md)
- [<span data-ttu-id="478d6-192">了解架构</span><span class="sxs-lookup"><span data-stu-id="478d6-192">Understand the schema</span></span>](advanced-hunting-schema-tables.md)
- [<span data-ttu-id="478d6-193">应用查询最佳做法</span><span class="sxs-lookup"><span data-stu-id="478d6-193">Apply query best practices</span></span>](advanced-hunting-best-practices.md)