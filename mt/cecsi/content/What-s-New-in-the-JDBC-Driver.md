---
title: What&#39;s New in the JDBC Driver
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
manager: jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# What&#39;s New in the JDBC Driver
    
## Updates in Microsoft JDBC Driver 6.0 for SQL Server  
 **Always Encrypted**  
  
 Support for the recently released Always Encrypted feature in SQL Server 2016, a new security feature that ensures sensitive data is never seen in plaintext in a SQL Server instance. Always Encrypted works by transparently encrypting the data in the application, so that SQL Server will only handle the encrypted data and not plaintext values. Even if the SQL instance or the host machine is compromised, all an attacker can get is ciphertext of sensitive data. For details see [Using Always Encrypted with the JDBC Driver](../content/Using-Always-Encrypted-with-the-JDBC-Driver.md).  
  
 **Internationalized Domain Name \(IDN\)**  
  
 Support for Internationalized Domain Names \(IDNs\) for server names. For details see Using International Domain Names on the [International Features of the JDBC Driver](../content/International-Features-of-the-JDBC-Driver.md) page.  
  
 **Parameterized Query**  
  
 Now supports retrieving parameter metadata with prepared statements for complex queries such as sub\-queries and\/or joins. Note that this improvement is available only when using SQL Server 2012 and newer versions.  
  
 **Azure Active Directory \(AAD\)**  
  
 AAD authentication is a mechanism of connecting to Azure SQL Database v12 using identities in AAD. Use AAD authentication to centrally manage identities of database users and as an alternative to SQL Server authentication. The JDBC Driver 6.0 allows you to specify your AAD credentials in the JDBC connection string to connect to Azure SQL DB.  For details see the authentication property on the [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md) page.  
  
 **Table\-Valued Parameters**  
  
 Table\-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server\-side logic for processing the data. You can use table\-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command. The incoming data rows are stored in a table variable that can then be operated on by using Transact\-SQL. For details see [Using Table-Valued Parameters](../content/Using-Table-Valued-Parameters.md).  
  
 **AlwaysOn Availability Groups \(AG\)**  
  
 The driver now supports transparent connections to AlwaysOn Availability Groups. The driver quickly discovers the current AlwaysOn topology of your server infrastructure and connects to the current active server transparently.  
  
## Updates in Microsoft JDBC Driver 4.2 for SQL Server and later  
 **Support for JDK 8**  
  
 Support for Java Development Kit \(JDK\) version 8.0 in addition to JDK 7.0, 6.0, and 5.0.  
  
 **JDBC 4.1 and 4.2 compliance**  
  
 Support for Java Database Connectivity API 4.1 and 4.2 specifications, in addition to 4.0. For details see [JDBC 4.1 Compliance for the JDBC Driver](../content/JDBC-4.1-Compliance-for-the-JDBC-Driver.md) and [JDBC 4.2 Compliance for the JDBC Driver](../content/JDBC-4.2-Compliance-for-the-JDBC-Driver.md).  
  
 **Bulk copy**  
  
 The bulk copy feature is used to quickly copy large amounts of data into tables or views in SQL Server databases. For details see [Using Bulk Copy with the JDBC Driver](../content/Using-Bulk-Copy-with-the-JDBC-Driver.md).  
  
 **XA transaction rollback option**  
  
 Added new timeout options for existing automatic rollback of unprepared transactions. For detail see [Understanding XA Transactions](../content/Understanding-XA-Transactions.md).  
  
 **New Kerberos Principal Connection Property**  
  
 Added a new connection property to facilitate flexibility with Kerberos connections. For detail see [Using Kerberos Integrated Authentication to Connect to SQL Server](../content/Using-Kerberos-Integrated-Authentication-to-Connect-to-SQL-Server.md).  
  
## Updates in Microsoft JDBC Driver 4.1 for SQL Server and later  
 **Support for JDK 7**  
  
 Support for Java Development Kit \(JDK\) version 7.0 in addition to JDK 6.0 and 5.0.  
  
## Updates in Microsoft JDBC Driver 4.0 for SQL Server and later  
 **Information about Connecting to an Azure SQL Database**  
  
 There is now a topic with information about connecting to an Azure SQL database. See [Connecting to an Azure SQL database](../content/Connecting-to-an-Azure-SQL-database.md) for more information.  
  
 **Support for High Availability, Disaster Recovery**  
  
 Support for high\-availability, disaster recovery connections to AlwaysOn Availability Groups in [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)]. See [JDBC Driver Support for High Availability, Disaster Recovery](../content/JDBC-Driver-Support-for-High-Availability--Disaster-Recovery.md) for more information.  
  
 **Using Kerberos Integrated Authentication to Connect to SQL Server**  
  
 Support for type 4 Kerberos integrated authentication for applications to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database. For more information, see [Using Kerberos Integrated Authentication to Connect to SQL Server](../content/Using-Kerberos-Integrated-Authentication-to-Connect-to-SQL-Server.md). \(Type 2 Kerberos integrated authentication is available in [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] versions prior to 4.0.\)  
  
 **Accessing Diagnostic Information in the Extended Events Log**  
  
 You can access information in the server's extended events log to understand connection failures. For more information, see [Accessing Diagnostic Information in the Extended Events Log](../content/Accessing-Diagnostic-Information-in-the-Extended-Events-Log.md).  
  
 **Additional Support for Sparse Columns**  
  
 If your application already accesses data in a table that uses sparse columns, you should see an increase in performance. You can get information about columns \(including sparse column information\) with [getColumns Method &#40;SQLServerDatabaseMetaData&#41;](../content/getColumns-Method--SQLServerDatabaseMetaData-.md). For more information about [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] sparse columns, see [Using Sparse Columns](http://go.microsoft.com/fwlink/?LinkId=224244).  
  
 **Xid.getFormatId**  
  
 Beginning in [!INCLUDE[jdbc_40](../content/includes/jdbc_40_md.md)], the JDBC driver will pass the format identifier from the application to the database server. To get the updated behavior, make sure the sqljdbc\_xa.dll on the server is updated. For more information on copying an updated version of sqljdbc\_xa.dll to the server, see [Understanding XA Transactions](../content/Understanding-XA-Transactions.md).  
  
## Itanium Not Supported for JDBC Driver 6.0, 4.2, 4.1, and 4.0 Applications  
  
 Microsoft JDBC Drivers 6.0, 4.2, 4.1, and 4.0 for SQL Server applications are not supported to run on an Itanium computer.  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  