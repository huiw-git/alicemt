---
title: FOR XML Support for the User-Defined Data Types (UDT)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
---
# FOR XML Support for the User-Defined Data Types (UDT)
  FOR XML does not support common language runtime \(CLR\) user\-defined data types \(UDTs\).  
  
 To use FOR XML with CLR user\-defined data types, make sure that the data type has an XML serialization, and use an explicit cast to XML in the FOR XML select clause.  
  
## See Also  
 [FOR XML Support for Various SQL Server Data Types](../../Topics\TopicNameNotContainA/FOR-XML-Support-for-Various-SQL-Server-Data-Types.md)  
  
  