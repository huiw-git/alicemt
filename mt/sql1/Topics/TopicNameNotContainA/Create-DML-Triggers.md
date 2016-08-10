---
title: "Create DML Triggers"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-dml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# Create DML Triggers
This topic describes how to create a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] DML trigger by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and by using the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] CREATE TRIGGER statement.  
  
##  <a name="Top"></a> Before You Begin  
  
### Limitations and Restrictions  
 For a list of limitations and restrictions related to creating DML triggers, see [CREATE TRIGGER (Transact-SQL)](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7).  
  
###  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the table or view on which the trigger is being created.  
  
##  <a name="Procedures"></a> How to Create a DML Trigger  
 You can use one of the following:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database, expand **Tables** and then expand the table **Purchasing.PurchaseOrderHeader**.  
  
3.  Right-click **Triggers**, and then select **New Trigger**.  
  
4.  On the **Query** menu, click **Specify Values for Template Parameters**. Alternatively, you can press (Ctrl-Shift-M) to open the **Specify Values for Template Parameters** dialog box.  
  
5.  In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.  
  
    |Parameter|Value|  
    |---------------|-----------|  
    |Author|*Your name*|  
    |Create Date|*Today's date*|  
    |Description|Checks the vendor credit rating before allowing a new purchase order with the vendor to be inserted.|  
    |Schema_Name|Purchasing|  
    |Trigger_Name|NewPODetail2|  
    |Table_Name|PurchaseOrderDetail|  
    |Data_Modification_Statement|Remove UPDATE and DELETE from the list.|  
  
6.  Click **OK**.  
  
7.  In the **Query Editor**, replace the comment `-- Insert statements for trigger here` with the following statement:  
  
    ```tsql  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
8.  To verify the syntax is valid, on the **Query** menu, click **Parse**. If an error message is returned, compare the statement with the information above and correct as needed and repeat this step.  
  
9. To create the DML trigger, from the **Query** menu, click **Execute**. The DML trigger is created as an object in the database.  
  
10. To see the DML trigger listed in Object Explorer, right-click **Triggers** and select **Refresh**.  
  
 [&#91;Top&#93;](#Top)  
  
###  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and then expand that instance.  
  
2.  From the **File** menu, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example creates the same stored DML trigger as above.  
  
    ```  
    -- Trigger valid for multirow and single row inserts  
    -- and optimal for single row inserts.  
    USE AdventureWorks2012;  
    GO  
    CREATE TRIGGER NewPODetail3  
    ON Purchasing.PurchaseOrderDetail  
    FOR INSERT AS  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
##  <a name="PowerShellProcedure"></a> [&#91;Top&#93;](#Top)