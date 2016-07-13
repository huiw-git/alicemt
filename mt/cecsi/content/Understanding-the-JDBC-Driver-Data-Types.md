---
title: Understanding the JDBC Driver Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
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
# Understanding the JDBC Driver Data Types
  [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports the use of JDBC basic and advanced data types within a Java application that uses [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] as its database.  
  
 The JDBC type system mediates the conversion between [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types and Java language types and objects. The JDBC types are modeled on the SQL\-92 and SQL\-99 types. The JDBC driver adheres to the JDBC specification and is designed to provide the right balance between predictability and flexibility.  
  
 The topics in this section describe how to use the basic and advanced data types, and how data types can be converted into other data types.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Using Basic Data Types](../content/Using-Basic-Data-Types.md)|Describes the JDBC basic data types. Includes examples of how to work with the data types by using result sets, parameterized queries, and stored procedures.|  
|[Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md)|Describes how the JDBC Driver generates dates.|  
|[Using Advanced Data Types](../content/Using-Advanced-Data-Types.md)|Describes the JDBC advanced data types.|  
|[Understanding Data Type Differences](../content/Understanding-Data-Type-Differences.md)|Describes differences between the various JDBC driver data types.|  
|[Understanding Data Type Conversions](../content/Understanding-Data-Type-Conversions.md)|Describes how data type conversion is handled when using getter and setter methods.|  
|[National Character Set Support](../content/National-Character-Set-Support.md)|Describes the support for the national character set types.|  
|[Supporting XML Data](../content/Supporting-XML-Data.md)|Describes the SQLXML interface. Also describes how to read and write an XML data from and to the relational database with the **SQLXML** Java data type.|  
|[Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md)|Discusses the interfaces that have the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] specific methods and constants that allow an application server to create a proxy of the class, Also discusses supports for the the java.sql.Wrapper interface.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  