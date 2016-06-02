---
title: Azure Blob Destination
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
---
# Azure Blob Destination
  The **Azure Blob Destination** component enables an SSIS package to write data to an Azure blob. The supported file formats are: CSV and AVRO. Ddrag\-drop **Azure Blob Destination** to the data flow designer and double\-click it to see the editor\).  
  
 The **Azure Blob Destination** is a component of the SQL Server Integration Services \(SSIS\) Feature Pack for Azure for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. Download the Feature Pack [here](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.  
  
2.  For the **Blob container name** field, specify the name of the blob container that contains source files.  
  
3.  For the **Blob name** field, specify the path for the blob.  
  
4.  For the **Blob file format** field, specify the blob format you want to use.  
  
5.  If the file format is CSV, you must specify the **Column delimiter character** value. Also  select **Column names in the first data row** if the first row in the file contains column names.  
  
6.  After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.  
  
  