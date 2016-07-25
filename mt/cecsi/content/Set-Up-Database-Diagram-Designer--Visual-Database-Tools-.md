---
title: "Set Up Database Diagram Designer (Visual Database Tools)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
caps.latest.revision: 4
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
# Set Up Database Diagram Designer (Visual Database Tools)
To use Database Diagram Designer, it must first be set up by a member of the **db_owner** role to control access to diagrams.  
  
### To set up database diagramming  
  
1.  From Object Explorer, expand a database node.  
  
2.  Expand the Database Diagrams node under the database connection.  
  
3.  Select **Yes** when prompted if you want to set up database diagramming.  
  
    > [!NOTE]  
    > This will create the database diagram table, system stored procedures, and a system function on the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
4.  Visual Studio will create the following objects on the instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]:  
  
    1.  sysdiagrams table  
  
    2.  sp_alterdiagram stored procedure  
  
    3.  sp_creatediagram stored procedure  
  
    4.  sp_dropdiagram stored procedure  
  
    5.  sp_renamediagram stored procedure  
  
    6.  fn_diagramobjects function  
  
    7.  sp_helpdiagrams stored procedure  
  
    8.  sp_helpdiagramsdefinition stored procedure  
  
    9. sp_upgraddiagrams stored procedure  
  
## See Also  
[Understand Database Diagram Ownership &#40;Visual Database Tools&#41;](../content/Understand-Database-Diagram-Ownership--Visual-Database-Tools-.md)  
[Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;](../content/Upgrade-Database-Diagrams-from-Previous-Editions--Visual-Database-Tools-.md)  
[ALTER AUTHORIZATION (Transact-SQL)](assetId:///8c805ae2-91ed-4133-96f6-9835c908f373)  
  
