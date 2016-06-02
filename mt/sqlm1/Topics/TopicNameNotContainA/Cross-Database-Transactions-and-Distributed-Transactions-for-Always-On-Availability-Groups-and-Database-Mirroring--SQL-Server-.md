---
title: Cross-Database Transactions and Distributed Transactions for Always On Availability Groups and Database Mirroring (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
---
# Cross-Database Transactions and Distributed Transactions for Always On Availability Groups and Database Mirroring (SQL Server)
  This topic describes cross\-database and distributed transactions support for Always On Availability Groups and database mirroring.  
  
## Support for cross\-database transactions within the same SQL Server instance  
 Cross\-database transactions within the same SQL Server instance are not supported for Always On Availability Groups. This means that no two databases in a cross\-database transaction may be hosted by the same SQL Server instance. This is true even if those databases are part of the same Availability Group.  
  
 Cross\-database transactions are not supported for database mirroring or for Always On Availability Groups in any version of SQL Server prior to SQL Server 2016.  
  
##  <a name="dtcsupport"></a> Support for distributed transactions  
 Distributed transactions are supported with Always On Availability Groups. This applies to distributed transactions between databases hosted by two different SQL Server instances. It also applies to distributed transactions between SQL Server and another DTC\-compliant server.  
  
 The following requirements must be met:  
  
-   Availability Groups must be running on Windows Server 2016 or Windows Server 2012 R2. For Windows Server 2012 R2, you must install the update in KB3090973 available at [https:\/\/support.microsoft.com\/en\-us\/kb\/3090973](https://support.microsoft.com/en-us/kb/3090973).  
  
-   Availability Groups must be created with the **CREATE AVAILABILITY GROUP** command and the **WITH DTC\_SUPPORT \= PER\_DB** clause. You cannot currently alter an existing Availability Group.  
  
 Distributed transactions are not supported for database mirroring.  
  
## Example scenario with database mirroring  
 The following database mirroring example illustrates how a logical inconsistency could occur. In this example, an application uses a cross\-database transaction to insert two rows of data: one row is inserted into a table in a mirrored database, A, and the other row is inserted into a table in another database, B. Database A is being mirrored in high\-safety mode with automatic failover. While the transaction is being committed, database A becomes unavailable, and the mirroring session automatically fails over to the mirror of database A.  
  
 After the failover, the cross\-database transaction might be successfully committed on database B but not on the failed\-over database. This would occur if the original principal server for database A had not sent the log for the cross\-database transaction to the mirror server before the failure. After the failover, that transaction would not exist on the new principal server. Databases A and B would become inconsistent, because the data inserted in database B remains intact, but the data inserted in database A has been lost.  
  
 A similar scenario can occur while using a MS DTC transaction. For example, after failover, the new principal contacts MS DTC. But MS DTC has no knowledge of the new principal server, and it terminates any transactions that are "preparing to commit," which are considered committed in other databases.  
  
> [!NOTE]  
>  Using Database Mirroring with DTC or using Always On Availability Groups with DTC in ways not approved in this topic is not supported.  This does not imply that aspects of the product unrelated to DTC are unsupported; however, any issues arising from the improper use of distributed transactions will not be supported.  
  
## See Also  
 [Always On Availability Groups: Interoperability &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md)  
  
  