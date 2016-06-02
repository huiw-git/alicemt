---
title: View or Modify the Properties of a Policy-Based Management Condition
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
---
# View or Modify the Properties of a Policy-Based Management Condition
  This topic describes how to view or modify the properties of a Policy\-Based Management condition in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view or modify a condition's properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the PolicyAdministratorRole role in the msdb database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or modify a condition's properties  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to view or modify.  
  
2.  Click the plus sign to expand the **Management** folder.  
  
3.  Click the plus sign to expand **Policy Management**.  
  
4.  Click the plus sign to expand the **Conditions** folder.  
  
5.  Right\-click the condition that you want to view or edit and select **Properties**. For more information on the available options in the **Open Condition –***condition\_name* dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../Topics\TopicNameNotContainA/Create-New-Condition-or-Open-Condition-Dialog-Box,-General-Page.md), [Open Condition Dialog Box, Dependent Policies Page](../../Topics\TopicNameNotContainA/Open-Condition-Dialog-Box,-Dependent-Policies-Page.md), [Create New Condition or Open Condition Dialog Box, Description Page](../../Topics\TopicNameNotContainA/Create-New-Condition-or-Open-Condition-Dialog-Box,-Description-Page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](../Topic/Advanced%20Edit%20\(Condition\)%20Dialog%20Box.md).  
  
6.  When finished, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To view a condition's properties  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 For more information, see [syspolicy_conditions &#40;Transact-SQL&#41;](../Topic/syspolicy_conditions%20\(Transact-SQL\).md).  
  
  