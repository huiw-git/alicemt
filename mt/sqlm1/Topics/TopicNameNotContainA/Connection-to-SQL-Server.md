---
title: Connection to SQL Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
---
# Connection to SQL Server
  When a login without a database role that includes write permission \(for example the **db\_owner** role\) to the MSXDBCDC database attempts to create an Oracle CDC instanced, the Connect to SQL Server dialog box is displayed.  
  
 In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db\_owner** database role to create the new Oracle CDC instance.  
  
 Enter the following information in the Connect to SQL Server dialog box.  
  
### Server Name  
 Type the name of the server where the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is located.  
  
### Authentication  
 Select one of the following:  
  
-   Windows Authentication  
  
-   **SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] you are connecting to.  
  
### Options  
 Click the arrow to view available options to be configured. You can choose to leave these options with their default value. The available options are:  
  
-   **Connection Timeout**: Type the time \(in seconds\) the program waits for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connection to be established before producing a timeout error. The default value is **15**.  
  
-   **Execution Timeout**: Type the time \(in seconds\) that the program waits for SQL command execution to finish before producing a timeout error. The default value is **30**.  
  
-   **Encrypt Connection**: Select **Encrypt Connection** to ensure that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connection that being established is encrypted to guarantee privacy.  
  
-   **Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.  
  
## See Also  
 [SQL Server Connection Required Permissions for the CDC Service](../../Topics\TopicNameNotContainA/SQL-Server-Connection-Required-Permissions-for-the-CDC-Service.md)  
  
  