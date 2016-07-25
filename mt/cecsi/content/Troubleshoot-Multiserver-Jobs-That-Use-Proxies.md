---
title: "Troubleshoot Multiserver Jobs That Use Proxies"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
caps.latest.revision: 4
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Troubleshoot Multiserver Jobs That Use Proxies
Distributed jobs whose steps are associated with a proxy run under the context of the proxy account on the target server. If job steps that use proxy accounts fail when downloaded from the master server, check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:  
  
-   "The job step requires a proxy account, however proxy matching is disabled on the target server."  
  
    To resolve this error, set the **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***<n*>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** registry subkey to **1 (true)**. By default, this subkey is set to **0** (**false**). The value of **MSSQL.**<*n*> is the instance name; for example, **MSSQL.1** or **MSSQL.3**.  
  
-   "Proxy not found."  
  
    To resolve this error, make sure a proxy account exists on the target server with the same name as the master server proxy account under which the job step runs.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../content/includes/ssNoteRegistry_md.md)]  
  
## See Also  
[Create a Multiserver Environment](../content/Create-a-Multiserver-Environment.md)  
  
