---
title: getMoreResults Method (int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.getMoreResults (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
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
# getMoreResults Method (int)
  Moves to the next result of this [SQLServerStatement](../content/SQLServerStatement-Class.md) object and deals with any currently open result set objects according to the instructions specified by the given mode.  
  
## Syntax  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### Parameters  
 *mode*  
  
 An **int** that indicates how to handle currently open result set objects. Must be one of the following constants:  
  
 CLOSE\_CURRENT\_RESULT  
  
 KEEP\_CURRENT\_RESULT \(not supported by the JDBC driver\)  
  
 CLOSE\_ALL\_RESULTS  
  
## Return Value  
 **true** if the returned result is a result set. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMoreResults method is specified by the getMoreResults method in the java.sql.Statement interface.  
  
 If the getMoreResults method is called before results are retrieved, it behaves as specified by the *mode* argument and moves to the next result.  
  
> [!NOTE]  
>  The JDBC driver does not support using the KEEP\_CURRENT\_RESULT constant. If it is used, an exception will be thrown.  
  
## See Also  
 [getMoreResults Method &#40;SQLServerStatement&#41;](../content/getMoreResults-Method--SQLServerStatement-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  