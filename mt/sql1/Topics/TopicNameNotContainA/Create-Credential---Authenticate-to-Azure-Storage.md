---
title: Create Credential - Authenticate to Azure Storage
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
---
# Create Credential - Authenticate to Azure Storage
  Use the **Backup to URL – Create Credential** dialog box to create a new SQL Credential.  
  
 When using this dialog box to create a credential, you must provide a Windows Azure Management Certificate added to the local certificate store or a publishing profile downloaded to your computer to validate the subscription and the storage account information.  
  
 **SQL Credential**  
 Specify the name of the SQL Credential you want to create.  
  
## Windows Azure Credentials  
 **Management Certificate**  
 Use this option to specify a certificate from the local certificate store that matches the management certificate from Windows Azure. For more information on Windows Azure management certificate, see [Create and Upload a Management Certificate for Windows Azure](http://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Subscription**  
 Select, type, or paste your Windows Azure subscription ID that matches the management certificate from the local certificate store.  
  
 **Publishing Profile**  
 Use this option if you have a publishing profile downloaded to your computer. If you use this option, the subscription ID, and the certificate are auto populated.  
  
> [!CAUTION]  
>  SQL Server currently supports publishing profile version 2.0. To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
  
## Storage Account  
 Select the storage account you want to use to store the backup files on.  
  
  