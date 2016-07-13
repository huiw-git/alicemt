---
title: Make a Master Server
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
manager:jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Make a Master Server
This topic describes how to make a master server [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../content/includes/tsql_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To make a master server, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server. Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:  
  
-   The master server registry subkey **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\<&#42;instance\_name&#42;>\\SQL Server Agent\\AllowDownloadedJobsToMatchProxyName** (REG\_DWORD) is set to 1 (true). By default, this subkey is set to 0 (false).  
  
-   A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.  
  
If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error\_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:  
  
-   "The job step requires a proxy account, however proxy matching is disabled on the target server."  
  
    To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.  
  
-   "Proxy not found."  
  
    To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.  
  
#### <a name="Permissions"></a>Permissions  
Permissions to execute this procedure default to members of the **sysadmin** fixed server role.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To make a master server  
  
1.  In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Right\-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Make this a Master**. The **Master Server Wizard** guides you through the process of making a master server and adding target servers.  
  
3.  From the **Master Server Operator** page, configure an operator for the master server To send notifications to operators by using e\-mail or pagers, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent must be configured to send e\-mail. To send notifications to operators by using **net send**, the Messenger service must be running on the server where [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent resides.  
  
    **E\-mail address**  
    Sets the e\-mail address for the operator.  
  
    **Pager address**  
    Sets the pager e\-mail address for the operator.  
  
    **Net send address**  
    Sets the **net send** address for the operator.  
  
4.  From the **Target Server** page, select target servers for the master server.  
  
    **Registered Servers**  
    Lists the servers registered in Microsoft [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] that are not already target servers.  
  
    **Target Servers**  
    Lists the servers that are target servers.  
  
    **>**  
    Move the selected server to the target server list.  
  
    **>>**  
    Move all servers to the target server list.  
  
    **<**  
    Remove the selected server from the target server list.  
  
    **<<**  
    Remove all servers from the target server list.  
  
    **Add connection**  
    Add a server to the target server list without registering the server.  
  
    **Connection**  
    Change the connection properties for the selected server.  
  
5.  From the **Master Server Login Credentials** page to specify if you want to create a new login for the target server, if necessary, and assign it rights to the master server.  
  
    **Create a new login if necessary and assign it rights to the MSX**  
    Create a new login on the target server if the login specified does not already exist.  
  
## <a name="TsqlProcedure"></a>Using Transact\-SQL  
  
#### To make a master server  
  
1.  Connect to the [!INCLUDE[ssDE](../content/includes/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example enlists the current server into the AdventureWorks1 master server. The location for the current server is Building 21, Room 309, Rack 5.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
For more information, see [sp_msx_enlist (Transact-SQL)](assetId:///ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## See Also  
[Create a Multiserver Environment](../content/Create-a-Multiserver-Environment.md)  
[Automated Administration Across an Enterprise](../content/Automated-Administration-Across-an-Enterprise.md)  
  
