---
title: Start the sqlcmd Utility
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
---
# Start the sqlcmd Utility
    
> [!NOTE]  
>  Windows Authentication is the default authentication mode for **sqlcmd**. To use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must specify a user name and password by using the **\-U** and **\-P** options.  
  
> [!NOTE]  
>  By default, [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)] installs as the named instance **sqlexpress**.  
  
### Start the sqlcmd utility and connect to a default instance of SQL Server  
  
1.  On the **Start** menu click **Run**. In the **Open** box type **cmd**, and then click **OK** to open a Command Prompt window. \(If you have not connected to this instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] before, you may have to configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to accept connections.\)  
  
2.  At the command prompt, type **sqlcmd**.  
  
3.  Press ENTER.  
  
     You now have a trusted connection to the default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is running on your computer.  
  
     **1\>** is the **sqlcmd** prompt that specifies the line number. Each time you press ENTER, the number increases by one.  
  
4.  To end the **sqlcmd** session, type **EXIT** at the **sqlcmd** prompt.  
  
### Start the sqlcmd utility and connect to a named instance of SQL Server  
  
1.  Open a Command Prompt window, and type **sqlcmd \-S***myServer\\instanceName*. Replace *myServer\\instanceName* with the name of the computer and the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that you want to connect to.  
  
2.  Press ENTER.  
  
     The **sqlcmd** prompt \(1\>\) indicates that you are connected to the specified instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
    > [!NOTE]  
    >  Entered [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements are stored in a buffer. They are executed as a batch when the GO command is encountered.  
  
## See Also  
 [Run Transact-SQL Script Files Using sqlcmd](../../Topics\TopicNameNotContainA/Run-Transact-SQL-Script-Files-Using-sqlcmd.md)  
  
  