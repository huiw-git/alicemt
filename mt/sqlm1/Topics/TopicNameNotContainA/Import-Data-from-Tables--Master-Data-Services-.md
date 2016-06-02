---
title: Import Data from Tables (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad5b83b1-8e40-4ef8-9ba8-4ea17a58b672
---
# Import Data from Tables (Master Data Services)
  You can add data and make data changes to a model in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], in bulk.  
  
 **Prerequisites**  
  
-   You must have permission to insert data into the stg.\<name\>\_Leaf, the stg.\<name\>\_Consolidated, stg.\<name\>\_Relationship table in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
-   You must have permissions to execute either the stg.udp\_\<name\>\_Leaf, stg.udp\_\<name\>\_Consolidated, or the stg.udp\_\<name\>\_Relationship stored procedure in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
-   The model must not have a status of **Committed**.  
  
 **To add, update, and delete data in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database**  
  
1.  Prepare the members for import into the appropriate staging table in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, including providing values for the required fields. For an overview of staging tables, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)  
  
    -   For leaf members the table is stg.\<name\>\_Leaf, where \<name\> refers to the corresponding entity. For information about the required fields, see [Leaf Member Staging Table &#40;Master Data Services&#41;](../Topic/Leaf%20Member%20Staging%20Table%20\(Master%20Data%20Services\).md)  
  
    -   For consolidated members, the table is stg.\<name\>\_Consolidated. For information about the required fields, see [Consolidated Member Staging Table &#40;Master Data Services&#41;](../Topic/Consolidated%20Member%20Staging%20Table%20\(Master%20Data%20Services\).md).  
  
    -   For moving the location of members in explicit hierarchies, the table is stg.\<name\>\_Relationship. For information about the required fields, see [Relationship Staging Table &#40;Master Data Services&#41;](../Topic/Relationship%20Staging%20Table%20\(Master%20Data%20Services\).md).  
  
         For an overview on moving members in explicit hierarchies, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md).  
  
    -   Use the **ImportType** field value to specify that you're creating new members, deactivating members, or deleting members. For more information about the values, see [Leaf Member Staging Table &#40;Master Data Services&#41;](../Topic/Leaf%20Member%20Staging%20Table%20\(Master%20Data%20Services\).md) and [Consolidated Member Staging Table &#40;Master Data Services&#41;](../Topic/Consolidated%20Member%20Staging%20Table%20\(Master%20Data%20Services\).md).  
  
         For an overview of deactivating and deleting members, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md).  
  
2.  Open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to the Database Engine instance for your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
     For more information, see [SQL Server Management Studio](../Topic/SQL%20Server%20Management%20Studio.md).  
  
3.  Import data into the staging tables by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export wizard.  
  
     For more information, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
4.  Load the data from the staging tables to the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] tables, by doing one of the following  
  
    -   Run the staging stored procedure that corresponds to the staging table that you want to move data to.  
  
         For an overview of staging stored procedures and staging tables, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md). For more information about parameters for staging stored procedures, and a code example, see [Staging Stored Procedure &#40;Master Data Services&#41;](../Topic/Staging%20Stored%20Procedure%20\(Master%20Data%20Services\).md).  
  
    -   Use the **Integration Management** functional area of Master Data Management.  
  
         On the **Staging Batches** page, select the model to which you're adding data to, in the drop\-down list, and then click **Start Batches**. The status of the batch processing is indicated in the **Status** field. For more information about the statuses, see [Import Statuses &#40;Master Data Services&#41;](../Topic/Import%20Statuses%20\(Master%20Data%20Services\).md).  
  
         ![Staging Batches Page in Master Data Manager](../../Images\Image\ImageNotContaina/mds_StagingBatchesPage.png "mds_StagingBatchesPage")  
  
         The staging process  is started at intervals determined by the **Staging batch interval** setting in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)]. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
5.  View errors that occurred during staging. For more information, see [View Errors that Occur During Staging &#40;Master Data Services&#41;](../Topic/View%20Errors%20that%20Occur%20During%20Staging%20\(Master%20Data%20Services\).md) and [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md).  
  
6.  Validate the data against business rules.  
  
     In Master Data Manager, navigate to the **Explorer** functional area for your model, and then apply business rules to validate the data. For more information , see [Validate Specific Members against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20Specific%20Members%20against%20Business%20Rules%20\(Master%20Data%20Services\).md). You can also use a stored procedure to validate the data. For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../Topic/Validation%20Stored%20Procedure%20\(Master%20Data%20Services\).md).  
  
     When you load data by from the staging tables, the data is not automatically validated against business rules. For more information on what validation is and when it occurs, see [Validation &#40;Master Data Services&#41;](../Topic/Validation%20\(Master%20Data%20Services\).md).  
  
  