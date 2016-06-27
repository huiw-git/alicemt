---
title: Storage Replica Overview
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e9b18e14-e692-458a-a39f-d5b569ae76c5
---
# Storage Replica Overview
This topic provides an overview of the new Storage Replica feature in [!INCLUDE[winthreshold_server_2](../compute/hyper-v/includes/winthreshold_server_2_md.md)] and includes the following sections:  
* [Goals and Supported Replication Scenarios](#BKMK_SR1)  
* [Storage Replica Features](#BKMK_SR2)  
* [Storage Replica Prerequisites](#BKMK_SR3)  
* [Background](#BKMK_SR4)    
  
## <a name="BKMK_SR1"></a> Goals and Supported Replication Scenarios  
This guide outlines how your business can benefit from this new functionality and the different replication scenarios that are supported by Storage Replica. It assumes that you have a previous working knowledge of Windows Server, Failover Clustering, File Servers, and Hyper-V, to include basic administration.  
  
### Why use Storage Replica?  
Storage Replica offers new disaster recovery and preparedness capabilities in [!INCLUDE[winthreshold_server_2](../compute/hyper-v/includes/winthreshold_server_2_md.md)]. For the first time, Windows Server offers the peace of mind of zero data loss, with the ability to synchronously protect data on different racks, floors, buildings, campuses, counties, and cities. After a disaster strikes, all data will exist elsewhere without any possibility of loss. The same applies *before* a disaster strikes; Storage Replica offers you the ability to switch workloads to safe locations prior to catastrophes when granted a few moments warning – again, with no data loss.  
  
Storage Replica allows more efficient use of multiple datacenters. By stretching clusters or replicating clusters, workloads can be run in multiple datacenters for quicker data access by local proximity users and applications, as well as better load distribution and use of compute resources. If a disaster takes one datacenter offline, you can move its typical workloads to the other site temporarily.  
  
Storage Replica may allow you to decommission existing file replication systems like DFSR that were pressed into duty as low-end disaster recovery solutions. While DFSR works very well over extremely low bandwidth networks, its latency is very high – often measured in hours or days. This is caused by its requirement for files to close and its artificial throttles meant to prevent network congestion. With those design characteristics, the newest and hottest files in a DFSR replica are the least likely to replicate. Storage Replica operates below the file level and has none of these restrictions.  
  
Storage Replica also supports asynchronous replication for longer ranges and higher latency networks. Because it is not checkpoint-based, and instead continuously replicates, the delta of changes will tend to be far lower than snapshot-based products. Furthermore, Storage Replica operates at the partition layer and therefore replicates all VSS snapshots created by Windows Server or backup software; this allows use of application-consistent data snapshots for point in time recovery, especially unstructured user data replicated asynchronously.  
  
### <a name="BKMK_SRSupportedScenarios"></a>Supported Storage Replica configurations in [!INCLUDE[winthreshold_server_2](../compute/hyper-v/includes/winthreshold_server_2_md.md)]  
Using this guide and [!INCLUDE[winthreshold_server_2](../compute/hyper-v/includes/winthreshold_server_2_md.md)], you can deploy storage replication in a stretch cluster, between cluster\-to\-cluster, and in server\-to\-server configurations \(see Figures 1\-3\). To reiterate from the [!INCLUDE[winthreshold_server_2](../compute/hyper-v/includes/winthreshold_server_2_md.md)] EULA, this feature is provided “AS\-IS” and is not supported in production environments.  
  
**Stretch Cluster** allows configuration of computers and storage in a single cluster, where some nodes share one set of asymmetric storage and some nodes share another, then synchronously or asynchronously replicate with site awareness. This scenario can utilize shared Storage Spaces on JBOD, SAN and iSCSI-attached LUNs. It is managed with PowerShell and the Failover Cluster Manager graphical tool, and allows for automated workload failover.  
  
![Storage_SR_StretchCluster](../storage/media/Storage_SR_StretchCluster.png "Storage_SR_StretchCluster")  
  
**FIGURE 1: Storage replication in a stretch cluster using Storage Replica**  
  
**Cluster to Cluster** allows replication between two separate clusters, where one cluster synchronously or asynchronously replicates with another cluster. This scenario can utilize shared Storage Spaces on JBOD, SAN and iSCSI-attached LUNs. It is managed with PowerShell and requires manual intervention for failover.  
  
![Cluster to Cluster Replication](../storage/media/Storage_SR_ClustertoCluster.png "Storage_SR_ClustertoCluster")  
  
**FIGURE 2: Cluster\-to\-cluster storage replication using Storage Replica**  
  
**Server to server** allows synchronous and asynchronous replication between two standalone servers, using Storage Spaces on JBOD, SAN and iSCSI-attached LUNs, and local drives. It is managed with PowerShell and requires manual intervention for failover.  
  
![Server to Server Storage Replication](../storage/media/Storage_SR_ServertoServer.png "Storage_SR_ServertoServer")  
  
**FIGURE 3: Server\-to\-server storage replication using Storage Replica**  
  
> [!NOTE] You can also configure server-to-self replication, using four separate volumes on one computer. However, this guide does not cover this scenario.  
  
## <a name="BKMK_SR2"> </a> Storage Replica Features  
  
* **Zero data loss, block-level replication**. With synchronous replication, there is no possibility of data loss. With block-level replication, there is no possibility of file locking.  
  
* **Simple deployment and management**. Storage Replica has a design mandate for ease of use. Creation of a replication partnership between two servers requires only a single PowerShell command. Deployment of stretch clusters uses intuitive wizard in the familiar Failover Cluster Manager tool.   
  
* **Guest and host**. All capabilities of Storage Replica are exposed in both virtualized guest and host-based deployments. This means guests can replicate their data volumes even if running on non-Windows virtualization platforms or in public clouds, as long as using Windows Server 2016 in the guest.  
  
* **SMB3-based**. Storage Replica uses the proven and mature technology of SMB 3, first released in Windows Server 2012. This means all of SMB’s advanced characteristics - such as multichannel and SMB direct support on RoCE, iWARP, and InfiniBand RDMA network cards – are available to Storage Replica.   
  
* **Security**. Unlike many vendor’s products, Storage Replica has industry-leading security technology baked in. This includes packet signing, AES-128-GCM full data encryption, support for Intel AES-NI encryption acceleration, and pre-authentication integrity man-in-the-middle attack prevention. Storage Replica utilizes Kerberos AES256 for all authentication between nodes.  
  
* **High performance initial sync**. Storage Replica supports seeded initial sync, where a subset of data already exists on a target from older copies, backups, or shipped drives. Initial replication will only copy the differing blocks, potentially shortening initial sync time and preventing data from using up limited bandwidth. Storage replicas block checksum calculation and aggregation means that initial sync performance is limited only by the speed of the storage and network.  
  
* **Consistency groups**. Write ordering guarantees that applications such as Microsoft SQL Server can write to multiple replicated volumes and know the data will write on the destination server sequentially.  
  
* **User delegation**. Users can be delegated permissions to manage replication without being a member of the built-in Administrators group on the replicated nodes, therefore limiting their access to unrelated areas.  
  
* **Network Constraint**. Storage Replica can be limited to individual networks by server and by replicated volumes, in order to provide application, backup, and management software bandwidth.  
  
* **Thin provisioning**. Support for thin provisioning in Storage Spaces and SAN devices is supported, in order to provide near-instantaneous initial replication times under many circumstances.  
  
[!INCLUDE[winthreshold_server_2](../compute/hyper-v/includes/winthreshold_server_2_md.md)] implements the following features in Storage Replica:  
  
|Feature|Details|  
|-----------|-----------|  
|Type|Host\-based|  
|Synchronous|Yes|  
|Asynchronous|Yes|  
|Storage hardware agnostic|Yes|  
|Replication unit|Volume \(Partition\)|  
|Windows Server Stretch Cluster creation|Yes|  
|Server to server replication|Yes|  
|Cluster to cluster replication|Yes|  
|Transport|SMB3|  
|Network|TCP\/IP or RDMA|  
|RDMA*|iWARP\, InfiniBand, RoCE v2|  
|Replication network port firewall requirements|Single IANA port \(TCP 445 or 5445\)|  
|Multipath\/Multichannel|Yes \(SMB3\)|  
|Kerberos support|Yes \(SMB3\)|  
|Over the wire encryption and signing|Yes \(SMB3\)|  
|Per\-volume failovers allowed|Yes|  
|Management UI in\-box|PowerShell, Failover Cluster Manager|  
  
\*May require additional long haul equipment and cabling.  
  
## <a name="BKMK_SR3"></a> Storage Replica Prerequisites  
  
* Active Directory Domain Services forest.  
* SAS JBODs, fibre channel SAN, shared VHDX, iSCSI Target, or local SCSI/SATA storage. SSD or faster recommended for replication log drives.  
* At least one 1GbE connection on each server for synchronous replication, but preferably RDMA.   
* At least 2GB of RAM and two cores per server.  
* A network between servers with enough bandwidth to contain your IO write workload and an average of ≤5ms round trip latency, for synchronous replication. Asynchronous replication does not have a latency recommendation.  
* The replicated storage cannot be located on the drive containing the Windows operating system folder.
   
##  <a name="BKMK_SR4"> </a> Background  
This section includes information about high-level industry terms, synchronous and asynchronous replication, changes and improvements between Technical Preview 4 and Technical Preview 5, and Storage Replica terminology.   
### High level industry terms  
Disaster Recovery (DR) refers to a contingency plan for recovering from site catastrophes so that the business continues to operate. Data DR means multiple copies of production data in a separate physical location. For example, a stretch cluster, where half the nodes are in one site and half are in another. Disaster Preparedness (DP) refers to a contingency plan for preemptively moving workloads to a different location prior to an oncoming disaster, such as a hurricane.  
  
Service level agreements (SLAs) define the availability of a business’ applications and their tolerance of down time and data loss during planned and unplanned outages. Recovery Time Objective (RTO) defines how long the business can tolerate total inaccessibility of data. Recovery Point Objective (RPO) defines how much data the business can afford to lose.  
  
### Synchronous Replication  
Synchronous replication guarantees that the application writes data to two locations at once before completion of the IO. This replication is more suitable for mission critical data, as it requires network and storage investments, as well as a risk of degraded application performance.  
  
When application writes occur on the source data copy, the originating storage does not acknowledge the IO immediately. Instead, those data changes replicate to the remote destination copy and return an acknowledgement. Only then does the application receive the IO acknowledgment. This ensures constant synchronization of the remote site with the source site, in effect extending storage IOs across the network. In the event of a source site failure, applications can failover to the remote site and resume their operations with assurance of zero data loss.  
  
|Mode|Diagram|Steps|  
|--------|-----------|---------|  
|**Synchronous**<br /><br />Zero Data Loss<br /><br />RPO|![Storage_SR_SynchronousV2](../storage/media/Storage_SR_SynchronousV2.png "Storage_SR_SynchronousV2")|1.  Application writes data<br />2.  Log data is written and the data is replicated to the remote site<br />3.  Log data is written at the remote site<br />4.  Acknowledgement from the remote site<br />5.  Application write acknowledged<br /><br />t & t1 : Data flushed to the volume, logs always write through|  
  
### Asynchronous Replication  
Contrarily, asynchronous replication means that when the application writes data, that data replicates to the remote site without immediate acknowledgment guarantees. This mode allows faster response time to the application as well as a DR solution that works geographically.  
  
When the application writes data, the replication engine captures the write and immediately acknowledges to the application. The captured data then replicates to the remote location. The remote node processes the copy of the data and lazily acknowledges back to the source copy. Since replication performance is no longer in the application IO path, the remote site’s responsiveness and distance are less important factors. There is risk of data loss if the source data is lost and the destination copy of the data was still in buffer without leaving the source.  
  
With its higher than zero RPO, asynchronous replication is less suitable for HA solutions like Failover Clusters, as they are designed for continuous operation with redundancy and no loss of data.  
  
|Mode|Diagram|Steps|  
|--------|-----------|---------|  
|**Asynchronous**<br /><br />Near zero data loss<br /><br />\(depends on multiple factors\)<br /><br />RPO|![Storage_SR_AsynchronousV2](../storage/media/Storage_SR_AsynchronousV2.png "Storage_SR_AsynchronousV2")|1.  Application writes data<br />2.  Log data written<br />3.  Application write acknowledged<br />4.  Data replicated to the remote site<br />5.  Log data written at the remote site<br />6.  Acknowledgement from the remote site<br /><br />t & t1 : Data flushed to the volume, logs always write through|  
  
### Changes and improvements between Technical Preview 4 and Technical Preview 5  
  
-   Asynchronous stretch clusters now supported. Unlike prior technical previews, which required use of synchronous replication, you can now configure stretch clusters over very high latency and lower bandwidth networks.  
  
-   RoCE V2 RDMA networks now supported. In addition to iWARP and InfiniBand networking, Storage Replica now also supports RDMA over Converged Ethernet V2.  
  
-   Thin provisioned storage now supported and can be utilized for greater initial sync efficiency and speed.  
  
-   Network Constraint. You can now control which networks Storage Replica is allowed to use.  
  
-   Failover Cluster Manager update. Now includes an updated wizard for selecting synchronous vs asynchronous stretch cluster replication.  
  
-   Integrated with the Cluster Health service for easier state monitoring and problem resolution.  
  
-   New Powershell  
  
    -   Delegation. You can use `Grant-SRDelegation` and `Revoke-SRDelegation` to configure users to manage replication without them needing to be members of the Administrators group.  
  
    -   Network Constraint. You can use `Set-SRNetworkConstraint`, `Remove-SRNetworkConstraint`, and `Get-SRNetworkConstraint` to control which network interfaces will allow replication.  
  
    -   Ability to generate graphed reports on Nano server using `Test-SRTopology`.  
  
    -   Updates to various cmdlets.  
  
-   Fixes. Many bug fixes, stability improvements, provisioning, and de-provisioning improvements, and known issues resolved.  
### Key Evaluation Points and Behaviors  
  
-   Test only. You cannot deploy Storage Replica in production environments using Windows Server 2016 Technical Preview. This version is only for evaluation purposes in a test lab environment.  
  
-   Performance. The Windows Server 2016 Technical Preview version of Storage Replica has not been fully optimized for performance.  
  
-   Network bandwidth and latency with fastest storage. There are physical limitations around synchronous replication. Because SR implements an IO filtering mechanism using logs and requiring network round trips, synchronous replication is likely make application writes slower. By using low latency, high-bandwidth networks as well as high-throughput disk subsystems for the logs, you will minimize performance overhead.  
  
-   The destination volume is not accessible while replicating. When you configure replication, the destination volume dismounts, making it inaccessible to any writes by users or visible in typical interfaces like File Explorer. Block-level replication technologies are incompatible with allowing access to the destination target’s mounted file system in a volume; NTFS and ReFS do not support users writing data to the volume while blocks change underneath them.  
  
-   The Microsoft implementation of asynchronous replication is different than most. Most industry implementations of asynchronous replication rely on snapshot-based replication, where periodic differential transfers move to the other node and merge. Storage Replica asynchronous replication operates just like synchronous replication, except that it removes the requirement for a serialized synchronous acknowledgment from the destination. This means that SR theoretically has a lower RPO as it continuously replicates. However, this also means it relies on internal application consistency guarantees rather than using snapshots to force consistency in application files. SR guarantees crash consistency in all replication modes  
  
-   Storage Replica is not DFSR. Many customers use DFSR as a disaster recovery solution even though often impractical for that scenario - DFSR cannot replicate open files and is designed to minimize bandwidth usage at the expense of performance, leading to large recovery point deltas. SR may allow you to retire DFSR from some of these types of disaster recovery duties.  
  
-   Storage Replica is not backup. Some IT environments deploy replication systems as backup solutions, due to their zero data loss options when compared to daily backups. SR replicates all changes to all blocks of data on the volume, regardless of the change type. If a user deletes all data from a volume, Storage Replica will replicate the deletion instantly to the other volume, irrevocably removing the data from both servers. Do not use SR as a replacement for a point-in-time backup solution.  
  
-   Storage Replica is not Hyper-V Replica or Microsoft SQL AlwaysOn Availability Groups. Storage Replica is a general purpose, storage-agnostic engine. By definition, it cannot tailor its behavior as ideally as application-level replication. This may lead to specific feature gaps that encourage you to deploy or remain on specific application replication technologies.  
  
> [!NOTE] This document contains a list of [known issues](../Topic/Storage%20Replica:%20Known%20Issues.md) and expected behaviors as well as [frequently asked questions](../Topic/Storage%20Replica:%20Frequently%20Asked%20Questions.md)  
 section.  
### Storage Replica terminology  
This guide frequently uses the following terms:  
  
-   The source is a computer’s volume that allows local writes and replicates outbound. Also known as “primary”.  
  
-   The destination is a computer’s volume that does not allow local writes and replicates inbound. Also known as "secondary".   
  
-   A replication partnership is the synchronization relationship between a source and destination computer for one or more volumes and utilizes a single log.  
  
-   A replication group is the organization of volumes and their replication configuration within a partnership, on a per server basis. A group may contain one or more volumes.  
  
## Related Topics  
  
-   [Storage Replica in Windows Server 2016 Technical Preview](../Topic/Storage%20Replica%20in%20Windows%20Server%202016%20Technical%20Preview.md)  
  
-   [Stretch Cluster Replication Using Shared Storage](../storage/Stretch-Cluster-Replication-Using-Shared-Storage.md)  
  
-   [Server to Server Storage Replication](../storage/Server-to-Server-Storage-Replication.md)  
  
-   [Cluster to Cluster Storage Replication](../storage/Cluster-to-Cluster-Storage-Replication.md)  
  
-   [Storage Replica: Known Issues](../Topic/Storage%20Replica:%20Known%20Issues.md)  
  
-   [Storage Replica: Frequently Asked Questions](../Topic/Storage%20Replica:%20Frequently%20Asked%20Questions.md)  
  
## See Also  
  
-   [Windows Server 2016 Technical Preview 5](../Topic/Windows%20Server%202016%20Technical%20Preview%205.md)  
  
-   [Storage Spaces Direct in Windows Server 2016 Technical Preview](../Topic/Storage%20Spaces%20Direct%20in%20Windows%20Server%202016%20Technical%20Preview.md)  
  
