---
title: Open Integration Services Projects in Data Quality Client
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
---
# Open Integration Services Projects in Data Quality Client
  The [!INCLUDE[ssDQSCleansingLong](../../Token\Other/ssDQSCleansingLong_md.md)] enables you to run a cleansing project in batch mode. However, at times you might want to review the cleansing results in an Integration Services package similar to how you can review the cleansing results in the **Manage and View Results** tab of a cleansing activity in a data quality project in DQS. DQS enables you to open Integration Services projects in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] just like any other data quality project from the **Open project** screen, and have an interactive cleansing experience of the cleansing results in an Integration Services project.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="LimitationsRestrictions"></a> Limitations and Restrictions  
  
-   Only completed Integration Services projects are available in the **Open project** screen in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]. Failed or running projects are not available in the **Open project** screen.  
  
-   Integration Services projects open at the interactive cleansing stage \(**Manage View and Results** tab\) in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]. You cannot go to the **Cleanse** or **Map** tabs. You can only go to the **Export** tab by clicking **Next**.  
  
-   You cannot delete a locked Integration Services project from [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]. You must first unlock it to delete.  
  
###  <a name="Prerequisites"></a> Prerequisites  
 You must have successfully completed running an Integration Services project containing a package with a DQS Cleansing component to see and open it in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)].  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have the dqs\_kb\_editor or dqs\_kb\_operator role on the DQS\_MAIN database to open an Integration Services project.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In This Topic](#Intro)  
  
##  <a name="Open"></a> Open an Integration Services Project  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **Open Data Quality Project**. The **Open project** screen appears.  
  
3.  In the **Open project** screen, you can identify an Integration Services project in either of the following ways:  
  
    1.  **Project Name**: Integration Services projects are listed using the following naming terminology: “Package.DQS Cleansing\_*\<DATE\>**\<TIME\>*\_{GUID}.” Every time you successfully run the same package in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], a new project is listed in the **Open project** screen.  
  
    2.  **Project Type**: Integration Services projects have **SSIS** as the project type in the **Open project** screen.  
  
     Select a project, and click **Next**.  
  
4.  The Integration Services project opens at the interactive cleansing stage \(**Manage View and Results** tab\). You can perform an interactive cleansing on the data in the Integration Services project. For detailed information about the **Manage and View Results** tab, see [Interactive Cleansing Stage](../Topic/Cleanse%20Data%20Using%20DQS%20\(Internal\)%20Knowledge.md#Interactive) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../Topic/Cleanse%20Data%20Using%20DQS%20\(Internal\)%20Knowledge.md).  
  
5.  Click **Next** to go to the **Export** tab where you can export the processed data to any of the following: a new table in the SQL Server database, a .csv file, or an Excel file. For detailed information about the **Export** tab, see [Export Stage](../Topic/Cleanse%20Data%20Using%20DQS%20\(Internal\)%20Knowledge.md#Export) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../Topic/Cleanse%20Data%20Using%20DQS%20\(Internal\)%20Knowledge.md)  
  
6.  After exporting the data, click **Finish** to close the Integration Services project.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In This Topic](#Intro)  
  
## See Also  
 [DQS Cleansing Transformation](../../Topics\TopicNameNotContainA/DQS-Cleansing-Transformation.md)   
 [Integration Services &#40;SSIS&#41; Projects](../Topic/Integration%20Services%20\(SSIS\)%20Projects.md)  
  
  