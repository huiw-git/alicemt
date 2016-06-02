---
title: Rebuild Index Task (Maintenance Plan)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
---
# Rebuild Index Task (Maintenance Plan)
  Use the **Rebuild Index Task** dialog to re\-create the indexes on the tables in the database with a new fill factor. The fill factor determines the amount of empty space on each page in the index, to accommodate future expansion. As data is added to the table, the free space fills because the fill factor is not maintained. Reorganizing data and index pages can re\-establish the free space.  
  
 The **Rebuild Index Task** uses the ALTER INDEX statement. For more info about the options described on this page, see [ALTER INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md).  
  
## Options  
 **Connection**  
 Select the server connection to use when performing this task.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described below.  
  
 **Databases**  
 Specify the databases affected by this task.  
  
-   **All databases**  
  
     Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases except tempdb.  
  
-   **All system databases**  
  
     Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system databases except tempdb. No maintenance tasks are run against user\-created databases.  
  
-   **All user databases**  
  
     Generate a maintenance plan that runs maintenance tasks against all user\-created databases. No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system databases.  
  
-   **These specific databases**  
  
     Generate a maintenance plan that runs maintenance tasks against only those databases that are selected. At least one database in the list must be selected if this option is chosen.  
  
    > [!NOTE]  
    >  Maintenance plans only run against databases set to compatibility level 80 or higher. Databases set to compatibility level 70 or lower are not displayed.  
  
 **Object**  
 Limit the **Selection** grid to display tables, views, or both.  
  
 **Selection**  
 Specify the tables or indexes affected by this task. Not available when **Tables and Views** is selected in the Object box.  
  
 **Default free space per page**  
 Drop the indexes on the tables in the database and re\-create them with the fill factor that was specified when the indexes were created.  
  
 **Change free space per page to**  
 Drop the indexes on the tables in the database and re\-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages. The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows. Valid values are from 0 through 100.  
  
 **Sort results in tempdb**  
 Use the `SORT_IN_TEMPDB` option, which determines where the intermediate sort results, generated during index creation, are temporarily stored. If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB`option is ignored.  
  
 **Pad index**  
 Specify index padding  
  
 **Keep index online**  
 Use the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.  
  
> [!NOTE]  
>  Online index operations are not available in every edition of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 **Do not rebuild indexes | Rebuild indexes offline**  
 Specify what to do for index types that cannot be rebuilt while they are online.  
  
 **MAXDOP**  
 Specify a value to limit the number of processors used in a parallel plan execution.  
  
 **Low Priority Used**  
 Select this option to wait for low priority locks.  
  
 **Abort after Wait**  
 Specify what to do after the time specified by **Max Duration** has elapsed.  
  
 **Max Duration**  
 Specify how long to wait for low priority locks.  
  
 **View T\-SQL**  
 View the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements performed against the server for this task, based on the selected options.  
  
> [!NOTE]  
>  When the number of objects affected is large, this display can take a considerable amount of time.  
  
## New Connection Dialog Box  
 **Connection name**  
 Enter a name for the new connection.  
  
 **Select or enter a server name**  
 Select a server to connect to when performing this task.  
  
 **Refresh**  
 Refresh the list of available servers.  
  
 **Enter information to log on to the server**  
 Specify how to authenticate against the server.  
  
 **Use Windows integrated security**  
 Connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] with Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [ALTER INDEX &#40;Transact-SQL&#41;](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](../Topic/DBCC%20DBREINDEX%20\(Transact-SQL\).md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../Topic/CREATE%20INDEX%20\(Transact-SQL\).md)   
 [SORT_IN_TEMPDB Option For Indexes](../../Topics\TopicNameNotContainA/SORT_IN_TEMPDB-Option-For-Indexes.md)   
 [Guidelines for Online Index Operations](../../Topics\TopicNameNotContainA/Guidelines-for-Online-Index-Operations.md)   
 [How Online Index Operations Work](../../Topics\TopicNameNotContainA/How-Online-Index-Operations-Work.md)   
 [Perform Index Operations Online](../../Topics\TopicNameNotContainA/Perform-Index-Operations-Online.md)  
  
  