---
title: "setHoldability Method (SQLServerConnection)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.setHoldability
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 552eebd0-4c38-43f0-961f-35244f99109b
caps.latest.revision: 11
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
# setHoldability Method (SQLServerConnection)
  Changes the holdability of [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects that are created by using this [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object to the given holdability.  
  
## Syntax  
  
```  
  
public void setHoldability(int nNewHold)  
```  
  
#### Parameters  
 *nNewHold*  
  
 An **int** value that contains one of the following holdability levels:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setHoldability method is specified by the setHoldability method in the java.sql.Connection interface.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  