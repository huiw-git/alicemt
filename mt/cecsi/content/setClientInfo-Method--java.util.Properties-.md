---
title: "setClientInfo Method (java.util.Properties)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
caps.latest.revision: 19
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
# setClientInfo Method (java.util.Properties)
  Sets the value of the connection's client information properties.  
  
## Syntax  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### Parameters  
 *properties*  
  
 A Properties object that contains the list of client information properties to set.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setClientInfo method is specified by the setClientInfo method in the java.sql.Connection interface.  
  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] does not support any client information properties. This method generates warnings if the *properties* input parameter does not refer to an empty property set. In other words, this method generates warnings for the properties that the application wants to set. Applications should use [getWarnings](../content/getWarnings-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class to retrieve each warning.  
  
## See Also  
 [setClientInfo Method &#40;SQLServerConnection&#41;](../content/setClientInfo-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  