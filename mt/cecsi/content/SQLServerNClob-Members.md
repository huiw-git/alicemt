---
title: SQLServerNClob Members
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
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
# SQLServerNClob Members
  The following tables list the members exposed by the [SQLServerNClob](../content/SQLServerNClob-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
 None.  
  
## Inherited Fields  
 None.  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[free](../content/free-Method--SQLServerNClob-.md)|This method frees the **NCLOB** object and releases the resources that it holds.|  
|[getAsciiStream](../content/getAsciiStream-Method--SQLServerNClob-.md)|Retrieves the **NCLOB** value designated by the **java.sql.NClob** object as an ASCII stream.|  
|[getCharacterStream](../content/getCharacterStream-Method--SQLServerNClob-.md)|Retrieves the **NCLOB** value designated by the **java.sql.NClob** object.|  
|[getSubString](../content/getSubString-Method--SQLServerNClob-.md)|Retrieves a copy of the specified substring in the **NCLOB** value designated by the **java.sql.NClob** object.|  
|[length](../content/length-Method--SQLServerNClob-.md)|Retrieves the number of characters in the **NCLOB** value designated by the **java.sql.NClob** object.|  
|[position](../content/position-Method--SQLServerNClob-.md)|Retrieves the character position of the specified **java.sql.NClob** object or substring in the **java.sql.NClob** based on the specified starting position.|  
|[setAsciiStream](../content/setAsciiStream-Method--SQLServerNClob-.md)|Retrieves a stream to be used to write ASCII characters to the **NCLOB** value that this **java.sql.NClob** object represents, starting at the specified position.|  
|[setCharacterStream](../content/setCharacterStream-Method--SQLServerNClob-.md)|Retrieves a stream to be used to write a stream of Unicode characters to the **NCLOB** value that this **java.sql.NClob** object represents, starting at the specified position.|  
|[setString](../content/setString-Method--SQLServerNClob-.md)|Writes the specified **String** to the **NCLOB** starting at the specified position.|  
|[truncate](../content/truncate-Method--SQLServerNClob-.md)|Truncates the **NCLOB** value to the specified length.|  
  
## Inherited Methods  
  
|Class inherited from|Methods|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## See Also  
 [SQLServerClob Class](../content/SQLServerClob-Class.md)  
  
  