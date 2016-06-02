---
title: SQL Full-text Filter Daemon Launcher (Service Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
---
# SQL Full-text Filter Daemon Launcher (Service Tab)
  Beginning in [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], the SQL Full\-text Filter Daemon Launcher \(FDHOST Launcher\) service is used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] full\-text. This service must be running if you use full\-text search. For information about the filter daemon host processes, see "Full\-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 Use the **Service**tab on the **SQL Full\-text Filter Daemon LauncherProperties** dialog box to view or specify the following options.  
  
## Options  
 **Binary Path**  
 Lists the location of the program files used by this service.  
  
 **Error Control**  
 1 indicates `SERVICE_ERROR_NORMAL`. If the service fails to start during computer start up, the startup program logs the error and displays a pop\-up message box but continues the startup operation. This value cannot be changed.  
  
 **Exit Code**  
 When an error occurs, the error number appears in this box. Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Knowledge Base or provide the number to your technical support staff.  
  
 **Host Name**  
 Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service.  
  
 **Name**  
 Indicates the display name of the service.  
  
 **Process ID**  
 Displays the Windows process ID.  
  
 **SQL Service Type**  
 Displays the type of service provided to calling processes. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installs several services.  
  
 **Start Mode**  
 Set this service to the following choices:  
  
-   Manual: This service does not automatically start when the computer starts. You must start the service using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, or some other tool.  
  
-   Automatic: This service attempts to start when this computer starts.  
  
-   Disabled: This service cannot be started.  
  
 **State**  
 Indicates whether this service is running, stopped, or disabled. "**…**" indicates a state change is pending.  
  
  