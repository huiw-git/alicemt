---
title: FileTable Schema
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1cb3880-cfda-40ac-91fc-d08998287f44
---
# FileTable Schema
  Describes the pre\-defined and fixed schema of a FileTable.  
  
|File attribute name|type|Size|Default|Description|File system accessibility|  
|-------------------------|----------|----------|-------------|-----------------|-------------------------------|  
|**path\_locator**|**hierarchyid**|variable|A **hierarchyid** that identifies the position of this item.|The position of this node in the hierarchical FileNamespace.<br /><br /> Primary key for the table.|Can be created and modified by setting the Windows path values.|  
|**stream\_id**|**\[uniqueidentifier\] rowguidcol**||A value returned by the **NEWID\(\)** function.|A unique ID for the FILESTREAM data.|Not applicable.|  
|**file\_stream**|**varbinary\(max\)**<br /><br /> **filestream**|variable|NULL|Contains the FILESTREAM data.|Not applicable.|  
|**file\_type**|**nvarchar\(255\)**|variable|NULL.<br /><br /> A create or rename operation in the file system populates the file extension value from the name.|Represents the type of the file.<br /><br /> This column can be used as the **TYPE COLUMN** when you create a full\-text index.<br /><br /> **file\_type** is a persisted computed column.|Calculated automatically. Cannot be set.|  
|**Name**|**nvarchar\(255\)**|variable|GUID value.|The file or directory name.|Can be created or modified by using Windows APIs.|  
|**parent\_path\_locator**|**hierarchyid**|variable|A **hierarchyid** that identifies the directory that contains this item.|The **hierarchyid** of the containing directory.<br /><br /> **parent\_path\_locator** is a persisted computed column.|Calculated automatically. Cannot be set.|  
|**cached\_file\_size**|**bigint**|||The size in bytes of the FILESTREAM data.<br /><br /> **cached\_file\_size** is a persisted computed column.|Although the cached file size is automatically kept up to date, it can go out of sync in unusual circumstances. To calculate the exact size, use the **DATALENGTH\(\)** function.|  
|**creation\_time**|**datetime2\(4\)**<br /><br /> **not null**|8 bytes|Current time.|The date and time that the file was created.|Calculated automatically. Can also be set by using Windows APIs.|  
|**last\_write\_time**|**datetime2\(4\)**<br /><br /> **not null**|8 bytes|Current time.|The date and time that the file was last updated.|Calculated automatically. Can also be set by using Windows APIs.|  
|**last\_access\_time**|**datetime2\(4\)**<br /><br /> **not null**|8 bytes|Current time.|The date and time that the file was last accessed.|Calculated automatically. Can also be set by using Windows APIs.|  
|**is\_directory**|**bit**<br /><br /> **not null**|1 byte|FALSE|Indicates whether the row represents a directory. This value is calculated automatically, and cannot be set.|Calculated automatically. Cannot be set.|  
|**is\_offline**|**bit**<br /><br /> **not null**|1 byte|FALSE|Offline file attribute.|Calculated automatically. Can also be set by using Windows APIs.|  
|**is\_hidden**|**bit**<br /><br /> **not null**|1 byte|FALSE|Hidden file attribute.|Calculated automatically. Can also be set by using Windows APIs.|  
|**is\_readonly**|**bit**<br /><br /> **not null**|1 byte|FALSE|Read\-only  file attribute.|Calculated automatically. Can also be set by using Windows APIs.|  
|**is\_archive**|**bit**<br /><br /> **not null**|1 byte|FALSE|Archive attribute.|Calculated automatically. Can also be set by using Windows APIs.|  
|**is\_system**|**bit**<br /><br /> **not null**|1 byte|FALSE|System file attribute.|Calculated automatically. Can also be set by using Windows APIs.|  
|**is\_temporary**|**bit**<br /><br /> **not null**|1 byte|FALSE|Temporary file attribute.|Calculated automatically. Can also be set by using Windows APIs.|  
  
## See Also  
 [Create, Alter, and Drop FileTables](../../Topics\TopicNameNotContainA/Create,-Alter,-and-Drop-FileTables.md)  
  
  