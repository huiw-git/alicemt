---
title: Configure Your Utility Control Point Data Warehouse (SQL Server Utility)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
---
# Configure Your Utility Control Point Data Warehouse (SQL Server Utility)
  Data collected by managed instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] are stored in the utility management data warehouse \(UMDW\); the UMDW file name is sysutility\_mdw.  
  
 You can configure the UMDW data retention period. For more information, see [Utility Administration &#40;SQL Server Utility&#41;](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md).  
  
 The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
-   UMDW name: Sysutility\_mdw.  
  
-   Collection set upload frequency: Every 15 minutes.  
  
 The UMDW directory is configurable: \<System drive\>:\\Program Files\\Microsoft SQL Server\\MSSQL10\_50.\<UCP\_Name\>\\MSSQL\\Data\\, where \<System drive\> is normally the C:\\ drive. The log file, Sysutility\_mdw\_\<GUID\>\_LOG, is located in the same directory.  
  
> [!NOTE]  
>  The UMDW \(sysutility\_mdw\) file location can be changed using detach\/attach or ALTER DATABASE. We recommend the use of ALTER DATABASE. For more information see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)  
  
  