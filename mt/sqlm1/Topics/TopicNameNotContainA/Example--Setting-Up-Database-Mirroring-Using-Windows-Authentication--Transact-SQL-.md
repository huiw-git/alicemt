---
title: Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35800769-aede-4aac-b077-0e0e487e302f
---
# Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)
  This example shows all the stages required to create a database mirroring session with a witness using Windows Authentication. The examples in this topic use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. Note that as an alternative to using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] steps, you can use the Configure Database Mirroring Security Wizard for database mirroring setup. For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md).  
  
## Prerequisite  
 The example uses the **AdventureWorks** sample database, which uses the simple recovery model by default. To use database mirroring with this database, you must alter it to use the full recovery model. To do this in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], use the ALTER DATABASE statement, as follows:  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks   
SET RECOVERY FULL;  
GO  
```  
  
 For information on changing the recovery model in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md).  
  
### Permissions  
 Requires ALTER permission on the database and CREATE ENDPOINT permission, or membership in the **sysadmin** fixed server role.  
  
## Example  
 In this example, the two partners and the witness are the default server instances on three computer systems. The three server instances run the same Windows domain, but the user account \(used as the startup service account\) is different for the example's witness server instance.  
  
 The following table summarizes the values used in this example.  
  
|Initial mirroring role|Host system|Domain user account|  
|----------------------------|-----------------|-------------------------|  
|Principal|PARTNERHOST1|*\<Mydomain\>\\\<dbousername\>*|  
|Mirror|PARTNERHOST5|*\<Mydomain\>\\\<dbousername\>*|  
|Witness|WITNESSHOST4|*\<Somedomain\>\\\<witnessuser\>*|  
  
1.  Create an endpoint on the principal server instance \(default instance on PARTNERHOST1\).  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=PARTNER)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    -- Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
2.  Create an endpoint on the mirror server instance \(default instance on PARTNERHOST5\).  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
3.  Create an endpoint on the witness server instance \(default instance on WITNESSHOST4\).  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    --Create a login for the partner server instances,  
    --which are both running as Mydomain\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [Mydomain\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
4.  Create the mirror database. For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md).  
  
5.  On the mirror server instance on PARTNERHOST5, set the server instance on PARTNERHOST1 as the partner \(making it the initial principal server instance\).  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1.COM:7022'  
    GO  
    ```  
  
6.  On the principal server instance on PARTNERHOST1, set the server instance on PARTNERHOST5 as the partner \(making it the initial mirror server instance\).  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5.COM:7022'  
    GO  
    ```  
  
7.  On the principal server, set the witness \(which is on WITNESSHOST4\).  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4.COM:7022'  
    GO  
    ```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md)  
  
-   [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](../Topic/Start%20the%20Configuring%20Database%20Mirroring%20Security%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](../Topic/Set%20Up%20a%20Mirror%20Database%20to%20Use%20the%20Trustworthy%20Property%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md)  
  
## See Also  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)   
 [Transport Security for Database Mirroring and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../Topic/Manage%20Metadata%20When%20Making%20a%20Database%20Available%20on%20Another%20Server%20Instance%20\(SQL%20Server\).md)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)  
  
  