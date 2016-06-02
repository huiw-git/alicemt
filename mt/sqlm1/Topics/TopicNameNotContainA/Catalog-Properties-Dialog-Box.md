---
title: Catalog Properties Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
---
# Catalog Properties Dialog Box
  Use the Catalog Properties dialog box to configure the SSISDB catalog. Catalog properties define how sensitive data is encrypted, how operations and project versioning data is retained, and when validation operations time out. The SSISDB catalog is a central storage and administration point for [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] projects, packages, parameters, and environments.  
  
 You can also view catalog properties in the catalog.catalog\_property view, and set the properties by using the catalog.configure\_catalog stored procedure. For more information, see [catalog.catalog_properties &#40;SSISDB Database&#41;](../Topic/catalog.catalog_properties%20\(SSISDB%20Database\).md) and [catalog.configure_catalog &#40;SSISDB Database&#41;](../Topic/catalog.configure_catalog%20\(SSISDB%20Database\).md).  
  
 For information on how to create the SSISDB catalog, see [Create the SSIS Catalog](../../Topics\TopicNameNotContainA/Create-the-SSIS-Catalog.md).  
  
 **What do you want to do?**  
  
-   [Open the Catalog Properties Dialog Box](#open_dialog)  
  
-   [Configure the Options](#options)  
  
##  <a name="open_dialog"></a> Open the Catalog Properties Dialog Box  
  
1.  Open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)].  
  
2.  Connect Microsoft SQL Server Database Engine.  
  
3.  In Object Explorer, expand the **Integration Services** node, right\-click **SSISDB**, and then click **Properties**.  
  
##  <a name="options"></a> Configure the Options  
  
### Options  
 The following table describes certain properties in the dialog box and the corresponding properties in the catalog.catalog\_property view.  
  
|Property Name \(Catalog Properties dialog box\)|Property Name \(catalog.catalog\_property view\)|Description|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Encryption Algorithm Name|ENCRYPTION\_CLEANUP\_ENABLED|Specifies the type of encryption that is used to encrypt the sensitive parameter values in the catalog. The following are the possible values:<br /><br /> DES<br /><br /> TRIPLE\_DES<br /><br /> TRIPLE\_DES\_3KEY<br /><br /> DESPX<br /><br /> AES\_128<br /><br /> AES\_192<br /><br /> AES\_256 \(default\)|  
|Validation Timeout \(seconds\)|VALIDATION\_TIMEOUT|Specify the maxium number of seconds a project validation or a package validation can run before it is stopped. The default value is 300 seconds.<br /><br /> Performing the validation is an asynchronous operation. The larger the project or package is, the longer it will take to validate.<br /><br /> For information on validating projects and packages, see [Integration Services Data Types in Expressions](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).|  
|Clean Logs Periodically|OPERATION\_CLEANUP\_ENABLED|Set the property to True to indicate that the SQL Server Agent job, operations cleanup, runs. Otherwise, set the property to False.|  
|Retention Period \(days\)|RETENTION\_WINDOW|Specify the maximum age of allowable operations data \(in days\). Data that is older than the specified number of days will be removed by the SQL Agent job, operations cleanup.|  
|Maximum Number of Versions per Project|MAX\_PROJECT\_VERSIONS|Specify how many versions of a project will be stored in the catalog. Older versions of projects that exceed the maximum will be removed when the project version cleanup job runs.|  
  
  