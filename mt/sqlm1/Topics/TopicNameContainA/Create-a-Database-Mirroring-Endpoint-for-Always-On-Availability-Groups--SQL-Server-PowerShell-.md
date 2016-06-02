---
title: Create a Database Mirroring Endpoint for Always On Availability Groups (SQL Server PowerShell)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
---
# Create a Database Mirroring Endpoint for Always On Availability Groups (SQL Server PowerShell)
  This topic describes how to create a database mirroring endpoint for use by [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using PowerShell.  
  
 **In This Topic**  
  
-   **Before you begin:**  [Security](#Security)  
  
-   **To create a database mirroring endpoint, using:**  [PowerShell](#PowerShellProcedure)  
  
## Before You Begin  
  
###  <a name="Security"></a> Security  
  
> [!IMPORTANT]  
>  The RC4 algorithm is deprecated. [!INCLUDE[ssNoteDepFutureDontUse](../../Token\Appliesto/ssNoteDepFutureDontUse_md.md)] We recommend that you use AES.  
  
####  <a name="Permissions"></a> Permissions  
 Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role. For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Endpoint%20Permissions%20\(Transact-SQL\).md).  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To create a database mirroring endpoint**  
  
1.  Change directory \(**cd**\) to the server instance for which you want to create the database mirroring endpoint.  
  
2.  Use the **New\-SqlHadrEndpoint** cmdlet to create the endpoint and then use the **Set\-SqlHadrEndpoint** to start the endpoint.  
  
###  <a name="PShellExample"></a> Example \(PowerShell\)  
 The following PowerShell commands create a database mirroring endpoint on an instance of SQL Server \(*Machine*\\*Instance*\). The endpoint uses port 5022.  
  
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
  
-   [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md)  
  
    -   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
    -   [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Specify a Server Network Address &#40;Database Mirroring&#41;](../Topic/Specify%20a%20Server%20Network%20Address%20\(Database%20Mirroring\).md)  
  
-   [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](../Topic/Specify%20the%20Endpoint%20URL%20When%20Adding%20or%20Modifying%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
 **To View Information About the Database Mirroring Endpoint**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../Topic/sys.database_mirroring_endpoints%20\(Transact-SQL\).md)  
  
## See Also  
 [Create an Availability Group &#40;Transact-SQL&#41;](../Topic/Create%20an%20Availability%20Group%20\(Transact-SQL\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  