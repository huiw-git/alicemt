---
title: Project Settings(Loading System objects) (OracleToSQL)
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
manager: b-tomb
---
# Project Settings(Loading System objects) (OracleToSQL)
The Loading System Objects page of the **Project Settings** dialog box lets you specify which Oracle system objects SSMA converts and loads into [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
The Loading System Objects pane is available in the **Project Settings** and **Default Project Settings** dialog boxes:  
  
-   To specify settings for all SSMA projects, on the **Tools** menu, select **Default Project Settings**, select migration project type for which settings are required to be viewed or changed from **Migration Target Version** drop down click **General** at the bottom of the left pane, and then click **Loading System Objects**.  
  
-   To specify settings for the current project, on the **Tools** menu, select **Project Settings**, click **General** at the bottom of the left pane, and then click **Loading System Objects**.  
  
## Default Settings  
Converting system objects consumes system resources and takes time. To improve performance, SSMA selects only the most frequently used system objects, as shown in the following list:  
  
-   SYS.DBMS\_OUTPUT  
  
-   SYS.DBMS\_PIPE  
  
-   SYS.DBMS\_UTILITY  
  
-   SYS.STANDARD  
  
-   SYS.UTL\_FILE  
  
-   SYS.DBMS\_LOB  
  
-   SYS.DBMS\_SQL  
  
-   SYS.DBMS\_SESSION  
  
If your Oracle objects refer to additional system objects, you should select those objects. If you do not select the system objects that are referenced by your Oracle database objects, SSMA will report conversion errors. If you receive conversion errors caused by missing system objects, select the missing objects in this dialog box. You can then repeat the conversion as necessary.  
  
