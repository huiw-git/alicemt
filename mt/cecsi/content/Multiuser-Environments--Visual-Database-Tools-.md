---
title: Multiuser Environments (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
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
# Multiuser Environments (Visual Database Tools)
A multiuser environment is one in which other users can connect and make changes to the same database that you are working with. As a result, several users might be working with the same database objects at the same time. Thus, a multiuser environment introduces the possibility of the database being affected by changes made by other users while you are making changes, and vice versa.  
  
A key issue when working with databases in a multiuser environment is access permissions. The permissions you have for the database determine the extent of the work you can do with the database. For example, to make changes to objects in a database, you must have the appropriate write permissions for the database. For more information about permissions in your database, see your database documentation. For more information see [Permissions and Visual Database Tools &#40;Visual Database Tools&#41;](../content/Permissions-and-Visual-Database-Tools--Visual-Database-Tools-.md).  
  
When you save changes made to tables, Table Designer verifies that the database has not been modified since you last saved changes. If another user has made changes, you will be notified that the database has been modified. You may need to reconcile these changes. For more information, see [Reconcile Changes Made by Multiple Users &#40;Visual Database Tools&#41;](../content/Reconcile-Changes-Made-by-Multiple-Users--Visual-Database-Tools-.md).  
  
In a multiuser environment there are special considerations to keep in mind to avoid conflicting changes. For more information, see [Issues of Database Evolution &#40;Visual Database Tools&#41;](../content/Issues-of-Database-Evolution--Visual-Database-Tools-.md).  
  
One way to avoid problems is to work in a copy of the database, such as a test database, when you make changes, then you can create a change script that you can run to make those changes on the original database after resolving conflicts offline. For more information see [Development, Test, and Production Databases &#40;Visual Database Tools&#41;](../content/Development--Test--and-Production-Databases--Visual-Database-Tools-.md).  
  
