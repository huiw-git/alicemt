---
title: How to Create and Edit a CDC Service
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
---
# How to Create and Edit a CDC Service
  These procedures describe how to create and edit a new Oracle CDC Service from the CDC Service Configuration Console.  
  
 This procedure requires a Windows user with administrator privileges on the computer where the Oracle CDC service is configured.  
  
### To create a new CDC service  
  
1.  From the **Start** menu, select **CDC Service Configuration for Oracle**.  
  
2.  From the left pane, right click Local CDC Services and select New Service  
  
     You can also click **New Service** from the **Actions** pane.  
  
3.  Type or enter the required information in the New Oracle CDC Service dialog box. See [Create and Edit an Oracle CDC Service](../../Topics\TopicNameNotContainA/Create-and-Edit-an-Oracle-CDC-Service.md) for information on how to enter information in the New Oracle CDC Service dialog box.  
  
     The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login provided in the New Oracle CDC Service dialog box is used by the Oracle CDC Service when the service runs. This login only needs to be a member of the public fixed\-server role, no other privileges are needed. Once new Oracle CDC Instances are added, that login receives **db\_owner** access to the associated [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] CDC databases.  
  
4.  When you finish entering the required information, click **OK**.  
  
     To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login with an update access to the MSXDBCDC database.  
  
     For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](../../Topics\TopicNameNotContainA/Connection-to-SQL-Server.md).  
  
5.  Click **OK** to close the New Oracle CDC Service dialog box.  
  
### To edit a CDC service  
  
1.  From the **Start** menu, select **CDC Service Configuration for Oracle**.  
  
2.  From the left pane, select **Local CDC Services** then right\-click the local service you want to edit and select **Properties**.  
  
     You can also select the service you are working with in the middle and then from the **Actions** pane, click **Properties**.  
  
3.  Type or enter the required information in the CDC Service Properties dialog box. See [Create and Edit an Oracle CDC Service](../../Topics\TopicNameNotContainA/Create-and-Edit-an-Oracle-CDC-Service.md) for information on how to enter information in the CDC Service Properties dialog box.  
  
4.  When you finish entering the required information, Click **OK**, the Connect to SQL Server dialog box opens.  
  
     When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed. Click **OK** in that dialog box to display the Connect to SQL Server dialog box. In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db\_owner** database role.  
  
     For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](../../Topics\TopicNameNotContainA/Connection-to-SQL-Server.md).  
  
5.  Click **OK** in the Connect to Oracle dialog box. Both dialog boxes close and the service is updated and registered.  
  
## See Also  
 [Change Data Capture Designer for Oracle by Attunity](../../Topics\TopicNameNotContainA/Change-Data-Capture-Designer-for-Oracle-by-Attunity.md)   
 [Create and Edit an Oracle CDC Service](../../Topics\TopicNameNotContainA/Create-and-Edit-an-Oracle-CDC-Service.md)  
  
  