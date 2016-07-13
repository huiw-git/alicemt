---
title: Force a Target Server to Poll the Master Server
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
manager:jhubbard
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
# Force a Target Server to Poll the Master Server
This topic describes how to force a target server to poll the master server. The target server must be a registered server on the master server.  
  
A job is a specified series of actions that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent performs. A multiserver job is a job that a master server runs on one or more target servers. Each target server can run one instance of the same job at the same time. Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects. The target server runs the job locally and then reconnects to the master server to upload the job outcome status.  
  
> [!NOTE]  
> If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.  
  
-   **Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)  
  
-   **To force a target server to poll the master server, using:** [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Restrictions"></a>Limitations and Restrictions  
The target server must be a registered server on the master server. You must run the instructions given in this topic from the master server.  
  
### <a name="Security"></a>Security  
For detailed information, see [Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../content/Choose-the-Right-SQL-Server-Agent-Service-Account-for-Multiserver-Environments.md).  
  
## <a name="SSMS"></a>Using SQL Server Management Studio  
**To force a target server to poll the master server**  
  
1.  In **Object Explorer**, expand the master server.  
  
2.  Right\-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.  
  
3.  Click a target server, and then click **Force Poll**.  
  
