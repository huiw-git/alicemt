---
title: Database Changes Detected Dialog Box (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
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
# Database Changes Detected Dialog Box (Visual Database Tools)
This dialog appears if you attempt to save a database diagram or selected tables but some of the database objects that will be affected by the save action are out of date with the database. Accepting the changes shown in this dialog box updates the database to match your diagram and overwrites other users' changes.  
  
> [!NOTE]  
> Although you cannot undo changes made to a table or database diagram, the changes are not saved to the database until you save the table or diagram. You can discard any unsaved changes by choosing **No** and closing all open diagrams without saving them.  
  
## Options  
**Warn about difference detection**  
Specify whether this dialog box appears the next time you attempt to save a database diagram or selected tables. Checked means that the dialog box continues to appear each time you save a diagram or table that is out of date with the database. Unchecked means that the dialog box does not appear. By default, this box is checked. If you uncheck this option, you can recheck it in the **Options** dialog box.  
  
**Yes**  
Update the database with all the changes shown in the list.  
  
**No**  
Cancel the save action.  
  
> [!NOTE]  
> To refresh your diagram to match the database, close it without saving changes, right\-click the diagram in Server Explorer and click Refresh, and then reopen the diagram.  
  
**Save Text File**  
Display the **Save As** dialog box, letting you specify a location for a text file containing a list of the database changes.  
  
## See Also  
[Reconcile a Database Diagram with a Modified Database &#40;Visual Database Tools&#41;](../content/Reconcile-a-Database-Diagram-with-a-Modified-Database--Visual-Database-Tools-.md)  
[Multiuser Environments &#40;Visual Database Tools&#41;](../content/Multiuser-Environments--Visual-Database-Tools-.md)  
  
