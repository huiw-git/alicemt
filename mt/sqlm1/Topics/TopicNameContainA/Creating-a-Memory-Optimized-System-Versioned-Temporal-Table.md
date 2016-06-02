---
title: Creating a Memory-Optimized System-Versioned Temporal Table
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c1fc682-bf5b-4096-a0ff-3235d71c205a
---
# Creating a Memory-Optimized System-Versioned Temporal Table
  Similar to creating a disk\-based history table, you can create a memory\-optimized temporal table in a number of ways.  
  
> [!NOTE]  
>  To create memory\-optimized tables, you must first create [The Memory Optimized Filegroup](../../Topics\TopicNameNotContainA/The-Memory-Optimized-Filegroup.md).  
  
 Creating a temporal table with a default history table is a convenient option when you want to control naming and still rely on system to create history table with default configuration. In the example below, a new  system\-versioned memory\-optimized temporal table linked to a new disk\-based history table.  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH   
    (  
        MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,  
            SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )   
    );  
```  
  
 Creating a temporal table linked to an existing history table is useful when you wish to add system\-versioning using an existing table, such as when you wish to migrate a custom temporal solution to built\-in support. In the example below, a new temporal table is created linked to an existing history table.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (  
        SYSTEM_VERSIONING = ON  
            (  
                HISTORY_TABLE = dbo.Department_History  
                , DATA_CONSISTENCY_CHECK = ON   
            )  
        , MEMORY_OPTIMIZED = ON  
        , DURABILITY = SCHEMA_AND_DATA  
    );  
```  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Creating%20a%20Memory-Optimized%20System-Versioned%20Temporal%20Table%20page)  
  
## See Also  
 [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)   
 [Working with Memory-Optimized System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Working-with-Memory-Optimized-System-Versioned-Temporal-Tables.md)   
 [Monitoring Memory-Optimized System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Monitoring-Memory-Optimized-System-Versioned-Temporal-Tables.md)   
 [Performance Considerations with Memory-Optimized System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Performance-Considerations-with-Memory-Optimized-System-Versioned-Temporal-Tables.md)   
 [Temporal Tables](../../Topics\TopicNameNotContainA/Temporal-Tables.md)   
 [Temporal Table System Consistency Checks](../../Topics\TopicNameNotContainA/Temporal-Table-System-Consistency-Checks.md)   
 [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md)   
 [Temporal Table Metadata Views and Functions](../../Topics\TopicNameNotContainA/Temporal-Table-Metadata-Views-and-Functions.md)  
  
  