---
title: Configure and Manage Advanced Analytics Extensions
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
---
# Configure and Manage Advanced Analytics Extensions
  After you have installed [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], you can make minor changes in the configuration of the R runtime and other services associated with [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] .  
  
  
 **In This Topic**  
  
-   [Provisioning User Accounts for SQL Server R Services](#bkmk_Provisioning)  
  
-   [Managing Memory Use by R Processes](#bkmk_ManagingMemory)  
  
-   [Changing the Service Defaults using the Configuration File](#bkmk_ChangingConfig)  
  
##  <a name="bkmk_Provisioning"></a> Provisioning User Accounts for SQL Server R Services  
 R runtime processes in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] run in the context of low\-privilege local user accounts. Running R runtime processes in individual low\-privilege accounts has the following benefits:  
  
-   Reduce privileges of the R runtime processes running on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer  
  
-   Provide isolation between the R runtime sessions  
  
 As part of installation process in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], a new Windows *user account pool* is created that contains the local user accounts required for running the R runtime process. You can modify the number of users if needed to support R. Your database administrator must also give this group permission to connect to any instance where R Services has been enabled. For more information, see [Modify the User Account Pool for SQL Server R Services](../../Topics\TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md).  
  
 However, an access control list \(ACL\) can be defined for sensitive resources on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to deny access to this group to prevent the R runtime process from getting access to the resources.  
  
-   The user account pool is linked to a specific instance.  For each instance on which R script has been enabled, a separate pool of worker accounts are created. Accounts cannot be shared between instances.
  
-   User account names in the pool are of the format SQLInstanceName*nn*. For example, if you are using the default instance as your R server, the user account pool supports account names such as MSSQLSERVER01, MSSQLSERVER02, and so forth.  
  
-   The size of the user account pool is static and the default value is 20. The number of R runtime sessions that can be launched simultaneously is limited by the size of this user account pool. However, this limit can be changed by an administrator by using SQL Server Configuration Manager.  
  
-   The users in the user account pool can be split evenly between users of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and data scientists connecting from remote clients.  
  
-   Password for the user accounts are auto\-generated at random. However, to make it easier to identify related accounts, you can configure a prefix to use with all passwords.  
  
 For more information about how to make changes to the user account pool, see [Modify the User Account Pool for SQL Server R Services](../../Topics\TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md).  
  
##  <a name="bkmk_ManagingMemory"></a> Managing Memory Use by R Processes  
 By default, the R runtime processes associated with [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] are limited to using no more than 20% of total machine memory. However, this limit can be increased by the administrator, if needed. For more information about how to determine how much memory is currently used, see [Configuration Properties](#bkmk_properties).  
  
 Generally, this amount will be inadequate for serious R tasks such as training model or predicting on many rows of data. You might need to reduce the amount of memory reserved for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(or for other services\) and use Resource Governor to define an external resource pool or pools and allocate. For more information, see [Resource Governance for R Services](../../Topics\TopicNameNotContainA/Resource-Governance-for-R-Services.md).  
  
##  <a name="bkmk_ChangingConfig"></a> Changing the Service Defaults using SQL Server Configuration File  
 You can control some aspects of the behavior of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] by editing the [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] configuration file. This file is created during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup and by default is saved as a plain text file in the following location:  
  
```  
<SQL Instance Path>\binn\rlauncher.config  
```  
  
 You must be an administrator on the computer that is running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to make changes to this file. If you edit the file, we recommend that you make a backup copy before saving changes.  
  
 For example, to use Notepad to open the configuration file for the default instance \(MSSQLSERVER\) , you would open a command prompt as administrator, and type the following command:  
  
```  
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
  
```  
  
###  <a name="bkmk_properties"></a> Configuration Properties  
 All settings take the form of a key\-value pair, with each setting on a separate line. For example, this property specifies that no more than 20 percent of system memory can be used by R processes:  
  
 Default: `MEMORY_LIMIT_PERCENT=20`  
  
 The following table lists each of the settings supported for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], with the permissible values.  
  
|Setting name|Value type|Default|Description|  
|------------------|----------------|-------------|-----------------|  
|JOB\_CLEANUP\_ON\_EXIT|Integer<br /><br /> 0 \= Disabled<br /><br /> 1 \= Enabled|1<br /><br /> Log files are removed on exit|Specifies whether the temporary working folder created for each R session should be cleaned up after the R session is completed. This setting is useful for debugging.<br /><br /> Note: This is an internal setting only – do not change this value.|  
|LOG\_DIRECTORY|String \(path\)|\<SQL Instance Path\>\\MSSQL\\Log E.g. C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Log|Indicates where the log files rlauncher.log and xp\_callrre.log are stored.<br /><br /> Note: This is an internal setting only – do not change this value.|  
|MEMORY\_LIMIT\_PERCENT|Integer<br /><br /> Range \= from 0 to 100|20<br /><br /> By default, a maximum of  20% of physical memory can be used for all R sessions.|Represents the maximum percentage of physical memory that can be used by all of the R sessions on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer, combined.<br /><br /> Assuming 8GB of physical memory on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer, the default value of 20 for this setting will limit all R sessions to use at max \(8GB \* 0.20\) \= 1.6GB.<br /><br /> If R sessions need more memory, you can increase this setting. However, note that if you change this value to use the maximum of 100, the R sessions can occupy the full physical memory available on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer.|  
|MPI\_HOME|String|C:\\Program Files\\Program Files\\Microsoft MPI|Indicates the root directory where Microsoft MPI binaries are installed. This setting is used for locating MPI binaries.<br /><br /> Note: This is an internal setting only – do not change this value.|  
|RHOME|String|C:\\Program Files\\RRO\\RRO\-3.2.2\-for\-RRE\-7.5.0\\R\-3.2.2|Indicates the root directory where Microsoft R Open is installed.<br /><br /> This setting is used for locating Rterm.exe  \(command\-line utility for running R batch jobs\)  .as well as the RevoScaleR package.<br /><br /> Note: This is an internal setting only – do not change this value.|  
|TRACE\_LEVEL|Integer<br /><br /> 1 \= Error<br /><br /> 2 \= Warning<br /><br /> 3 \= Information|1<br /><br /> Output warnings only|Configures the trace verbosity level of the R launcher \(MSSQLLAUNCHPAD\) for debugging purposes. This setting affects the verbosity of the traces stored in the following trace files, both of which are located in the path specified by the LOG\_DIRECTORY setting:<br /><br /> **rlauncher.log**: The trace file generated for R sessions launched by T\-SQL queries.<br /><br /> **xp\_callree.log**: The trace file generated for an R session that was invoked as a result of a RevoScaleR package function triggered from a client machine. For more information about this scenario, see [Data Exploration and Predictive Modeling with R](../../Topics\TopicNameNotContainA/Data-Exploration-and-Predictive-Modeling-with-R.md).|  
|USER\_POOL\_SIZE|Integer|10|Controls the maximum number of user pool accounts that can launch R sessions. This number also determines how many R sessions you can execute in parallel.<br /><br /> This is a read\-only setting and should not be changed manually. If you need to change the number of user accounts for R sessions, run RegisterRExt.exe and change the value.|  
|WORKING\_DIRECTORY|String \(path\)  \(NOTE: Short path for working directory\)|\<SQL Instance Path\>\\MSSQL\\Extens~1 <br />E.g. C:\\PROGRA~1\\MI3EDC~1\\MSSQL1~2.MSS\\MSSQL\\EXTENS~1|Specifies the root directory of all the temporary working directories for all R sessions for a particular [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]instance.<br /><br /> Note: This is an internal setting only – do not change this value.|  
  
## See Also  
 [Getting Started with SQL Server R Services](../../Topics\TopicNameNotContainA/Getting-Started-with-SQL-Server-R-Services.md)  
  
  