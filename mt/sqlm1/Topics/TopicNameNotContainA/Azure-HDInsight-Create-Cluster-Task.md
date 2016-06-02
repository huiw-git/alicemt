---
title: Azure HDInsight Create Cluster Task
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
---
# Azure HDInsight Create Cluster Task
  The **Azure HDInsight Create Cluster Task** enables an SSIS package to create an Azure HDInsight cluster in the specified Azure subscription.  
  
 The **Azure HDInsight Create Cluster Task** is a component of the SQL Server Integration Services \(SSIS\) Feature Pack for Azure for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. Download the Feature Pack [here](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  -   Creating a new HDInsight cluster usually takes 10 minutes.  
> -   There is a cost associated with creation and running of an Azure HDInsight cluster. See [HDInsight Pricing](http://azure.microsoft.com/en-us/pricing/details/hdinsight/) topic for details.  
  
 To add an **Azure HDInsight Create Cluster Task**, drag\-drop it to the SSIS Designer, and double\-click or right\-click and click **Edit** to see the following **Azure HDInsight Create Cluster Task Editor** dialog box.  
  
 The following table provides description of fields in this dialog box.  
  
|||  
|-|-|  
|**Field**|**Description**|  
|AzureSubscriptionConnection|Select an existing Azure Subscription Connection Manager or create a new one that refers to an Azure subscription that hosts the HDInsight cluster.|  
|AzureStorageConnection|Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account that will be associated with the HDInsight cluster.|  
|Location|Specify the location of the HDInsight cluster. The cluster must be created in the same location as the Azure Storage..|  
|ClusterName|Specify a name for the HDInsight cluster to be created.|  
|ClusterSize|Specify the number of nodes you want to be in the cluster.|  
|BlobContainer|Specify the name of the default storage container associated with the HDInsight cluster.|  
|UserName|Specify the name of the user who has access to the cluster.|  
|Password|Specify the password for the user.|  
|FailIfExists|Specify whether the task should fail if the cluster already exists.|  
  
> [!NOTE]  
>  The location of the HDInsight cluster and the Azure Storage must be the same.  
  
  