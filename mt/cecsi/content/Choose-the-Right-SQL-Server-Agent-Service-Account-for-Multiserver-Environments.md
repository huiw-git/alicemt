---
title: Choose the Right SQL Server Agent Service Account for Multiserver Environments
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Choose the Right SQL Server Agent Service Account for Multiserver Environments
The Windows account you choose for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service can affect the behavior of a multiserver environment, as follows:  
  
-   If you run the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service under an account that is not a member of the local Windows Administrators group, enlisting target servers to master servers may fail. If it does, the following error message is returned:  
  
    "The enlistment operation failed."  
  
    Restart the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent services to resolve this issue.  
  
-   When the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service is run under the Local System account, master server\-target server operations are supported only if both the master server and the target server reside on the same computer. If you use this configuration, the following message is returned when you enlist target servers to a master server:  
  
    "Ensure the agent start\-up account for *<target\_server\_computer\_name>* has rights to log on as targetServer."  
  
    You can ignore this informational message. The enlistment operation should complete successfully.  
  
For more information about choosing an account for the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service, see [Select an Account for the SQL Server Agent Service](../content/Select-an-Account-for-the-SQL-Server-Agent-Service.md).  
  
