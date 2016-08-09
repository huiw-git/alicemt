---
title: "Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01796551-578d-4425-9b9e-d87210f7ba72
caps.latest.revision: 25
manager: jhubbard
---
# Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)
By default, backing up using compression significantly increases CPU usage, and the additional CPU consumed by the compression process can adversely impact concurrent operations. Therefore, you might want to create a low-priority compressed backup in a session whose CPU usage is limited by[Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md) when CPU contention occurs. This topic presents a scenario that classifies the sessions of a particular [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] user by mapping them to a Resource Governor workload group that limits CPU usage in such cases.  
  
> [!IMPORTANT]  
>  In a given Resource Governor scenario, session classification might be based on a user name, an application name, or anything else that can differentiate a connection. For more information, see [Resource Governor Classifier Function](../../Topics/TopicNameNotContainA/Resource-Governor-Classifier-Function.md) and [Resource Governor Workload Group](../../Topics/TopicNameNotContainA/Resource-Governor-Workload-Group.md).  
  
##  <a name="Top"></a> This topic contains the following set of scenarios, which are presented in sequence:  
  
1.  [Setting Up a Login and User for Low-Priority Operations](#setup_login_and_user)  
  
2.  [Configuring Resource Governor to Limit CPU Usage](#configure_RG)  
  
3.  [Verifying the Classification of the Current Session (Transact-SQL)](#verifying)  
  
4.  [Compressing Backups Using a Session with Limited CPU](#creating_compressed_backup)  
  
##  <a name="setup_login_and_user"></a> Setting Up a Login and User for Low-Priority Operations  
 The scenario in this topic requires a low-priority [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login and user. The user name will be used to classify sessions running in the login and route them to a Resource Governor workload group that limits CPU usage.  
  
 The following procedure describes the steps for setting up a login and user for this purpose, followed by a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] example, "Example A: Setting Up a Login and User (Transact-SQL)."  
  
### To set up a login and database user for classifying sessions  
  
1.  Create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login for creating low-priority compressed backups.  
  
     **To create a login**  
  
    -   [Create a Login](../../Topics/TopicNameContainA/Create-a-Login.md)  
  
    -   [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01)  
  
2.  Optionally, grant VIEW SERVER STATE to this login.  
  
    -   [GRANT System Object Permissions (Transact-SQL)](assetId:///9d4e89f4-478f-419a-8b50-b096771e3880)  
  
     For more information, see [GRANT Database Principal Permissions (Transact-SQL)](assetId:///012588a2-cbe1-48f0-a731-b4a2b83203d5).  
  
3.  Create a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] user for this login.  
  
     **To create a user**  
  
    -   [Create a Database User](../../Topics/TopicNameContainA/Create-a-Database-User.md)  
  
    -   [CREATE USER (Transact-SQL)](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80)  
  
4.  To enable sessions of this login and user to back up a given database, add the user to the db_backupoperator database role of that database. Do this for each database that this user will back up. Optionally, add the user to other fixed database roles.  
  
     **To add a user to a fixed database role**  
  
    -   [sp_addrolemember (Transact-SQL)](assetId:///a583c087-bdb3-46d2-b9e5-3921b3e6d10b)  
  
     For more information, see [GRANT Database Principal Permissions (Transact-SQL)](assetId:///012588a2-cbe1-48f0-a731-b4a2b83203d5).  
  
### Example A: Setting Up a Login and User (Transact-SQL)  
 The following example is relevant only if you choose to create a new [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login and user for low-priority backups. Alternatively, you can use an existing login and user, if an appropriate one exists.  
  
> [!IMPORTANT]  
>  The following example uses a sample login and user name, *domain_name*`\MAX_CPU`. Replace these with the names of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login and user that you plan to use when creating your low-priority compressed backups.  
  
 This example creates a login for the *domain_name*`\MAX_CPU` Windows account and then grants VIEW SERVER STATE permission to the login. This permission enables you to verify the Resource Governor classification of sessions of the login. The example then creates a user for *domain_name*`\MAX_CPU` and adds it to the db_backupoperator fixed database role for the [!INCLUDE[ssSampleDBnormal](../../Topics/TopicNameContainA/tokens/ssSampleDBnormal_md.md)] sample database. This user name will be used by the Resource Governor classifier function.  
  
```tsql  
-- Create a SQL Server login for low-priority operations  
USE master;  
CREATE LOGIN [domain_name\MAX_CPU] FROM WINDOWS;  
GRANT VIEW SERVER STATE TO [domain_name\MAX_CPU];  
GO  
-- Create a SQL Server user in AdventureWorks2012 for this login  
USE AdventureWorks2012;  
CREATE USER [domain_name\MAX_CPU] FOR LOGIN [domain_name\MAX_CPU];  
EXEC sp_addrolemember 'db_backupoperator', 'domain_name\MAX_CPU';  
GO  
  
```  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="configure_RG"></a> Configuring Resource Governor to Limit CPU Usage  
  
> [!NOTE]  
>  Ensure that Resource Governor is enabled. For more information, see [Enable Resource Governor](../../Topics/TopicNameNotContainA/Enable-Resource-Governor.md).  
  
 In this Resource Governor scenario, configuration comprises the following basic steps:  
  
1.  Create and configure a Resource Governor resource pool that limits the maximum average CPU bandwidth that will be given to requests in the resource pool when CPU contention occurs.  
  
2.  Create and configure a Resource Governor workload group that uses this pool.  
  
3.  Create a *classifier function*, which is a user-defined function (UDF) whose return values are used by Resource Governor for classifying sessions so that they are routed to the appropriate workload group.  
  
4.  Register the classifier function with Resource Governor.  
  
5.  Apply the changes to the Resource Governor in-memory configuration.  
  
> [!NOTE]  
>  For information about Resource Governor resource pools, workload groups, and classification, see [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md).  
  
 The [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements for these steps are described in the procedure, "To configure Resource Governor for limiting CPU usage," which is followed by a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] example of the procedure.  
  
 **To configure Resource Governor (SQL Server Management Studio)**  
  
-   [Configure Resource Governor Using a Template](../../Topics/TopicNameContainA/Configure-Resource-Governor-Using-a-Template.md)  
  
-   [Create a Resource Pool](../../Topics/TopicNameContainA/Create-a-Resource-Pool.md)  
  
-   [Create a Workload Group](../../Topics/TopicNameContainA/Create-a-Workload-Group.md)  
  
### To configure Resource Governor for limiting CPU usage (Transact-SQL)  
  
1.  Issue a [CREATE RESOURCE POOL](assetId:///82712505-c6f9-4a65-a469-f029b5a2d6cd) statement to create a resource pool. The example for this procedure uses the following syntax:  
  
     *CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );  
  
     *Value* is an integer from 1 to 100 that indicates the percentage of maximum average CPU bandwidth. The appropriate value depends on your environment. For the purpose of illustration, the example in this topic uses 20%  percent (MAX_CPU_PERCENT = 20.)  
  
2.  Issue a [CREATE WORKLOAD GROUP](assetId:///d949e540-9517-4bca-8117-ad8358848baa) statement to create a workload group for low-priority operations whose CPU usage you want to govern. The example for this procedure uses the following syntax:  
  
     CREATE WORKLOAD GROUP *group_name* USING *pool_name*;  
  
3.  Issue a [CREATE FUNCTION](assetId:///864b393f-225f-4895-8c8d-4db59ea60032) statement to create a classifier function that maps the workload group created in the preceding step to the user of the low-priority login. The example for this procedure uses the following syntax:  
  
     CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname  
  
     WITH SCHEMABINDING  
  
     AS  
  
     BEGIN  
  
     DECLARE @workload_group_name AS *sysname*  
  
     IF (SUSER_NAME() = '*user_of_low_priority_login*')  
  
     SET @workload_group_name = '*workload_group_name*'  
  
     RETURN @workload_group_name  
  
     END  
  
     For information about the components of this CREATE FUNCTION statement, see:  
  
    -   [DECLARE @local_variable (Transact-SQL)](assetId:///d1635ebb-f751-4de1-8bbc-cae161f90821)  
  
    -   [SUSER_SNAME (Transact-SQL)](assetId:///11ec7d86-d429-4004-a436-da25df9f8761)  
  
        > [!IMPORTANT]  
        >  SUSER_NAME is just one of several system functions that can be used in a classifier function. For more information, see [Create and Test a Classifier User-Defined Function](../../Topics/TopicNameContainA/Create-and-Test-a-Classifier-User-Defined-Function.md).  
  
    -   [SET @local_variable (Transact-SQL)](assetId:///d410e06e-061b-4c25-9973-b2dc9b60bd85).  
  
4.  Issue an [ALTER RESOURCE GOVERNOR](assetId:///442c54bf-a0a6-4108-ad20-db910ffa6e3c) statement to register the classifier function with Resource Governor. The example for this procedure uses the following syntax:  
  
     ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);  
  
5.  Issue a second ALTER RESOURCE GOVERNOR statement to apply the changes to the Resource Governor in-memory configuration, as follows:  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    ```  
  
### Example B: Configuring Resource Governor (Transact-SQL)  
 The following example performs the following steps within a single transaction:  
  
1.  Creates the `pMAX_CPU_PERCENT_20` resource pool.  
  
2.  Creates the `gMAX_CPU_PERCENT_20` workload group.  
  
3.  Creates the `rgclassifier_MAX_CPU()` classifier function, which uses the user name created in the preceding example.  
  
4.  Registers the classifier function with Resource Governor.  
  
 After committing the transaction, the example applies the configuration changes requested in the ALTER WORKLOAD GROUP or ALTER RESOURCE POOL statements.  
  
> [!IMPORTANT]  
>  The following example uses the user name of the sample [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] user created in "Example A: Setting Up a Login and User (Transact-SQL)," *domain_name*`\MAX_CPU`. Replace this with the name of the user of the login that you plan to use for creating low-priority compressed backups.  
  
```tsql  
-- Configure Resource Governor.  
BEGIN TRAN  
USE master;  
-- Create a resource pool that sets the MAX_CPU_PERCENT to 20%.   
CREATE RESOURCE POOL pMAX_CPU_PERCENT_20  
   WITH  
      (MAX_CPU_PERCENT = 20);  
GO  
-- Create a workload group to use this pool.   
CREATE WORKLOAD GROUP gMAX_CPU_PERCENT_20  
USING pMAX_CPU_PERCENT_20;  
GO  
-- Create a classification function.  
-- Note that any request that does not get classified goes into   
-- the 'Default' group.  
CREATE FUNCTION dbo.rgclassifier_MAX_CPU() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
    DECLARE @workload_group_name AS sysname  
      IF (SUSER_NAME() = 'domain_name\MAX_CPU')  
          SET @workload_group_name = 'gMAX_CPU_PERCENT_20'  
    RETURN @workload_group_name  
END;  
GO  
  
-- Register the classifier function with Resource Governor.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION= dbo.rgclassifier_MAX_CPU);  
COMMIT TRAN;  
GO  
-- Start Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="verifying"></a> Verifying the Classification of the Current Session (Transact-SQL)  
 Optionally, log in as the user that you specified in your classifier function, and verify the session classification by issuing the following [SELECT](assetId:///dc85caea-54d1-49af-b166-f3aa2f3a93d0) statement in Object Explorer:  
  
```tsql  
USE master;  
SELECT sess.session_id, sess.login_name, sess.group_id, grps.name   
FROM sys.dm_exec_sessions AS sess   
JOIN sys.dm_resource_governor_workload_groups AS grps   
    ON sess.group_id = grps.group_id  
WHERE session_id > 50;  
GO  
```  
  
 In the results pane, the **name** column should list one or more sessions for the workload-group name that you specified in your classifier function.  
  
> [!NOTE]  
>  For information about the dynamic management views called by this SELECT statement, see [sys.dm_exec_sessions (Transact-SQL)](assetId:///2b7e8e0c-eea0-431e-819f-8ccd12ec8cfa) and [sys.dm_resource_governor_workload_groups (Transact-SQL)](assetId:///f63c4914-1272-43ef-b135-fe1aabd953e0).  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="creating_compressed_backup"></a> Compressing Backups Using a Session with Limited CPU  
 To create a compressed backup in a session with a limited maximum CPU, log in as the user specified in your classifier function. In your backup command, either specify WITH COMPRESSION ([!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]) or select **Compress backup** ([!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]). To create a compressed database backup, see [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md).  
  
### Example C: Creating a Compressed Backup (Transact-SQL)  
 The following [BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1) example creates a compressed full backup of the [!INCLUDE[ssSampleDBnormal](../../Topics/TopicNameContainA/tokens/ssSampleDBnormal_md.md)] database in a newly formatted backup file, `Z:\SQLServerBackups\AdvWorksData.bak`.  
  
```tsql  
--Run backup statement in the gBackup session.  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   MEDIADESCRIPTION='AdventureWorks2012 Compressed Data Backups'  
   DESCRIPTION='First database backup on AdventureWorks2012 Compressed Data Backups media set'  
   COMPRESSION;  
GO  
```  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Create and Test a Classifier User-Defined Function](../../Topics/TopicNameContainA/Create-and-Test-a-Classifier-User-Defined-Function.md)   
 [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md)