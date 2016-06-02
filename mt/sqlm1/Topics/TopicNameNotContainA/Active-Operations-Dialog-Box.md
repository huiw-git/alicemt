---
title: Active Operations Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
---
# Active Operations Dialog Box
  Use the **Active Operations** dialog box to view the status of currently running [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] operations on the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server, such as deployment, validation, and package execution. This data is stored in the SSISDB catalog.  
  
 For more information about related [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] views, see [catalog.operations &#40;SSISDB Database&#41;](../Topic/catalog.operations%20\(SSISDB%20Database\).md), [catalog.validations &#40;SSISDB Database&#41;](../Topic/catalog.validations%20\(SSISDB%20Database\).md), and [catalog.executions &#40;SSISDB Database&#41;](../Topic/catalog.executions%20\(SSISDB%20Database\).md)  
  
 **What do you want to do?**  
  
-   [Open the Active Operations Dialog Box](../../Topics\TopicNameNotContainA/Active-Operations-Dialog-Box.md)  
  
-   [Options](#options)  
  
##  <a name="open_dialog"></a> Open the Active Operations Dialog Box  
  
1.  Open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)].  
  
2.  Connect Microsoft SQL Server Database Engine  
  
3.  In Object Explorer, expand the **Integration Services** node, right\-click **SSISDB**, and then click **Active Operations**.  
  
## Configure the Options  
  
###  <a name="options"></a> Options  
 **Type**  
 Specifies the type of operation. The following are the possible values for the **Type** field and the corresponding values in the operations\_type column of the Transact\-SQL **catalog.operations** view.  
  
|||  
|-|-|  
|Integration Services initialization|1|  
|Operations cleanup \(SQL Agent job\)|2|  
|Project versions cleanup \(SQL Agent job\)|3|  
|Deploy project|101|  
|Restore project|106|  
|Create and start package execution|200|  
|Stop operation \(stopping a validation or execution|202|  
|Validate project|300|  
|Validate package|301|  
|Configure catalog|1000|  
  
 **Stop**  
 Click to stop a currently running operation.  
  
  