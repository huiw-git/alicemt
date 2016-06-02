---
title: Disable Foreign Key Constraints for Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
---
# Disable Foreign Key Constraints for Replication
  You can disable foreign key constraints for replication in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. This can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  If a table is published using replication, foreign key constraints are automatically disabled for operations performed by replication agents. When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked. The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To disable a foreign key constraint for replication, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To disable a foreign key constraint for replication  
  
1.  In **Object Explorer**, expand the table with the foreign key constraint you want to modify, and then expand the **Keys** folder.  
  
2.  Right\-click the foreign key constraint and then click **Modify**.  
  
3.  In the **Foreign Key Relationships** dialog box, select a value of **No** for **Enforce For Replication**.  
  
4.  Click **Close**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To disable a foreign key constraint for replication  
  
1.  To perform this task in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], drop the foreign key constraint. Then add a new foreign key constraint and specify the NOT FOR REPLICATION option.  
  
 For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md).  
  
###  <a name="TsqlExample"></a>  