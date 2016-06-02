---
title: Parsing Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
---
# Parsing Data
  Data flows in packages extract and load data between heterogeneous data stores, which may use a variety of standard and custom data types. In a data flow, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] sources do the work of extracting data, parsing string data, and converting data to an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data type. Subsequent transformations may parse data to convert it to a different data type, or create column copies with different data types. Expressions used in components may also cast arguments and operands to different data types. Finally, when the data is loaded into a data store, the destination may parse the data to convert it to a data type that the destination uses. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Types of Parsing  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides two types of parsing for converting data: Fast parse and Standard parse.  
  
-   Fast parse is a fast, simple set of parsing routines that does not support locale\-specific data type conversions, and supports only the most frequently used date and time formats. For more information, see [Fast Parse](../../Topics\TopicNameNotContainA/Fast-Parse.md).  
  
-   Standard parse is a rich set of parsing routines that supports all the data type conversions that are provided by the Automation data type conversion APIs available in Oleaut32.dll and Ole2dsip.dll. For more information, see [Standard Parse](../../Topics\TopicNameNotContainA/Standard-Parse.md).  
  
  