---
title: Getting the Driver Version
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
manager:jhubbard
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
# Getting the Driver Version
  The version of the installed [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] can be found in the following ways:  
  
-   Call the [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) methods [getDriverMajorVersion](../content/getDriverMajorVersion-Method--SQLServerDatabaseMetaData-.md), [getDriverMinorVersion](../content/getDriverMinorVersion-Method--SQLServerDatabaseMetaData-.md), or [getDriverVersion](../content/getDriverVersion-Method--SQLServerDatabaseMetaData-.md).  
  
-   The version is displayed in the readme.txt file of the product distribution.  
  
 In addition, the JDBC driver name can be returned from the [getDriverName](../content/getDriverName-Method--SQLServerDatabaseMetaData-.md) method call on the SQLServerDatabaseMetaData class. It will return, for example, "Microsoft JDBC Driver 4.0 for SQL Server".  
  
 The following is an example of the output from calls to the methods of the SQLServerDatabaseMetaData class:  
  
 `getDriverName = Microsoft JDBC Driver 4.0 for SQL Server`  
  
 `getDriverMajorVersion = 4`  
  
 `getDriverMinorVersion = 0`  
  
 `getDriverVersion = 4.0.` *xxx.x*  
  
 Where "xxx.x" is the final version number.  
  
## See Also  
 [Diagnosing Problems with the JDBC Driver](../content/Diagnosing-Problems-with-the-JDBC-Driver.md)  
  
  