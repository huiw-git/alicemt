---
title: cancel Method (SQLServerStatement)
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
  - SQLServerStatement.cancel
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
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
# cancel Method (SQLServerStatement)
  Cancels the SQL statement that is currently being run by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final void cancel()  
```  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This cancel method is specified by the cancel method in the java.sql.Statement interface.  
  
 When executing a statement that produces a single large forward\-only, read\-only result set, you might only be interested in some initial set of rows in the returned result set. In this case, the application might call the [cancel](../content/cancel-Method--SQLServerStatement-.md) method of the associated statement object before closing the result set in order to minimize the processing time needed to discard the remaining unnecessary rows. We recommend considering the tradeoff between the processing time that would be saved and the time and the additional round trip to the server needed to cancel the execution when deciding whether to use this technique or not.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  