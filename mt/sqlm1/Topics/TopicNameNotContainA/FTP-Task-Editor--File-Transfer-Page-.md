---
title: FTP Task Editor (File Transfer Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
---
# FTP Task Editor (File Transfer Page)
  Use the **File Transfer** page of the **FTP Task Editor** dialog box to configure the FTP operation that the task performs.  
  
 To learn about this task, see [FTP Task](../../Topics\TopicNameNotContainA/FTP-Task.md).  
  
## Options  
 **IsRemotePathVariable**  
 Indicate whether the remote path is stored in a variable. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|The destination path is stored in a variable. Selecting the value displays the dynamic option, **RemoteVariable**.|  
|**False**|The destination path is specified in a File connection manager. Selecting the value displays the dynamic option, **RemotePath**.|  
  
 **OverwriteFileAtDestination**  
 Specify whether a file at the destination can be overwritten.  
  
 **IsLocalPathVariable**  
 Indicate whether the local path is stored in a variable. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|The destination path is stored in a variable. Selecting the value displays the dynamic option, **LocalVariable**.|  
|**False**|The destination path is specified in a File connection manager. Selecting the value displays the dynamic option, **LocalPath**.|  
  
 **Operation**  
 Select the FTP operation to perform. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**Send files**|Send files. Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.|  
|**Receive files**|Receive files. Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.|  
|**Create local directory**|Create a local directory. Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.|  
|**Create remote directory**|Create a remote directory. Selecting this value displays the dynamic options, **RemoteVariable** and **RemotelPath**.|  
|**Remove local directory**|Removes a local directory. Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.|  
|**Remove remote directory**|Remove a remote directory. Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.|  
|**Delete local files**|Delete local files. Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.|  
|**Delete remote files**|Delete remote files. Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.|  
  
 **IsTransferASCII**  
 Indicate whether files transferred to and from the remote FTP server should be transferred in ASCII mode.  
  
## IsRemotePathVariable Dynamic Options  
  
### IsRemotePathVariable \= True  
 **RemoteVariable**  
 Select an existing user\-defined variable, or click \<**New variable...**\> to create a user\-defined variable.  
  
 **Related Topics:** [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md), Add Variable  
  
### IsRemotePathVariable \= False  
 **RemotePath**  
 Select an existing FTP connection manager, or click \<**New connection…**\> to create a connection manager.  
  
 **Related Topics:** [FTP Connection Manager](../../Topics\TopicNameNotContainA/FTP-Connection-Manager.md), [FTP Connection Manager Editor](../../Topics\TopicNameNotContainA/FTP-Connection-Manager-Editor.md)  
  
## IsLocalPathVariable Dynamic Options  
  
### IsLocalPathVariable \= True  
 **LocalVariable**  
 Select an existing user\-defined variable, or click \<**New variable...**\> to create a variable.  
  
 **Related Topics:** [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md), Add Variable  
  
### IsLocalPathVariable \= False  
 **LocalPath**  
 Select an existing File connection manager, or click \<**New connection…**\> to create a connection manager.  
  
 **Related Topics**: [Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md), [File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md)  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [FTP Task Editor &#40;General Page&#41;](../Topic/FTP%20Task%20Editor%20\(General%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
  