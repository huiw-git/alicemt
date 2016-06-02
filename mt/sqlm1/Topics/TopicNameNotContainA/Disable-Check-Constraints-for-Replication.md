---
title: Disable Check Constraints for Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af98fc70-24dd-4bd3-a0a3-f701dfa67b2c
---
# Disable Check Constraints for Replication
  You can disable check constraints in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. You can also explicitly disable check constraints for replication, which can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  If a table is published using replication, check constraints are automatically disabled for operations performed by replication agents. When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked. The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted. For more information, see [Specify Schema Options](../../Topics\TopicNameNotContainA/Specify-Schema-Options.md).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To disable a check constraint for replication  
  
1.  In **Object Explorer**, expand the table with the check constraint you want to modify, and then expand the **Constraints** folder.  
  
2.  Right\-click the check constraint you wish to modify and then click **Modify**.  
  
3.  In the **Check Constraints** dialog box, under **Table Designer**, select a value of **No** for **Enforce For Replication**.  
  
4.  Click **Close**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To disable a check constraint for replication  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example creates a table with an IDENTITY column and a CHECK constraint on the table. The example then drops the constraint and recreates it specifying the NOT FOR REPLICATION clause.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.doc_exd (column_a int IDENTITY (1,1)   
    CONSTRAINT exd_check CHECK (column_a > 1))   
  
    ALTER TABLE dbo.doc_exd   
    DROP CONSTRAINT exd_check;   
    GO  
    ALTER TABLE dbo.doc_exd    
    ADD CONSTRAINT exd_check CHECK NOT FOR REPLICATION (column_a > 1);  
    ```  
  
 For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md).  
  
###  <a name="TsqlExample"></a>   
## See Also  
 [Specify Schema Options](../../Topics\TopicNameNotContainA/Specify-Schema-Options.md)  
  
  