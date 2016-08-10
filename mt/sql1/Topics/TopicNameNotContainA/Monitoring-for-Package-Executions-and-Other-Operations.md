---
title: "Monitoring for Package Executions and Other Operations"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# Monitoring for Package Executions and Other Operations
You can monitor [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package executions, project validations, and other operations by using one of more of the following tools. Certain tools such as data taps are available only for projects that are deployed to the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server.  
  
-   Logs  
  
     For more information, see [Integration Services (SSIS) Logging](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Logging.md).  
  
-   Reports  
  
     For more information, see [Reports for the Integration Services Server](../../Topics/TopicNameNotContainA/Reports-for-the-Integration-Services-Server.md).  
  
-   Views  
  
     For more information, see [Views (Integration Services Catalog)](assetId:///d0294d43-4852-46dc-9afa-d0c19ea9aa03).  
  
-   Performance counters  
  
     For more information, see [Performance Counters](../../Topics/TopicNameNotContainA/Performance-Counters.md).  
  
-   Data taps  
  
## Operation Types  
 Several different types of operations are monitored in the **SSISDB** catalog, on the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server. Each operation can have multiple messages associated with it. Each message can be classified into one of several different types. For example, a message can be of type Information, Warning, or Error. For the full list of message types, see the documentation for the Transact-SQL [catalog.operation_messages (SSISDB Database)](assetId:///0b3cbe38-ce24-47ca-83ef-6538a5299d1a) view. For a full list of the operations types, see [catalog.operations (SSISDB Database)](assetId:///9455c5b1-60ff-45fc-8599-cc3abbd6daf5).  
  
 Nine different status types are used to indicate the status of an operation. For a full list of the status types, see the [catalog.operations (SSISDB Database)](assetId:///9455c5b1-60ff-45fc-8599-cc3abbd6daf5) view.  
  
## Related Content  
 Blog entry, [SSIS T-SQL API Overview](http://go.microsoft.com/fwlink/?LinkId=249051), on blogs.msdn.com.