---
title: Security Overview (Integration Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01aa0b88-d477-4581-9a3b-2efc3de2b133
---
# Security Overview (Integration Services)
  Security in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] consists of several layers that provide a rich and flexible security environment. These security layers include the use of digital signatures, package properties, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database roles, and operating system permissions. Most of these security features fall into the categories of identity and access control.  
  
## Identity Features  
 By implementing identity features in your packages, you can achieve the following goal:  
  
 **Ensure that you only open and run packages from trusted sources**.  
  
 To ensure that you only open and run packages from trusted sources, you first have to identify the source of packages. You can identify the source by signing packages with certificates. Then, when you open or run the packages, you can have [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] check for the presence and the validity of the digital signatures. For more information, see [Identify the Source of Packages with Digital Signatures](../../Topics\TopicNameNotContainA/Identify-the-Source-of-Packages-with-Digital-Signatures.md).  
  
## Access Control Features  
 By implementing identity features in your packages, you can achieve the following goal:  
  
 **Ensure that only authorized users open and run packages**.  
  
 To ensure that only authorized users open and run packages, you have to control access to the following information:  
  
-   Control access to the contents of packages, especially sensitive data.  
  
-   Control access to packages and package configurations that are stored in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   Control accesss to packages and to related files such as configurations, logs, and checkpoint files that are stored in the file system.  
  
-   Control access to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service and to the information about packages that the service displays in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
### Controlling Access to the Contents of Packages  
 To help restrict access to the contents of a package, you can encrypt packages by setting the ProtectionLevel property of the package. You can set this property to the level of protection that your package requires. For example, in a team development environment, you can encrypt a package by using a password that is known only to the team members who work on the package.  
  
 When you set the ProtectionLevel property of a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] automatically detects sensitive properties and handles these properties according to the specified package protection level. For example, you set the ProtectionLevel property for a package to a level that encrypts sensitive information with a password. For this package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] automatically encrypts the values of all sensitive properties and will not display the corresponding data without the correct password being supplied.  
  
 Typically, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] identifies properties as sensitive if those properties contain information, such as a password or a connection string, or if those properties correspond to variables or task\-generated XML nodes. Whether [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] considers a property sensitive depends on whether the developer of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] component, such as a connection manager or task, has designated the property as sensitive. Users cannot add properties to, nor can they remove properties from, the list of properties that are considered sensitive.If you write custom tasks, connection managers, or data flow components, you can specify which properties [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] should treat as sensitive.  
  
 For more information, see [Access Control for Sensitive Data in Packages](../../Topics\TopicNameNotContainA/Access-Control-for-Sensitive-Data-in-Packages.md).  
  
### Controlling Access to Packages  
 You can save [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages to the msdb database in an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or to the file system as XML files that have the .dtsx file name extension. For more information, see [Save Packages](../../Topics\TopicNameNotContainA/Save-Packages.md).  
  
#### Saving Packages to the msdb Database  
 Saving the packages to the msdb database helps provide security at the server, database, and table levels. In the msdb database, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages are stored in the sysssispackages table. Because the packages are saved to the sysssispackages and sysdtspackages tables in the msdb database, the packages are automatically backed up when you backup the msdb database.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] packages stored in the msdb database can also be protected by applying the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] database\-level roles. [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes three fixed database\-level roles db\_ssisadmin, db\_ssisltduser, and db\_ssisoperator for controlling access to packages. A reader and a writer role can be associated with each package. You can also define custom database\-level roles to use in [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. Roles can be implemented only on packages that are saved to the msdb database in an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../Topic/Integration%20Services%20Roles%20\(SSIS%20Service\).md).  
  
#### Saving Packages to the File System  
 If you store packages to the file system instead of in the msdb database, make sure to secure the package files and the folders that contain package files.  
  
### Controlling Access to Files Used by Packages  
 Packages that have been configured to use configurations, checkpoints, and logging generate information that is stored outside the package. This information might be sensitive and should be protected. Checkpoint files can be saved only to the file system, but configurations and logs can be saved to the file system or to tables in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. Configurations and logs that are saved to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] are subject to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security, but information written to the file system requires additional security.  
  
 For more information, see [Access to Files Used by Packages](../../Topics\TopicNameNotContainA/Access-to-Files-Used-by-Packages.md).  
  
#### Storing Package Configurations Securely  
 Package configurations can be saved to a table in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database or to the file system.  
  
 Configurations can be saved to any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, not just the msdb database. Thus, you are able to specify which database serves as the repository of package configurations. You can also specify the name of the table that will contain the configurations, and [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] automatically creates the table with the correct structure. Saving the configurations to a table makes it possible to provide security at the server, database, and table levels. In addition, configurations that are saved to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] are automatically backed up when you back up the database.  
  
 If you store configurations in the file system instead of in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], make sure to secure the folders that contain the package configuration files.  
  
 For more information about configurations, see [Package Configurations](../../Topics\TopicNameNotContainA/Package-Configurations.md).  
  
### Controlling Access to the Integration Services Service  
 [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] uses the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service to list stored packages. To prevent unauthorized users from viewing information about packages that are stored on local and remote computers, and thereby learning private information, restrict access to computers that run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.  
  
 For more information, see [Access to the Integration Services Service](../../Topics\TopicNameNotContainA/Access-to-the-Integration-Services-Service.md).  
  
## Related Tasks  
 The following list contains links to topics that show you how to perform a certain task pertaining to the security.  
  
-   [Create a User-Defined Role](../../Topics\TopicNameContainA/Create-a-User-Defined-Role.md)  
  
-   [Assign a Reader and Writer Role to a Package](../../Topics\TopicNameContainA/Assign-a-Reader-and-Writer-Role-to-a-Package.md)  
  
-   [Implement a Signing Policy by Setting a Registry Value](../../Topics\TopicNameContainA/Implement-a-Signing-Policy-by-Setting-a-Registry-Value.md)  
  
-   [Sign a Package by Using a Digital Certificate](../../Topics\TopicNameContainA/Sign-a-Package-by-Using-a-Digital-Certificate.md)  
  
-   [Set or Change the Protection Level of Packages](../../Topics\TopicNameNotContainA/Set-or-Change-the-Protection-Level-of-Packages.md)  
  
## See Also  
 [SQL Server Integration Services](../../Topics\TopicNameNotContainA/SQL-Server-Integration-Services.md)  
  
  