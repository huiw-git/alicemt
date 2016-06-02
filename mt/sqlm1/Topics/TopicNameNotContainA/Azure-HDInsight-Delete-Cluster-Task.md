---
title: Azure HDInsight Delete Cluster Task
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
---
# Azure HDInsight Delete Cluster Task
  The **Azure HDInsight Delete Cluster Task** enables an SSIS package to delete an Azure HDInsight cluster in the specified Azure subscription.  
  
 The **Azure HDInsight Delete Cluster Task** is a component of the SQL Server Integration Services \(SSIS\) Feature Pack for Azure for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. Download the Feature Pack [here](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  Deleting an HDInsight cluster usually takes 10 minutes.  
  
 To add an **Azure HDInsight Delete Cluster Task**, drag\-drop it to the SSIS Designer, and double\-click or right\-click and click **Edit** to see the following **Azure HDInsight Delete Cluster Task Editor** dialog box.  
  
 The following table provides description of fields in the dialog box.  
  
|||  
|-|-|  
|**Field**|**Description**|  
|AzureSubscriptionConnection|Select an existing Azure Subscription Connection Manager or create a new one that refers to an Azure subscription that hosts the HDInsight cluster.|  
|ClusterName|Specify the name of the cluster to be deleted.|  
|FailIfNotExists|Specify whether the task should fail if the cluster does not exist.|  
  
  