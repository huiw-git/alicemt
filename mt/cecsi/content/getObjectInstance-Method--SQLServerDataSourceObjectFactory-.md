---
title: getObjectInstance Method (SQLServerDataSourceObjectFactory)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSourceObjectFactory.getObjectInstance
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
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
# getObjectInstance Method (SQLServerDataSourceObjectFactory)
  Retrieves an instance of the specified data source object.  
  
## Syntax  
  
```  
  
public java.lang.Object getObjectInstance(java.lang.Object ref,  
                                          javax.naming.Name name,  
                                          javax.naming.Context c,  
                                          java.util.Hashtable h)  
```  
  
#### Parameters  
 *ref*  
  
 An **Object** value.  
  
 *name*  
  
 The name of the object.  
  
 *c*  
  
 The context relative to the specified name.  
  
 *h*  
  
 The environment that is used in creating the object.  
  
## Return Value  
 An **Object** value.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getObjectInstance method is specified by the getObjectInstance method in the javax.naming.spi.ObjectFactory interface.  
  
## See Also  
 [SQLServerDataSourceObjectFactory Methods](../content/SQLServerDataSourceObjectFactory-Methods.md)   
 [SQLServerDataSourceObjectFactory Members](../content/SQLServerDataSourceObjectFactory-Members.md)   
 [SQLServerDataSourceObjectFactory Class](../content/SQLServerDataSourceObjectFactory-Class.md)  
  
  