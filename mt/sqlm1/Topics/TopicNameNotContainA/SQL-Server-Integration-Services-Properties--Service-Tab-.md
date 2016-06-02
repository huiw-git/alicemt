---
title: SQL Server Integration Services Properties (Service Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
---
# SQL Server Integration Services Properties (Service Tab)
  Use the **Service**tab on the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] **Properties** dialog box to view or specify the following options.  
  
## Options  
 **Binary Path**  
 Displays the location of the program files used by this service.  
  
 **Error Control**  
 1 indicates `SERVICE_ERROR_NORMAL`. If the service fails to start during computer start up, the startup program logs the error and displays a pop\-up message box but continues the startup operation. This value cannot be changed.  
  
 **Exit Code**  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows error code defining any problems encountered in starting or stopping the service. This property is set to **ERROR\_SERVICE\_SPECIFIC\_ERROR** \(1066\) when the error is unique to the service represented by this class, and information about the error is available in the **ServiceSpecificExitCode** property. The service sets this value to NO\_ERROR \(0\) when running, and again upon normal termination.  
  
 **Host Name**  
 Displays the name of the computer or cluster running the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] service.  
  
 **Name**  
 Indicates the display name of the service.  
  
 **Process ID**  
 Displays the Windows process ID.  
  
 **SQL Service Type**  
 Displays the type of service provided to calling processes. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installs several services.  
  
 **Start Mode**  
 Set this service to the following choices:  
  
-   Manual: This service does not automatically start when the computer starts. You must start the service using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, or some other tool.  
  
-   Automatic: This service attempts to start when this computer starts.  
  
-   Disabled: This service cannot be started.  
  
 **State**  
 Indicates whether this service is running, stopped, or disabled. "**…**" indicates a state change is pending.  
  
  