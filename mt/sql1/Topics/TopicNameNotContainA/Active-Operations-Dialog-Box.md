---
title: "Active Operations Dialog Box"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Active Operations Dialog Box
Use the **Active Operations** dialog box to view the status of currently running [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] operations on the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server, such as deployment, validation, and package execution. This data is stored in the SSISDB catalog.  
  
 For more information about related [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] views, see [catalog.operations (Integration Services Catalog)](assetId:///9455c5b1-60ff-45fc-8599-cc3abbd6daf5), [catalog.validations (Integration Services Catalog)](assetId:///dbafe110-b480-48f3-b45f-31d71ca68f62), and [catalog.executions (Integration Services Catalog)](assetId:///879f13b0-331d-4dee-a079-edfaca11ae5b)  
  
 **What do you want to do?**  
  
-   [Open the Active Operations Dialog Box](../../Topics/TopicNameNotContainA/Active-Operations-Dialog-Box.md#open_dialog)  
  
-   [Configure the Options](#options)  
  
##  <a name="open_dialog"></a> Open the Active Operations Dialog Box  
  
1.  Open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)][!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
2.  Connect Microsoft SQL Server Database Engine  
  
3.  In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Active Operations**.  
  
## Configure the Options  
  
###  <a name="options"></a> Options  
 **Type**  
 Specifies the type of operation. The following are the possible values for the **Type** field and the corresponding values in the operations_type column of the Transact-SQL **catalog.operations** view.  
  
|||  
|-|-|  
|Integration Services initialization|1|  
|Operations cleanup (SQL Agent job)|2|  
|Project versions cleanup (SQL Agent job)|3|  
|Deploy project|101|  
|Restore project|106|  
|Create and start package execution|200|  
|Stop operation (stopping a validation or execution|202|  
|Validate project|300|  
|Validate package|301|  
|Configure catalog|1000|  
  
 **Stop**  
 Click to stop a currently running operation.