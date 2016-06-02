---
title: Hadoop Hive Task
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10ff37c0-9f3f-442a-889b-c351afbdc74c
---
# Hadoop Hive Task
  Use the Hadoop Hive Task to run Hive script on a Hadoop cluster.  
  
 To add a Hadoop Hive Task, drag and drop it to the designer. Then double\-click on the task, or right\-click and click **Edit**, to open the **Hadoop Hive Task Editor** dialog box.  
  
 ![Hadoop Hive Task Editor](../../Images\Image\ImageNotContaina/Hadoop-hive-task.png "Hadoop-hive-task")  
  
## Options  
 Configure the following options in the **Hadoop Hive Task Editor** dialog box.  
  
|Field|Description|  
|-----------|-----------------|  
|**Hadoop Connection**|Specify an existing Hadoop Connection Manager or create a new one. This connection manager indicates  where the the WebHCat service is hosted.|  
|**SourceType**|Specify the source type of the query. Available values are **ScriptFile** and **DirectInput**.|  
|**InlineScript**|When the value of **SourceType** is **DirectInput**, specify the hive script.|  
|**HadoopScriptFilePath**|When the value of **SourceType** is **ScriptFile**, specify the script file path on Hadoop.|  
|**TimeoutInMinutes**|Specify a timeout value in minutes. The Hadoop job stops if it has not finished before the timeout elapses. Specify 0 to schedule the Hadoop job to run asynchronously.|  
  
## See Also  
 [Hadoop Connection Manager](../../Topics\TopicNameNotContainA/Hadoop-Connection-Manager.md)  
  
  