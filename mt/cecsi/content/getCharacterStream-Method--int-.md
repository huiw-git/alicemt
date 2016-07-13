---
title: getCharacterStream Method (int)
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
  - SQLServerResultSet.getCharacterStream (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
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
# getCharacterStream Method (int)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a java.io.Reader object.  
  
## Syntax  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 A Reader object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getCharacterStream method is specified by the getCharacterStream method in the java.sql.ResultSet interface.  
  
 This method will read only [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Unicode character data types such as nchar, nvarchar, nvarchar\(max\), and ntext. All other data types, including the ASCII character types, will cause an exception to be thrown. To read the ASCII data types, use the [getAsciiStream](../content/getAsciiStream-Method--SQLServerResultSet-.md) method.  
  
## See Also  
 [getCharacterStream Method &#40;SQLServerResultSet&#41;](../content/getCharacterStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  