---
title: SQLServerBlob Members
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90e48555-ea83-4a90-80a3-51bc685015ec
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
# SQLServerBlob Members
  The following tables list the members that are exposed by the [SQLServerBlob](../content/SQLServerBlob-Class.md) class.  
  
## Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[SQLServerBlob](../content/SQLServerBlob-Constructor--SQLServerConnection--byte-.md)|Initializes a new instance of the SQLServerBlob class.|  
  
## Fields  
 None.  
  
## Inherited Fields  
 None.  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[free](../content/free-Method--SQLServerBlob-.md)|This method frees the BLOB object and releases the resources that it holds.|  
|[getBinaryStream](../content/getBinaryStream-Method--SQLServerBlob-.md)|Returns an input stream to read data from the BLOB.|  
|[getBytes](../content/getBytes-Method--SQLServerBlob-.md)|Gets the BLOB data as an array of bytes.|  
|[length](../content/length-Method--SQLServerBlob-.md)|Returns the number of bytes in the BLOB object.|  
|[position](../content/position-Method--SQLServerBlob-.md)|Returns the position of a specified pattern in the BLOB based on the given pattern and the starting index.|  
|[setBinaryStream](../content/setBinaryStream-Method--SQLServerBlob-.md)|Retrieves a stream that can be used to write to the BLOB value.|  
|[setBytes](../content/setBytes-Method--SQLServerBlob-.md)|Writes the given array of bytes into the BLOB starting at the given position, and then returns the number of bytes written.|  
|[truncate](../content/truncate-Method--SQLServerBlob-.md)|Truncates a BLOB given the length.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## See Also  
 [SQLServerBlob Class](../content/SQLServerBlob-Class.md)  
  
  