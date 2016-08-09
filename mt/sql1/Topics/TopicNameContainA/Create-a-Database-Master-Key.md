---
title: "Create a Database Master Key"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
caps.latest.revision: 17
caps.handback.revision: 0
manager: jhubbard
---
# Create a Database Master Key
This topic describes how to create a database master key in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   [To create a database master key using Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires CONTROL permission on the database.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To create a database master key  
  
1.  Choose a password for encrypting the copy of the master key that will be stored in the database.  
  
2.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
3.  On the Standard bar, click **New Query**.  
  
4.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- Creates a database master key for the "AdventureWorks2012" database.   
    -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."  
    USE AdventureWorks2012;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
    GO  
    ```  
  
 For more information, see [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76).