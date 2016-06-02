---
title: Monitor and Enforce Best Practices by Using Policy-Based Management
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46788407-187e-4b0b-bfe4-529af8d77c60
---
# Monitor and Enforce Best Practices by Using Policy-Based Management
  Policy\-Based Management allows you to monitor best practices for the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a set of policy files you can import as best practice policies, and then evaluate the policies against a target set that includes instances, instance objects, databases, or database objects. Evaluate policies manually, set policies to evaluate a target set according to a schedule, or set policies to evaluate a target set according to an event. For more information about Policy\-Based Management, see [Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md).  
  
## Policy and Rules for Database Engine  
 The following table lists the policies included with the installation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and information about the best practices rules each policy evaluates. The policies are stored as XML files and must be imported into [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information about how to import policies, see [Import a Policy-Based Management Policy](../../Topics\TopicNameContainA/Import-a-Policy-Based-Management-Policy.md).  
  
|Policy name|Best practice rule|  
|-----------------|------------------------|  
|Asymmetric Key Encryption Algorithm|[Asymmetric Keys Encryption Strength](../../Topics\TopicNameNotContainA/Asymmetric-Keys-Encryption-Strength.md)|  
|Backup and Data File Location|[Backup Files Must Be on Separate Devices from the Database Files](../../Topics\TopicNameNotContainA/Backup-Files-Must-Be-on-Separate-Devices-from-the-Database-Files.md)|  
|Data and Log File Location|[Place Data and Log Files on Separate Drives](../../Topics\TopicNameNotContainA/Place-Data-and-Log-Files-on-Separate-Drives.md)|  
|Database Auto Close|[Set the AUTO_CLOSE Database Option to OFF](../../Topics\TopicNameNotContainA/Set-the-AUTO_CLOSE-Database-Option-to-OFF.md)|  
|Database Auto Shrink|[Set the AUTO_SHRINK Database Option to OFF](../../Topics\TopicNameNotContainA/Set-the-AUTO_SHRINK-Database-Option-to-OFF.md)|  
|Database Collation|[Set the Collation of User-defined Databases to Match Those of the master and model Databases](../../Topics\TopicNameNotContainA/Set-the-Collation-of-User-defined-Databases-to-Match-Those-of-the-master-and-model-Databases.md)|  
|Database Page Verification|[Set the PAGE_VERIFY Database Option to CHECKSUM](../../Topics\TopicNameNotContainA/Set-the-PAGE_VERIFY-Database-Option-to-CHECKSUM.md)|  
|Database Page Status|[Check Integrity of Database with Suspect Pages](../../Topics\TopicNameNotContainA/Check-Integrity-of-Database-with-Suspect-Pages.md)|  
|Guest Permissions|[Guest Permissions on User Databases](../../Topics\TopicNameNotContainA/Guest-Permissions-on-User-Databases.md)|  
|Last Successful Backup Date|[Outdated Backup](../../Topics\TopicNameNotContainA/Outdated-Backup.md)|  
|Public Not Granted Server Permissions|[Server public Permissions](../../Topics\TopicNameNotContainA/Server-public-Permissions.md)|  
|SQL Server 64\-bit Affinity Mask Overlap|[Correct Affinity Mask and Affinity Input and Output Mask Overlap](../../Topics\TopicNameNotContainA/Correct-Affinity-Mask-and-Affinity-Input-and-Output-Mask-Overlap.md)|  
|SQL Server Affinity Mask|[Keep the Affinity Mask Default Value](../../Topics\TopicNameNotContainA/Keep-the-Affinity-Mask-Default-Value.md)|  
|SQL Server Blocked Process Threshold|[Increase or Disable Blocked Process Threshold](../../Topics\TopicNameNotContainA/Increase-or-Disable-Blocked-Process-Threshold.md)|  
|SQL Server Default Trace|[Default Trace Log Files Disabled](../../Topics\TopicNameNotContainA/Default-Trace-Log-Files-Disabled.md)|  
|SQL Server Dynamic Locks|[Keep the Locks Configuration Option Default Value](../../Topics\TopicNameNotContainA/Keep-the-Locks-Configuration-Option-Default-Value.md)|  
|SQL Server Lightweight Pooling|[Disable Lightweight Pooling](../../Topics\TopicNameNotContainA/Disable-Lightweight-Pooling.md)|  
|SQL Server Login Mode|[Choose an Authentication Mode](../../Topics\TopicNameNotContainA/Choose-an-Authentication-Mode.md)|  
|SQL Server Max Degree of Parallelism|[Set the Max Degree of Parallelism Option for Optimal Performance](../../Topics\TopicNameNotContainA/Set-the-Max-Degree-of-Parallelism-Option-for-Optimal-Performance.md)|  
|SQL Server Max Worker Threads for 32\-bit SQL Server 2000|[Verify Max Worker Threads Setting](../../Topics\TopicNameNotContainA/Verify-Max-Worker-Threads-Setting.md)|  
|SQL Server Max Worker Threads for 64\-bit SQL Server 2000|[Verify Max Worker Threads Setting](../../Topics\TopicNameNotContainA/Verify-Max-Worker-Threads-Setting.md)|  
|SQL Server Max Worker Threads for SQL Server 2005 and above|[Verify Max Worker Threads Setting](../../Topics\TopicNameNotContainA/Verify-Max-Worker-Threads-Setting.md)|  
|SQL Server Network Packet Size|[Network Packet Size Should Not Exceed 8060 Bytes](../../Topics\TopicNameNotContainA/Network-Packet-Size-Should-Not-Exceed-8060-Bytes.md)|  
|SQL Server Password Expiration|[SQL Server Login Password Expiration](../../Topics\TopicNameNotContainA/SQL-Server-Login-Password-Expiration.md)|  
|SQL Server Password Policy|[SQL Server Login Password Strength](../../Topics\TopicNameNotContainA/SQL-Server-Login-Password-Strength.md)|  
|Symmetric Key Encryption for User Databases|[Symmetric Keys on User Databases](../../Topics\TopicNameNotContainA/Symmetric-Keys-on-User-Databases.md)|  
|Symmetric Key for master Database|[Symmetric Keys on System Databases](../../Topics\TopicNameNotContainA/Symmetric-Keys-on-System-Databases.md)|  
|Symmetric Key for System Databases|[Symmetric Keys on System Databases](../../Topics\TopicNameNotContainA/Symmetric-Keys-on-System-Databases.md)|  
|Trustworthy Database|[Trustworthy Bit](../../Topics\TopicNameNotContainA/Trustworthy-Bit.md)|  
|Windows Event Log Cluster Disk Resource Corruption Error|[Detect SCSI Host Adapter Issues](../../Topics\TopicNameNotContainA/Detect-SCSI-Host-Adapter-Issues.md)|  
|Windows Event Log Device Driver Control Error|[Device Driver Control Error](../../Topics\TopicNameNotContainA/Device-Driver-Control-Error.md)|  
|Windows Event Log Device Not Ready Error|[Device Not Ready Error](../../Topics\TopicNameNotContainA/Device-Not-Ready-Error.md)|  
|Windows Event Log Failed I\_O Request Error|[Detect Failed Input and Output Requests](../../Topics\TopicNameNotContainA/Detect-Failed-Input-and-Output-Requests.md)|  
|Windows Event Log I\_O Delay Warning|[Check Disk Input and Output Subsystem for IO Delay Problems](../../Topics\TopicNameNotContainA/Check-Disk-Input-and-Output-Subsystem-for-IO-Delay-Problems.md)|  
|Windows Event Log I\_O Error During Hard Page Fault Error|[Input and Output Error During Hard Page Fault](../../Topics\TopicNameNotContainA/Input-and-Output-Error-During-Hard-Page-Fault.md)|  
|Windows Event Log Read Retry Error|[Check Disk Input-Output Subsystem for Read Retry Problems](../../Topics\TopicNameNotContainA/Check-Disk-Input-Output-Subsystem-for-Read-Retry-Problems.md)|  
|Windows Event Log Storage System I\_O Timeout Error|[Storage System Input-Output Time-out](../../Topics\TopicNameNotContainA/Storage-System-Input-Output-Time-out.md)|  
|Windows Event Log System Failure Error|[Unexpected System Failures](../../Topics\TopicNameNotContainA/Unexpected-System-Failures.md)|  
  
## See Also  
 [Working with Policy-Based Management Facets](../../Topics\TopicNameNotContainA/Working-with-Policy-Based-Management-Facets.md)  
  
  