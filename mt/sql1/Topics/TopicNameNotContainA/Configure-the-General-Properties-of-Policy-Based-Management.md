---
title: "Configure the General Properties of Policy-Based Management"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Configure the General Properties of Policy-Based Management
This topic describes how to configure the properties for Policy-Based Management in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To configure Policy-Based Management, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the PolicyAdministratorRole fixed database role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To configure Policy-Based Management  
  
1.  In **Object Explorer**, click the plus sign to expand the server where you want to configure Policy-Based Management properties.  
  
2.  Click the plus sign to expand the **Management** folder.  
  
3.  Right-click **Policy Management** and select **Properties**.  
  
     The following options are available in **Policy Management Properties** dialog box.  
  
     **Enabled**  
     Specifies whether Policy-Based Management is enabled.  
  
     **HistoryRetentionInDays**  
     Specifies the number of days that policy evaluation history should be retained. If this value is 0 (the default), the history will not be automatically removed.  
  
     **LogOnSuccess**  
     Specifies whether Policy-Based Management logs successful policy evaluations.  
  
    -   When this value is false (the default), only failed policy evaluations are logged.  
  
    -   When this value is true, both successful and failed policy evaluations are logged.  
  
4.  When finished, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To configure Policy-Based Management  
  
1.  In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  On the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**.  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 For more information, see [sp_syspolicy_configure (Transact-SQL)](assetId:///70c10922-9345-4190-ba69-808a43f760da).