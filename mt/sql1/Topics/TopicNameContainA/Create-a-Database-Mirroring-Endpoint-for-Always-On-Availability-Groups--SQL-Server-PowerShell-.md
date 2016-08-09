---
title: "Create a Database Mirroring Endpoint for Always On Availability Groups (SQL Server PowerShell)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Create a Database Mirroring Endpoint for Always On Availability Groups (SQL Server PowerShell)
This topic describes how to create a database mirroring endpoint for use by [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using PowerShell.  
  
 **In This Topic**  
  
-   **Before you begin:**  [Security](#Security)  
  
-   **To create a database mirroring endpoint, using:**  [PowerShell](#PowerShellProcedure)  
  
## Before You Begin  
  
###  <a name="Security"></a> Security  
  
> [!IMPORTANT]  
>  The RC4 algorithm is deprecated. [!INCLUDE[ssNoteDepFutureDontUse](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureDontUse_md.md)] We recommend that you use AES.  
  
####  <a name="Permissions"></a> Permissions  
 Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role. For more information, see [GRANT Endpoint Permissions (Transact-SQL)](assetId:///9eda885c-fc3a-4c9d-8de6-ce07fb35a934).  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To create a database mirroring endpoint**  
  
1.  Change directory (**cd**) to the server instance for which you want to create the database mirroring endpoint.  
  
2.  Use the **New-SqlHadrEndpoint** cmdlet to create the endpoint and then use the **Set-SqlHadrEndpoint** to start the endpoint.  
  
###  <a name="PShellExample"></a> Example (PowerShell)  
 The following PowerShell commands create a database mirroring endpoint on an instance of SQL Server (*Machine*\\*Instance*). The endpoint uses port 5022.  
  
> [!IMPORTANT]  
>  This example works only on a server instance that currently lack a database mirroring endpoint.  
  
```  
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"  
  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To Configure a Database Mirroring Endpoint**  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Windows-Authentication--Transact-SQL-.md)  
  
-   [Use Certificates for a Database Mirroring Endpoint (Transact-SQL)](../../Topics/TopicNameContainA/Use-Certificates-for-a-Database-Mirroring-Endpoint--Transact-SQL-.md)  
  
    -   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md)  
  
    -   [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Inbound-Connections--Transact-SQL-.md)  
  
-   [Specify a Server Network Address (Database Mirroring)](../../Topics/TopicNameContainA/Specify-a-Server-Network-Address--Database-Mirroring-.md)  
  
-   [Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)](../../Topics/TopicNameNotContainA/Specify-the-Endpoint-URL-When-Adding-or-Modifying-an-Availability-Replica--SQL-Server-.md)  
  
 **To View Information About the Database Mirroring Endpoint**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](assetId:///f2285199-97ad-473c-a52d-270044dd862b)  
  
## See Also  
 [Create an Availability Group (Transact-SQL)](../../Topics/TopicNameNotContainA/Create-an-Availability-Group--Transact-SQL-.md)   
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)