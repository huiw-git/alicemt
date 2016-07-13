---
title: Development, Test, and Production Databases (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
manager: jhubbard
translation.priority.mt: 
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
# Development, Test, and Production Databases (Visual Database Tools)
If you have two databases with identical structure, you can make changes in one database and propagate those changes to the other. For example, if you have a personal development database and a group\-wide test database, you can modify the development database, then propagate those changes to the test database.  
  
To accomplish this, perform all the modifications in a single session with the development database, create a Change Script of your session and later run the script on the test database.  
  
## See Also  
[Multiuser Environments &#40;Visual Database Tools&#41;](../content/Multiuser-Environments--Visual-Database-Tools-.md)  
  
