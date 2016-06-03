---
title: Log In to an Instance of SQL Server (Command Prompt)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
---
# Log In to an Instance of SQL Server (Command Prompt)
  This topic describes how to test connectivity to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], use the **sqlcmd** utility.  
  
##  <a name="SSMSProcedure"></a>  
  
#### To log in to the default instance of SQL Server  
  
1.  From a command prompt, enter the following command to connect by using Windows Authentication:  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### To log in to a named instance of SQL Server  
  
1.  From a command prompt, enter the following command to connect by using Windows Authentication:  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## See Also  
 [sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)   
 [osql Utility](../../Topics\TopicNameNotContainA/osql-Utility.md)  
  
  