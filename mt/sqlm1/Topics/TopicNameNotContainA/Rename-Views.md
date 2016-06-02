---
title: Rename Views
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-views
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
---
# Rename Views
  You can rename a view in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
> [!WARNING]  
>  If you rename a view, code and applications that depend on the view may fail. These include other views, queries, stored procedures, user\-defined functions, and client applications. Note that these failures will cascade.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To rename a view, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a view](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 Obtain a list of all dependencies on the view. Any objects, scripts or applications that reference the view must be modified to reflect the new name of the view. For more information, see [Get Information About a View](../../Topics\TopicNameContainA/Get-Information-About-a-View.md). We recommend that you drop the view and recreate it with a new name instead of renaming the view. By recreating the view, you update the dependency information for the objects that are referenced in the view.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT is required, and CREATE VIEW permission in the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To rename a view  
  
1.  In **Object Explorer**, expand the database that contains the view you wish to rename and then expand the **View** folder.  
  
2.  Right\-click the view you wish to rename and select **Rename**.  
  
3.  Enter the view’s new name.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To rename a view**  
  
 While you can use **sp\_rename** to change the name of the view, we recommend that you delete the existing view and then re\-create it with the new name.  
  
 For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](../Topic/CREATE%20VIEW%20\(Transact-SQL\).md) and [DROP VIEW &#40;Transact-SQL&#41;](../Topic/DROP%20VIEW%20\(Transact-SQL\).md).  
  
##  <a name="FollowUp"></a> Follow Up: After Renaming a View  
 Ensure that all objects, scripts, and applications that reference the view’s old name now use the new name.  
  
  