---
title: "XML System Stored Procedures"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# XML System Stored Procedures
SQL Server provides the following system stored procedures that are used together with OPENXML:  
  
-   [sp_xml_preparedocument (Transact-SQL)](assetId:///95f41cff-c52a-4182-8ac6-bf49369d214c)  
  
-   [sp_xml_removedocument](assetId:///f9dca50a-8baf-4170-90bc-e72783ce5b73)  
  
 To write queries by using OPENXML, you must first create an internal representation of the XML document by calling **sp_xml_preparedocument**. The stored procedure returns a handle to the internal representation of the XML document. This handle is then passed to OPENXML. OPENXML provides rowset views of the document based on XPaths. Specifically, this is one row pattern and one or more column patterns.  
  
> [!NOTE]  
>  The document handle that is returned by **sp_xml_preparedocument** is valid for the duration of the session.  
  
 The internal representation of an XML document can be removed from memory by calling the **sp_xml_removedocument** system stored procedure.  
  
## See Also  
 [OPENXML](assetId:///8088b114-7d01-435a-8e0d-b81abacc86d6)   
 [OPENXML (SQL Server)](../../Topics/TopicNameNotContainA/OPENXML--SQL-Server-.md)