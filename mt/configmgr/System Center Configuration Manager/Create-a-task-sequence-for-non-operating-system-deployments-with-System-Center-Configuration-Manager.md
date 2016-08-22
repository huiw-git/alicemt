---
title: "Create a task sequence for non-operating system deployments with System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
caps.latest.revision: 6
---
# Create a task sequence for non-operating system deployments with System Center Configuration Manager
Task sequences in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] are used to automate a variety of tasks within your environment. These tasks are primarily designed and tested for deploying operating systems.  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] has many other features that should be the primary technology that you use for scenarios such as [application installation](http://technet.microsoft.com/library/mt627959\(TechNet.10\).aspx), [software updates installation](http://technet.microsoft.com/library/mt634340\(TechNet.10\).aspx), [setting configuration](http://technet.microsoft.com/library/mt629310\(TechNet.10\).aspx), or custom automation. There are other Microsoft System Center automation technologies, such as [Orchestrator](https://technet.microsoft.com/library/hh237242.aspx) and [Service Management Automation](https://technet.microsoft.com/library/dn469260.aspx) that you should also consider.  
  
 The power of task sequences lies in their flexibility and how you  can use them to configure client settings, distribute software, update drivers, edit user states, and perform other tasks independent of operating system deployment. You can create a custom task sequence to add any number of tasks. While basic  use of custom task sequences for non-operating system deployment is supported, there is no way to test all of the possible configurations and the chance of having problems increases as you develop more complex task sequences.  
  
 The following steps can be used in a non-operating system deployment custom task sequence:  
  
-   [Check Readiness](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_CheckReadiness)  
  
-   [Connect To Network Folder](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_ConnectToNetworkFolder)  
  
-   [Download Package Content](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_DownloadPackageContent)  
  
-   [Install Application](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_InstallApplication)  
  
-   [Install Package](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_InstallPackage)  
  
-   [Install Software Updates](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_InstallSoftwareUpdates)  
  
-   [Restart Computer](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_RestartComputer)  
  
-   [Run Command Line](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_RunCommandLine)  
  
-   [Run PowerShell Script](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_RunPowerShellScript)  
  
-   [Set Dynamic Variables](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_SetDynamicVariables)  
  
-   [Set Task Sequence Variable](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_SetTaskSequenceVariable)  
  
## See Also  
 [Create a custom task sequence with System Center Configuration Manager](../System Center Configuration Manager/Create-a-custom-task-sequence-with-System-Center-Configuration-Manager.md)