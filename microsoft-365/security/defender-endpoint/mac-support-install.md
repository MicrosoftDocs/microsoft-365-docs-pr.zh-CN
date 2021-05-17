---
title: 解决 Mac 上 Microsoft Defender for Endpoint 的安装问题
description: 解决 Mac 上的 Microsoft Defender for Endpoint 中的安装问题。
keywords: microsoft， defender， Microsoft Defender for Endpoint， mac， 安装
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
ms.openlocfilehash: 5166de3a7c7017979a93ac7026636ba24671892e
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935145"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a><span data-ttu-id="d8f84-104">解决 macOS 上的 Microsoft Defender for Endpoint 的安装问题</span><span class="sxs-lookup"><span data-stu-id="d8f84-104">Troubleshoot installation issues for Microsoft Defender for Endpoint on macOS</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


<span data-ttu-id="d8f84-105">**适用于：**</span><span class="sxs-lookup"><span data-stu-id="d8f84-105">**Applies to:**</span></span>

- [<span data-ttu-id="d8f84-106">macOS 上的 Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="d8f84-106">Microsoft Defender for Endpoint on macOS</span></span>](microsoft-defender-endpoint-mac.md)
- [<span data-ttu-id="d8f84-107">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="d8f84-107">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [<span data-ttu-id="d8f84-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="d8f84-108">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="d8f84-109">想要体验 Microsoft Defender for Endpoint？</span><span class="sxs-lookup"><span data-stu-id="d8f84-109">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="d8f84-110">注册免费试用版。</span><span class="sxs-lookup"><span data-stu-id="d8f84-110">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a><span data-ttu-id="d8f84-111">安装失败</span><span class="sxs-lookup"><span data-stu-id="d8f84-111">Installation failed</span></span>

<span data-ttu-id="d8f84-112">对于手动安装，安装向导的"摘要"页显示"安装过程中出错。</span><span class="sxs-lookup"><span data-stu-id="d8f84-112">For manual installation, the Summary page of the installation wizard says, "An error occurred during installation.</span></span> <span data-ttu-id="d8f84-113">安装程序遇到导致安装失败的错误。</span><span class="sxs-lookup"><span data-stu-id="d8f84-113">The Installer encountered an error that caused the installation to fail.</span></span> <span data-ttu-id="d8f84-114">请与软件制造商联系寻求帮助。"</span><span class="sxs-lookup"><span data-stu-id="d8f84-114">Contact the software manufacturer for assistance."</span></span> <span data-ttu-id="d8f84-115">对于 MDM 部署，它显示为常规安装失败。</span><span class="sxs-lookup"><span data-stu-id="d8f84-115">For MDM deployments, it displays as a generic installation failure as well.</span></span>

<span data-ttu-id="d8f84-116">尽管我们不会向最终用户显示确切的错误，但我们在 中日志文件安装进度。 `/Library/Logs/Microsoft/mdatp/install.log`</span><span class="sxs-lookup"><span data-stu-id="d8f84-116">While we do not display an exact error to the end user, we keep a log file with installation progress in `/Library/Logs/Microsoft/mdatp/install.log`.</span></span> <span data-ttu-id="d8f84-117">每个安装会话都附加到此日志文件。</span><span class="sxs-lookup"><span data-stu-id="d8f84-117">Each installation session appends to this log file.</span></span> <span data-ttu-id="d8f84-118">只能用于 `sed` 输出上次安装会话：</span><span class="sxs-lookup"><span data-stu-id="d8f84-118">You can use `sed` to output the last installation session only:</span></span>

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

<span data-ttu-id="d8f84-119">本示例中，实际原因的前缀为 `[ERROR]` 。</span><span class="sxs-lookup"><span data-stu-id="d8f84-119">In this example, the actual reason is prefixed with `[ERROR]`.</span></span>
<span data-ttu-id="d8f84-120">安装失败，因为不支持这些版本之间的降级。</span><span class="sxs-lookup"><span data-stu-id="d8f84-120">The installation failed because a downgrade between these versions is not supported.</span></span>

## <a name="mdatp-install-log-missing-or-not-updated"></a><span data-ttu-id="d8f84-121">MDATP安装日志丢失或未更新</span><span class="sxs-lookup"><span data-stu-id="d8f84-121">MDATP install log missing or not updated</span></span>

<span data-ttu-id="d8f84-122">在极少数情况下，安装不会在 MDATP /Library/Logs/Microsoft/mdatp/install.日志文件。</span><span class="sxs-lookup"><span data-stu-id="d8f84-122">In rare cases, installation leaves no trace in MDATP's /Library/Logs/Microsoft/mdatp/install.log file.</span></span>
<span data-ttu-id="d8f84-123">你可以验证安装是否发生，并分析可能的错误，通过查询 macOS 日志 (当没有客户端 UI 支持时，这对 MDM 部署) 。</span><span class="sxs-lookup"><span data-stu-id="d8f84-123">You can verify that an installation happened and analyze possible errors by querying macOS logs (this is helpful in MDM deployment, when there is no client UI).</span></span> <span data-ttu-id="d8f84-124">建议您使用较窄的时间窗口来运行查询，并按日志记录进程名称进行筛选，因为将会存在大量信息。</span><span class="sxs-lookup"><span data-stu-id="d8f84-124">We recommend that you use a narrow time window to run a query, and that you filter by the logging process name, as there will be a huge amount of information.</span></span>

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
