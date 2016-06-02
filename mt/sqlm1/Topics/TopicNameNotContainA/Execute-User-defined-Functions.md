---
title: Execute User-defined Functions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-udf
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
---
# Execute User-defined Functions
  You can execute a user defined function in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To execute a user\-defined function, using:**  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
 In Transact\-SQL, parameters can be supplied either by using *value* or by using @*parameter\_name*\=*value.* A parameter is not part of a transaction; therefore, if a parameter is changed in a transaction that is later rolled back, the value of the parameter does not revert to its previous value. The value returned to the caller is always the value at the time the module returns.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Permissions are not required to run the EXECUTE statement. However, permissions are required on the securables that are referenced within the EXECUTE string. For example, if the string contains an INSERT statement, the caller of the EXECUTE statement must have INSERT permission on the target table. Permissions are checked at the time EXECUTE statement is encountered, even if the EXECUTE statement is included within a module. For more information, see [EXECUTE &#40;Transact-SQL&#41;](../Topic/EXECUTE%20\(Transact-SQL\).md)  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To execute a user\-defined function  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 For more information, see [EXECUTE &#40;Transact-SQL&#41;](../Topic/EXECUTE%20\(Transact-SQL\).md).  
  
  