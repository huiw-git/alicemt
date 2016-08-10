---
title: "Subscribe or Unsubscribe a Database  to a Policy Category"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Subscribe or Unsubscribe a Database  to a Policy Category
This topic describes how to subscribe or unsubscribe a database to a policy category.in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To subscribe or unsubscribe a database to a policy category., using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the db_owner fixed database role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To subscribe or unsubscribe a database to a policy category  
  
1.  In **Object Explorer**, click the plus sign to expand the server that contains the database wherein you want to manage category subscriptions.  
  
2.  Click the plus sign to expand the **Databases** folder.  
  
3.  Right-click the database wherein you want to manage category subscriptions, point to **Policies**, and select **Categories**  
  
     The following options are available in the **Categories** dialog box:  
  
     Expand column  
     Click to expand a policy category. This lists all the policies that are included in the category.  
  
     **Name**  
     The name of the policy category.  
  
     **Subscribed**  
     Indicates whether the target has subscribed to the policy category. If this check box is disabled, the policy category is set for **Mandate Database Subscriptions**. This means that the policy category applies to all databases on the server.  
  
     **Policy**  
     When policy groups are expanded, displays the policies in the policy category.  
  
     **Enabled**  
     Indicates whether the policies are enabled or disabled.  
  
     **Execution Mode**  
     Displays the execution mode of the policy.  
  
     **History**  
     Click the View History hyperlink to open the Log File Viewer to see the policy history.  
  
4.  To subscribe to a Policy-Based Management category, select the category's check box under the **Subscribed** column. To unsubscribe from a category, clear the check box.  
  
5.  When finished, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To subscribe a database to a policy category  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 For more information, see [sp_syspolicy_subscribe_to_policy_category (Transact-SQL)](assetId:///de88cc49-bcc8-4dc6-8e59-ad85cfbfb2fb).  
  
#### To unsubscribe a database to a policy category  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 For more information, see [sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL)](assetId:///47abab63-e605-40e8-a54e-2241e2e01afd).