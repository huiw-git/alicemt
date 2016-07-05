---
title: setCharacterStream Method (int, java.io.Reader)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
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
# setCharacterStream Method (int, java.io.Reader)
  Sets the designated parameter to the specified java.io.Reader object.  
  
> [!NOTE]  
>  This feature is introduced starting with the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver version 2.0.  
  
## Syntax  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### Parameters  
 *parameterIndex*  
  
 An **int** that indicates the parameter number.  
  
 *reader*  
  
 The java.io.Reader object that contains the Unicode data.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setCharacterStream method is specified by the setCharacterStream method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [setCharacterStream Method &#40;SQLServerPreparedStatement&#41;](../content/setCharacterStream-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)  
  
  