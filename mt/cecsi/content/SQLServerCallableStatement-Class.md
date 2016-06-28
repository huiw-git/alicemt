---
title: SQLServerCallableStatement Class
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
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
# SQLServerCallableStatement Class
  Lets you specify the stored procedure name to call along with input and output parameters. This class also provides the ability to retrieve the return status value with the ? \= call\( ?, ..\) syntax.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Implements:** [ISQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md)  
  
 **Extends:** [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md)  
  
## Syntax  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## Remarks  
 SQLServerCallableStatement lets you specify the stored procedure name to call along with input and output parameters. SQLServerCallableStatement also provides the ability to retrieve the return status value with the `? = call( ?, ..)` syntax.  
  
 This class supports unwrapping to SQLServerCallableStatement class, ISQLServerCallableStatement interface, java.sql.CallableStatement interface, and the classes and interfaces supported by SQLServerPreparedStatement for unwrapping. For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
 When one of the SQLServerCallableStatement set methods is called for a type, if that type conflicts with the type specified with [registerOutParameter](../content/registerOutParameter-Method--SQLServerCallableStatement-.md), the type specified by the last SQLServerCallableStatement set method is used. However, this may cause incompatible data type conversion errors. If a SQLServerCallableStatement set method is not called, the type specified with the first [registerOutParameter](../content/registerOutParameter-Method--SQLServerCallableStatement-.md) call is used.  
  
 The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0 is compliant with the JDBC 4.0 recommendation that a result set and update counts must be retrieved before retrieving OUT parameters. If OUT parameters are retrieved before the result set and update counts have been completely processed, any result sets and update counts that have not been processed are lost.  
  
## See Also  
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  