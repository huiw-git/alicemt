---
title: Monitoring for Package Executions and Other Operations
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
---
# Monitoring for Package Executions and Other Operations
  You can monitor [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package executions, project validations, and other operations by using one of more of the following tools. Certain tools such as data taps are available only for projects that are deployed to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server.  
  
-   Logs  
  
     For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md).  
  
-   Reports  
  
     For more information, see [Reports for the Integration Services Server](../../Topics\TopicNameNotContainA/Reports-for-the-Integration-Services-Server.md).  
  
-   Views  
  
     For more information, see [Views &#40;Integration Services Catalog&#41;](../Topic/Views%20\(Integration%20Services%20Catalog\).md).  
  
-   Performance counters  
  
     For more information, see [Performance Counters](../../Topics\TopicNameNotContainA/Performance-Counters.md).  
  
-   Data taps  
  
## Operation Types  
 Several different types of operations are monitored in the **SSISDB** catalog, on the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server. Each operation can have multiple messages associated with it. Each message can be classified into one of several different types. For example, a message can be of type Information, Warning, or Error. For the full list of message types, see the documentation for the Transact\-SQL [catalog.operation_messages &#40;SSISDB Database&#41;](../Topic/catalog.operation_messages%20\(SSISDB%20Database\).md) view. For a full list of the operations types, see [catalog.operations &#40;SSISDB Database&#41;](../Topic/catalog.operations%20\(SSISDB%20Database\).md).  
  
 Nine different status types are used to indicate the status of an operation. For a full list of the status types, see the [catalog.operations &#40;SSISDB Database&#41;](../Topic/catalog.operations%20\(SSISDB%20Database\).md) view.  
  
## Related Content  
 Blog entry, [SSIS T\-SQL API Overview](http://go.microsoft.com/fwlink/?LinkId=249051), on blogs.msdn.com.  
  
  