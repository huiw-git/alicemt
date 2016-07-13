---
title: Set Encryption Options on Target Servers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
manager:jhubbard
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
# Set Encryption Options on Target Servers
If you cannot use a certificate for Secure Sockets Layer (SSL) encrypted communications between master servers and some or all of your target servers, but you want to encrypt the channel between them, configure the target server to use the level of security required.  
  
To configure the appropriate level of security required for a specific master server\/target server communication channel, set the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent registry subkey **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\**<*instance\_name*>**\\SQLServerAgent\\MsxEncryptChannelOptions(REG\_DWORD)** on the target server to one of the following values. The value of <*instance\_name*> is **MSSQL.***n*. For example, **MSSQL.1** or **MSSQL.3**.  
  
|Value|Description|  
|---------|---------------|  
|**0**|Disables encryption between this target server and the master server. Choose this option only when the channel between the target server and master server is secured by another means.|  
|**1**|Enables encryption only between this target server and the master server, but no certificate validation is required.|  
|**2**|Enables full SSL encryption and certificate validation between this target server and the master server. This setting is the default. Unless you have specific reason to choose a different value, we recommend not changing it.|  
  
If **1** or **2** is specified, you must have SSL enabled on both the master and target servers. If **2** is specified, you must also have a properly signed certificate present on the master server.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../content/includes/ssNoteRegistry_md.md)]  
  
## See Also  
[How to: Enable Encrypted Connections to the Database Engine (SQL Server Configuration Manager)](assetId:///e1e55519-97ec-4404-81ef-881da3b42006)  
  
