---
title: "Catalog Properties Dialog Box"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Catalog Properties Dialog Box
Use the Catalog Properties dialog box to configure the SSISDB catalog. Catalog properties define how sensitive data is encrypted, how operations and project versioning data is retained, and when validation operations time out. The SSISDB catalog is a central storage and administration point for [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] projects, packages, parameters, and environments.  
  
 You can also view catalog properties in the catalog.catalog_property view, and set the properties by using the catalog.configure_catalog stored procedure. For more information, see [catalog.catalog_property](assetId:///e604a382-95c8-4764-b268-742eb5c6d4cf) and [catalog.configure_catalog](assetId:///72690c61-f462-4c25-9fce-08a687b0bd41).  
  
 For information on how to create the SSISDB catalog, see [Create the SSIS Catalog](../../Topics/TopicNameNotContainA/Create-the-SSIS-Catalog.md).  
  
 **What do you want to do?**  
  
-   [Open the Catalog Properties dialog box.](#open_dialog)  
  
-   [Configure the Options](#options)  
  
##  <a name="open_dialog"></a> Open the Catalog Properties Dialog Box  
  
1.  Open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)][!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
2.  Connect Microsoft SQL Server Database Engine.  
  
3.  In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Properties**.  
  
##  <a name="options"></a> Configure the Options  
  
### Options  
 The following table describes certain properties in the dialog box and the corresponding properties in the catalog.catalog_property view.  
  
|Property Name (Catalog Properties dialog box)|Property Name (catalog.catalog_property view)|Description|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Encryption Algorithm Name|ENCRYPTION_CLEANUP_ENABLED|Specifies the type of encryption that is used to encrypt the sensitive parameter values in the catalog. The following are the possible values:<br /><br /> DES<br /><br /> TRIPLE_DES<br /><br /> TRIPLE_DES_3KEY<br /><br /> DESPX<br /><br /> AES_128<br /><br /> AES_192<br /><br /> AES_256 (default)|  
|Validation Timeout (seconds)|VALIDATION_TIMEOUT|Specify the maxium number of seconds a project validation or a package validation can run before it is stopped. The default value is 300 seconds.<br /><br /> Performing the validation is an asynchronous operation. The larger the project or package is, the longer it will take to validate.<br /><br /> For information on validating projects and packages, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).|  
|Clean Logs Periodically|OPERATION_CLEANUP_ENABLED|Set the property to True to indicate that the SQL Server Agent job, operations cleanup, runs. Otherwise, set the property to False.|  
|Retention Period (days)|RETENTION_WINDOW|Specify the maximum age of allowable operations data (in days). Data that is older than the specified number of days will be removed by the SQL Agent job, operations cleanup.|  
|Maximum Number of Versions per Project|MAX_PROJECT_VERSIONS|Specify how many versions of a project will be stored in the catalog. Older versions of projects that exceed the maximum will be removed when the project version cleanup job runs.|