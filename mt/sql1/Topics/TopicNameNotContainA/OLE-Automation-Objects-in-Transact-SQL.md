---
title: OLE Automation Objects in Transact-SQL
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-ole
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
---
# OLE Automation Objects in Transact-SQL
  [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] includes several system stored procedures that allow OLE Automation objects to be referenced in [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] batches, stored procedures, and triggers. These system stored procedures run as extended stored procedures, and the OLE Automation objects that are executed through the stored procedures run in the address space of an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)] in the same way that an extended stored procedure runs.  
  
 The OLE Automation stored procedures enable [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] batches to reference SQL-DMO objects and custom OLE Automation objects, such as objects that expose the **IDispatch** interface. A custom in-process OLE server that is created by using [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[vbprvb](../../Topics/TopicNameContainA/includes/vbprvb_md.md)] must have an error handler (specified with the **On Error GoTo** statement) for the **Class_Initialize** and **Class_Terminate** subroutines. Unhandled errors in the **Class_Initialize** and **Class_Terminate** subroutines can cause unpredictable errors, such as an access violation in an instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)]. Error handlers for other subroutines are also recommended.  
  
 The first step when using an OLE Automation object in [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] is to call the **sp_OACreate** system stored procedure to create an instance of the object in the address space of the instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)].  
  
 After an instance of the object has been created, call the following stored procedures to work with the properties, methods, and error information related to the object:  
  
-   **sp_OAGetProperty** obtains the value of a property.  
  
-   **sp_OASetProperty** sets the value of a property.  
  
-   **sp_OAMethod** calls a method.  
  
-   **sp_OAGetErrorInfo** obtains the most recent error information.  
  
 When there is no more need for the object, call **sp_OADestroy** to deallocate the instance of the object created by using **sp_OACreate**.  
  
 OLE Automation objects return data through property values and methods. **sp_OAGetProperty** and **sp_OAMethod** return these data values in the form of a result set.  
  
 The scope of an OLE Automation object is a batch. All references to the object must be contained in a single batch, stored procedure, or trigger.  
  
 When it references objects, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] OLE Automation objects support traversing the referenced object to other objects that it contains. For example, when using the SQL-DMO **SQLServer** object, references can be made to databases and tables contained on that server.  
  
## Related Content  
 [Object Hierarchy Syntax &#40;Transact-SQL&#41;](../Topic/Object%20Hierarchy%20Syntax%20\(Transact-SQL\).md)  
  
 [Surface Area Configuration](../../Topics/TopicNameNotContainA/Surface-Area-Configuration.md)  
  
 [Ole Automation Procedures Server Configuration Option](../../Topics/TopicNameNotContainA/Ole-Automation-Procedures-Server-Configuration-Option.md)  
  
 [sp_OACreate &#40;Transact-SQL&#41;](../Topic/sp_OACreate%20\(Transact-SQL\).md)  
  
 [sp_OAGetProperty &#40;Transact-SQL&#41;](../Topic/sp_OAGetProperty%20\(Transact-SQL\).md)  
  
 [sp_OASetProperty &#40;Transact-SQL&#41;](../Topic/sp_OASetProperty%20\(Transact-SQL\).md)  
  
 [sp_OAMethod &#40;Transact-SQL&#41;](../Topic/sp_OAMethod%20\(Transact-SQL\).md)  
  
 [sp_OAGetErrorInfo &#40;Transact-SQL&#41;](../Topic/sp_OAGetErrorInfo%20\(Transact-SQL\).md)  
  
 [sp_OADestroy &#40;Transact-SQL&#41;](../Topic/sp_OADestroy%20\(Transact-SQL\).md)  
  
  