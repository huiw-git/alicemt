---
title: Replication Merge Agent
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
---
# Replication Merge Agent
  The Replication Merge Agent is a utility executable that applies the initial snapshot held in the database tables to the Subscribers. It also merges incremental data changes that occurred at the Publisher after the initial snapshot was created, and reconciles conflicts either according to the rules you configure or using a custom resolver you create.  
  
> [!NOTE]  
>  Parameters can be specified in any order. When optional parameters are not specified, values from predefined registry settings on the local computer are used.  
  
## Syntax  
  
```  
  
replmerg [-?]   
-Publisher server_name[\instance_name]  
-PublisherDB publisher_database  
-Publication publication  
-Subscriber server_name[\instance_name]  
-SubscriberDB subscriber_database  
[-AltSnapshotFolder alt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFile def_path_and_file_name]  
[-DestThreads number_of_destination_threads]  
[-Distributor server_name[\instance_name]]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatch download_generations_per_batch]  
[-DownloadReadChangesPerBatch download_read_changes_per_batch]  
[-DownloadWriteChangesPerBatch download_write_changes_per_batch]  
[-DynamicSnapshotLocation dynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddress ftp_address]  
[-FtpPassword ftp_password]  
[-FtpPort ftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostname host_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogin internet_login]  
[-InternetPassword internet_password]  
[-InternetProxyLogin internet_proxy_login]  
[–InternetProxyPassword internet_proxy_password]  
[-InternetProxyServer internet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeout internet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageInterval keep_alive_message_interval_seconds]  
[-LoginTimeOut login_time_out_seconds]  
[-MakeGenerationInterval make_generation_interval_seconds]  
[-MaxBcpThreads number_of_threads]  
[-MaxDownloadChanges number_of_download_changes]  
[-MaxUploadChanges number_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSize packet_size]   
[-PollingInterval polling_interval]  
[-ProfileName profile_name]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOut query_time_out_seconds]  
[-SrcThreads number_of_source_threads]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePath subscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLogin subscriber_login]  
[-SubscriberPassword subscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatch upload_generations_per_batch]  
[-UploadReadChangesPerBatch upload_read_changes_per_batch]  
[-UploadWriteChangesPerBatch upload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateInterval validate_interval]  
```  
  
## Arguments  
 **\-?**  
 Prints all available parameters.  
  
 **\-Publisher** *server\_name*\[**\\***instance\_name*\]  
 Is the name of the Publisher. Specify *server\_name* for the default instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on that server. Specify *server\_name***\\***instance\_name* for a named instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on that server.  
  
 **\-PublisherDB** *publisher\_database*  
 Is the name of the Publisher database.  
  
 **\-Publication** *publication*  
 Is the name of the publication. This parameter is only valid if the publication is set to always have a snapshot available for new or reinitialized subscriptions.  
  
 **\-Subscriber** *server\_name*\[**\\***instance\_name*\]  
 Is the name of the Subscriber. Specify *server\_name* for the default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on that server. Specify *server\_name***\\***instance\_name* for a named instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on that server.  
  
 **\-SubscriberDB** *subscriber\_database*  
 Is the name of the Subscriber database.  
  
 **\-AltSnapshotFolder** *alt\_snapshot\_folder\_path*  
 Is the path to the folder that contains the initial snapshot for a subscription.  
  
 **\-Continuous**  
 Specifies whether the agent attempts to poll replicated transactions continually. If specified, the agent polls replicated transactions from the source at polling intervals, even if there are no transactions pending.  
  
 **\-DestThreads** *number\_of\_destination\_threads*  
 Specifies the number of destination threads that the Merge Agent uses to apply changes at the destination. The destination is the Publisher during upload and the Subscriber during download. The default is 4.  
  
 **\-DefinitionFile** *def\_path\_and\_file\_name*  
 Is the path of the agent definition file. An agent definition file contains command prompt arguments for the agent. The content of the file is parsed as an executable file. Use double quotation marks \("\) to specify argument values containing arbitrary characters.  
  
 **\-Distributor** *server\_name*\[**\\***instance\_name*\]  
 Is the Distributor name. Specify *server\_name* for the default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on that server. Specify *server\_name***\\***instance\_name* for a named instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on that server. For Distributor \(push\) distribution, the name defaults to the name of the default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on the local computer.  
  
 **\-DistributorLogin** *distributor\_login*  
 Is the Distributor login name.  
  
 **\-DistributorPassword** *distributor\_password*  
 Is the Distributor password.  
  
 **\-DistributorSecurityMode** \[ **0**| **1**\]  
 Specifies the security mode of the Distributor. A value of **0** indicates [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication Mode \(default\), and a value of **1** indicates Windows Authentication Mode.  
  
 **\-DownloadGenerationsPerBatch** *download\_generations\_per\_batch*  
 Is the number of generations to be processed in a single batch while downloading changes from the Publisher to the Subscriber. A generation is defined as a logical group of changes per article. The default for a reliable communication link is 100. The default for an unreliable communication link is 10.  
  
 **\-DownloadReadChangesPerBatch** *download\_read\_changes\_per\_batch*  
 Is the number of changes to be read in a single batch while downloading changes from the Publisher to the Subscriber. The default is 100.  
  
 **\-DownloadWriteChangesPerBatch** *download\_write\_changes\_per\_batch*  
 Is the number of changes to be applied in a single batch while downloading changes from the Publisher to the Subscriber. The default is 100.  
  
 **\-DynamicSnapshotLocation** *dynamic\_snapshot\_location*  
 Is the location of the filtered data snapshot files when the publication uses parameterized row filters.  
  
 **\-EncryptionLevel** \[ **0** | **1** | **2** \]  
 Is the level of Secure Sockets Layer \(SSL\) encryption used by the Merge Agent when making connections.  
  
|EncryptionLevel value|Description|  
|---------------------------|-----------------|  
|**0**|Specifies that SSL is not used.|  
|**1**|Specifies that SSL is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer.|  
|**2**|Specifies that SSL is used, and that the certificate is verified.|  
  
 For more information, see [Security Overview &#40;Replication&#41;](../Topic/Security%20Overview%20\(Replication\).md).  
  
 **\-ExchangeType** \[ **1**| **2**| **3**\]  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../Token\Appliesto/ssNoteDepFutureDontUse_md.md)] To restrict uploading, use the **@subscriber\_upload\_options** of **sp\_addmergearticle** instead.  
  
 Specifies the type of data exchange during synchronization, which can be one of the following:  
  
|ExchangeType value|Description|  
|------------------------|-----------------|  
|**1**|Agent should upload data changes from the Subscriber to the Publisher.|  
|**2**|Agent should download data changes from the Publisher to the Subscriber.|  
|**3** \(default\)|Agent should first upload data changes from the Subscriber to the Publisher and then download data changes from the Publisher to the Subscriber. You must use this option with Web synchronization.|  
  
 Download\-only articles enable you to control the synchronization behavior of individual articles in a publication, and they can provide a performance benefit. For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../../Topics\TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Download-Only-Articles.md).  
  
 If using **ExchangeType** to separate the upload and download phase of merge replication into separate sessions, you must run the merge agent with **ExchangeType** set to 1 first and then run the merge agent again with the value 2. Failure to run the merge agent with both parameters will cause metadata to be deleted and require you to reinitialize the subscription \(without upload\).  
  
 **\-FastRowCount** \[**0**|**1**\]  
 Specifies what type of rowcount calculation method should be used for rowcount validation. A value of **1** \(default\) indicates the fast method. A value of **0** indicates the full rowcount method.  
  
 **\-FileTransferType** \[**0**|**1**\]  
 Specifies the file transfer type. A value of **0** indicates UNC \(universal naming convention\), and a value of **1** indicates FTP \(file transfer protocol\).  
  
 **\-ForceConvergenceLevel** \[**0**|**1**|**2** \( **Publisher**| **Subscriber**| **Both**\)\]  
 Specifies the level of convergence the Merge Agent should use, and can be one of the following:  
  
|ForceConvergenceLevel value|Description|  
|---------------------------------|-----------------|  
|**0** \(default\)|Default. Perform a standard merge without additional convergence.|  
|**1**|Force convergence for all generations.|  
|**2**|Force convergence for all generations and correct corrupt lineages. When specifying this value, specify where lineages should be corrected: the Publisher, the Subscriber, or both the Publisher and the Subscriber.|  
  
 **\-FtpAddress** *ftp\_address*  
 Is the network address of the FTP service for the Distributor. When not specified, **Distributor** is used.  
  
 **\-FtpPassword** *ftp\_password*  
 Is the user password used to connect to the FTP service.  
  
 **\-FtpPort** *ftp\_port*  
 Is the port number of the FTP service for the Distributor. When not specified, the default port number for FTP service \(21\) is used.  
  
 **\-FtpUserName** *ftp\_user\_name*  
 Is the user name used to connect to the FTP service. When not specified, anonymous is used.  
  
 **\-HistoryVerboseLevel** \[**1**|**2**|**3**\]  
 Specifies the amount of history logged during a merge operation. You can minimize the effect of history logging on performance by selecting **1**.  
  
|HistoryVerboseLevel value|Description|  
|-------------------------------|-----------------|  
|**0**|Log the final agent status message, final session details, and any errors.|  
|**1**|Log incremental session details at each session status, including percent complete, in addition to the final agent status message, final session details, and any errors.|  
|**2**|Default. Log both incremental session details at each session status and article level session details, including percent complete, in addition to the final agent status message, final session details, and any errors. Agent status messages are also logged.|  
|**3**|The same as **\-HistoryVerboseLevel** \= **2**, except that more agent progress messages are logged.|  
  
 **\-Hostname** *host\_name*  
 Is the network name of the local computer. The default is the local computer name.  
  
 **\-InteractiveResolution** \[**0**|**1**\]  
 Specifies whether interactive conflict resolution is used when a conflict occurs during synchronization. The default is **0**, indicating that interactive conflict resolution is not used.  
  
 **\-InternetLogin** *internet\_login*  
 Specifies the login name used when connecting to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication listener ISAPI DLL that requires authentication.  
  
 **\-InternetPassword** *internet\_password*  
 Specifies the password used when connecting to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication listener ISAPI DLL that requires authentication.  
  
 **\-InternetProxyLogin**  *internet\_proxy\_login*  
 Specifies the login name used when connecting to a proxy server, defined in *internet\_proxy\_server*, that requires authentication.  
  
 **–InternetProxyPassword**  *internet\_proxy\_password*  
 Specifies the password used when connecting to a proxy server, defined in *internet\_proxy\_server*, that requires authentication.  
  
 **\-InternetProxyServer**  *internet\_proxy\_server*  
 Specifies the proxy server to use when accessing the HTTP resource specified in *internet\_url*.  
  
 **\-InternetSecurityMode** \[**0**|**1**\]  
 Specifies the IIS security mode used when connecting to the Web server during Web synchronization. A value of **0** indicates Basic Authentication, and a value of **1** indicates Windows Integrated Authentication \(default\).  
  
 **\-InternetTimeout** *internet\_timeout*  
 Is the number of seconds before a connection to the to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication listener ISAPI DLL times out.  
  
 **\-InternetURL** *internet\_url*  
 Specifies the URL used to connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication listener ISAPI DLL. This property must be specified.  
  
 **\-KeepAliveMessageInterval** *keep\_alive\_message\_interval\_seconds*  
 Is the number of seconds before the history thread checks if any of the existing connections is waiting for a response from the server. This value can be decreased to avoid having the checkup agent mark the Merge Agent as suspect when executing a long\-running batch. The default is **300** seconds.  
  
 **\-LoginTimeOut** *login\_time\_out\_seconds*  
 Is the number of seconds before the login times out. The default is **15** seconds.  
  
 **\-MakeGenerationInterval** *make\_generation\_interval\_seconds*  
 Is the number of seconds to wait between creating generations, or batches of changes, to download to the client. The default is **1** second.  
  
 Makegeneration is the process that prepares Publisher changes to be downloaded to Subscribers, and it can be a performance bottleneck during downloads. If the makegeneration process already ran within the interval specified by **\-MakeGenerationInterval**, the process is skipped for the current synchronization session. This can benefit synchronization concurrency and is especially helpful if Subscribers do not expect to download changes.  
  
 **\-MaxBcpThreads** *number\_of\_threads*  
 Specifies the number of bulk copy operations that can be performed in parallel. The maximum number of threads and ODBC connections that exist simultaneously is the lesser of **MaxBcpThreads** or the number of bulk copy requests that appear in the system table **sysmergeschemachange** in the publication database. **MaxBcpThreads** must have a value greater than 0 and has no hard\-coded upper limit. The default is **1**.  
  
 **\-MaxDownloadChanges** *number\_of\_download\_changes*  
 Specifies the maximum number of changed rows that should be downloaded from the Publisher to the Subscriber. The number of rows downloaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass. By default all changes that are ready to be downloaded are sent.  
  
 **\-MaxUploadChanges** *number\_of\_upload\_changes*  
 Specifies the maximum number of changed rows that should be uploaded from the Subscriber to the Publisher. The number of rows uploaded may be higher than the specified maximum because: complete generations are processed; and parallel destination threads may run, each of which processes at least 100 changes in its first pass. By default all changes that are ready to be uploaded are sent.  
  
 **\-MetadataRetentionCleanup** \[**0**|**1**\]  
 Specifies if metadata is removed from [MSmerge\_genhistory](../Topic/MSmerge_genhistory%20\(Transact-SQL\).md), [MSmerge\_contents](../Topic/MSmerge_contents%20\(Transact-SQL\).md), [MSmerge\_tombstone](../Topic/MSmerge_tombstone%20\(Transact-SQL\).md), [MSmerge\_past\_partition\_mappings](../Topic/MSmerge_past_partition_mappings%20\(Transact-SQL\).md), and [MSmerge\_current\_partition\_mappings](../Topic/MSmerge_current_partition_mappings.md) based on the publication retention period. The default is **1**, indicating that cleanup should occur. A value of **0** indicates that cleanup should not occur automatically.  
  
 **\-Output** *output\_path\_and\_file\_name*  
 Is the path of the agent output file. If the file name is not provided, the output is sent to the console. If the specified file name exists, the output is appended to the file.  
  
 **\-OutputVerboseLevel** \[**0**|**1**|**2**\]  
 Specifies whether the output should be verbose. If the verbose level is **0**, only error messages are printed. If the verbose level is **1**, all of the progress report messages are printed. If the verbose level is **2** \(default\), all error messages and progress report messages are printed, which is useful for debugging.  
  
 **\-ParallelUploadDownload** \[**0**|**1**\]  
 Specifies whether the Merge Agent should process in parallel the changes uploaded to the Publisher and those downloaded to the Subscriber, which is useful in high volume environments with high network bandwidth. If **ParallelUploadDownload** is **1**, then parallel processing is enabled.  
  
 **\-PacketSize**  
 Is the packet size, in bytes. The default is 4096 \(bytes\).  
  
 **\-PollingInterval** *polling\_interval*  
 Is how often, in seconds, the Publisher or Subscriber is queried for data changes. The default is 60 seconds.  
  
 **\-ProfileName** *profile\_name*  
 Specifies an agent profile to use for agent parameters. If **ProfileName** is NULL, the agent profile is disabled. If **ProfileName** is not specified, the default profile for the agent type is used. For information, see [Replication Agent Profiles](../../Topics\TopicNameNotContainA/Replication-Agent-Profiles.md).  
  
 **\-PublisherFailoverPartner** *server\_name*\[**\\***instance\_name*\]  
 Specifies the failover partner instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] participating in a database mirroring session with the publication database. For more information, see [Database Mirroring and Replication &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20and%20Replication%20\(SQL%20Server\).md).  
  
 **\-PublisherLogin** *publisher\_login*  
 Is the Publisher login name. If **PublisherSecurityMode** is **0** \(for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication\), this parameter must be specified.  
  
 **\-PublisherPassword** *publisher\_password*  
 Is the Publisher password. If **PublisherSecurityMode** is **0** \(for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication\), this parameter must be specified.  
  
 **\-PublisherSecurityMode** \[**0**|**1**\]  
 Specifies the security mode of the Publisher. A value of **0** indicates [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication \(default\), and a value of **1** indicates Windows Authentication Mode.  
  
 **\-QueryTimeOut** *query\_time\_out\_seconds*  
 Is the number of seconds before the query times out. The default is 300 seconds. The Merge Agent also uses the value of **QueryTimeout** to determine how long to wait for generation of a partitioned snapshot when this value is greater than 1800.  
  
 **\-SrcThreads** *number\_of\_source\_threads*  
 Specifies the number of source threads that the Merge Agent uses to enumerate changes from the source. The source is the Subscriber during upload and the Publisher during download. The default is **3**.  
  
 **\-StartQueueTimeout** *start\_queue\_timeout\_seconds*  
 Is the maximum number of seconds that the Merge Agent waits when the number of concurrent merge processes running is at the limit set by the **@max\_concurrent\_merge** property of **sp\_addmergepublication**. If the maximum number of seconds is reached and the Merge Agent is still waiting, it will exit. A value of 0 means that the agent waits indefinitely, although it can be cancelled.  
  
 **\-SubscriberDatabasePath** *subscriber\_database\_path*  
 Is the path to the Jet database \(.mdb file\) if **SubscriberType** is **2** \(allows a connection to a Jet database without an ODBC Data Source Name \(DSN\)\).  
  
 **\-SubscriberDBAddOption** \[**0**| **1**| **2**| **3**\]  
 Specifies whether there is an existing Subscriber database.  
  
|SubscriberDBAddOption value|Description|  
|---------------------------------|-----------------|  
|**0**|Use the existing database \(default\).|  
|**1**|Create a new, empty Subscriber database.|  
|**2**|Create a new database and attach it to the specified file.|  
|**3**|Create a new database, attach the database, and enable all subscriptions that might exist at the file.|  
  
> [!NOTE]  
>  When you use values **2** and **3**, the database path for the Subscriber must be specified in the **SubscriberDatabasePath** option.  
  
 **\-SubscriberLogin** *subscriber\_login*  
 Is the Subscriber login name. If **SubscriberSecurityMode** is **0** \(for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication\), this parameter must be specified.  
  
 **\-SubscriberPassword** *subscriber\_password*  
 Is the Subscriber password. If **SubscriberSecurityMode** is **0** \(for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication\), this parameter must be specified.  
  
 **\-SubscriberSecurityMode** \[ **0**| **1**\]  
 Specifies the security mode of the Subscriber. A value of **0** indicates [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication \(default\), and a value of **1** indicates Windows Authentication Mode.  
  
 **\-SubscriberConflictClean** \[ **0**| **1**\]  
 Is if conflict tables are cleaned\-up at the Subscriber during the synchronization process, where a value of **1** indicates that conflict tables at the Subscriber are cleaned\-up. This parameter is used only for subscriptions to publications with decentralized conflict logging.  
  
 **\-SubscriberType** \[ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**\]  
 Specifies the type of Subscriber connection used by the Merge Agent. Only the default value of **0** is supported for this parameter.  
  
 **\-SubscriptionType**\[ **0**| **1**| **2**\]  
 Specifies the subscription type for distribution. A value of **0** indicates a push subscription \(default\), a value of **1** indicates a pull subscription, and a value of **2** indicates an anonymous subscription.  
  
 **\-SyncToAlternate** \[ **0|1**\]  
 Specifies whether the Merge Agent is synchronizing between a Subscriber and an alternate Publisher. A value of **1** indicates that it is an alternate Publisher. The default is **0**.  
  
 **\-UploadGenerationsPerBatch** *upload\_generations\_per\_batch*  
 Is the number of generations to be processed in a single batch while uploading changes from the Subscriber to the Publisher. A generation is defined as a logical group of changes per article. The default for a reliable communication link is **100**. The default for an unreliable communication link is **1**.  
  
 **\-UploadReadChangesPerBatch** *upload\_read\_changes\_per\_batch*  
 Is the number of changes to be read in a single batch while uploading changes from the Subscriber to the Publisher. The default is **100**.  
  
 **\-UploadWriteChangesPerBatch** *upload\_write\_changes\_per\_batch*  
 Is the number of changes to be applied in a single batch while uploading changes from the Subscriber to the Publisher. The default is **100**.  
  
 **\-UseInprocLoader**  
 Improves the performance of the initial snapshot by causing the Merge Agent to use the BULK INSERT command when applying snapshot files to the Subscriber. This parameter is deprecated because it is not compatible with the XML data type. If you are not replicating XML data, this parameter can be used. This parameter cannot be used with character mode snapshots. If you use this parameter, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account at the Subscriber must have read permissions on the directory where the snapshot .bcp data files are located. When this parameter is not used, the ODBC driver loaded by the agent reads from the files, so the security context of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account is not used.  
  
 **\-Validate** \[**0**|**1**|**2**|**3**\]  
 Specifies whether validation should be done at the end of the merge session, and, if so, what type of validation. The value of **3** is the recommended value.  
  
|Validate value|Description|  
|--------------------|-----------------|  
|**0** \(default\)|No validation.|  
|**1**|Rowcount\-only validation.|  
|**2**|Rowcount and checksum validation.|  
|**3**|Rowcount and binary checksum validation.|  
  
> [!NOTE]  
>  Validation by using binary checksum or checksum can incorrectly report a failure if data types are different at the Subscriber than they are at the Publisher. For more information, see the section "Considerations for Data Validation" in [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md).  
  
 **\-ValidateInterval** *validate\_interval*  
 Is how often, in minutes, the subscription is validated in continuous mode. The default is **60** minutes.  
  
## Remarks  
  
> [!IMPORTANT]  
>  If you have installed [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent to run under a local system account rather than under a domain user account \(the default\), the service can access only the local computer. If the Merge Agent that runs under [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is configured to use Windows Authentication Mode when it logs in to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the Merge Agent fails. The default setting is [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
 To start the Merge Agent, execute **replmerg.exe** from the command prompt. For information, see [Replication Agent Executables](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
 The merge agent history for the current session is not removed while running in continuous mode. A long running agent can result in a large number of entries in the merge history tables which could impact performance. To resolve this problem switch to scheduled mode, or continue to use continuous mode but create a dedicated job to periodically restart the merge agent, or reduce the verbosity of the history level to reduce the number of rows and therefor reduce the performance impact.  
  
## See Also  
 [Replication Agent Administration](../../Topics\TopicNameNotContainA/Replication-Agent-Administration.md)  
  
  