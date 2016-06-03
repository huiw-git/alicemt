---
title: Using Try..Catch in Natively Compiled Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f730e70c-4f92-411d-9984-289e241e43ee
robots: noindex,nofollow
---
# Using Try..Catch in Natively Compiled Stored Procedures
  You can use try..catch blocks inside a natively compiled stored procedure. The following constructs are supported:  
  
-   ERROR\_LINE  
  
-   ERROR\_MESSAGE  
  
-   ERROR\_NUMBER  
  
-   ERROR\_PROCEDURE  
  
-   ERROR\_SEVERITY  
  
-   ERROR\_STATE  
  
```tsql  
CREATE PROCEDURE test_try_catch  
with native_compilation, schemabinding, execute as owner   
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
  BEGIN TRY  
    -- generate error  
    declare @i int = 1,  
    @j int = 0  
    select @i/@j  
  END TRY  
  BEGIN CATCH  
    -- Execute error retrieval routine.  
    SELECT  
    ERROR_SEVERITY() AS ErrorSeverity  
    ,ERROR_STATE() AS ErrorState  
    ,ERROR_PROCEDURE() AS ErrorProcedure  
    ,ERROR_LINE() AS ErrorLine  
    ,ERROR_MESSAGE() AS ErrorMessage  
  END CATCH  
end  
go  
  
exec test_try_catch  
go  
```  
  
## See Also  
 [Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)  
  
  