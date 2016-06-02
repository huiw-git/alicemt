---
title: Azure HDInsight Pig Task
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
---
# Azure HDInsight Pig Task
  Use the **Azure HDInsight Pig Task** to run Pig script on an Azure HDInsight cluster.   
To add an **Azure HDInsight Pig Task**, drag\-drop it to the SSIS Designer, and double\-click or right\-click and click **Edit** to see the following **Azure HDInsight Pig Task Editor** dialog box.  
  
 The **Azure HDInsight Pig Task** is a component of the SQL Server Integration Services \(SSIS\) Feature Pack for Azure for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. Download the Feature Pack [here](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  For the **AzureSubscriptionConnection** field, select an existing Azure Subscription Connection Manager or create a new one that refers to an Azure subscription that hosts the HDInsight cluster.  
  
2.  For the **HDInsightClusterName** field, input the name of HDInsight cluster on which you want to run the Pig script.  
  
3.  For the **LocalLogFolder** field, click **… \(ellipsis\)**, select the folder to which you want to download Pig processing logs from the HDInsight cluster.  
  
4.  There are two ways to specify the Pig script:  
  
    1.  **In\-line script**: click **… \(ellipsis\)** next to the **Script** field, and type in\-line script in the **Enter Script** dialog box.  
  
    2.  **Script file**: upload the script file to a blob location and specify its **BlobName**. If the blob is not in the default storage or container of the HDInsight cluster, **ExternalStorageAccountName** and **ExternalBlobContainer** must be specified. For external blob, make sure that it is configured as public accessible.  
  
     If both are specified, script file will be used and in\-line script will be ignored.  
  
  