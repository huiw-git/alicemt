---
title: "Associate users with a destination computer in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-28
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 07c3c6d9-f056-4c4d-bc70-ede5ca933807
caps.latest.revision: 9
caps.handback.revision: 0
---
# Associate users with a destination computer in System Center Configuration Manager
When you use [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to deploy operating system you can associate users with the destination computer where the operating system is deployed. This configuration includes the following:  
  
-   That a single user is the primary user of the destination computer.  
  
-   That multiple users are the primary users of the destination computer.  
  
 User device affinity supports user-centric management for when you deploy applications. When you associate a user with the destination computer on which to install an operating system, you can later deploy applications to that user and the applications automatically install on the destination computer. However, although you can configure support for user device affinity when you deploy operating systems, you cannot use user device affinity to deploy operating systems.  
  
 For more information about user device affinity, see [Link users and devices with user device affinity in System Center Configuration Manager](../System Center Configuration Manager/Link-users-and-devices-with-user-device-affinity-in-System-Center-Configuration-Manager.md).  
  
## How to specify a user when you deploy operating systems  
 The following table lists the actions that you can take to integrate user device affinity into your operating system deployments. You can integrate user device affinity into PXE deployments, bootable media deployments, and pre-staged media deployments.  
  
|Action|More information|  
|------------|----------------------|  
|Create a task sequence that includes the **SMSTSAssignUsersMode** variable|Add the **SMSTSAssignUsersMode** variable to the beginning of your task sequence by using the  [Set Task Sequence Variable](../System Center Configuration Manager/Task-sequence-steps-in-System-Center-Configuration-Manager.md#BKMK_SetTaskSequenceVariable) task sequence step. This variable specifies how the task sequence handles the user information.<br /><br /> Set the variable to one of the following values:<br /><br /> <br /><br /> **Auto**: The task sequence automatically creates a relationship between the user and destination computer and deploys the operating system.<br /><br /> **Pending**: The task sequence creates a relationship between the user and the destination computer, but waits for approval from the administrative user before the operating system is deployed.<br /><br /> **Disabled**: The task sequence does not associate a user with the destination computer and continues to deploy the operating system.<br /><br /> <br /><br /> This variable can also be set on a computer or collection. For more information about the built-in variables, see [Task sequence built-in variables in System Center Configuration Manager](../System Center Configuration Manager/Task-sequence-built-in-variables-in-System-Center-Configuration-Manager.md).|  
|Create a prestart command that gathers the user information|The prestart command can be a Visual Basic (VB) script that has an input box, or it can be an HTML application (HTA) that validates the user data that is entered.<br /><br /> The prestart command must set the **SMSTSUdaUsers** variable that is used when the task sequence is run. This variable can be set on a computer, a collection, or a task sequence variable. Use the following format when you add multiple users: *domain\user1, domain\user2, domain\user3*.|  
|Configure how distribution points and media associate the user with the destination computer|When you [configure a distribution point to accept PXE boot requests](https://technet.microsoft.com/library/mt627944\(TechNet.10\).aspx#BKMK_PXEDistributionPoint) and when you create [bootable media](http://technet.microsoft.com/library/mt627921\(TechNet.10\).aspx) or [pre-staged media](https://technet.microsoft.com/library/mt627922\(TechNet.10\).aspx) by using the Create Task Sequence Media Wizard, you can specify how the distribution point or media supports associating users with the destination computer where the operating system is deployed.<br /><br /> Configuring user device affinity support does not have a built-in method to validate the user identity. This can be important when a technician who is provisioning the computer enters the information on behalf of the user. In addition to setting how the user information is handled by the task sequence, configuring these options on the distribution point and media provides the ability to restrict the deployments that are started from a PXE boot or from a specific type of media.|  
  
## See Also  
 [Prepare for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Prepare-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)