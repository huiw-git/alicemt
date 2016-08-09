---
title: "Create Unique Constraints"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# Create Unique Constraints
You can create a unique constraint in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] to ensure no duplicate values are entered in specific columns that do not participate in a primary key. Creating a unique constraint automatically creates a corresponding unique index.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To create a unique constraint, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To create a unique constraint  
  
1.  In **Object Explorer**, right-click the table to which you want to add a unique constraint, and click **Design**.  
  
2.  On the **Table Designer** menu, click **Indexes/Keys**.  
  
3.  In the **Indexes/Keys** dialog box, click **Add**.  
  
4.  In the grid under **General**, click **Type** and choose **Unique Key** from the drop-down list box to the right of the property.  
  
5.  On the **File** menu, click **Save***table name*.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To create a unique constraint  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example creates the table `TransactionHistoryArchive4` and creates a unique constraint on the column `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### To create a unique constraint on an existing table  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example creates a unique constraint on the columns `PasswordHash` and `PasswordSalt` in the table `Person.Password`.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### To create a unique constraint in an new table  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example creates a table and defines a unique constraint on the column `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     For more information, see [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1), [CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b), and [table_constraint (Transact-SQL)](assetId:///ac2a11e0-cc77-4e27-b107-4fe5bc6f5195).  
  
###  <a name="TsqlExample"></a>