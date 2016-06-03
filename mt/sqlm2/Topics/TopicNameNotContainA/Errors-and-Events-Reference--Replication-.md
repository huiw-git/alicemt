---
title: Errors and Events Reference (Replication)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e67d1bab-47b6-441d-ab9c-251a2ca499e1
---
# Errors and Events Reference (Replication)
  This section of the documentation contains cause and resolution information for a number of errors related to replication.  
  
|Error|Message|  
|-----------|-------------|  
|[MSSQL_ENG002601](../../Topics\TopicNameNotContainA/MSSQL_ENG002601.md)|Cannot insert duplicate key row in object '%.\*ls' with unique index '%.\*ls'.|  
|[MSSQL_ENG002627](../../Topics\TopicNameNotContainA/MSSQL_ENG002627.md)|Violation of %ls constraint '%.\*ls'. Cannot insert duplicate key in object '%.\*ls'.|  
|[MSSQL_ENG003165](../../Topics\TopicNameNotContainA/MSSQL_ENG003165.md)|Database '%ls' was restored, however an error was encountered while replication was being restored\/removed. The database has been left offline. See the topic MSSQL\_ENG003165 in SQL Server Books Online.|  
|[MSSQL_ENG003724](../../Topics\TopicNameNotContainA/MSSQL_ENG003724.md)|Cannot %S\_MSG the %S\_MSG '%.\*ls' because it is being used for replication.|  
|[MSSQL_ENG004929](../../Topics\TopicNameNotContainA/MSSQL_ENG004929.md)|Cannot alter the %S\_MSG '%.\*ls' because it is being published for replication.|  
|MSSQL\_ENG007395. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Unable to start a nested transaction for OLE DB provider "%ls" for linked server "%ls". A nested transaction was required because the XACT\_ABORT option was set to OFF.|  
|[MSSQL_ENG014005](../../Topics\TopicNameNotContainA/MSSQL_ENG014005.md)|Could not drop publication. A subscription exists to it.|  
|[MSSQL_ENG014010](../../Topics\TopicNameNotContainA/MSSQL_ENG014010.md)|The server '%s' is not defined as a subscription server.|  
|[MSSQL_ENG014114](../../Topics\TopicNameNotContainA/MSSQL_ENG014114.md)|'%s' is not configured as a Distributor.|  
|[MSSQL_ENG014117](../../Topics\TopicNameNotContainA/MSSQL_ENG014117.md)|'%s' is not configured as a distribution database.|  
|[MSSQL_ENG014120](../../Topics\TopicNameNotContainA/MSSQL_ENG014120.md)|Could not drop the distribution database '%s'. This distributor database is associated with a Publisher.|  
|[MSSQL_ENG014121](../../Topics\TopicNameNotContainA/MSSQL_ENG014121.md)|Could not drop the Distributor '%s'. This Distributor has associated distribution databases.|  
|[MSSQL_ENG014144](../../Topics\TopicNameNotContainA/MSSQL_ENG014144.md)|Cannot drop Subscriber '%s'. There are subscriptions for it in the publication database '%s'.|  
|[MSSQL_ENG014150](../../Topics\TopicNameNotContainA/MSSQL_ENG014150.md)|Replication\-%s: agent %s succeeded. %s|  
|[MSSQL_ENG014151](../../Topics\TopicNameNotContainA/MSSQL_ENG014151.md)|Replication\-%s: agent %s failed. %s|  
|[MSSQL_ENG014152](../../Topics\TopicNameNotContainA/MSSQL_ENG014152.md)|Replication\-%s: agent %s scheduled for retry. %s|  
|[MSSQL_ENG014157](../../Topics\TopicNameNotContainA/MSSQL_ENG014157.md)|The subscription created by Subscriber '%s' to publication '%s' has expired and has been dropped.|  
|[MSSQL_ENG014160](../../Topics\TopicNameNotContainA/MSSQL_ENG014160.md)|The threshold \[%s:%s\] for the publication \[%s\] has been set. One or more subscriptions to this publication have expired.|  
|[MSSQL_ENG014161](../../Topics\TopicNameNotContainA/MSSQL_ENG014161.md)|The threshold \[%s:%s\] for the publication \[%s\] has been set. Make sure that the logreader and distribution agents are running and can match the latency requirement.|  
|[MSSQL_ENG014162](../../Topics\TopicNameNotContainA/MSSQL_ENG014162.md)|The threshold \[%s:%s\] for the publication \[%s\] has been set. Please make sure that the merge agent is running and can match the expected requirement.|  
|[MSSQL_ENG014163](../../Topics\TopicNameNotContainA/MSSQL_ENG014163.md)|The threshold \[%s:%s\] for the publication \[%s\] has been set. Please make sure that the merge agent is running and can match the expected requirement.|  
|[MSSQL_ENG014164](../../Topics\TopicNameNotContainA/MSSQL_ENG014164.md)|The threshold \[%s:%s\] for the publication \[%s\] has been set. Please make sure that the merge agent is running and can match the expected requirement.|  
|[MSSQL_ENG014165](../../Topics\TopicNameNotContainA/MSSQL_ENG014165.md)|The threshold \[%s:%s\] for the publication \[%s\] has been set. Please make sure that the merge agent is running and can match the expected requirement.|  
|[MSSQL_ENG018456](../../Topics\TopicNameNotContainA/MSSQL_ENG018456.md)|Login failed for user '%.\*ls'.%.\*ls|  
|[MSSQL_ENG018752](../../Topics\TopicNameNotContainA/MSSQL_ENG018752.md)|Only one Log Reader Agent or log\-related procedure \(sp\_repldone, sp\_replcmds, and sp\_replshowcmds\) can connect to a database at a time. If you executed a log\-related procedure, drop the connection over which the procedure was executed or execute sp\_replflush over that connection before starting the Log Reader Agent or executing another log\-related procedure.|  
|[MSSQL_ENG020554](../../Topics\TopicNameNotContainA/MSSQL_ENG020554.md)|The replication agent has not logged a progress message in %ld minutes. This might indicate an unresponsive agent or high system activity. Verify that records are being replicated to the destination and that connections to the Subscriber, Publisher, and Distributor are still active.|  
|[MSSQL_ENG020557](../../Topics\TopicNameNotContainA/MSSQL_ENG020557.md)|Agent shutdown. For more information, see the SQL Server Agent job history for job '%s'.|  
|[MSSQL_ENG020572](../../Topics\TopicNameNotContainA/MSSQL_ENG020572.md)|Subscriber '%s' subscription to article '%s' in publication '%s' has been reinitialized after a validation failure.|  
|[MSSQL_ENG020574](../../Topics\TopicNameNotContainA/MSSQL_ENG020574.md)|Subscriber '%s' subscription to article '%s' in publication '%s' failed data validation.|  
|[MSSQL_ENG020575](../../Topics\TopicNameNotContainA/MSSQL_ENG020575.md)|Subscriber '%s' subscription to article '%s' in publication '%s' passed data validation.|  
|[MSSQL_ENG020596](../../Topics\TopicNameNotContainA/MSSQL_ENG020596.md)|Only '%s' or members of db\_owner can drop the anonymous agent.|  
|[MSSQL_ENG020598](../../Topics\TopicNameNotContainA/MSSQL_ENG020598.md)|The row was not found at the Subscriber when applying the replicated command.|  
|[MSSQL_ENG021075](../../Topics\TopicNameNotContainA/MSSQL_ENG021075.md)|The initial snapshot for publication '%s' is not yet available.|  
|[MSSQL_ENG021076](../../Topics\TopicNameNotContainA/MSSQL_ENG021076.md)|The initial snapshot for article '%s' is not yet available.|  
|[MSSQL_ENG021286](../../Topics\TopicNameNotContainA/MSSQL_ENG021286.md)|Conflict table '%s' does not exist.|  
|[MSSQL_ENG021330](../../Topics\TopicNameNotContainA/MSSQL_ENG021330.md)|Failed to create a sub\-directory under the replication working directory.\(%ls\)|  
|[MSSQL_ENG021331](../../Topics\TopicNameNotContainA/MSSQL_ENG021331.md)|Failed to copy user script file to the Distributor.\(%ls\)|  
|[MSSQL_ENG021385](../../Topics\TopicNameNotContainA/MSSQL_ENG021385.md)|Snapshot failed to process publication '%s'. Possibly due to active schema change activity or new articles being added.|  
|MSSQL\_ENG021617. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Unable to run SQL\*PLUS. Make certain that a current version of the Oracle client code is installed at the distributor.|  
|MSSQL\_ENG021620. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|The version of SQL\*PLUS that is accessible through the system Path variable is not current enough to support Oracle publishing. Make certain that a current version of the Oracle client code is installed at the distributor.|  
|MSSQL\_ENG021624. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Unable to locate the registered Oracle OLEDB provider, OraOLEDB.Oracle, at distributor '%s'. Make certain that a current version of the Oracle OLEDB provider is installed and registered at the distributor.|  
|MSSQL\_ENG021626. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Unable to connect to Oracle database server '%s' using the Oracle OLEDB provider OraOLEDB.Oracle.|  
|MSSQL\_ENG021627. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Unable to connect to Oracle database server '%s' using the Microsoft OLEDB provider MSDAORA.|  
|MSSQL\_ENG021628. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Unable to update the registry of distributor '%s' to allow Oracle OLEDB provider OraOLEDB.Oracle to run in process with SQL Server. Make certain that current login is authorized to modify SQL Server owned registry keys.|  
|MSSQL\_ENG021629. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|The CLSID registry key indicating that the Oracle OLEDB Provider for Oracle, OraOLEDB.Oracle, has been registered is not present at the distributor. Make certain that the Oracle OLEDB provider is installed and registered at the distributor.|  
|MSSQL\_ENG021642. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|Heterogeneous publishers require a linked server. A linked server named '%s' already exists. Please remove linked server or choose a different publisher name.|  
|MSSQL\_ENG021663. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|No valid primary key found for source table \[%s\].\[%s\].|  
|MSSQL\_ENG021684. See [Troubleshooting Oracle Publishers](../../Topics\TopicNameNotContainA/Troubleshooting-Oracle-Publishers.md).|The permissions associated with the administrator login for Oracle publisher '%s' are not sufficient.|  
|[MSSQL_ENG021797](../../Topics\TopicNameNotContainA/MSSQL_ENG021797.md)|'%s' must be a valid Windows Login in the form: 'MACHINE\\Login' or 'DOMAIN\\Login'. Please see the documentation for '%s'.|  
|[MSSQL_ENG021798](../../Topics\TopicNameNotContainA/MSSQL_ENG021798.md)|The '%s' agent job must be added via '%s' before continuing. Please see the documentation for '%s'.|  
|[MSSQL_REPL020011](../../Topics\TopicNameNotContainA/MSSQL_REPL020011.md)|The process could not execute '%1' on '%2'.|  
|[MSSQL_REPL027056](../../Topics\TopicNameNotContainA/MSSQL_REPL027056.md)|The merge process was unable to change generation history at the '%1'. When troubleshooting, restart the synchronization with verbose history logging and specify an output file to which to write.|  
|[MSSQL_REPL027183](../../Topics\TopicNameNotContainA/MSSQL_REPL027183.md)|The merge process failed to enumerate changes in articles with parameterized row filters. If this failure continues, increase the query timeout for this process, reduce the retention period for the publication, and improve indexes on published tables.|  
  
  