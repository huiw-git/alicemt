---
title: "Find the Objects That Have the Most Locks Taken on Them"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fcbadbda-c91c-43f0-a1b5-601e40110e07
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# Find the Objects That Have the Most Locks Taken on Them
Database administrators often need to identify the source of locks that are hindering database performance.  
  
 For example, you are monitoring your production server for any possible bottlenecks. You suspect that there might be highly contested resources, and would like to know how many locks are taken on those objects. Once the most frequently locked objects are identified, steps can be taken to optimize access to the contended objects.  
  
 To do this, use Query Editor in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
### To find the objects that have the most locks  
  
1.  In Query Editor, issue the following statements.  
  
    ```  
    -- Find objects in a particular database that have the most  
    -- lock acquired. This sample uses AdventureWorksDW2012.  
    -- Create the session and add an event and target.  
    --   
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='LockCounts')  
    DROP EVENT session LockCounts ON SERVER  
    GO  
    DECLARE @dbid int  
  
    SELECT @dbid = db_id('AdventureWorksDW2012')  
  
    DECLARE @sql nvarchar(1024)  
    SET @sql = '  
    CREATE event session LockCounts ON SERVER  
    ADD EVENT sqlserver.lock_acquired (WHERE database_id =' + CAST(@dbid AS nvarchar) +')  
    ADD TARGET package0.histogram(   
    SET filtering_event_name=''sqlserver.lock_acquired'', source_type=0, source=''resource_0'')'  
  
    EXEC (@sql)  
    GO  
    ALTER EVENT session LockCounts ON SERVER   
    STATE=start  
    GO  
    --   
    -- Create a simple workload that takes locks.  
    --   
    USE AdventureWorksDW2012  
    GO  
    SELECT TOP 1 * FROM dbo.vAssocSeqLineItems  
    GO  
    -- The histogram target output is available from the   
    -- sys.dm_xe_session_targets dynamic management view in  
    -- XML format.  
    -- The following query joins the bucketizing target output with  
    -- sys.objects to obtain the object names.  
    --  
    SELECT name, object_id, lock_count FROM   
    (SELECT objstats.value('.','bigint') AS lobject_id,   
    objstats.value('@count', 'bigint') AS lock_count  
    FROM (  
    SELECT CAST(xest.target_data AS XML)  
    LockData  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'LockCounts'  
    ) Locks  
    CROSS APPLY LockData.nodes('//HistogramTarget/Slot') AS T(objstats)  
     ) LockedObjects   
    INNER JOIN sys.objects o  
    ON LockedObjects.lobject_id = o.object_id  
    WHERE o.type != 'S' AND o.type = 'U'  
    ORDER BY lock_count desc  
    GO  
    --   
    -- Stop the event session.  
    --   
    ALTER EVENT SESSION LockCounts ON SERVER  
    state=stop  
    GO  
  
    ```  
  
 After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:  
  
-   name  
  
-   object_id  
  
-   lock_count  
  
## See Also  
 [CREATE EVENT SESSION (Transact-SQL)](assetId:///67683027-2b0f-47aa-b223-604731af8b4d)   
 [ALTER EVENT SESSION (Transact-SQL)](assetId:///da006ac9-f914-4995-a2fb-25b5d971cd90)   
 [sys.dm_xe_session_targets](assetId:///76fbc3e1-ad88-4a47-8bf1-471c3bee5ad8)   
 [sys.dm_xe_sessions](assetId:///defd6efb-9507-4247-a91f-dc6ff5841e17)   
 [sys.server_event_sessions](assetId:///796f3093-6a3e-4d67-8da6-b9810ae9ef5b)