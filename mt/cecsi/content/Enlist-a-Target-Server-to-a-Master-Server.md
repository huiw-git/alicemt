---
title: Enlist a Target Server to a Master Server
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
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
# Enlist a Target Server to a Master Server
This topic describes how to add target servers to a multiserver administration configuration. Run this procedure from the master server. in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], [!INCLUDE[tsql](../content/includes/tsql_md.md)], or SQL Server Management Objects (SMO).  
  
For information about how the Windows account used for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service affects a multiserver environment, see [Create a Multiserver Environment](../content/Create-a-Multiserver-Environment.md).  
  
Full Secure Sockets Layer (SSL) encryption and certificate validation is enabled for connections between master servers and target servers by default. For more information, see [Set Encryption Options on Target Servers](../content/Set-Encryption-Options-on-Target-Servers.md).  
  
**In This Topic**  
  
-   **To enlist a target server, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To enlist a target server  
  
1.  In **Object Explorer**, expand a server that is configured as a master server.  
  
2.  Right\-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Add Target Servers**.  
  
3.  Complete the Target Server Wizard, which guides you through the process.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To enlist a target server  
  
1.  Use the **sp\_msx\_enlist** stored procedure.  For more information, see [sp_msx_enlist (Transact-SQL)](assetId:///ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)  
  
## See Also  
[Automated Administration Across an Enterprise](../content/Automated-Administration-Across-an-Enterprise.md)  
  
