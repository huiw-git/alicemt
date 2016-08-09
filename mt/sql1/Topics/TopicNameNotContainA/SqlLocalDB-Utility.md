---
title: "SqlLocalDB Utility"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
caps.latest.revision: 18
caps.handback.revision: 0
manager: jhubbard
---
# SqlLocalDB Utility
Use the **SqlLocalDB** utility to create an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssExpCurrent](../../Topics/TopicNameNotContainA/tokens/ssExpCurrent_md.md)]**LocalDB**. The **SqlLocalDB** utility (SqlLocalDB.exe) is a simple command line tool to enable users and developers to create and manage an instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB**. For information about how to use **LocalDB**, see [SQL Server 2016 Express LocalDB](../../Topics/TopicNameNotContainA/SQL-Server-2016-Express-LocalDB.md).  
  
## Syntax  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name>  <instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] [" <user_SID> " | " <user_account> " ] " <private-name> " " <shared-name> "  
    | [ unshare  | u ] " <shared-name> "  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## Arguments  
 [ **create** &#124; **c** ] *<instance-name>* *<instance-version>* [**-s** ]  
 Creates a new of instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB**. **SqlLocalDB** uses the version of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)] binaries specified by *<instance-version>* argument. The version number is specified in numeric format with at least one decimal. The minor version numbers (service packs) are optional. For example the following two version numbers are both acceptable: 11.0, or 11.0.1186. The specified version must be installed on the computer. If not specified, the version number defaults to the version of the **SqlLocalDB** utility. Adding **–s** starts the new instance of **LocalDB**.  
  
 [ **share** &#124; **h** ]  
 Shares the specified private instance of **LocalDB** using the specified shared name. If the user SID or account name is omitted, it defaults to the current user.  
  
 [ **unshared** &#124; **u** ]  
 Stops the sharing of the specified shared instance of **LocalDB**.  
  
 [ **delete** &#124; **d** ] *<instance-name>*  
 Deletes the specified instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB**.  
  
 [ **start** &#124; **s** ] "*<instance-name>*"  
 Starts the specified instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB**. When successful the statement returns the named pipe address of the **LocalDB**.  
  
 [ **stop** &#124; **p** ] *<instance-name>* [**-i** ] [**-k** ]  
 Stops the specified instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB**. Adding **–i** requests the instance shutdown with the **NOWAIT** option. Adding **–k** kills the instance process without contacting it.  
  
 [ **info** &#124; **i** ] [ *<instance-name>* ]  
 Lists all instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB** owned by the current user.  
  
 *<instance-name>* returns the name, version, state (Running or Stopped), last start time for the specified instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB**, and the local pipe name of the **LocalDB**.  
  
 [ **trace** &#124; **t** ] **on** &#124; **off**  
 **trace on** enables tracing for the **SqlLocalDB** API calls for the current user. **trace off** disables tracing.  
  
 **-?**  
 Returns brief descriptions of each **SqlLocalDB** option.  
  
## Remarks  
 The *instance name* argument must follow the rules for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] identifiers or it must be enclosed in double quotes.  
  
 Executing SqlLocalDB without arguments returns the help text.  
  
 Operations other than start can only be performed on an instance belonging to currently logged in user. An SQLLOCALDB Instance, when shared, can only be started and stopped by the owner of the instance.  
  
## Examples  
  
### A. Creating an Instance of LocalDB  
 The following example creates an instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)]**LocalDB** named `DEPARTMENT` using the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] binaries and starts the instance.  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### B. Working with a Shared Instance of LocalDB  
 Open a command prompt using Administrator privileges.  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd –S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 Execute the following code to connect to the shared instance of **LocalDB** using the `NewLogin` login.  
  
```  
sqlcmd –S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## See Also  
 [SQL Server 2016 Express LocalDB](../../Topics/TopicNameNotContainA/SQL-Server-2016-Express-LocalDB.md)