---
title: Remove Database Mirroring (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
---
# Remove Database Mirroring (SQL Server)
  This topic describes how to remove database mirroring from a database in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  At any time, the database owner can manually stop a database mirroring session by removing mirroring from the database.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To remove database mirroring, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After Removing Database Mirroring](#FollowUp)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove database mirroring  
  
1.  During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and select the database.  
  
3.  Right\-click the database, select **Tasks**, and then click **Mirror**. This opens the **Mirroring** page of the **Database Properties** dialog box.  
  
4.  In the **Select a Page** pane, click **Mirroring**.  
  
5.  To remove mirroring, click **Remove Mirroring**. A prompt asks for confirmation. If you click **Yes**, the session is stopped and mirroring is removed from the database.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 To remove database mirroring, use the **Database Properties**. use the **Mirroring** page of the **Database Properties** dialog box.  
  
#### To remove database mirroring  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] of either mirroring partner.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Issue the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement:  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     where *database\_name* is the mirrored database whose session you want to remove.  
  
     The following example removes database mirroring from the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] sample database.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="FollowUp"></a> Follow Up: Removing Database Mirroring  
  
> [!NOTE]  
>  For information about the impact of removing mirroring, see [Removing Database Mirroring &#40;SQL Server&#41;](../Topic/Removing%20Database%20Mirroring%20\(SQL%20Server\).md).  
  
-   **If you intend to restart mirroring on the database**  
  
     Any log backups taken on the principal database after mirroring was removed must all be applied to the mirror database before you can restart mirroring.  
  
-   **If you do not intent to restart mirroring**  
  
     Optionally, you can recover the former mirror database. On the server instance that was the mirror server, you can use the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement:  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  If you recover this database, two divergent databases with the same name are online. Therefore, you need to ensure that clients can access only one of them—typically the most recent principal database.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;](../Topic/Pause%20or%20Resume%20a%20Database%20Mirroring%20Session%20\(SQL%20Server\).md)  
  
-   [Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;](../Topic/Remove%20the%20Witness%20from%20a%20Database%20Mirroring%20Session%20\(SQL%20Server\).md)  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md)  
  
## See Also  
 [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md)   
 [Setting Up Database Mirroring &#40;SQL Server&#41;](../Topic/Setting%20Up%20Database%20Mirroring%20\(SQL%20Server\).md)   
 [Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  