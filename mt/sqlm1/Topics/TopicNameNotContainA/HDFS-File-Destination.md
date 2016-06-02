---
title: HDFS File Destination
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
---
# HDFS File Destination
  The HDFS File Destination component enables an SSIS package to write data to a HDFS file. The supported file formats are Text, Avro, and ORC.  
  
 To configure the HDFS File Destination, drag and drop the HDFS File Source on the data flow designer and double\-click the component to open the editor.  
  
 ![HDFS File Destination Editor](../../Images\Image\ImageNotContaina/HDFS-file-dest.png "HDFS-file-dest")  
  
## Options  
 Configure the following options on the **General** tab of the **Hadoop File Destination Editor** dialog box.  
  
|Field|Description|  
|-----------|-----------------|  
|**Hadoop Connection**|Specify an existing Hadoop Connection Manager or create a new one. This connection manager indicates  where the HDFS files are hosted.|  
|**File Path**|Specify the name of the HDFS file.|  
|**File format**|Specify the format for the HDFS file. The available options are Text, Avro, and ORC.|  
|**Column delimiter character**|If you select Text format, specify the column delimiter character.|  
|**Column  names in the first data row**|If you select Text format, specify whether the first row in the file contains column names.|  
  
 After you configure these options, select the **Columns** tab to map source columns to destination columns in the data flow.  
  
## See Also  
 [Hadoop Connection Manager](../../Topics\TopicNameNotContainA/Hadoop-Connection-Manager.md)   
 [HDFS File Source](../../Topics\TopicNameNotContainA/HDFS-File-Source.md)  
  
  