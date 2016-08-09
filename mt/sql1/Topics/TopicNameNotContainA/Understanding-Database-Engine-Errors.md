---
title: "Understanding Database Engine Errors"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# Understanding Database Engine Errors
Errors raised by the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] have the attributes described in the following table.  
  
|Attribute|Description|  
|---------------|-----------------|  
|Error number|Each error message has a unique error number.|  
|Error message string|The error message contains diagnostic information about the cause of the error. Many error messages have substitution variables in which information, such as the name of the object generating the error, is inserted.|  
|Severity|The severity indicates how serious the error is. Errors that have a low severity, such as 1 or 2, are information messages or low-level warnings. Errors that have a high severity indicate problems that should be addressed as soon as possible. For more information about severities, see [Database Engine Error Severities](../../Topics/TopicNameNotContainA/Database-Engine-Error-Severities.md).|  
|State|Some error messages can be raised at multiple points in the code for the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)]. For example, an 1105 error can be raised for several different conditions. Each specific condition that raises an error assigns a unique state code.<br /><br /> When you are viewing databases that contain information about known issues, such as the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Knowledge Base, you can use the state number to determine whether the recorded issue is the same as the error you have encountered. For example, if a Knowledge Base Article describes an 1105 error that has a state of 2 and the 1105 error message you received had a state of 3, the error probably has a different cause than the one reported in the article.<br /><br /> A [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] support engineer can also use the state code from an error to find the location in the source code where that error code is being raised. This information might provide additional ideas on how to diagnose the problem.|  
|Procedure name|Is the name of the stored procedure or trigger in which the error has occurred.|  
|Line number|Indicates which statement in a batch, stored procedure, trigger, or function generated the error.|  
  
 All system and user-defined error messages in an instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] are contained in the **sys.messages** catalog view. You can use the RAISERROR statement to return user-defined errors to an application.  
  
 All database APIs, such as the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] **SQLClient** namespace, ActiveX Data Objects (ADO), OLE DB, and Open Database Connectivity (ODBC), report the basic error attributes. This information includes the error number and message string. However, not all the APIs report all the other error attributes.  
  
 Information about an error that occurs in the scope of the TRY block of a TRY…CATCH construct can be obtained in [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] code by using functions such as ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE in the scope of the associated CATCH block. For more information, see [TRY...CATCH (Transact-SQL)](assetId:///248df62a-7334-4bca-8262-235a28f4b07f).  
  
## Examples  
 The following example queries the `sys.messages` catalog view to return a list of all system and user-defined error messages in the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] that have English text (`1033`).  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 For more information, see [sys.messages (Transact-SQL)](assetId:///8c16ecdf-68f4-4a2a-b594-086e3344e58a).  
  
## See Also  
 [sys.messages (Transact-SQL)](assetId:///8c16ecdf-68f4-4a2a-b594-086e3344e58a)   
 [RAISERROR (Transact-SQL)](assetId:///483588bd-021b-4eae-b4ee-216268003e79)   
 [@@ERROR (Transact-SQL)](assetId:///c8b43477-b6c0-49bf-a608-394a0b6cc7a2)   
 [TRY...CATCH (Transact-SQL)](assetId:///248df62a-7334-4bca-8262-235a28f4b07f)   
 [ERROR_LINE (Transact-SQL)](assetId:///47335734-0baf-45a6-8b3b-6c4fd80d2cb8)   
 [ERROR_MESSAGE (Transact-SQL)](assetId:///f32877a6-5f17-418c-a32c-5a1a344b3c45)   
 [ERROR_NUMBER (Transact-SQL)](assetId:///1de85fff-1ca2-4b31-841b-926e571cb150)   
 [ERROR_PROCEDURE (Transact-SQL)](assetId:///b81edbf0-856a-498f-ba87-48ff1426d980)   
 [ERROR_SEVERITY (Transact-SQL)](assetId:///50228f2f-6949-4d2e-8e43-fad11bf973ab)   
 [ERROR_STATE (Transact-SQL)](assetId:///6059af00-83fe-409f-ab7c-daad111bc671)