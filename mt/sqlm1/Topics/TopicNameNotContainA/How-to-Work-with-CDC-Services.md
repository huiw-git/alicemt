---
title: How to Work with CDC Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
---
# How to Work with CDC Services
  This procedure describes how to use the CDC Service Configuration Console to prepare a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance to work with Oracle CDC Services and to create a new CDC service.  
  
### To work with CDC services  
  
1.  From the **Start** menu, select the **CDC Service Configuration for Oracle**.  
  
2.  From the left pane, select **Local CDC Services** \(the root level\).  
  
3.  You carry out the one or both of the following tasks:  
  
    -   **Prepare SQL Server**  
  
         Select this option from the **Actions** pane on the right side of the CDC Service Configuration Console.  
  
         You can also right\-click **Local CDC Services** and select **Prepare SQL Server**.  
  
         The Preparing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Instance for Oracle CDC dialog box opens.  
  
         To prepare the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance for Oracle CDC services, the login must have a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login with the `dbcreator` fixed server role. This login is used to create the MSXDBCDC database that is required for adding Oracle CDC Services and, later on, Oracle CDC Instances.  
  
         For information on how to use this dialog box, see [Prepare SQL Server for CDC](../../Topics\TopicNameNotContainA/Prepare-SQL-Server-for-CDC.md). For information on how to enable a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance for CDC, see [How to Prepare SQL Server for CDC](../../Topics\TopicNameNotContainA/How-to-Prepare-SQL-Server-for-CDC.md).  
  
    -   **Create a new CDC service**  
  
         Click **New Service** from the **Actions** pane on the right side of the CDC Service Configuration Console.  
  
         You can also right\-Click **Local CDC Services** and select **New Service**.  
  
         The New Oracle CDC Service dialog box opens.  
  
         For information on how to use this dialog box, see [Create and Edit an Oracle CDC Service](../../Topics\TopicNameNotContainA/Create-and-Edit-an-Oracle-CDC-Service.md). For information on how to create or edit a CDC service, see [How to Create and Edit a CDC Service](../../Topics\TopicNameContainA/How-to-Create-and-Edit-a-CDC-Service.md).  
  
         The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login used by the Oracle CDC Service only needs to be a member of the `public` fixed\-server role, no other privileges are needed. However, to create the Oracle CDC Service, the login must have write permission to the MSXDBCDC database, for example the **db\_owner** database role must be assigned to the login. When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed. Click **OK** in that dialog box to display the Connect to SQL Server dialog box.  
  
         For information on how to enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db\_owner** database role, see [Create and Edit an Oracle CDC Service](../../Topics\TopicNameNotContainA/Create-and-Edit-an-Oracle-CDC-Service.md) and [Connection to SQL Server](../../Topics\TopicNameNotContainA/Connection-to-SQL-Server.md).  
  
## See Also  
 [Work with CDC Services](../../Topics\TopicNameNotContainA/Work-with-CDC-Services.md)  
  
  