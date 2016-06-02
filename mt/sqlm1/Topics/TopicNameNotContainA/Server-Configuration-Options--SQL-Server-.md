---
title: Server Configuration Options (SQL Server)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f38eba6-39b1-4f1d-ba24-ee4f7e2bc969
---
# Server Configuration Options (SQL Server)
  You can manage and optimize [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resources through configuration options by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or the sp\_configure system stored procedure. The most commonly used server configuration options are available through [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]; all configuration options are accessible through sp\_configure. Consider the effects on your system carefully before setting these options. For more information, see [View or Change Server Properties &#40;SQL Server&#41;](../Topic/View%20or%20Change%20Server%20Properties%20\(SQL%20Server\).md).  
  
> [!IMPORTANT]  
>  Advanced options should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician.  
  
## Categories of Configuration Options  
 Configuration options take effect either:  
  
-   Immediately after setting the option and issuing the RECONFIGURE \(or in some cases, RECONFIGURE WITH OVERRIDE\) statement.  
  
     \-or\-  
  
-   After performing the above actions and restarting the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 Options that require [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to restart will initially show the changed value only in the value column. After restart, the new value will appear in both the value column and the value\_in\_use column.  
  
 Some options require a server restart before the new configuration value takes effect. If you set the new value and run sp\_configure before restarting the server, the new value appears in the configuration options value column, but not in the value\_in\_use column. After restarting the server, the new value appears in the value\_in\_use column.  
  
 Self\-configuring options are those that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] adjusts according to the needs of the system. In most cases, this eliminates the need for setting the values manually. Examples include the min server memory and max server memory options and the user connections option.  
  
## Configuration Options Table  
 The following table lists all available configuration options, the range of possible settings, and default values. Configuration options are marked with letter codes as follows:  
  
-   A\= Advanced options, which should be changed only by an experienced database administrator or a certified [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technician, and which require setting show advanced options to 1.  
  
-   RR \= Options requiring a restart of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
-   RP \= Options that require a restart of the PolyBase Engine.  
  
-   SC \= Self\-configuring options.  
  
    |Configuration option|Minimum value|Maximum value|Default|  
    |--------------------------|-------------------|-------------------|-------------|  
    |[access check cache bucket count](../../Topics\TopicNameNotContainA/access-check-cache-Server-Configuration-Options.md) \(A\)|0|16384|0|  
    |[access check cache quota](../../Topics\TopicNameNotContainA/access-check-cache-Server-Configuration-Options.md) \(A\)|0|2147483647|0|  
    |[ad hoc distributed queries](../../Topics\TopicNameNotContainA/ad-hoc-distributed-queries-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[affinity I\/O mask](../../Topics\TopicNameNotContainA/affinity-Input-Output-mask-Server-Configuration-Option.md) \(A, RR\)|\-2147483648|2147483647|0|  
    |[affinity64 I\/O mask](../../Topics\TopicNameNotContainA/affinity64-Input-Output-mask-Server-Configuration-Option.md) \(A, only available on 64\-bit version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\)|\-2147483648|2147483647|0|  
    |[affinity mask](../../Topics\TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md) \(A\)|\-2147483648|2147483647|0|  
    |[affinity64 mask](../../Topics\TopicNameNotContainA/affinity64-mask-Server-Configuration-Option.md) \(A, RR\), only available on 64\-bit version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|\-2147483648|2147483647|0|  
    |[Agent XPs](../../Topics\TopicNameNotContainA/Agent-XPs-Server-Configuration-Option.md) \(A\)|0|1|0<br /><br /> \(Changes to 1 when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is started. Default value is 0 if [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is set to automatic start during Setup.\)|  
    |[allow updates](../../Topics\TopicNameNotContainA/allow-updates-Server-Configuration-Option.md) \(Obsolete. Do not use. Will cause an error during reconfigure.\)|0|1|0|  
    |[automatic soft\-NUMA disabled](http://msdn.microsoft.com/library/ms345357.aspx)|0|1|0|  
    |[backup checksum default](../../Topics\TopicNameNotContainA/backup-checksum-default.md)|0|1|0|  
    |[backup compression default](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md)|0|1|0|  
    |[blocked process threshold](../../Topics\TopicNameNotContainA/blocked-process-threshold-Server-Configuration-Option.md) \(A\)|0|86400|0|  
    |[c2 audit mode](../../Topics\TopicNameNotContainA/c2-audit-mode-Server-Configuration-Option.md) \(A, RR\)|0|1|0|  
    |[clr enabled](../../Topics\TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md)|0|1|0|  
    |[common criteria compliance enabled](../../Topics\TopicNameNotContainA/common-criteria-compliance-enabled-Server-Configuration-Option.md) \(A, RR\)|0|1|0|  
    |[contained database authentication](../../Topics\TopicNameNotContainA/contained-database-authentication-Server-Configuration-Option.md)|0|1|0|  
    |[cost threshold for parallelism](../../Topics\TopicNameNotContainA/Configure-the-cost-threshold-for-parallelism-Server-Configuration-Option.md) \(A\)|0|32767|5|  
    |[cross db ownership chaining](../../Topics\TopicNameNotContainA/cross-db-ownership-chaining-Server-Configuration-Option.md)|0|1|0|  
    |[cursor threshold](../../Topics\TopicNameNotContainA/Configure-the-cursor-threshold-Server-Configuration-Option.md) \(A\)|\-1|2147483647|\-1|  
    |[Database Mail XPs](../../Topics\TopicNameNotContainA/Database-Mail-XPs-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[default full\-text language](../../Topics\TopicNameNotContainA/Configure-the-default-full-text-language-Server-Configuration-Option.md) \(A\)|0|2147483647|1033|  
    |[default language](../../Topics\TopicNameNotContainA/Configure-the-default-language-Server-Configuration-Option.md)|0|9999|0|  
    |[default trace enabled](../../Topics\TopicNameNotContainA/default-trace-enabled-Server-Configuration-Option.md) \(A\)|0|1|1|  
    |[disallow results from triggers](../../Topics\TopicNameNotContainA/disallow-results-from-triggers-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[EKM provider enabled](../../Topics\TopicNameNotContainA/EKM-provider-enabled-Server-Configuration-Option.md)|0|1|0|  
    |[external scripts enabled](../../Topics\TopicNameNotContainA/external-scripts-enabled-Server-Configuration-Option.md) \(RR\)<br /><br /> <br /><br /> **Applies to**: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \([!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658).|0|1|0|  
    |[filestream\_access\_level](../../Topics\TopicNameNotContainA/filestream-access-level-Server-Configuration-Option.md)|0|2|0|  
    |[fill factor](../../Topics\TopicNameNotContainA/Configure-the-fill-factor-Server-Configuration-Option.md) \(A, RR\)|0|100|0|  
    |ft crawl bandwidth \(max\), see [ft crawl bandwidth](../../Topics\TopicNameNotContainA/ft-crawl-bandwidth-Server-Configuration-Option.md)\(A\)|0|32767|100|  
    |ft crawl bandwidth \(min\), see [ft crawl bandwidth](../../Topics\TopicNameNotContainA/ft-crawl-bandwidth-Server-Configuration-Option.md)\(A\)|0|32767|0|  
    |ft notify bandwidth \(max\), see [ft notify bandwidth](../../Topics\TopicNameNotContainA/ft-notify-bandwidth-Server-Configuration-Option.md)\(A\)|0|32767|100|  
    |ft notify bandwidth \(min\), see [ft notify bandwidth](../../Topics\TopicNameNotContainA/ft-notify-bandwidth-Server-Configuration-Option.md)\(A\)|0|32767|0|  
    |[PolyBase Hadoop and Azure blob storage](../Topic/PolyBase%20Connectivity%20Configuration%20\(Transact-SQL\).md)\(RP\)|0|7|0|  
    |[index create memory](../../Topics\TopicNameNotContainA/Configure-the-index-create-memory-Server-Configuration-Option.md) \(A, SC\)|704|2147483647|0|  
    |[in\-doubt xact resolution](../../Topics\TopicNameNotContainA/in-doubt-xact-resolution-Server-Configuration-Option.md) \(A\)|0|2|0|  
    |[lightweight pooling](../../Topics\TopicNameNotContainA/lightweight-pooling-Server-Configuration-Option.md) \(A, RR\)|0|1|0|  
    |[locks](../../Topics\TopicNameNotContainA/Configure-the-locks-Server-Configuration-Option.md) \(A, RR, SC\)|5000|2147483647|0|  
    |[max degree of parallelism](../../Topics\TopicNameNotContainA/Configure-the-max-degree-of-parallelism-Server-Configuration-Option.md) \(A\)|0|32767|0|  
    |[max full\-text crawl range](../../Topics\TopicNameNotContainA/max-full-text-crawl-range-Server-Configuration-Option.md) \(A\)|0|256|4|  
    |[max server memory](../../Topics\TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md) \(A, SC\)|16|2147483647|2147483647|  
    |[max text repl size](../../Topics\TopicNameNotContainA/Configure-the-max-text-repl-size-Server-Configuration-Option.md)|0|2147483647|65536|  
    |[max worker threads](../../Topics\TopicNameNotContainA/Configure-the-max-worker-threads-Server-Configuration-Option.md) \(A\)|128|32767<br /><br /> \(1024 is the maximum recommended for 32\-bit [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], 2048 for 64\-bit [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].\)\([!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] was the last version available on 32\-bit operating system.\)|0<br /><br /> Zero auto\-configures the number of max worker threads depending on the number of processors, using the formula \(256\+\(*\<processors\>* \-4\) \* 8\) for 32\-bit [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and twice that for 64\-bit [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. \([!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] was the last version available on 32\-bit operating system.\)|  
    |[media retention](../../Topics\TopicNameNotContainA/Configure-the-media-retention-Server-Configuration-Option.md) \(A, RR\)|0|365|0|  
    |[min memory per query](../../Topics\TopicNameNotContainA/Configure-the-min-memory-per-query-Server-Configuration-Option.md) \(A\)|512|2147483647|1024|  
    |[min server memory](../../Topics\TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md) \(A, SC\)|0|2147483647|0|  
    |[nested triggers](../../Topics\TopicNameNotContainA/Configure-the-nested-triggers-Server-Configuration-Option.md)|0|1|1|  
    |[network packet size](../../Topics\TopicNameNotContainA/Configure-the-network-packet-size-Server-Configuration-Option.md) \(A\)|512|32767|4096|  
    |[Ole Automation Procedures](../../Topics\TopicNameNotContainA/Ole-Automation-Procedures-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[open objects](../../Topics\TopicNameNotContainA/open-objects-Server-Configuration-Option.md) \(A, RR, obsolete\)|0|2147483647|0|  
    |[optimize for ad hoc workloads](../../Topics\TopicNameNotContainA/optimize-for-ad-hoc-workloads-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[PH\_timeout](../../Topics\TopicNameNotContainA/PH-timeout-Server-Configuration-Option.md) \(A\)|1|3600|60|  
    |[precompute rank](../../Topics\TopicNameNotContainA/precompute-rank-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[priority boost](../../Topics\TopicNameNotContainA/Configure-the-priority-boost-Server-Configuration-Option.md) \(A, RR\)|0|1|0|  
    |[query governor cost limit](../../Topics\TopicNameNotContainA/Configure-the-query-governor-cost-limit-Server-Configuration-Option.md) \(A\)|0|2147483647|0|  
    |[query wait](../../Topics\TopicNameNotContainA/Configure-the-query-wait-Server-Configuration-Option.md) \(A\)|\-1|2147483647|\-1|  
    |[recovery interval](../../Topics\TopicNameNotContainA/Configure-the-recovery-interval-Server-Configuration-Option.md) \(A, SC\)|0|32767|0|  
    |[remote access](../../Topics\TopicNameNotContainA/Configure-the-remote-access-Server-Configuration-Option.md) \(RR\)|0|1|1|  
    |[remote admin connections](../../Topics\TopicNameNotContainA/remote-admin-connections-Server-Configuration-Option.md)|0|1|0|  
    |[remote data archive](../../Topics\TopicNameNotContainA/Configure-the-remote-data-archive-Server-Configuration-Option.md)|0|1|0|  
    |[remote login timeout](../../Topics\TopicNameNotContainA/Configure-the-remote-login-timeout-Server-Configuration-Option.md)|0|2147483647|10|  
    |[remote proc trans](../../Topics\TopicNameNotContainA/Configure-the-remote-proc-trans-Server-Configuration-Option.md)|0|1|0|  
    |[remote query timeout](../../Topics\TopicNameNotContainA/Configure-the-remote-query-timeout-Server-Configuration-Option.md)|0|2147483647|0|  
    |[Replication XPs Option](../../Topics\TopicNameNotContainA/Replication-XPs-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[scan for startup procs](../../Topics\TopicNameNotContainA/Configure-the-scan-for-startup-procs-Server-Configuration-Option.md) \(A, RR\)|0|1|0|  
    |[server trigger recursion](../../Topics\TopicNameNotContainA/server-trigger-recursion-Server-Configuration-Option.md)|0|1|1|  
    |[set working set size](../../Topics\TopicNameNotContainA/set-working-set-size-Server-Configuration-Option.md) \(A, RR, obsolete\)|0|1|0|  
    |[show advanced options](../../Topics\TopicNameNotContainA/show-advanced-options-Server-Configuration-Option.md)|0|1|0|  
    |[SMO and DMO XPs](../../Topics\TopicNameNotContainA/SMO-and-DMO-XPs-Server-Configuration-Option.md) \(A\)|0|1|1|  
    |[transform noise words](../../Topics\TopicNameNotContainA/transform-noise-words-Server-Configuration-Option.md) \(A\)|0|1|0|  
    |[two digit year cutoff](../../Topics\TopicNameNotContainA/Configure-the-two-digit-year-cutoff-Server-Configuration-Option.md) \(A\)|1753|9999|2049|  
    |[user connections](../../Topics\TopicNameNotContainA/Configure-the-user-connections-Server-Configuration-Option.md) \(A, RR, SC\)|0|32767|0|  
    |[user options](../../Topics\TopicNameNotContainA/Configure-the-user-options-Server-Configuration-Option.md)|0|32767|0|  
    |[xp\_cmdshell](../../Topics\TopicNameNotContainA/xp_cmdshell-Server-Configuration-Option.md) \(A\)|0|1|0|  
  
## See Also  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)  
  
  