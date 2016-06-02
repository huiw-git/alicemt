---
title: Oracle Credentials for Running Script
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
---
# Oracle Credentials for Running Script
  To run the Oracle supplemental logging script from the Oracle CDC Designer console, the program prompts you for the credentials of the Oracle user who is running the script. To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA\_LOG\_GROUPS view.  
  
## Task List  
 Enter the following in this dialog box:  
  
 **Authentication**  
  
 Select one of the following:  
  
-   **Windows Authentication**: Select this to use the current Windows domain credentials. You can use this option only if the Oracle database is configured to work with Windows authentication.  
  
-   **Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Source Oracle database you are connecting to.  
  
## See Also  
 [How to Manage a CDC Instance](../../Topics\TopicNameContainA/How-to-Manage-a-CDC-Instance.md)   
 [Review and Generate Supplemental Logging Scripts](../../Topics\TopicNameNotContainA/Review-and-Generate-Supplemental-Logging-Scripts.md)  
  
  