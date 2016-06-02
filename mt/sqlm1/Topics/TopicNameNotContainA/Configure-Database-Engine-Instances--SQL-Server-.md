---
title: Configure Database Engine Instances (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
---
# Configure Database Engine Instances (SQL Server)
  Each instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] must be configured to meet the performance and availability requirements defined for the databases hosted by the instance. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] includes configuration options that control behaviors such as resource usage and the availability of features such as auditing or trigger recursion.  
  
## Instance Configuration  
 When a database is deployed into production there is often a service level agreement \(SLA\) defining areas such as the levels of performance required from the database and the required availability level of the database. The terms of the SLA typically drive configuration requirements for the instance.  
  
 An instance is usually configured immediately after it has been installed. The initial configuration is usually determined by the SLA requirements of the types of databases planned to be deployed to the instance. After the databases have been deployed, the database administrators monitor the performance of the instance and adjust the configuration settings as needed if the performance metrics show the instance is not meeting the SLA requirements.  
  
## Configuration Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes the various instance configuration options and how to view or change these options.|[Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)|  
|Describes how to view and configure the default locations of new data and log files in the instance.|[View or Change the Default Locations for Data and Log Files &#40;SQL Server Management Studio&#41;](../Topic/View%20or%20Change%20the%20Default%20Locations%20for%20Data%20and%20Log%20Files%20\(SQL%20Server%20Management%20Studio\).md)|  
|Describes how to configure SQL Server to use soft\-NUMA.|[Soft-NUMA &#40;SQL Server&#41;](../Topic/Soft-NUMA%20\(SQL%20Server\).md)|  
|Describes how to map a TCP\/IP port to non\-uniform memory access \(NUMA\) node affinity.|[Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;](../Topic/Map%20TCP%20IP%20Ports%20to%20NUMA%20Nodes%20\(SQL%20Server\).md)|  
|Describes how to enable the Windows Lock Pages In Memory policy. This policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.|[Enable the Lock Pages in Memory Option &#40;Windows&#41;](../Topic/Enable%20the%20Lock%20Pages%20in%20Memory%20Option%20\(Windows\).md)|  
  
## See Also  
 [Database Engine Instances &#40;SQL Server&#41;](../Topic/Database%20Engine%20Instances%20\(SQL%20Server\).md)  
  
  