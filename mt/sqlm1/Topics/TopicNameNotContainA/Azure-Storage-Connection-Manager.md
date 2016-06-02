---
title: Azure Storage Connection Manager
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
---
# Azure Storage Connection Manager
  The **Azure Storage connection manager** enables an SSIS package to connect to an Azure Storage account by using the values you specify for the properties: Storage Account Name and Account Key.  
  
 The **Azure Storage connection manager** is a component of the SQL Server Integration Services \(SSIS\) Feature Pack for Azure for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. Download the Feature Pack [here](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  In the **Add SSIS Connection Manager** dialog box, select **AzureStorage**, and click **Add**.  
  
2.  In the Azure Storage Connection Manager Editor dialog box, choose **Use Azure account** to connect to an Azure Storage Service via internet or choose **Use local developer account** to connect to the local service hosted by the Azure Storage Emulator.  
  
3.  If you selected **Use Azure account** option, do the following:  
  
    1.  Specify values for the **Storage account name** and **Account key** field. These values will be stored as sensitive data in SSIS package.  
  
    2.  Select **Use HTTPS** if you want to use HTTPS instead of HTTP to connect to the Azure Storage Service.  
  
4.  Click **OK** to close the dialog box.  
  
5.  You can see the properties of the connection manager you created in the **Properties** window.  
  
  