---
title: "Set the Collation of User-defined Databases to Match Those of the master and model Databases"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
robots: noindex,nofollow
---
# Set the Collation of User-defined Databases to Match Those of the master and model Databases
This rule checks whether user-defined databases are defined by using a database collation that is the same as the collation for master or model.  
  
## Best Practices Recommendations  
 We recommend that the collations of user-defined databases match the collation of master or model. Otherwise, collation conflicts can occur that might prevent code from executing. For example, when a stored procedure joins one table to a temporary table, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] might end the batch and return a collation conflict error if the collations of the user-defined database and the model database are different. This occurs because temporary tables are created in tempdb, which bases its collation on that of model.  
  
 If you experience collation conflict errors, consider one of the following solutions:  
  
-   Export the data from the user database and import it into new tables that have the same collation as the master and model databases.  
  
-   Rebuild the system databases to use a collation that matches the user database collation. For more information about how to rebuild the system databases, see [Rebuild System Databases](../../Topics/TopicNameNotContainA/Rebuild-System-Databases.md).  
  
-   Modify any stored procedures that join user tables to tables in tempdb to create the tables in tempdb by using the collation of the user database. To do this, add the `COLLATE database_default` clause to the column definitions of the temporary table, as shown in the following example:  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## For More Information  
 [Set or Change the Database Collation](../../Topics/TopicNameNotContainA/Set-or-Change-the-Database-Collation.md)  
  
 [Set or Change the Column Collation](../../Topics/TopicNameNotContainA/Set-or-Change-the-Column-Collation.md)  
  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)  
  
 [COLLATE (Transact-SQL)](assetId:///76763ac8-3e0d-4bbb-aa53-f5e7da021daa)  
  
 [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)  
  
 [Microsoft Knowledge Base article 325335](http://go.microsoft.com/fwlink/?linkid=117751)  
  
 [How to: Install SQL Server 2008 from the Command Prompt](http://go.microsoft.com/fwlink/?LinkId=81585)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)