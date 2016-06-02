---
title: Importing and Exporting Knowledge
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
---
# Importing and Exporting Knowledge
  You can create knowledge bases and domains directly in the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] application, or you can import knowledge into, or export it from, a knowledge base. In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] application, you can use a data file for import and export operations, or an Excel file for import operations. The data file used is an encrypted file that is created by [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) with a .dqs extension. The files created by Microsoft Excel can have an extension of .xlsx, .xls, or .csv. These operations give you more flexibility in building and sharing the knowledge that you use to perform data cleansing and matching.  
  
> [!IMPORTANT]  
>  You can export *all* the knowledge bases in your [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] to a DQS backup file \(.dqsb\) at once by running the DQSInstaller.exe file from the command prompt. Similarly, you can import *all* the knowledge bases from a DQS backup file \(.dqsb\) to your [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] at once by running the DQSInstaller.exe file from the command prompt. For information about doing so, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../../Topics\TopicNameNotContainA/Export-and-Import-DQS-Knowledge-Bases-Using-DQSInstaller.exe.md) in the DQS installation guide.  
  
## In This Section  
 You can perform the following import and export operations:  
  
|||  
|-|-|  
|Export a domain in a knowledge base to a .dqs data file|[Export a Domain to a .dqs File](../../Topics\TopicNameContainA/Export-a-Domain-to-a-.dqs-File.md)|  
|Import a domain from a .dqs data file into an existing knowledge base|[Import a Domain from a .dqs File](../../Topics\TopicNameContainA/Import-a-Domain-from-a-.dqs-File.md)|  
|Export an entire knowledge base to a .dqs data file|[Export a Knowledge Base to a .dqs File](../../Topics\TopicNameContainA/Export-a-Knowledge-Base-to-a-.dqs-File.md)|  
|Import an entire knowledge base to a .dqs data file|[Import a Knowledge Base from a .dqs File](../../Topics\TopicNameContainA/Import-a-Knowledge-Base-from-a-.dqs-File.md)|  
|Import values from an Excel file into a domain|[Import Values from an Excel File into a Domain](../../Topics\TopicNameContainA/Import-Values-from-an-Excel-File-into-a-Domain.md)|  
|Import domains from an Excel file into a knowledge base|[Import Domains from an Excel File in Knowledge Discovery](../../Topics\TopicNameNotContainA/Import-Domains-from-an-Excel-File-in-Knowledge-Discovery.md)|  
|Import knowledge gathered during cleansing into a knowledge base|[Import Cleansing Project Values into a Domain](../../Topics\TopicNameContainA/Import-Cleansing-Project-Values-into-a-Domain.md)|  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Building a knowledge base by running knowledge discovery and interactively managing knowledge|[Building a Knowledge Base](../../Topics\TopicNameContainA/Building-a-Knowledge-Base.md)|  
|Creating a single domain, and adding knowledge to the domain.|[Managing a Domain](../../Topics\TopicNameContainA/Managing-a-Domain.md)|  
|Creating a composite domain, and adding knowledge to the domain.|[Managing a Composite Domain](../../Topics\TopicNameContainA/Managing-a-Composite-Domain.md)|  
  
  