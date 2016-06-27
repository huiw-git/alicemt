---
title: Troubleshooting Active Directory Replication Problems
ms.custom: 
  - x
ms.prod: windows-server-threshold
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - active-directory-domain-services
ms.tgt_pltfrm: na
ms.assetid: 13964079-3aaa-4551-9140-9687b333e752
---
# Troubleshooting Active Directory Replication Problems
Active Directory replication problems can have several different sources. For example, Domain Name System \(DNS\) problems, networking issues, or security problems can all cause Active Directory replication to fail.  
  
 The rest of this topic explains tools and a general methodology to fix Active Directory replication errors. For a hands\-on lab that demonstrates how to troubleshoot Active Directory replication problems, see [TechNet Virtual Lab: Troubleshooting Active Directory Replication Errors](http://go.microsoft.com/?linkid=9844718).  
  
 The following subtopics cover symptoms, causes, and how to resolve specific replication errors:  
  
-   [Fixing Replication Lingering Object Problems \(Event IDs 1388, 1988, 2042\)](http://technet.microsoft.com/library/cc949124\(WS.10\).aspx)  
  
-   [Fixing Replication Security Problems](http://technet.microsoft.com/library/cc949132\(WS.10\).aspx)  
  
-   [Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](http://technet.microsoft.com/library/cc949133\(WS.10\).aspx)  
  
-   [Fixing Replication Connectivity Problems \(Event ID 1925\)](http://technet.microsoft.com/library/cc949131\(WS.10\).aspx)  
  
-   [Fixing Replication Topology Problems \(Event ID 1311\)](http://technet.microsoft.com/library/cc949129\(WS.10\).aspx)  
  
-   [Verify DNS Functionality to Support Directory Replication](http://technet.microsoft.com/library/dd728017\(WS.10\).aspx)  
  
-   [Replication error 8614 The Active Directory cannot replicate with this server because the time since the last replication with this server has exceeded the tombstone lifetime](http://technet.microsoft.com/library/replication-error-8614-the-active-directory-cannot-replicate-with-this-server-because-the-time-since-the-last-replication-with-this-server-has-exceeded-the-tombstone-lifetime\(WS.10\).aspx)  
  
-   [Replication error 8524 The DSA operation is unable to proceed because of a DNS lookup failure](http://technet.microsoft.com/library/replication-error-8524-the-dsa-operation-is-unable-to-proceed-because-of-a-dns-lookup-failure\(WS.10\).aspx)  
  
-   [Replication error 8456 or 8457 The source &#124; destination server is currently rejecting replication requests](http://technet.microsoft.com/library/replication-error-8456-the-source-server-is-currently-rejecting-replication-requests-or-replication-error-8457-the-destination-server-is-currently-rejecting-replication-requests\(WS.10\).aspx)  
  
-   [Replication error 8453 Replication access was denied](http://technet.microsoft.com/library/replication-error-8453-replication-access-was-denied\(WS.10\).aspx)  
  
-   [Replication error 8452 The naming context is in the process of being removed or is not replicated from the specified server](http://technet.microsoft.com/library/replication-error-8452-the-naming-context-is-in-the-process-of-being-removed-or-is-not-replicated-from-the-specified-server\(WS.10\).aspx)  
  
-   [Replication error 5 Access is denied](http://technet.microsoft.com/library/replication-error-5-access-is-denied\(WS.10\).aspx)  
  
-   [Replication error \-2146893022 The target principal name is incorrect](http://technet.microsoft.com/library/replication-error-2146893022-the-target-principal-name-is-incorrect\(WS.10\).aspx)  
  
-   [Replication error 1753 There are no more endpoints available from the endpoint mapper](http://technet.microsoft.com/library/replication-error-1753-there-are-no-more-endpoints-available-from-the-endpoint-mapper\(WS.10\).aspx)  
  
-   [Replication error 1722 The RPC server is unavailable](http://technet.microsoft.com/library/replication-error-1722-the-rpc-server-is-unavailable\(WS.10\).aspx)  
  
-   [Replication error 1396 Logon Failure The target account name is incorrect](http://technet.microsoft.com/library/replication-error-1396-logon-failure-the-target-account-name-is-incorrect\(WS.10\).aspx)  
  
-   [Replication error 1256 The remote system is not available](http://technet.microsoft.com/library/replication-error-1256-the-remote-system-is-not-available\(WS.10\).aspx)  
  
-   [Replication error 1127 While accessing the hard disk, a disk operation failed even after retries](http://technet.microsoft.com/library/replication-error-1127-while-accessing-the-hard-disk-a-disk-operation-failed-even-after-retries\(WS.10\).aspx)  
  
-   [Replication error 8451 The replication operation encountered a database error](http://technet.microsoft.com/library/replication-error-8451-the-replication-operation-encountered-a-database-error\(WS.10\).aspx)  
  
-   [Replication error 8606 Insufficient attributes were given to create an object](http://technet.microsoft.com/library/replication-error-8606-insufficient-attributes-were-given-to-create-an-object\(WS.10\).aspx)  
  
 **In this topic**  
  
-   [Introduction and resources for troubleshooting Active Directory replication](../../identity/ad-ds/Troubleshooting-Active-Directory-Replication-Problems.md#BKMK_Intro)  
  
-   [Event and tool solution recommendations](#BKMK_event_tool)  
  
-   [Ruling out intentional disruptions or hardware failures](#BKMK_ruling_out)  
  
-   [Root causes](#BKMK_root_causes)  
  
-   [General approach to fixing problems](#BKMK_general_approach)  
  
-   [Using Repadmin to retrieve replication status](#BKMK_using_repadmin)  
  
-   [Replication problems and resolutions](#BKMK_problems_resolutions)  
  
-   [Event messages that indicate Active Directory replication problems](#BKMK_event_messages)  
  
##  <a name="BKMK_Intro"></a> Introduction and resources for troubleshooting Active Directory replication  
 Inbound or outbound replication failure causes Active Directory objects that represent the replication topology, replication schedule, domain controllers, users, computers, passwords, security groups, group memberships, and Group Policy to be inconsistent between domain controllers. Directory inconsistency and replication failure cause either operational failures or inconsistent results, depending on the domain controller that is contacted for the operation, and can prevent the application of Group Policy and access control permissions. Active Directory Domain Services \(AD DS\) depends on network connectivity, name resolution, authentication and authorization, the directory database, the replication topology, and the replication engine. When the root cause of a replication problem is not immediately obvious, determining the cause among the many possible causes requires systematic elimination of probable causes.  
  
 For a UI\-based tool to help monitor replication and diagnose errors, see [Active Directory Replication Status Tool](http://www.microsoft.com/download/details.aspx?id=30005). There is also a [hands\-on lab](http://go.microsoft.com/?linkid=9844718) that demonstrates how to use Active Directory Replication Status and other tools to troubleshoot errors.  
  
 For a comprehensive document that describes how you can use the Repadmin tool to troubleshoot Active Directory replication is available; see Monitoring and Troubleshooting Active Directory Replication Using Repadmin \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=122830](http://go.microsoft.com/fwlink/?LinkId=122830)\).  
  
 For information about how Active Directory replication works, see the following technical references:  
  
-   Active Directory Replication Model Technical Reference \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=65958](http://go.microsoft.com/fwlink/?LinkId=65958)\)  
  
-   Active Director Replication Topology Technical Reference \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=93578](http://go.microsoft.com/fwlink/?LinkId=93578)\)  
  
##  <a name="BKMK_event_tool"></a> Event and tool solution recommendations  
 Ideally, the red \(Error\) and yellow \(Warning\) events in the Directory Service event log suggest the specific constraint that is causing replication failure on the source or destination domain controller. If the event message suggests steps for a solution, try the steps that are described in the event. The Repadmin tool and other diagnostic tools also provide information that can help you resolve replication failures.  
  
 For detailed information about using Repadmin for troubleshooting replication problems, see Monitoring and Troubleshooting Active Directory Replication Using Repadmin \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=122830](http://go.microsoft.com/fwlink/?LinkId=122830)\).  
  
##  <a name="BKMK_ruling_out"></a> Ruling out intentional disruptions or hardware failures  
 Sometimes replication errors occur because of intentional disruptions. For example, when you troubleshoot Active Directory replication problems, rule out intentional disconnections and hardware failures or upgrades first.  
  
### Intentional disconnections  
 If replication errors are reported by a domain controller that is attempting replication with a domain controller that has been built in a staging site and is currently offline awaiting its deployment in the final production site \(a remote site, such as a branch office\), you can account for those replication errors. To avoid separating a domain controller from the replication topology for extended periods, which causes continuous errors until the domain controller is reconnected, consider adding such computers initially as member servers and using the install from media \(IFM\) method to install Active Directory Domain Services \(AD DS\). You can use the Ntdsutil command\-line tool to create installation media that you can store on removable media \(CD, DVD, or other media\) and ship to the destination site. Then, you can use the installation media to install AD DS on the domain controllers at the site, without the use of replication. For more information about IFM, see [Installing an Additional Domain Controller by Using IFM](../Topic/Installing%20an%20Additional%20Domain%20Controller%20by%20Using%20IFM.md).  
  
### Hardware failures or upgrades  
 If replication problems occur as a result of hardware failure \(for example, failure of a motherboard, disk subsystem, or hard drive\), notify the server owner so that the hardware problem can be resolved.  
  
 Periodic hardware upgrades can also cause domain controllers to be out of service. Ensure that your server owners have a good system of communicating such outages in advance.  
  
### Firewall configuration  
 By default, Active Directory replication remote procedure calls \(RPCs\) occur dynamically over an available port through the RPC Endpoint Mapper \(RPCSS\) on port 135. Make sure that Windows Firewall with Advanced Security and other firewalls are configured properly to allow for replication. For information about specifying the port for Active Directory replication and port settings, see article 224196 in the Microsoft Knowledge Base \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=22578](http://go.microsoft.com/fwlink/?LinkId=22578)\). For information about the ports that Active Directory replication uses, see Active Directory Replication Tools and Settings \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=123774](http://go.microsoft.com/fwlink/?LinkId=123774)\). For information about managing Active Directory replication over firewalls, see Active Directory Replication over Firewalls \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=123775](http://go.microsoft.com/fwlink/?LinkId=123775)\).  
  
## Responding to failure of an outdated server running Windows 2000 Server  
 If a domain controller running Windows 2000 Server has failed for longer than the number of days in the tombstone lifetime, the solution is always the same:  
  
1.  Move the server from the corporate network to a private network.  
  
2.  Either forcefully remove Active Directory or reinstall the operating system.  
  
3.  Remove the server metadata from Active Directory so that the server object cannot be revived.  
  
> [!NOTE]  
>  You can use a script to clean up server metadata on most Windows operating systems. For information about using this script, see Remove Active Directory Domain Controller Metadata \([http:\/\/go.microsoft.com\/fwlink\/?LinkID\=123599](http://go.microsoft.com/fwlink/?LinkID=123599)\). By default, NTDS Settings objects that are deleted are revived automatically for a period of 14 days. Therefore, if you do not remove server metadata \(use Ntdsutil or the script mentioned previously to perform metadata cleanup\), the server metadata is reinstated in the directory, which prompts replication attempts to occur. In this case, errors will be logged persistently as a result of the inability to replicate with the missing domain controller.  
  
##  <a name="BKMK_root_causes"></a> Root causes  
 If you rule out intentional disconnections, hardware failures, and outdated Windows 2000 domain controllers, the remainder of replication problems almost always have one of the following root causes:  
  
-   Network connectivity: The network connection might be unavailable, or network settings are not configured properly.  
  
-   Name resolution: DNS misconfigurations are a common cause of replication failures.  
  
-   Authentication and authorization: Authentication and authorization problems cause "Access denied" errors when a domain controller tries to connect to its replication partner.  
  
-   Directory database \(store\): The directory database might not be able to process transactions fast enough to keep up with replication time\-outs.  
  
-   Replication engine: If intersite replication schedules are too short, replication queues might be too large to process in the time that is required by the outbound replication schedule. In this case, replication of some changes can be stalled indefinitely—potentially, long enough to exceed the tombstone lifetime.  
  
-   Replication topology: Domain controllers must have intersite links in AD DS that map to real wide area network \(WAN\) or virtual private network \(VPN\) connections. If you create objects in AD DS for the replication topology that are not supported by the actual site topology of your network, replication that requires the misconfigured topology fails.  
  
##  <a name="BKMK_general_approach"></a> General approach to fixing problems  
 Use the following general approach to fixing replication problems:  
  
1.  Monitor replication health daily, or use Repadmin.exe to retrieve replication status daily.  
  
2.  Attempt to resolve any reported failure in a timely manner by using the methods that are described in event messages and this guide. If software might be causing the problem, uninstall the software before you continue with other solutions.  
  
3.  If the problem that is causing replication to fail cannot be resolved by any known methods, remove AD DS from the server and then reinstall AD DS. For more information about reinstalling AD DS, see Decommissioning a Domain Controller \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=128290](http://go.microsoft.com/fwlink/?LinkId=128290)\).  
  
4.  If AD DS cannot be removed normally while the server is connected to the network, use one of the following methods to resolve the problem:  
  
    -   Force AD DS removal in Directory Services Restore Mode \(DSRM\), clean up server metadata, and then reinstall AD DS.  
  
    -   Reinstall the operating system, and rebuild the domain controller.  
  
     For more information about forcing removal of AD DS, see Forcing the Removal of a Domain Controller \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=128291](http://go.microsoft.com/fwlink/?LinkId=128291)\).  
  
##  <a name="BKMK_using_repadmin"></a> Using Repadmin to retrieve replication status  
 Replication status is an important way for you to evaluate the status of the directory service. If replication is working without errors, you know the domain controllers that are online. You also know that the following systems and services are working:  
  
-   DNS infrastructure  
  
-   Kerberos authentication protocol  
  
-   Windows Time service \(W32time\)  
  
-   Remote procedure call \(RPC\)  
  
-   Network connectivity  
  
 Use Repadmin to monitor replication status daily by running a command that assesses the replication status of all the domain controllers in your forest. The procedure generates a .csv file that you can open in Microsoft Excel and filter for replication failures.  
  
 You can use the following procedure to retrieve the replication status of all domain controllers in the forest.  
  
 **Requirements**  
  
-   Membership in **Enterprise Admins**, or equivalent, is the minimum required to complete this procedure. [!INCLUDE[review_details](../../identity/ad-ds/includes/review_details_md.md)]  
  
-   Tools:  
  
     Repadmin.exe  
  
     Excel \(Microsoft Office\)  
  
#### To generate a repadmin \/showrepl spreadsheet for domain controllers  
  
1.  Open a Command Prompt as an administrator: On the **Start** menu, right\-click **Command Prompt**, and then click **Run as administrator**. If the **User Account Control** dialog box appears, provide Enterprise Admins credentials, if required, and then click **Continue**.  
  
2.  At the command prompt, type the following command, and then press ENTER:  
  
     `repadmin /showrepl * /csv >showrepl.csv`  
  
3.  Open Excel.  
  
4.  Click the **Office** button, click **Open**, navigate to **showrepl.csv**, and then click **Open**.  
  
5.  Hide or delete column **A** as well as the **Transport Type** column, as follows:  
  
6.  Select a column that you want to hide or delete.  
  
    -   To hide the column, right\-click the column, and then click **Hide**.  
  
         Or  
  
    -   To delete the column, right\-click the selected column, and then click **Delete**.  
  
7.  Select row 1 beneath the column heading row. On the **View** tab, click **Freeze Panes**, and then click **Freeze Top Row**.  
  
8.  Select the entire spreadsheet. On the **Data** tab, click **Filter**.  
  
9. In the **Last Success Time** column, click the down arrow, and then click **Sort Ascending**.  
  
10. In the **Source DC** column, click the filter down arrow, point to **Text Filters**, and then click **Custom Filter**.  
  
11. In the **Custom AutoFilter** dialog box, under **Show rows where**, click **does not contain**. In the adjacent text box, type **del** to eliminate from view the results for deleted domain controllers.  
  
12. Repeat step 11 for the **Last Failure Time** column, but use the value **does not equal**, and then type the value **0**.  
  
13. Resolve replication failures.  
  
 For every domain controller in the forest, the spreadsheet shows the source replication partner, the time that replication last occurred, and the time that the last replication failure occurred for each naming context \(directory partition\). By using **Autofilter** in Excel, you can view the replication health for working domain controllers only, failing domain controllers only, or domain controllers that are the least or most current, and you can see the replication partners that are replicating successfully.  
  
##  <a name="BKMK_problems_resolutions"></a> Replication problems and resolutions  
 Replication problems are reported in event messages and in various error messages that occur when an application or service attempts an operation. Ideally, these messages are collected by your monitoring application or when you retrieve replication status.  
  
 Most replication problems are identified in the event messages that are logged in the Directory Service event log. Replication problems might also be identified in the form of error messages in the output of the **repadmin \/showrepl** command.  
  
### repadmin \/showrepl error messages that indicate replication problems  
 To identify Active Directory replication problems, use the **repadmin \/showrepl** command, as described in the previous section. The following table shows error messages that this command generates, along with the root causes of the errors and links to topics that provide solutions for the errors.  
  
|Repadmin error|Root cause|Solution|  
|--------------------|----------------|--------------|  
|The time since last replication with this server has exceeded the tombstone lifetime.|A domain controller has failed inbound replication with the named source domain controller long enough for a deletion to have been tombstoned, replicated, and garbage\-collected from AD DS.|[Event ID 2042: It has been too long since this machine replicated](../Topic/Event%20ID%202042:%20It%20has%20been%20too%20long%20since%20this%20machine%20replicated.md)|  
|No inbound neighbors.|If no items appear in the “Inbound Neighbors” section of the output that is generated by **repadmin \/showrepl**, the domain controller was not able to establish replication links with another domain controller.|[Fixing Replication Connectivity Problems \(Event ID 1925\)](../../identity/ad-ds/Fixing-Replication-Connectivity-Problems--Event-ID-1925-.md)|  
|Access is denied.|A replication link exists between two domain controllers, but replication cannot be performed properly as a result of an authentication failure.|[Fixing Replication Security Problems](../../identity/ad-ds/Fixing-Replication-Security-Problems.md)|  
|Last attempt at \<date \- time\> failed with the “Target account name is incorrect.”|This problem can be related to connectivity, DNS, or authentication issues.<br /><br /> If this is a DNS error, the local domain controller could not resolve the globally unique identifier \(GUID\)–based DNS name of its replication partner.|[Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](../../identity/ad-ds/Fixing-Replication-DNS-Lookup-Problems--Event-IDs-1925--2087--2088-.md)<br /><br /> [Fixing Replication Security Problems](../../identity/ad-ds/Fixing-Replication-Security-Problems.md)<br /><br /> [Fixing Replication Connectivity Problems \(Event ID 1925\)](../../identity/ad-ds/Fixing-Replication-Connectivity-Problems--Event-ID-1925-.md)|  
|LDAP Error 49.|The domain controller computer account might not be synchronized with the Key Distribution Center \(KDC\).|[Fixing Replication Security Problems](../../identity/ad-ds/Fixing-Replication-Security-Problems.md)|  
|Cannot open LDAP connection to local host|The administration tool could not contact AD DS.|[Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](../../identity/ad-ds/Fixing-Replication-DNS-Lookup-Problems--Event-IDs-1925--2087--2088-.md)|  
|Active Directory replication has been preempted.|The progress of inbound replication was interrupted by a higher\-priority replication request, such as a request that was generated manually with the **repadmin \/sync** command.|Wait for replication to complete. This informational message indicates normal operation.|  
|Replication posted, waiting.|The domain controller posted a replication request and is waiting for an answer. Replication is in progress from this source.|Wait for replication to complete. This informational message indicates normal operation.|  
  
###  <a name="BKMK_event_messages"></a> Event messages that indicate Active Directory replication problems  
 The following table lists common events that might indicate problems with Active Directory replication, along with root causes of the problems and links to topics that provide solutions for the problems.  
  
|Event ID and source|Root cause|Solution|  
|-------------------------|----------------|--------------|  
|1311 — NTDS KCC|The replication configuration information in AD DS does not accurately reflect the physical topology of the network.|[Fixing Replication Topology Problems \(Event ID 1311\)](../../identity/ad-ds/Fixing-Replication-Topology-Problems--Event-ID-1311-.md)|  
|1388 — NTDS Replication|Strict replication consistency is not in effect, and a lingering object has been replicated to the domain controller.|[Fixing Replication Lingering Object Problems \(Event IDs 1388, 1988, 2042\)](../../identity/ad-ds/Fixing-Replication-Lingering-Object-Problems--Event-IDs-1388--1988--2042-.md)|  
|1925 — NTDS KCC|The attempt to establish a replication link for a writable directory partition failed. This event can have different causes, depending on the error.|[Fixing Replication Connectivity Problems \(Event ID 1925\)](../../identity/ad-ds/Fixing-Replication-Connectivity-Problems--Event-ID-1925-.md)<br /><br /> [Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](../../identity/ad-ds/Fixing-Replication-DNS-Lookup-Problems--Event-IDs-1925--2087--2088-.md)|  
|1988 — NTDS Replication|The local domain controller has attempted to replicate an object from a source domain controller that is not present on the local domain controller because it may have been deleted and already garbage\-collected. Replication will not proceed for this directory partition with this partner until the situation is resolved.|[Fixing Replication Lingering Object Problems \(Event IDs 1388, 1988, 2042\)](../../identity/ad-ds/Fixing-Replication-Lingering-Object-Problems--Event-IDs-1388--1988--2042-.md)|  
|2042 — NTDS Replication|Replication has not occurred with this partner for a tombstone lifetime, and replication cannot proceed.|[Fixing Replication Lingering Object Problems \(Event IDs 1388, 1988, 2042\)](../../identity/ad-ds/Fixing-Replication-Lingering-Object-Problems--Event-IDs-1388--1988--2042-.md)|  
|2087 — NTDS Replication|AD DS could not resolve the DNS host name of the source domain controller to an IP address, and replication failed.|[Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](../../identity/ad-ds/Fixing-Replication-DNS-Lookup-Problems--Event-IDs-1925--2087--2088-.md)|  
|2088 — NTDS Replication|AD DS could not resolve the DNS host name of the source domain controller to an IP address, but replication succeeded.|[Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](../../identity/ad-ds/Fixing-Replication-DNS-Lookup-Problems--Event-IDs-1925--2087--2088-.md)|  
|5805 — Net Logon|A machine account failed to authenticate, which is usually caused by either multiple instances of the same computer name or the computer name not replicating to every domain controller.|[Fixing Replication Security Problems](../../identity/ad-ds/Fixing-Replication-Security-Problems.md)|  
  
 For more information about replication concepts, see “Active Directory Replication Technologies” in the Windows Server 2003 Technical Reference \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=41950](http://go.microsoft.com/fwlink/?LinkId=41950)\).  
  
 **In this section**  
  
 See the following topics for detailed information about troubleshooting Active Directory replication problems:  
  
 [Fixing Replication Lingering Object Problems \(Event IDs 1388, 1988, 2042\)](../../identity/ad-ds/Fixing-Replication-Lingering-Object-Problems--Event-IDs-1388--1988--2042-.md)  
  
 [Fixing Replication Security Problems](../../identity/ad-ds/Fixing-Replication-Security-Problems.md)  
  
 [Fixing Replication DNS Lookup Problems \(Event IDs 1925, 2087, 2088\)](../../identity/ad-ds/Fixing-Replication-DNS-Lookup-Problems--Event-IDs-1925--2087--2088-.md)  
  
 [Fixing Replication Connectivity Problems \(Event ID 1925\)](../../identity/ad-ds/Fixing-Replication-Connectivity-Problems--Event-ID-1925-.md)  
  
 [Fixing Replication Topology Problems \(Event ID 1311\)](../../identity/ad-ds/Fixing-Replication-Topology-Problems--Event-ID-1311-.md)