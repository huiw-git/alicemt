---
title: Copy a Policy-Based Management Facet State to an XML File
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
---
# Copy a Policy-Based Management Facet State to an XML File
  This topic describes how to how to copy the state of a Policy\-Based Management facet to an XML file in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To copy a facet state to an XML file, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To copy a facet state to an XML file  
  
1.  In Object Explorer, right\-click an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], instance object, database, or database object, and then click **Facets**.  
  
2.  In the **View Facets –***object\_name* dialog box, click **Export Current State as Policy**.  
  
3.  In the **Export as Policy** dialog box, type the path and name of the file; or use the Browse \(**...**\) button to locate the file, and then type the name of the XML file. For more information on the available options in this dialog box, see [Export As Policy Dialog Box](../../Topics\TopicNameNotContainA/Export-As-Policy-Dialog-Box.md)  
  
4.  When finished, click **OK**.  
  
  