---
title: "Using Transparent Network IP Resolution"
ms.custom: na
ms.date: 07/22/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7491b62b-9ca0-4ff8-89c0-f7eb41ef73db
caps.latest.revision: 2
---
# Using Transparent Network IP Resolution
TransparentNetwork IP Resolution is a revision of the existing MultiSubnet Failover feature that affects the connection sequence of the driver in the case where the first resolved IP of the hostname does not respond and there are multiple IPs associated with the hostname. It interacts with MultiSubnetFailover to provide the following three connection sequences:

* 0: One IP is attempted, followed by all IPs in parallel
* 1: All IPs are attempted in parallel
* 2: All IPs are attempted one after another

|Transparent Network IP Resolution|Multisubnet Failover|Behaviour|
|:-:|:-:|:-:|
|(default)|(default)|0|
|(default)|Enabled|1|
|(default)|Disabled|0|
|Enabled|(default)|0|
|Enabled|Enabled|1|
|Enabled|Disabled|0|
|Disabled|(default)|2|
|Disabled|Enabled|1|
|Disabled|Disabled|2|

The Transparent Network IP Resolution connection string and DSN keyword controls this setting at the connection-string level. The default is enabled.

Connection String Keyword|Values|Default
-|-|-
TransparentNetworkIPResolution|Yes/No|Yes

The SQL_COPT_SS_TNIR pre-connection attribute allows an application to control this setting programmatically:

Connection Attribute|	Size/Type|	Default| Value|	Description
-|-|-|-|-
SQL_COPT_SS_TNIR (1249)|	SQL_IS_INTEGER or SQL_IS_UINTEGER|	SQL_IS_ON (1)/	SQL_IS_OFF (0)|SQL_IS_ON (1)|Enables or disables TNIR.


--------------------------------------------------
## See Also  
* [Microsoft ODBC Driver for SQL Server on Windows](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Windows.md)
* [SQL Server Multi-Subnet Clustering (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)