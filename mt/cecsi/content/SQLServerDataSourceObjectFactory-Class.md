---
title: SQLServerDataSourceObjectFactory Class
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
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
# SQLServerDataSourceObjectFactory Class
  Represents an object factory to materialize data sources from the Java Naming and Directory Interface \(JNDI\).  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.lang.Object  
  
 **Implements:** javax.naming.spi.ObjectFactory  
  
## Syntax  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## Remarks  
 This method is inherited by all the data source classes. As part of its support for the Referenceable interface, [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] exposes this class that implements an ObjectFactory. Java Application Servers will call getReference on a data source class, and this will create a Reference object that internally uses the class name as its class factory.  
  
 When the Java Application Server has to dereference the Reference object, it creates an instance of the SQLServerDataSourceObjectFactory object and calls the [getObjectInstance](../content/getObjectInstance-Method--SQLServerDataSourceObjectFactory-.md) method, passing in the Reference object, to retrieve the data source instance.  
  
## See Also  
 [SQLServerDataSourceObjectFactory Members](../content/SQLServerDataSourceObjectFactory-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  