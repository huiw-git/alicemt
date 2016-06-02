---
title: Security Center for SQL Server Database Engine and Azure SQL Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
---
# Security Center for SQL Server Database Engine and Azure SQL Database
  This page provides links to help you locate the information that you need about security and protection in the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and [!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)].  
  
 **Legend**  
  
 ![security-center-legend](../../Images\Image\ImageNotContaina/security-center-legend.PNG "security-center-legend")  
  
##  <a name="Who"></a> Authentication: Who are you?  
  
|||  
|-|-|  
|**Who Authenticates?**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Windows Authentication<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication|Who Authenticates? \(Windows or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\)<br /><br /> [Choose an Authentication Mode](../../Topics\TopicNameNotContainA/Choose-an-Authentication-Mode.md)<br /><br /> [Connecting to SQL Database By Using Azure Active Directory Authentication](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)|  
|**Where Authenticated?**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") At master Database: Logins and DB Users<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") At User Database: Contained DB Users|Authenticate at the master database \(Logins and database users\)<br /><br /> [Create a SQL Server Login](../../Topics\TopicNameContainA/Create-a-Login.md)<br /><br /> [Managing Databases and Logins in Azure SQL Database](http://msdn.microsoft.com/library/ee336235.aspx)<br /><br /> [Create a Database User](../../Topics\TopicNameContainA/Create-a-Database-User.md)<br /><br /> <br /><br /> Authenticate at a user database<br /><br /> [Contained Database Users - Making Your Database Portable](../../Topics\TopicNameNotContainA/Contained-Database-Users---Making-Your-Database-Portable.md)|  
|**Using Other Identities**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Credentials<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Execute as Another Login<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Execute as Another Database User|[Credentials &#40;Database Engine&#41;](../Topic/Credentials%20\(Database%20Engine\).md)<br /><br /> [Execute as Another Login](../Topic/EXECUTE%20AS%20\(Transact-SQL\).md)<br /><br /> [Execute as Another Database User](../Topic/EXECUTE%20AS%20\(Transact-SQL\).md)|  
  
##  <a name="What"></a> Authorization: What can you do?  
  
|||  
|-|-|  
|**Granting, Revoking, and Denying Permissions**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Securable Classes<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Granular Server Permissions<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Granular Database Permissions|[Permissions Hierarchy &#40;Database Engine&#41;](../Topic/Permissions%20Hierarchy%20\(Database%20Engine\).md)<br /><br /> [Permissions](../Topic/Permissions%20\(Database%20Engine\).md)<br /><br /> [Securables](../../Topics\TopicNameNotContainA/Securables.md)<br /><br /> [Getting Started with Database Engine Permissions](../../Topics\TopicNameNotContainA/Getting-Started-with-Database-Engine-Permissions.md)|  
|**Security by Roles**<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Server Level Roles<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Database Level Roles|[Server-Level Roles](../../Topics\TopicNameNotContainA/Server-Level-Roles.md)<br /><br /> [Database-Level Roles](../../Topics\TopicNameNotContainA/Database-Level-Roles.md)|  
|**Restricting Data Access to Selected Data Elements**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Restrict Data Access With Views\/Procedures<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Row\-Level Security<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Dynamic Data Masking<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Signed Objects|Restrict Data Access Using [Views](../../Topics\TopicNameNotContainA/Views.md) and [Procedures](../Topic/Stored%20Procedures%20\(Database%20Engine\).md)<br /><br /> [Row\-Level Security \(SQL Server\)](../../Topics\TopicNameNotContainA/Row-Level-Security.md)<br /><br /> [Row\-Level Security \(Azure SQL Database\)](http://msdn.microsoft.com/library/azure/dn765131.aspx)<br /><br /> [Dynamic Data Masking \(SQL Server\)](../../Topics\TopicNameNotContainA/Dynamic-Data-Masking.md)<br /><br /> [Dynamic Data Masking \(Azure SQL Database\)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [Signed Objects](../Topic/ADD%20SIGNATURE%20\(Transact-SQL\).md)|  
  
##  <a name="Encrypt"></a> Encryption: Storing Secret Data  
  
|||  
|-|-|  
|**Encrypting Files**<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") BitLocker Encryption \(Drive Level\)<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") NTFS Encryption \(Folder Level\)<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Transparent Data Encryption \(File Level\)<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Backup Encryption \(File Level\)|[BitLocker \(Drive Level\)](http://support.microsoft.com/kb/2855131)<br /><br /> [NTFS Encryption \(Folder Level\)](http://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [Transparent Data Encryption \(File Level\)](../Topic/Transparent%20Data%20Encryption%20\(TDE\).md)<br /><br /> [Backup Encryption \(File Level\)](../../Topics\TopicNameNotContainA/Backup-Encryption.md)|  
|**Encrypting Sources**<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Extensible Key Management Module<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Keys Stored in the Azure Key Vault<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Always Encrypted|[Extensible Key Management Module](../Topic/Extensible%20Key%20Management%20\(EKM\).md)<br /><br /> [Keys Stored in the Azure Key Vault](../Topic/Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md)<br /><br /> [Always Encrypted](../Topic/Always%20Encrypted%20\(Database%20Engine\).md)|  
|**Column, Data, & Key Encryption**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Encrypt by Certificate<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Encrypt by Symmetric Key<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Encrypt by Asymmetric Key<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Encrypt by Passphrase|[Encrypt by Certificate](../Topic/ENCRYPTBYCERT%20\(Transact-SQL\).md)<br /><br /> [Encrypt by Asymmetric Key](../Topic/ENCRYPTBYASYMKEY%20\(Transact-SQL\).md)<br /><br /> [Encrypt by Symmetric Key](../Topic/ENCRYPTBYKEY%20\(Transact-SQL\).md)<br /><br /> [Encrypt by Passphrase](../Topic/ENCRYPTBYPASSPHRASE%20\(Transact-SQL\).md)<br /><br /> [Encrypt a Column of Data](../../Topics\TopicNameContainA/Encrypt-a-Column-of-Data.md)|  
  
##  <a name="Connect"></a> Connection Security: Restricting and Securing  
  
|||  
|-|-|  
|**Firewall Protection**<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Windows Firewall Settings<br /><br /> ![security-center-sqldb](../../Images\Image\ImageNotContaina/security-center-sqldb.png "security-center-sqldb") Azure Service Firewall Settings<br /><br /> ![security-center-sqldb](../../Images\Image\ImageNotContaina/security-center-sqldb.png "security-center-sqldb") Database Firewall Settings|[Configure a Windows Firewall for Database Engine Access](../../Topics\TopicNameContainA/Configure-a-Windows-Firewall-for-Database-Engine-Access.md)<br /><br /> [Azure SQL Database Firewall Settings](../Topic/sp_set_database_firewall_rule%20\(Azure%20SQL%20Database\).md)<br /><br /> [Azure Service Firewall Settings](../Topic/sp_set_firewall_rule%20\(Azure%20SQL%20Database\).md)|  
|**Encrypting Data in Transit**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Forced SSL Connections<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") Optional SSL Connections|[Secure Sockets Layer for the Database Engine](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md)<br /><br /> [Secure Sockets Layer for SQL Database](https://msdn.microsoft.com/library/azure/ff394108.aspx)<br /><br /> [TLS 1.2 support for Microsoft SQL Server](https://support.microsoft.com/kb/3135244)|  
  
##  <a name="Audit"></a> Auditing: Recording Access  
  
|||  
|-|-|  
|**Automated Auditing**<br /><br /> ![security-center-sqlserver](../../Images\Image\ImageNotContaina/security-center-sqlserver.png "security-center-sqlserver") [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Audit \(Server and DB Level\)<br /><br /> ![security-center-sqldb](../../Images\Image\ImageNotContaina/security-center-sqldb.png "security-center-sqldb") [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] Audit \(Database Level\)<br /><br /> ![security-center-sqldb](../../Images\Image\ImageNotContaina/security-center-sqldb.png "security-center-sqldb") Threat Detection|[SQL Server Audit &#40;Database Engine&#41;](../Topic/SQL%20Server%20Audit%20\(Database%20Engine\).md)<br /><br /> [SQL Database Auditing](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> [Get started with SQL Database Threat Detection](https://azure.microsoft.com/documentation/articles/sql-database-threat-detection-get-started/)|  
|**Custom Audit**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Triggers|Custom Audit Implementation: Creating [DDL Triggers](../../Topics\TopicNameNotContainA/DDL-Triggers.md) and [DML Triggers](../../Topics\TopicNameNotContainA/DML-Triggers.md)|  
|**Compliance**<br /><br /> ![security-center-both](../../Images\Image\ImageNotContaina/security-center-both.png "security-center-both") Compliance|SQL Server:<br />                        [Common Criteria](http://go.microsoft.com/fwlink/?LinkId=616319)<br /><br /> SQL Database:<br />                        [Microsoft Azure Trust Center: Compliance by Feature](http://azure.microsoft.com/support/trust-center/services/)|  
  
##  <a name="SQLInjection"></a> SQL Injection  
 SQL injection is an attack in which malicious code is inserted into strings that are later passed to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] for parsing and execution. Any procedure that constructs SQL statements should be reviewed for injection vulnerabilities because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will execute all syntactically valid queries that it receives. All database systems have some risk of SQL Injection, and many of the vulnerabilities are introduced in the application that is querying the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. You can thwart SQL injection attacks by using stored procedures and parameterized commands, avoiding dynamic SQL, and restricting permissions on all users.  For more information, see [SQL Injection](../../Topics\TopicNameNotContainA/SQL-Injection.md).  
  
 Additional links for application programmers:  
  
-   [Application Security Scenarios in SQL Server](https://msdn.microsoft.com/library/bb669057.aspx)  
  
-   [Writing Secure Dynamic SQL in SQL Server](https://msdn.microsoft.com/library/bb669091.aspx)  
  
-   [How To: Protect From SQL Injection in ASP.NET](https://msdn.microsoft.com/library/ff648339.aspx)  
  
## See Also  
 [Getting Started with Database Engine Permissions](../../Topics\TopicNameNotContainA/Getting-Started-with-Database-Engine-Permissions.md)   
 [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md)   
 [Principals &#40;Database Engine&#41;](../Topic/Principals%20\(Database%20Engine\).md)   
 [SQL Server Certificates and Asymmetric Keys](../../Topics\TopicNameNotContainA/SQL-Server-Certificates-and-Asymmetric-Keys.md)   
 [SQL Server Encryption](../../Topics\TopicNameNotContainA/SQL-Server-Encryption.md)   
 [Surface Area Configuration](../../Topics\TopicNameNotContainA/Surface-Area-Configuration.md)   
 [Strong Passwords](../../Topics\TopicNameNotContainA/Strong-Passwords.md)   
 [TRUSTWORTHY Database Property](../../Topics\TopicNameNotContainA/TRUSTWORTHY-Database-Property.md)   
 [Database Engine Features and Tasks](../../Topics\TopicNameNotContainA/Database-Engine-Features-and-Tasks.md)  
  
  