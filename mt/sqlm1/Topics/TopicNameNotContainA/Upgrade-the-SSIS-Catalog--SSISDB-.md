---
title: Upgrade the SSIS Catalog (SSISDB)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 170c3dc9-f5bf-4599-ae56-d24a620f23e8
---
# Upgrade the SSIS Catalog (SSISDB)
  Run the SSISDB Upgrade Wizard to upgrade the SSIS Catalog database, SSISDB, when the database is older than the current version of the SQL Server instance. This occurs when one of the following conditions is true.  
  
-   You restored the database from an older version of SQL Server.  
  
-   You did not remove the database from an Always On Availability Group before upgrading the SQL Server instance. This prevents the automatic upgrade of the database. For more info, see [Upgrading SSISDB in an availability group](../Topic/Always%20On%20for%20SSIS%20Catalog%20\(SSISDB\).md#Upgrade).  
  
 The wizard can only upgrade the database on a local  server instance.  
  
## Upgrade the SSIS Catalog \(SSISDB\) by running the SSISDB Upgrade Wizard  
  
1.  Backup the SSIS Catalog database, SSISDB.  
  
2.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], expand the local server, and then expand **Integration Services Catalogs**.  
  
3.  Right\-click on **SSISDB**, and then select **Database Upgrade** to launch the SSISDB Upgrade Wizard.  
  
     ![Launch the SSISDB upgrade wizard](../../Images\Image\ImageNotContaina/SSISDB-Upgrade-Wizard-1.png "SSISDB Upgrade Wizard 1")  
  
4.  On the **Select Instance** page, select a SQL Server instance on the local server.  
  
    > [!IMPORTANT]  
    >  The wizard can only upgrade the database on a local server instance.  
  
     Select the checkbox to indicate that you have backed up the SSISDB database before running the wizard.  
  
     ![Select the server in the SSISDB Upgrade Wizard](../../Images\Image\ImageNotContaina/SSISDB-Upgrade-Wizard-2.png "SSISDB Upgrade Wizard 2")  
  
5.  Select **Upgrade** to upgrade the SSIS Catalog database.  
  
6.  On the **Result** page, review the results.  
  
     ![Review the results in the SSISDB Upgrade Wizard](../../Images\Image\ImageNotContaina/SSISDB-Upgrade-Wizard-3.png "SSISDB Upgrade Wizard 3")  
  
  