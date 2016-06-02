---
title: rsModelGenerationError - Reporting Services Error
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
---
# rsModelGenerationError - Reporting Services Error
    
## Details  
  
|||  
|-|-|  
|Product Name|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|  
|Event ID|rsRenderingError|  
|Event Source|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Component|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]|  
|Message Text|An error occurred while generating model. \(rsModelGenerationError\) \(ReportingServicesLibrary\) %1|  
  
## Explanation  
 The report model could not be generated. In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]2005 SP1 and earlier versions, this error is most likely displayed when the System.Data.DataSet object cannot handle a table or relationship within the database schema, such as when, for example, two foreign keys are defined on the same column within a table.  
  
## User Action  
 To determine the specific reason that caused this message to appear, review the report server log files, which are located at \\Microsoft SQL Server\\\<SQL Server Instance\>\\Reporting Services\\LogFiles.  
  
## Internal\-Only  
  