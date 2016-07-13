---
title: Default SQL Server Data Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
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
  - zh-cn
  - zh-tw
---
# Default SQL Server Data Types
When sending data to the server, the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] converts data from its PHP data type to a SQL Server data type if no SQL Server data type has been specified by the user. The table that follows lists the PHP data type \(the data type being sent to the server\) and the default SQL Server data type \(the data type to which the data is converted\). For details about how to specify data types when sending data to the server, see [How to: Specify SQL Server Data Types When Using the SQLSRV Driver](../Topic/How%20to:%20Specify%20SQL%20Server%20Data%20Types%20When%20Using%20the%20SQLSRV%20Driver.md).  
  
|PHP Data Type|Default SQL Server Type in the SQLSRV Driver|Default SQL Server Type in the PDO\_SQLSRV Driver|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar\(1\)|not supported|  
|Boolean|bit|bit|  
|Integer|int|int|  
|Float|float\(24\)|not supported|  
|String \(length less than 8000 bytes\)|varchar\(<string length>\)|varchar\(<string length>\)|  
|String \(length greater than 8000 bytes\)|varchar\(max\)|varchar\(max\)|  
|Resource|Not supported.|Not supported.|  
|Stream \(encoding: not binary\)|varchar\(max\)|varchar\(max\)|  
|Stream \(encoding: binary\)|varbinary|varbinary|  
|Array|Not supported.|Not supported.|  
|Object|Not supported.|Not supported.|  
|DateTime \(1\)|datetime|Not supported.|  
  
## See Also  
[Constants &#40;Microsoft Drivers for PHP for SQL Server&#41;](../content/Constants--Microsoft-Drivers-for-PHP-for-SQL-Server-.md)  
[Converting Data Types](../content/Converting-Data-Types.md)  
[sqlsrv_field_metadata](../content/sqlsrv_field_metadata.md)  
[PHP Types](http://go.microsoft.com/fwlink/?LinkId=109071)  
[Data Types \(Transact\-SQL\)](http://go.microsoft.com/fwlink/?LinkId=109068)  
  
