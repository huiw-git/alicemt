---
title: "Flat File Source Editor (Connection Manager Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Flat File Source Editor (Connection Manager Page)
Use the **Connection Manager** page of the **Flat File Source Editor** dialog box to select the connection manager that the Flat File source will use. The Flat File source reads data from a text file, which can be in a delimited, fixed width, or mixed format.  
  
 A Flat File source can use one of the following types of connection managers:  
  
-   A Flat File connection manager if the source is a single flat file. For more information, see [Flat File Connection Manager](../../Topics/TopicNameNotContainA/Flat-File-Connection-Manager.md).  
  
-   A Multiple Flat Files connection manager if the source is multiple flat files and the Data Flow task is inside a loop container, such as the For Loop container. On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides. For more information, see [Multiple Flat Files Connection Manager](../../Topics/TopicNameNotContainA/Multiple-Flat-Files-Connection-Manager.md).  
  
 To learn more about the Flat File source, see [Flat File Source](../../Topics/TopicNameNotContainA/Flat-File-Source.md).  
  
## Options  
 **Flat file connection manager**  
 Select an existing connection manager from the list, or create a new connection manager by clicking **New**.  
  
 **New**  
 Create a new connection manager by using the **Flat File Connection Manager Editor** dialog box.  
  
 **Retain null values from the source as null values in the data flow**  
 Specify whether to keep null values when data is extracted. The default value of this property is **false**. When this value is f**alse**, the Flat File source replaces null values from the source data with appropriate default values for each column, such as empty strings for string columns and zero for numeric columns.  
  
 **Preview**  
 Preview results by using the **Data View** dialog box. Preview can display up to 200 rows.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Flat File Source Editor (Columns Page)](../../Topics/TopicNameNotContainA/Flat-File-Source-Editor--Columns-Page-.md)   
 [Flat File Source Editor (Error Output Page)](../../Topics/TopicNameNotContainA/Flat-File-Source-Editor--Error-Output-Page-.md)   
 [Flat File Connection Manager](../../Topics/TopicNameNotContainA/Flat-File-Connection-Manager.md)