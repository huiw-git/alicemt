---
title: Create a Data Quality Project
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
---
# Create a Data Quality Project
  This topic describes how to create a data quality project by using [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]. A data quality project is used to run the cleansing or matching activity in [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 You must have a relevant knowledge base to use in the data quality project for the cleansing or matching activity.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have the dqs\_kb\_editor or dqs\_kb\_operator role on the DQS\_MAIN database to create a data quality project.  
  
##  <a name="Create"></a> Create a Data Quality Project  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **New data quality project**.  
  
3.  In the **New Data Quality Project** screen:  
  
    1.  In the **Name** box, type a name for the new data quality project.  
  
    2.  \(Optional\) In the **Description** box, type a description for the new data quality project.  
  
    3.  In the **Use Knowledge base** list, click to select a knowledge base to be used for the data quality project. The **Knowledge base details: \<Knowledge\_Base\_Name\>** area on the right side displays the domain names available in the selected knowledge base.  
  
    4.  In the **Select Activity** area, click on an activity that you want to perform using this data quality project:  
  
        -   **Cleansing**: Select this activity to cleanse the source data.  
  
        -   **Matching**: Select this activity to perform matching. This activity is available only if the knowledge base selected for the data quality project contains a matching policy.  
  
4.  Click **Create** to create a data quality project.  
  
##  <a name="FollowUp"></a> Follow Up: After Creating a Data Quality Project  
 After you create a data quality project, you are presented with a wizard that you use to perform the selected activity: cleansing or matching. For more information about the cleansing and matching activities, see [Data Cleansing](../../Topics\TopicNameNotContainA/Data-Cleansing.md) and [Data Matching](../../Topics\TopicNameNotContainA/Data-Matching.md).  
  
  