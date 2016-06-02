---
title: Immediately Apply Member Permissions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
---
# Immediately Apply Member Permissions (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], instead of waiting for member security to be applied at regular intervals, you can apply member permissions immediately.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. For more information, see [Database Object Security &#40;Master Data Services&#41;](../Topic/Database%20Object%20Security%20\(Master%20Data%20Services\).md).  
  
### To immediately apply hierarchy member permissions  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance for your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
2.  Create a new query.  
  
3.  Type the following text, replacing *database* with the name of your database and *Model\_Name* with the name of the model.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  Run the query.  
  
## See Also  
 [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)   
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)  
  
  