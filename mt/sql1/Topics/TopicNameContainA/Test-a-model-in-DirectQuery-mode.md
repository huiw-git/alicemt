---
title: "Test a model in DirectQuery mode"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: 12
---
# Test a model in DirectQuery mode
Review your options for testing a DirectQuery model at each stage of development, starting with design.  
  
## Excel or client applications  
 Excel uses MDX to retrieve data from an  Analysis Services database In previous releases, DirectQuery models didn't accept MDX queries from Excel, but in SQL Server 2016, you can use Excel to connect to Tabular models in DirectQuery mode, if the model is at compatibility level 1200.  
  
 **Analyze in Excel** is a toolbar option in SQL Server Data Tools (SSDT) that opens the current model in a local desktop application of Excel, connected to the local workspace database. When you add sample data to a Tabular model, that data is available for testing in Excel. See [Add  sample data to a DirectQuery model in Design Mode](../../Topics/TopicNameContainA/Add--sample-data-to-a-DirectQuery-model-in-Design-Mode.md).  
  
## SQL Profiler or xEvents to monitor query execution on backend systems  
 Start up a session trace, connected to the SQL Server relational database, to monitor connections coming from the Tabular model:  
  
-   [Monitor Analysis Services with SQL Server Extended Events](../../Topics/TopicNameNotContainA/Monitor-Analysis-Services-with-SQL-Server-Extended-Events.md)  
  
-   [Use SQL Server Profiler to Monitor Analysis Services](../../Topics/TopicNameNotContainA/Use-SQL-Server-Profiler-to-Monitor-Analysis-Services.md)  
  
 If you are using Oracle or Teradata, use the trace monitoring tools for those systems.