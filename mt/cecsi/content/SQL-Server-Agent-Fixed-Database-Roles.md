---
title: SQL Server Agent Fixed Database Roles
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 719ce56b-d6b2-414a-88a8-f43b725ebc79
manager: jhubbard
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
# SQL Server Agent Fixed Database Roles
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] has the following **msdb** database fixed database roles, which give administrators finer control over access to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent. The roles listed from least to most privileged access are:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
When users who are not members of one of these roles are connected to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] in [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], the **SQL Server Agent** node in Object Explorer is not visible. A user must be a member of one of these fixed database roles or a member of the **sysadmin** fixed server role to use [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent.  
  
## Permissions of SQL Server Agent Fixed Database Roles  
The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent database role permissions are concentric in relation to one another \-\- more privileged roles inherit the permissions of less privileged roles on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent objects (including alerts, operators, jobs, schedules, and proxies). For example, if members of least\-privileged **SQLAgentUserRole** have been granted access to proxy\_A, members of both **SQLAgentReaderRole** and **SQLAgentOperatorRole** automatically have access to this proxy even though access to proxy\_A has not been explicitly granted to them. This may have security implications, which are discussed in the following sections about each role.  
  
### SQLAgentUserRole Permissions  
**SQLAgentUserRole** is the least privileged of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles. It has permissions on only operators, local jobs, and job schedules. Members of **SQLAgentUserRole** have permissions on only local jobs and job schedules that they own. They cannot use multiserver jobs (master and target server jobs), and they cannot change job ownership to gain access to jobs that they do not already own. **SQLAgentUserRole** members can view a list of available proxies only in the **Job Step Properties** dialog box of [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. Only the **Jobs** node in [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] Object Explorer is visible to members of **SQLAgentUserRole**.  
  
> [!IMPORTANT]  
> Consider the security implications before granting proxy access to members of **the**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]**Agentdatabaseroles**. The **SQLAgentReaderRole** and the **SQLAgentOperatorRole** are automatically members of the **SQLAgentUserRole**. This means that members of **SQLAgentReaderRole** and **SQLAgentOperatorRole** have access to all [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxies that have been granted to the **SQLAgentUserRole** and can use those proxies.  
  
The following table summarizes **SQLAgentUserRole** permissions on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent objects.  
  
|Action|Operators|Local jobs<br /><br />(owned jobs only)|Job schedules<br /><br />(owned schedules only)|Proxies|  
|----------|-------------|-----------------------------------|-------------------------------------------|-----------|  
|Create\/modify\/delete|No|Yes<br /><br />Cannot change job ownership.|Yes|No|  
|View list (enumerate)|Yes<br /><br />Can get list of available operators for use in **sp\_notify\_operator** and the **Job Properties** dialog box of Management Studio.|Yes|Yes|Yes<br /><br />List of proxies only available in the **Job Step Properties** dialog box of Management Studio.|  
|Enable\/disable|No|Yes|Yes|Not applicable|  
|View properties|No|Yes|Yes|No|  
|Execute\/stop\/start|Not applicable|Yes|Not applicable|Not applicable|  
|View job history|Not applicable|Yes|Not applicable|Not applicable|  
|Delete job history|Not applicable|No<br /><br />Members of **SQLAgentUserRole** must explicitly be granted the EXECUTE permission on **sp\_purge\_jobhistory** to delete job history on jobs that they own. They cannot delete job history for any other jobs.|Not applicable|Not applicable|  
|Attach\/detach|Not applicable|Not applicable|Yes|Not applicable|  
  
### SQLAgentReaderRole Permissions  
**SQLAgentReaderRole** includes all the **SQLAgentUserRole** permissions as well as permissions to view the list of available multiserver jobs, their properties, and their history. Members of this role can also view the list of all available jobs and job schedules and their properties, not just those jobs and job schedules that they own. **SQLAgentReaderRole** members cannot change job ownership to gain access to jobs that they do not already own. Only the **Jobs** node in [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] Object Explorer is visible to members of the **SQLAgentReaderRole**.  
  
> [!IMPORTANT]  
> Consider the security implications before granting proxy access to members of **the**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]**Agentdatabaseroles**. Members of **SQLAgentReaderRole** are automatically members of the **SQLAgentUserRole**. This means that members of **SQLAgentReaderRole** have access to all [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxies that have been granted to **SQLAgentUserRole** and can use those proxies.  
  
The following table summarizes **SQLAgentReaderRole** permissions on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent objects.  
  
|Action|Operators|Local jobs|Multiserver jobs|Job schedules|Proxies|  
|----------|-------------|--------------|--------------------|-----------------|-----------|  
|Create\/modify\/delete|No|Yes  (owned jobs only)<br /><br />Cannot change job ownership.|No|Yes (owned schedules only)|No|  
|View list (enumerate)|Yes<br /><br />Can get list of available operators for use in **sp\_notify\_operator** and the **Job Properties** dialog box of Management Studio.|Yes|Yes|Yes|Yes<br /><br />List of proxies only available in the **Job Step Properties** dialog box of Management Studio.|  
|Enable\/disable|No|Yes (owned jobs only)|No|Yes (owned schedules only)|Not applicable|  
|View properties|No|Yes|Yes|Yes|No|  
|Edit properties|No|Yes (owned jobs only)|No|Yes (owned schedules only)|No|  
|Execute\/stop\/start|Not applicable|Yes (owned jobs only)|No|Not applicable|Not applicable|  
|View job history|Not applicable|Yes|Yes|Not applicable|Not applicable|  
|Delete job history|Not applicable|No<br /><br />Members of **SQLAgentReaderRole** must explicitly be granted the EXECUTE permission on **sp\_purge\_jobhistory** to delete job history on jobs that they own. They cannot delete job history for any other jobs.|No|Not applicable|Not applicable|  
|Attach\/detach|Not applicable|Not applicable|Not applicable|Yes (owned schedules only)|Not applicable|  
  
### SQLAgentOperatorRole Permissions  
**SQLAgentOperatorRole** is the most privileged of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles. It includes all the permissions of **SQLAgentUserRole** and **SQLAgentReaderRole**. Members of this role can also view properties for operators and proxies, and enumerate available proxies and alerts on the server.  
  
**SQLAgentOperatorRole** members have additional permissions on local jobs and schedules. They can execute, stop, or start all local jobs, and they can delete the job history for any local job on the server. They can also enable or disable all local jobs and schedules on the server. To enable or disable local jobs or schedules, members of this role must use the stored procedures **sp\_update\_job** and **sp\_update\_schedule**. Only the parameters that specify the job or schedule name or identifier and the **@enabled** parameter can be specified by members of **SQLAgentOperatorRole**. If they specify any other parameters, execution of these stored procedures fails. **SQLAgentOperatorRole** members cannot change job ownership to gain access to jobs that they do not already own.  
  
The **Jobs**, **Alerts**, **Operators**, and **Proxies** nodes in [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] Object Explorer are visible to members of **SQLAgentOperatorRole**. Only the **Error Logs** node is not visible to members of this role.  
  
> [!IMPORTANT]  
> Consider the security implications before granting proxy access to members of **the**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]**Agentdatabaseroles**. Members of **SQLAgentOperatorRole** are automatically members of **SQLAgentUserRole** and **SQLAgentReaderRole**. This means that members of **SQLAgentOperatorRole** have access to all [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent proxies that have been granted to either **SQLAgentUserRole** or **SQLAgentReaderRole** and can use those proxies.  
  
The following table summarizes **SQLAgentOperatorRole** permissions on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent objects.  
  
|Action|Alerts|Operators|Local jobs|Multiserver jobs|Job schedules|Proxies|  
|----------|----------|-------------|--------------|--------------------|-----------------|-----------|  
|Create\/modify\/delete|No|No|Yes  (owned jobs only)<br /><br />Cannot change job ownership.|No|Yes (owned schedules only)|No|  
|View list (enumerate)|Yes|Yes<br /><br />Can get list of available operators for use in **sp\_notify\_operator** and the **Job Properties** dialog box of Management Studio.|Yes|Yes|Yes|Yes|  
|Enable\/disable|No|No|Yes<br /><br />**SQLAgentOperatorRole** members can enable or disable local jobs they do not own by using the stored procedure **sp\_update\_job** and specifying values for the **@enabled** and the **@job\_id** (or **@job\_name**) parameters. If a member of this role specifies any other parameters for this stored procedure, execution of the procedure will fail.|No|Yes<br /><br />**SQLAgentOperatorRole** members can enable or disable schedules they do not own by using the stored procedure **sp\_update\_schedule** and specifying values for the **@enabled** and the **@schedule\_id** (or **@name**) parameters. If a member of this role specifies any other parameters for this stored procedure, execution of the procedure will fail.|Not applicable|  
|View properties|Yes|Yes|Yes|Yes|Yes|Yes|  
|Edit properties|No|No|Yes (owned jobs only)|No|Yes (owned schedules only)|No|  
|Execute\/stop\/start|Not applicable|Not applicable|Yes|No|Not applicable|Not applicable|  
|View job history|Not applicable|Not applicable|Yes|Yes|Not applicable|Not applicable|  
|Delete job history|Not applicable|Not applicable|Yes|No|Not applicable|Not applicable|  
|Attach\/detach|Not applicable|Not applicable|Not applicable|Not applicable|Yes (owned schedules only)|Not applicable|  
  
## Assigning Users Multiple Roles  
Members of the **sysadmin** fixed server role have access to all [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent functionality. If a user is not a member of the **sysadmin** role, but is a member of more than one [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database role, it is important to remember the concentric permissions model of these roles. Because more privileged roles always contain all the permissions of less privileged roles, a user who is a member of more than one role automatically has the permissions associated with the most privileged role that the user is a member of.  
  
## See Also  
[Implement SQL Server Agent Security](../content/Implement-SQL-Server-Agent-Security.md)  
[sp_update_job (Transact-SQL)](assetId:///cbdfea38-9e42-47f3-8fc8-5978b82e2623)  
[sp_update_schedule (Transact-SQL)](assetId:///97b3119b-e43e-447a-bbfb-0b5499e2fefe)  
[sp_notify_operator (Transact-SQL)](assetId:///c440f5c9-9884-4196-b07c-55d87afb17c3)  
[sp_purge_jobhistory (Transact-SQL)](assetId:///237f9bad-636d-4262-9bfb-66c034a43e88)  
  
