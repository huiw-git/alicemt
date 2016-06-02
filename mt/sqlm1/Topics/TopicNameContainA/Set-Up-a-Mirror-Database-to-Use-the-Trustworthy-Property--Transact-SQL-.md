---
title: Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
---
# Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)
  When a database is backed up, the TRUSTWORTHY database property is set to OFF. Therefore, on a new mirror database TRUSTWORTHY is always OFF. If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.  
  
> [!NOTE]  
>  For information about this database property, see [TRUSTWORTHY Database Property](../../Topics\TopicNameNotContainA/TRUSTWORTHY-Database-Property.md).  
  
## Procedure  
  
#### To setup a mirror database to use the Trustworthy Property  
  
1.  On the principal server instance, verify that the principal database has the Trustworthy property turned on.  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     For more information, see [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md).  
  
2.  After starting mirroring, verify that the database is currently the principal database, the session is using a synchronous operating mode, and the session is already synchronized.  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](../Topic/sys.database_mirroring%20\(Transact-SQL\).md).  
  
3.  Once the mirroring session is synchronized, manually fail over to the mirror database.  
  
     This can be done in either SQL Server Management Studio or using Transact\-SQL:  
  
    -   [Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;](../Topic/Manually%20Fail%20Over%20a%20Database%20Mirroring%20Session%20\(SQL%20Server%20Management%20Studio\).md)  
  
    -   [Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](../Topic/Manually%20Fail%20Over%20a%20Database%20Mirroring%20Session%20\(Transact-SQL\).md)  
  
4.  Turn on the trustworthy database property using the following ALTER DATABASE command:  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     For more information, see[ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
5.  Optionally, manually failover again to return to the original principal.  
  
6.  Optionally, switch to asynchronous, high\-performance mode by setting SAFETY to OFF and ensuring that WITNESS is also set to OFF.  
  
     In Transact\-SQL:  
  
    -   [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](../Topic/Change%20Transaction%20Safety%20in%20a%20Database%20Mirroring%20Session%20\(Transact-SQL\).md)  
  
    -   [Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;](../Topic/Remove%20the%20Witness%20from%20a%20Database%20Mirroring%20Session%20\(SQL%20Server\).md)  
  
     In SQL Server Management Studio:  
  
    -   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
## See Also  
 [TRUSTWORTHY Database Property](../../Topics\TopicNameNotContainA/TRUSTWORTHY-Database-Property.md)   
 [Set Up an Encrypted Mirror Database](../../Topics\TopicNameNotContainA/Set-Up-an-Encrypted-Mirror-Database.md)  
  
  