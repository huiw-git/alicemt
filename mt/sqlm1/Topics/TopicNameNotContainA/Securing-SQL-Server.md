---
title: Securing SQL Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d93489e-e9bb-45b3-8354-21f58209965d
---
# Securing SQL Server
  Securing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can be viewed as a series of steps, involving four areas: the platform, authentication, objects \(including data\), and applications that access the system. The following topics will guide you through creating and implementing an effective security plan.  
  
 You can find more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security at the [SQL Server](http://go.microsoft.com/fwlink/?LinkID=31629) Web site. This includes a best practice guide and a security checklist. This site also contains the latest service pack information and downloads.  
  
## Platform and Network Security  
 The platform for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] includes the physical hardware and networking systems connecting clients to the database servers, and the binary files that are used to process database requests.  
  
### Physical Security  
 Best practices for physical security strictly limit access to the physical server and hardware components. For example, use locked rooms with restricted access for the database server hardware and networking devices. In addition, limit access to backup media by storing it at a secure offsite location.  
  
 Implementing physical network security starts with keeping unauthorized users off the network. The following table contains more information about networking security information.  
  
|For information about|See|  
|---------------------------|---------|  
|[!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] and network access to other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] editions|"Configuring and Securing the Server Environment" in [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] Books Online|  
  
### Operating System Security  
 Operating system service packs and upgrades include important security enhancements. Apply all updates and upgrades to the operating system after you test them with the database applications.  
  
 Firewalls also provide effective ways to implement security. Logically, a firewall is a separator or restrictor of network traffic, which can be configured to enforce your organization's data security policy. If you use a firewall, you will increase security at the operating system level by providing a chokepoint where your security measures can be focused. The following table contains more information about how to use a firewall with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|For information about|See|  
|---------------------------|---------|  
|Configuring a firewall to work with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[Configure a Windows Firewall for Database Engine Access](../../Topics\TopicNameContainA/Configure-a-Windows-Firewall-for-Database-Engine-Access.md)|  
|Configuring a firewall to work with [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]|[Configure a Windows Firewall for Access to the SSIS Service](../../Topics\TopicNameContainA/Configure-a-Windows-Firewall-for-Access-to-the-SSIS-Service.md)|  
|Configuring a firewall to work with [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]|[Configure the Windows Firewall to Allow Analysis Services Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-Analysis-Services-Access.md)|  
|Opening specific ports on a firewall to enable access to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md)|  
|Configuring support for Extended Protection for Authentication by using channel binding and service binding|[Connect to the Database Engine Using Extended Protection](../../Topics\TopicNameNotContainA/Connect-to-the-Database-Engine-Using-Extended-Protection.md)|  
  
 Surface area reduction is a security measure that involves stopping or disabling unused components. Surface area reduction helps improve security by providing fewer avenues for potential attacks on a system. The key to limiting the surface area of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] includes running required services that have "least privilege" by granting services and users only the appropriate rights. The following table contains more information about services and system access.  
  
|For information about|See|  
|---------------------------|---------|  
|Services required for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md)|  
  
 If your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system uses Internet Information Services \(IIS\), additional steps are required to help secure the surface of the platform. The following table contains information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Internet Information Services.  
  
|For information about|See|  
|---------------------------|---------|  
|IIS security with [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)]|"IIS Security" in [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] Books Online|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Authentication|[Authentication in Reporting Services](../Topic/Authentication%20in%20Reporting%20Services.md)|  
|[!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] and IIS access|"Internet Information Services Security Flowchart" in [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] Books Online|  
  
### SQL Server Operating System Files Security  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses operating system files for operation and data storage. Best practices for file security requires that you restrict access to these files. The following table contains information about these files.  
  
|For information about|See|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] program files|[File Locations for Default and Named Instances of SQL Server](../../Topics\TopicNameNotContainA/File-Locations-for-Default-and-Named-Instances-of-SQL-Server.md)|  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service packs and upgrades provide enhanced security. To determine the latest available service pack available for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see the [SQL Server](http://go.microsoft.com/fwlink/?LinkID=31629) Web site.  
  
 You can use the following script to determine the service pack installed on the system.  
  
```  
SELECT CONVERT(char(20), SERVERPROPERTY('productlevel'));  
GO  
```  
  
## Principals and Database Object Security  
 Principals are the individuals, groups, and processes granted access to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. “Securables” are the server, database, and objects the database contains. Each has a set of permissions that can be configured to help reduce the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] surface area. The following table contains information about principals and securables.  
  
|For information about|See|  
|---------------------------|---------|  
|Server and database users, roles, and processes|[Principals &#40;Database Engine&#41;](../Topic/Principals%20\(Database%20Engine\).md)|  
|Server and database objects security|[Securables](../../Topics\TopicNameNotContainA/Securables.md)|  
|The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security hierarchy|[Permissions Hierarchy &#40;Database Engine&#41;](../Topic/Permissions%20Hierarchy%20\(Database%20Engine\).md)|  
  
### Encryption and Certificates  
 Encryption does not solve access control problems. However, it enhances security by limiting data loss even in the rare occurrence that access controls are bypassed. For example, if the database host computer is misconfigured and a malicious user obtains sensitive data, such as credit card numbers, that stolen information might be useless if it is encrypted. The following table contains more information about encryption in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|For information about|See|  
|---------------------------|---------|  
|The encryption hierarchy in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[Encryption Hierarchy](../../Topics\TopicNameNotContainA/Encryption-Hierarchy.md)|  
|Implementing secure connections|[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md)|  
|Encryption functions|[Cryptographic Functions &#40;Transact-SQL&#41;](../Topic/Cryptographic%20Functions%20\(Transact-SQL\).md)|  
  
 Certificates are software "keys" shared between two servers that enable secure communications by way of strong authentication. You can create and use certificates in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to enhance object and connection security. The following table contains information about how to use certificates with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|For information about|See|  
|---------------------------|---------|  
|Creating a certificate for use by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../Topic/CREATE%20CERTIFICATE%20\(Transact-SQL\).md)|  
|Using a certificate with database mirroring|[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md)|  
  
## Application Security  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security best practices include writing secure client applications.  
  
 For more information about how to help secure client applications at the networking layer, see [Client Network Configuration](../../Topics\TopicNameNotContainA/Client-Network-Configuration.md).  
  
## SQL Server Security Tools, Utilities, Views, and Functions  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides tools, utilities, views, and functions that can be used to configure and administer security.  
  
### SQL Server Security Tools and Utilities  
 The following table contains information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools and utilities that you can use to configure and administer security.  
  
|For information about|See|  
|---------------------------|---------|  
|Connecting to, configuring, and controlling [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[Use SQL Server Management Studio](../Topic/Use%20SQL%20Server%20Management%20Studio.md)|  
|Connecting to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and running queries at the command prompt|[sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)|  
|Network configuration and control for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|[SQL Server Configuration Manager](../../Topics\TopicNameNotContainA/SQL-Server-Configuration-Manager.md)|  
|Enabling and disabling features by using Policy\-Based Management|[Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md)|  
|Manipulating symmetric keys for a report server|[rskeymgmt Utility &#40;SSRS&#41;](../Topic/rskeymgmt%20Utility%20\(SSRS\).md)|  
  
### SQL Server Security Catalog Views and Functions  
 The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] exposes security information in several views and functions that are optimized for performance and utility. The following table contains information about security views and functions.  
  
|For information about|See|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security catalog views, which return information about database\-level and server\-level permissions, principals, roles, and so on. In addition, there are catalog views that provide information about encryption keys, certificates, and credentials.|[Security Catalog Views &#40;Transact-SQL&#41;](../Topic/Security%20Catalog%20Views%20\(Transact-SQL\).md)|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security functions, which return information about the current user, permissions and schemas.|[Security Functions &#40;Transact-SQL&#41;](../Topic/Security%20Functions%20\(Transact-SQL\).md)|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security dynamic management views.|[Security-Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;](../Topic/Security-Related%20Dynamic%20Management%20Views%20and%20Functions%20\(Transact-SQL\).md)|  
  
## Related Content  
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)  
  
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)  
  
  