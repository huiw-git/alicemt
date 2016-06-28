---
title: Delete Objects
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
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
# Delete Objects
Use this dialog box to delete a database or database object.  
  
## UIElement List  
**Object to be deleted**  
Displays the names, types, owners, and status of the objects that are about to be deleted, as well as any messages about errors during execution.  
  
> [!NOTE]  
> Running **Delete** on a database is equivalent to issuing DROP DATABASE in [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**Show Dependencies**  
Click to display both the objects that are dependent on the currently selected object and objects that the current object is dependent on (upward and downward dependency). The information displayed in the **Show Dependencies** dialog box is read\-only.  
  
> [!NOTE]  
> The **Show Dependencies** button does not appear for all types of database objects. To view dependencies when the **Show Dependencies** button is not available, right\-click the object in Object Explorer, and then click **View Dependencies**.  
  
**Delete backup and restore history information for databases**  
Only appears when a database is deleted, this check box causes the backup and restore history for the subject database to be deleted from the **msdb** database.  
  
**Close existing connections**  
Only appears when a database is deleted, this check box terminates connections to the subject database.  
  
