---
title: "Configure Your Utility Control Point Data Warehouse (SQL Server Utility)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Configure Your Utility Control Point Data Warehouse (SQL Server Utility)
Data collected by managed instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] are stored in the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.  
  
 You can configure the UMDW data retention period. For more information, see [Utility Administration (SQL Server Utility)](../../Topics/TopicNameNotContainA/Utility-Administration--SQL-Server-Utility-.md).  
  
 The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]:  
  
-   UMDW name: Sysutility_mdw.  
  
-   Collection set upload frequency: Every 15 minutes.  
  
 The UMDW directory is configurable: <System drive\>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where <System drive\> is normally the C:\ drive. The log file, Sysutility_mdw_<GUID\>_LOG, is located in the same directory.  
  
> [!NOTE]  
>  The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE. We recommend the use of ALTER DATABASE. For more information see [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da).  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)