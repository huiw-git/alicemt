---
title: Security Architecture for Web Synchronization
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74eee587-d5f5-4d1a-bbae-7f4e3f27e23b
---
# Security Architecture for Web Synchronization
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] enables fine\-grained control over the configuration of Web synchronization security. This topic provides a comprehensive list of all the components that can be included in a Web synchronization configuration and information about the connections that are made between components. [!INCLUDE[ssNoteWinAuthentication](../../Token\Other/ssNoteWinAuthentication_md.md)]  
  
 The following illustration shows all the possible connections, but some connections might not be required in a particular topology. For example, a connection to an FTP server is required only if the snapshot is delivered by using FTP.  
  
 ![Components and connections in Web synchronization](../../Images\Image\ImageNotContaina/WebSyncArchitecture.gif "WebSyncArchitecture")  
  
 The following tables describe the components and connections that are shown in the illustration.  
  
## A. Windows User Under Which the Merge Agent Runs  
 During synchronization, the Merge Agent \(A\) is started at the Subscriber. The Merge Agent can be started from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job step or from a stand\-alone custom application. If the Merge Agent is started from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job step, the Merge Agent runs under the context of a Windows user that you specify. If you do not specify a Windows user, the Merge Agent runs under the context of the Windows service account for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent.  
  
|Type of account|Where the account is specified|  
|---------------------|------------------------------------|  
|Windows user|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: the **@job\_login** and **@job\_password** parameters of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br /><br /> RMO \(Replication Management Objects\): the [P:Microsoft.SqlServer.Replication.IprocessSecurityContext.Login](assetId:///P:Microsoft.SqlServer.Replication.IprocessSecurityContext.Login) and [P:Microsoft.SqlServer.Replication.IprocessSecurityContext.Password](assetId:///P:Microsoft.SqlServer.Replication.IprocessSecurityContext.Password) properties for [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity).|  
|Windows service account for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager|  
|Stand\-alone application|The Merge Agent runs under the context of the Windows user that is running the application.|  
  
## B. Connection to the Subscriber  
 The Merge Agent connects to the Subscriber by using Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. The Windows user or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login that you specify must be associated with a database user that is a member of the **dbowner** fixed database role in the subscription database.  
  
> [!NOTE]  
>  Windows Authentication is always used when the Merge Agent is started from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job. Windows Authentication is also used when the Merge Agent is started programmatically unless [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication is explicitly specified.  
  
|Type of authentication|Where the authentication is specified|  
|----------------------------|-------------------------------------------|  
|-   Windows Authentication.|The Merge Agent makes connections under the context of the Windows user that is specified for the Merge Agent \(A\).|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication is used only if the following is specified:<br /><br /> -   RMO: a value of [Standard](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Standard) for [SubscriberSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriberSecurityMode).<br />-   Merge Agent command line: a value of **0** for **SubscriberSecurityMode**.|RMO: [SubscriberLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriberLogin) and [SubscriberPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriberPassword).<br /><br /> Merge Agent command line: **\-SubscriberLogin** and **\-SubscriberLogin**.|  
  
## C. Connection to an Outgoing Proxy Server  
 Specify a Windows user for this connection only if there is an outgoing proxy server that restricts access to the internal network of the Subscriber.  
  
|Type of authentication|Where the authentication is specified|  
|----------------------------|-------------------------------------------|  
|Windows Authentication|RMO: [InternetProxyLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetProxyLogin) and [InternetProxyPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetProxyPassword) with [InternetProxyServer](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetProxyServer).<br /><br /> Merge Agent command line: **\-InternetProxyLogin** and **\-InternetProxyPassword** with **\-InternetProxyServer**.|  
  
## D. Connection to IIS  
 After connecting to the Subscriber and extracting any changes from the subscription database, the Merge Agent makes an HTTPS request to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Internet Information Services \(IIS\) and uploads data changes as an XML message. The Merge Agent must have logon permissions to IIS.  
  
|Type of authentication|Where the authentication is specified|  
|----------------------------|-------------------------------------------|  
|Basic Authentication is used if one of the following is specified:<br /><br /> -   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: a value of **0** for the **@internet\_security\_mode** parameter of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br />-   RMO: a value of [Standard](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Standard) for [InternetSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetSecurityMode).<br />-   Merge Agent command line: a value of **0** for **\-InternetSecurityMode**.|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: the **@internet\_login** and **@internet\_password** parameters of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br /><br /> RMO: [InternetLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetLogin) and [InternetPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetPassword).<br /><br /> Merge Agent command line: **\-InternetLogin** and **\-InternetPassword**.|  
|Integrated Authentication<sup>1</sup> is used if one of the following is specified:<br /><br /> -   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: a value of **1** for the **@internet\_security\_mode** parameter of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br />-   RMO: a value of [Integrated](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Integrated) for [InternetSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.InternetSecurityMode).<br />-   Merge Agent command line: a value of **1** for **\-InternetSecurityMode**.|The Merge Agent makes connections under the context of the Windows user that is specified for the Merge Agent \(A\).|  
  
 <sup>1</sup> Integrated authentication can be used only if all computers are in the same domain or are in multiple domains that have trust relationships with each other.  
  
> [!NOTE]  
>  Delegation is required if you use Integrated Authentication. We recommend that you use Basic Authentication and SSL for connections from the Subscriber to IIS.  
  
## E. Connection to the Publisher  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Listener and Merge Replication Reconciler components are hosted on the computer that is running IIS. These components perform the following actions:  
  
-   Pick up the HTTPS request that is described in the section "D. Connection to IIS".  
  
-   Make an SQL connection to the publication database and apply the uploaded changes to the publication database.  
  
-   Extract the downloaded changes and send an HTTPS response back to the Merge Agent.  
  
 The Merge Replication Reconciler connects to the Publisher by using either Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. The Windows user or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login that you specify must comply with the following:  
  
-   Be in the publication access list \(PAL\). For more information, see [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md).  
  
-   Be associated with a user in the publication database.  
  
|Type of authentication|Where the authentication is specified|  
|----------------------------|-------------------------------------------|  
|Windows Authentication is used if one of the following is specified:<br /><br /> -   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: a value of **1** for the **@publisher\_security\_mode** parameter of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br />-   RMO: a value of [Integrated](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Integrated) for [PublisherSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode).<br />-   Merge Agent command line: a value of **1** for **\-PublisherSecurityMode**.|The Merge Agent makes connections to the Publisher under the context of the Windows user that is specified for the connection to IIS \(D\). If the Publisher and IIS are on different computers and Integrated Authentication is used for the connection \(D\), you must enable Kerberos delegation on the computer that is running IIS. For more information, see the Windows documentation.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication is used if one of the following is specified:<br /><br /> -   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: a value of **0** for the **@publisher\_security\_mode** parameter of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br />-   RMO: a value of [Standard](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Standard) for [PublisherSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode).<br />-   Merge Agent command line: a value of **0** for **\-PublisherSecurityMode**.|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: the **@publisher\_login** and **@publisher\_password** parameters of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br /><br /> RMO: [PublisherLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin) and [PublisherPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword).<br /><br /> Merge Agent command line: **\-PublisherLogin** and **\-PublisherPassword**.|  
  
## F. Connection to the Distributor  
 The Merge Replication Reconciler that is hosted on the computer that is running IIS also makes connections to the Distributor. The Merge Replication Reconciler connects to the Distributor by using either Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. The Windows user or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login that you specify must comply with the following:  
  
-   Be in the publication access \(PAL\). For more information, see [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md).  
  
-   Be associated with a database user in the distribution database. The user can be the **Guest** user.  
  
 The snapshot share is typically on the Distributor. For more information about snapshot shares, see the section "H. Access to the snapshot share" later in this topic.  
  
|-   Type of authentication|Where the authentication is specified|  
|-------------------------------|-------------------------------------------|  
|Windows Authentication is used if one of the following is specified:<br /><br /> -   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: a value of **1** for the **@distributor\_security\_mode** parameter of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br />-   RMO: a value of [Integrated](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Integrated) for [DistributorSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode).<br />-   Merge Agent command line: a value of **1** for **\-DistributorSecurityMode**.|The Merge Agent makes connections to the Distributor under the context of the Windows user that is specified for the connection to IIS \(D\). If the Distributor and IIS are on different computers and Integrated Authentication is used for the connection \(D\), you must enable Kerberos delegation on the computer that is running IIS. For more information, see the Windows documentation.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication is used if one of the following is specified:<br /><br /> -   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: a value of **0** for the **@distributor\_security\_mode** parameter of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br />-   RMO: a value of [Standard](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Standard) for [DistributorSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode).<br />-   Merge Agent command line: a value of **0** for **\-DistributorSecurityMode**.|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: the **@distributor\_login** and **@distributor\_password** parameters of [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md).<br /><br /> RMO: [DistributorLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin) and [DistributorPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword)<br /><br /> Merge Agent command line: **\-DistributorLogin** and **\-DistributorPassword**.|  
  
## G. Connection to an FTP Server  
 Specify a Windows user for this connection only if you will download snapshot files from an FTP server, instead of from a UNC location, to the computer that is running IIS before you apply the snapshot to the Subscriber. For more information, see [Transfer Snapshots Through FTP](../../Topics\TopicNameNotContainA/Transfer-Snapshots-Through-FTP.md).  
  
|Type of authentication|Where the authentication is specified|  
|----------------------------|-------------------------------------------|  
|Windows Authentication|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)]: the **@ftp\_login** and **@ftp\_password** parameters of [sp\_addmergepublication](../Topic/sp_addmergepublication%20\(Transact-SQL\).md).<br /><br /> RMO: [FtpLogin](assetId:///P:Microsoft.SqlServer.Replication.Publication.FtpLogin) and [FtpPassword](assetId:///P:Microsoft.SqlServer.Replication.Publication.FtpPassword).|  
  
## H. Access to the Snapshot Share  
 The snapshot share is accessed by the Merge Replication Reconciler that is hosted on the computer that is running IIS.  
  
|Type of authentication|Where the authentication is specified|  
|----------------------------|-------------------------------------------|  
|Windows Authentication|The Merge Agent accesses the snapshot share under the context of the Windows user that is specified for the connection to IIS \(D\). If the snapshot share and IIS are on different computers and Integrated Authentication is used for the connection \(D\), you must enable Kerberos delegation on the computer that is running IIS. For more information, see the Windows documentation.|  
  
## I. Application Pool Account for IIS  
 This account is used to start the W3wp.exe process on the computer that is running IIS for [!INCLUDE[winxpsvr](../../Token\Other/winxpsvr_md.md)] or the Dllhost.exe process on [!INCLUDE[win2kfamily](../../Token\Other/win2kfamily_md.md)]. These processes host applications on the computer that is running IIS, such as the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Listener and Merge Replication Reconciler. This account should have read and execute permissions on the following replication DLLs on the computer that is running IIS:  
  
-   Replisapi  
  
-   Replrec  
  
-   Replprov  
  
-   Msgprox  
  
-   Xmlsub  
  
 The account should also be part of IIS\_WPG group. For more information, see the section "Setting Permissions for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Listener" in [Configure IIS for Web Synchronization](../../Topics\TopicNameNotContainA/Configure-IIS-for-Web-Synchronization.md).  
  
|Type of account|Where the account is specified|  
|---------------------|------------------------------------|  
|Any Windows user that has the required permissions.|Internet Information Services \(IIS\) Manager.|  
  
## See Also  
 [Configure Web Synchronization](../../Topics\TopicNameNotContainA/Configure-Web-Synchronization.md)   
 [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md)  
  
  