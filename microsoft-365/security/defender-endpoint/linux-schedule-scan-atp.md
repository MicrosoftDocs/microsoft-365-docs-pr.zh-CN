---
title: '如何使用 Microsoft Defender for Endpoint (Linux) '
description: 了解如何为 Microsoft Defender for Endpoint (Linux) 安排自动扫描时间，以更好地保护组织的资产。
keywords: 'microsoft， defender， Microsoft Defender for Endpoint， linux， 扫描， 防病毒， 适用于终结点的 microsoft defender (linux) '
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
ms.openlocfilehash: 5a4beaefb2fcc12d46cf61c22644217dce1807a6
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2021
ms.locfileid: "52845362"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>使用 Microsoft Defender for Endpoint (Linux) 

若要运行 Linux 扫描，请参阅支持 [的命令](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands)。

Linux (和 Unix) 具有一个称为 **crontab** (类似于任务计划程序) 运行计划任务的工具。

## <a name="pre-requisite"></a>先决条件

> [!NOTE]
> 若要获取所有时区的列表，请运行以下命令： `timedatectl list-timezones`<br>
> 时区示例：
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>设置 Cron 作业
使用以下命令：

**备份 crontab 条目**

`sudo crontab -l > /var/tmp/cron_backup_200919.dat`

> [!NOTE]
> 其中 200919 == YRMMDD

> [!TIP]
> 在编辑或删除之前，请执行这一操作。 <br>

若要编辑 crontab，并添加一个新作业作为根用户： <br>
`sudo crontab -e`

> [!NOTE]
> 默认编辑器为 VIM。

你可能会看到：

0 * * * * * /etc/opt/microsoft/mdatp/logrorate.sh

按"插入"

添加以下条目：

CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log

> [!NOTE]
>本示例中，我们设置为 00 分钟，即 2 a.m。  (24 小时制的 24 小时制) 、月中的任意一天、任何一个月的星期六。 这意味着它将于星期六的上午 2：00 运行。 太平洋 (UTC –8) 。

按"Esc"

键入不带双引号的"：wq"。

> [!NOTE]
> w == 写入，q == quit

若要查看 cron 作业，请键入 `sudo crontab -l`

:::image type="content" source="/microsoft-365/security/defender-endpoint/images/linux-mdatp-1" alt-text="linux mdatp":::

**检查 cron 作业运行**

`sudo grep mdatp /var/log/cron`

**检查 mdatp_cron_job.log**

`sudo nano mdatp_cron_job.log`

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>对于使用"Ansible"、"用户"或"时形"的

使用以下命令：
### <a name="to-set-cron-jobs-in-ansible"></a>在 Ansible 中设置 cron 作业

`cron – Manage cron.d and crontab entries`

有关详细信息，请参阅 [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html)。

### <a name="to-set-crontabs-in-chef"></a>在管理中设置裁剪
`cron resource`

有关详细信息，请参阅 [https://docs.chef.io/resources/cron/](https://docs.chef.io/resources/cron/)。

### <a name="to-set-cron-jobs-in-puppet"></a>在"创建"中设置 cron 作业
资源类型：cron

有关详细信息，请参阅 [https://puppet.com/docs/puppet/5.5/types/cron.html](https://puppet.com/docs/puppet/5.5/types/cron.html)。

使用改进实现自动化：Cron 作业和计划任务

有关详细信息，请参阅 [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/)。

## <a name="additional-information"></a>其他信息

**获取有关 crontab 的帮助**

`man crontab`

**获取当前用户的 crontab 文件列表**

`crontab -l`

**获取其他用户的 crontab 文件列表**

`crontab -u username -l`

**备份 crontab 条目**

`crontab -l > /var/tmp/cron_backup.dat`

> [!TIP]
> 在编辑或删除之前，请执行这一操作。 <br>

**还原 crontab 条目**

`crontab /var/tmp/cron_backup.dat`

**编辑 crontab 并作为根用户添加新作业**

`sudo crontab -e`

**编辑 crontab 并添加新作业**

`crontab -e`

**编辑其他用户的 crontab 条目**

`crontab -u username -e`

**删除所有 crontab 条目**

`crontab -r`

**删除其他用户的 crontab 条目**

`crontab -u username -r`

**说明**

+—————-分钟 (值：0 – 59)  (特殊字符： 、 – * /)   <br>
|+————-小时 (值：0 – 23)  (特殊字符： 、 – * /)  <br>
| |+———-月中的 (值：1 – 31)  (特殊字符： 、 – * / L W C)   <br>
| | |+——-月 (值：1 – 12)  (特殊字符：，- * / )   <br>
| | | |+-- 一周中的 (值：0 – 6)  (Sunday=0 或 7)  (特殊字符： 、 – * / L W C)  <br>
| | | | |*****要执行的命令


