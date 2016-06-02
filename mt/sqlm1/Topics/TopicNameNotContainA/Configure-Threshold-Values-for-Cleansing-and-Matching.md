---
title: Configure Threshold Values for Cleansing and Matching
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
---
# Configure Threshold Values for Cleansing and Matching
  This topic describes how to configure threshold values that will be used during the computer\-assisted cleansing and matching activities in [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have the dqs\_administrator role on the DQS\_MAIN database to configure these threshold values.  
  
##  <a name="Configure"></a> Configuring the Threshold Values  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **Configuration**.  
  
3.  Next, click the **General Settings** tab. This tab enables you to specify threshold values for cleansing as well as matching activities.  
  
4.  To specify threshold values for the cleansing activity, specify appropriate values in the following boxes under the **Interactive Cleansing** area:  
  
    -   **Min score for suggestions**: The minimum score or the confidence level that will be used by DQS for suggesting replacements for a value during the computer\-assisted cleansing process. Enter a value in the decimal notation of the corresponding percentage value. For example, type 0.75 for 75%. This value should be less than or equal to the value specified in the **Min score for auto corrections** box. The default value is 0.7.  
  
    -   **Min score for auto corrections**: The minimum score or the confidence level that will be used by DQS for automatically correcting a value during the computer\-assisted cleansing process. Enter a value in the decimal notation of the corresponding percentage value. For example, enter 0.9 for 90%. The default value is 0.8.  
  
5.  To specify threshold value for the matching activity, specify a value in the **Min record score** box under the **Matching** area. This value signifies the minimum score for a record to be considered as a match for another record. The default value is 80%.  
  
6.  Click **Close**.  
  
  