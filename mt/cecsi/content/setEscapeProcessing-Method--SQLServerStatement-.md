---
title: setEscapeProcessing Method (SQLServerStatement)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.setEscapeProcessing
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
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
# setEscapeProcessing Method (SQLServerStatement)
  Sets the escape processing mode.  
  
> [!NOTE]  
>  Escape processing for [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] is always enabled. Setting this method to false has no effect.  
  
## Syntax  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### Parameters  
 *enable*  
  
 **true** to enable escape processing. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setEscapeProcessing method is specified by the setEscapeProcessing method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  