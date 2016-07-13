---
title: Update Table Dialog Box (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
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
# Update Table Dialog Box (Visual Database Tools)
This dialog box allows you to specify the table to be updated.  
  
This dialog box appears if more than one table is displayed in the Diagram pane when you change a query's type to be an Update query.  
  
Select the table to update, and then choose **OK**.\\  
  
> [!NOTE]  
> If the table is published for replication, you must make schema changes using the Transact\-SQL statement [ALTER TABLE](assetId:///f1745145-182d-4301-a334-18f799d361d1) or SQL Server Management Objects (SMO). When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table. You cannot drop published objects, therefore the schema change will fail.  
  
## See Also  
[Create Update Queries &#40;Visual Database Tools&#41;](../content/Create-Update-Queries--Visual-Database-Tools-.md)  
  
