---
title: getPrecision Method (SQLServerParameterMetaData)
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
  - SQLServerParameterMetaData.getPrecision
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
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
# getPrecision Method (SQLServerParameterMetaData)
  Retrieves the number of decimal digits of the designated parameter.  
  
## Syntax  
  
```  
  
public int getPrecision(int param)  
```  
  
#### Parameters  
 *param*  
  
 An **int** that indicates parameter index.  
  
## Return Value  
 An **int** that indicates the precision of the designated parameter.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getPrecision method is specified by the getPrecision method in the java.sql.ParameterMetaData interface.  
  
 For number types, this method gets the number of decimal digits. For character types, it gets the maximum length in characters. For binary types, it gets the maximum length in bytes. Where the number of digits is unknown, this method returns "0".  
  
## See Also  
 [SQLServerParameterMetaData Methods](../content/SQLServerParameterMetaData-Methods.md)   
 [SQLServerParameterMetaData Members](../content/SQLServerParameterMetaData-Members.md)   
 [SQLServerParameterMetaData Class](../content/SQLServerParameterMetaData-Class.md)  
  
  