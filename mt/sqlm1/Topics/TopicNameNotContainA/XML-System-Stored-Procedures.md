---
title: XML System Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
---
# XML System Stored Procedures
  SQL Server provides the following system stored procedures that are used together with OPENXML:  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](../Topic/sp_xml_preparedocument%20\(Transact-SQL\).md)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](../Topic/sp_xml_removedocument%20\(Transact-SQL\).md)  
  
 To write queries by using OPENXML, you must first create an internal representation of the XML document by calling **sp\_xml\_preparedocument**. The stored procedure returns a handle to the internal representation of the XML document. This handle is then passed to OPENXML. OPENXML provides rowset views of the document based on XPaths. Specifically, this is one row pattern and one or more column patterns.  
  
> [!NOTE]  
>  The document handle that is returned by **sp\_xml\_preparedocument** is valid for the duration of the session.  
  
 The internal representation of an XML document can be removed from memory by calling the **sp\_xml\_removedocument** system stored procedure.  
  
## See Also  
 [OPENXML &#40;Transact-SQL&#41;](../Topic/OPENXML%20\(Transact-SQL\).md)   
 [OPENXML &#40;SQL Server&#41;](../Topic/OPENXML%20\(SQL%20Server\).md)  
  
  