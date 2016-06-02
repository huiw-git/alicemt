---
title: Grant DQS Roles to Users
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
---
# Grant DQS Roles to Users
  This topic describes how to create SQL logins based on a Windows principal, and grant [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) roles on the DQS\_MAIN database.  
  
## Prerequisites  
  
-   You must have completed the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] installation by running the DQSInstaller.exe file. For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](../../Topics\TopicNameNotContainA/Run-DQSInstaller.exe-to-Complete-Data-Quality-Server-Installation.md).  
  
-   Your Windows user account must be a member of the appropriate fixed server role \(such as securityadmin, serveradmin, or sysadmin\) to create SQL login, and grant them DQS roles.  
  
### To create SQL login and grant DQS roles  
  
1.  Start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
2.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], expand your SQL Server instance, and then expand **Security**.  
  
3.  Right\-click the **Security** folder, point to **New**, and then click **Login**.  
  
4.  In the **Login – New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.  
  
5.  After the user is validated, click the **User Mapping** page in the left pane.  
  
6.  In the right pane, select the check box under the **Map** column for the **DQS\_MAIN** database, and then select the **dqs\_administrator**, **dqs\_kb\_editor**, or **dqs\_kb\_operator** check box in the **Database role membership for: DQS\_MAIN** pane, depending on the access level needed for the user. For information about the three DQS roles, see [DQS Security](../../Topics\TopicNameNotContainA/DQS-Security.md).  
  
7.  In the **Login – New** dialog box, click **OK** to apply the changes.  
  
    > [!NOTE]  
    >  If you grant the **dqs\_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes \(**dq\_kb\_editor** and **dqs\_kb\_operator**\) are also selected.  
  
## Next Steps  
 Try logging on to [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] by using the Windows user account for which you just created a SQL login, and granted a DQS role.  
  
## See Also  
 [Install Data Quality Services](../../Topics\TopicNameNotContainA/Install-Data-Quality-Services.md)   
 [Create a Login](../../Topics\TopicNameContainA/Create-a-Login.md)  
  
  