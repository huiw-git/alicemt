---
title: setClientInfo Method (java.lang.String, java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
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
# setClientInfo Method (java.lang.String, java.lang.String)
  Sets the value of the specified client information property.  
  
## Syntax  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### Parameters  
 *name*  
  
 A String that contains the name of the client information property to set.  
  
 *value*  
  
 A String that contains the value to set the client infomation property to.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setClientInfo method is specified by the setClientInfo method in the java.sql.Connection interface.  
  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] does not support any client information properties. In the 2.0 JDBC Driver, this method generates a warning for a property. Applications should use [getWarnings](../content/getWarnings-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class to retrieve a warning.  
  
## See Also  
 [setClientInfo Method &#40;SQLServerConnection&#41;](../content/setClientInfo-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  