---
title: Import a Domain from a .dqs File
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
---
# Import a Domain from a .dqs File
  This topic describes how to import a domain from a .dqs file into an existing knowledge base in [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\). A .dqs data file is created by exporting a domain or knowledge base from the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] application. A .dqs data file is encrypted, so cannot be viewed.  
  
 Using a .dqs data file to export a domain from one knowledge base and then import it to another knowledge base simplifies the knowledge generation process, saving time and effort. It enables you to share a domain and its knowledge with others, saving them time. You can import either one single domain or one composite domain \(containing multiple single domains\). A .dqs file containing a single domain includes all domain data including domain properties, values, and rules data, except for the mapped reference data information. A .dqs file containing a composite domain includes all composite domain data, including all domain data for the singles domains that are contained within the composite domain, and the composite domain properties, value relations, and CD rules, except for the mapped reference data. Published and unpublished data will be imported.  
  
 When you import a domain, the name of the domain remains the same as the name of the domain that was originally exported, unless the domain name already exists, in which case DQS will append “\_1” to the name. This is also true if you import a composite domain that contains an individual domain with the same name as an existing domain.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 To import a domain from a .dqs file, you must have already exported one single domain or one composite domain \(containing multiple single domains\) into the .dqs file. The .dqs file must only contain one domain. You must also have created and opened a knowledge base to import the domain into.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have the dqs\_kb\_editor or the dqs\_administrator role on the DQS\_MAIN database to import a domain from a .dqs data file.  
  
##  <a name="Import"></a> Import a domain from a .dqs file  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, open a knowledge base in the Domain Management activity.  
  
3.  Click the **Import Domain from data file** icon.  
  
4.  In the **Import from Data File** dialog box, move to the folder that you want to import the file from, select the file \(of type DQS File\), and then click **Open**.  
  
5.  In the **Import Domain** dialog box, click **OK**.  
  
    > [!NOTE]  
    >  The import operation will succeed only if the .dqs file that you are importing from contains only one single domain or one composite domain \(containing multiple single domains\).  
  
6.  Verify that the domain that you imported is displayed in the **Domain** list. If you imported a composite domain, verify that the composite domain and the single domains contained in it are all in the **Domain** list.  
  
##  <a name="FollowUp"></a> Follow Up: After Importing a Domain from a .dqs File  
 After you import a domain from a .dqs file, you can add knowledge to the domain or use the domain in a cleansing or matching project, depending on the contents of the domain. For more information, see [Perform Knowledge Discovery](../../Topics\TopicNameNotContainA/Perform-Knowledge-Discovery.md), [Managing a Domain](../../Topics\TopicNameContainA/Managing-a-Domain.md), [Managing a Composite Domain](../../Topics\TopicNameContainA/Managing-a-Composite-Domain.md), [Create a Matching Policy](../../Topics\TopicNameContainA/Create-a-Matching-Policy.md), [Data Cleansing](../../Topics\TopicNameNotContainA/Data-Cleansing.md), or [Data Matching](../../Topics\TopicNameNotContainA/Data-Matching.md).  
  
  