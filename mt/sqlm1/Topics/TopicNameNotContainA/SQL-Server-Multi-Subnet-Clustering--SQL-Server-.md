---
title: SQL Server Multi-Subnet Clustering (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd909612-99cc-4962-a8fb-e9a5b918e221
---
# SQL Server Multi-Subnet Clustering (SQL Server)
  A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] multi\-subnet failover cluster is a configuration where each failover cluster node is connected to a different subnet or different set of subnets. These subnets can be in the same location or in geographically dispersed sites. Clustering across geographically dispersed sites is sometimes referred to as stretch clusters. As there is no shared storage that all the nodes can access, data should be replicated between the data storage on the multiple subnets. With data replication, there is more than one copy of the data available. Therefore, a multi\-subnet failover cluster provides a disaster recovery solution in addition to high availability.  
  
 **In this Topic:**  
  
-   [SQL Server Multi\-Subnet Failover Cluster \(Two\-Nodes, Two\-Subnets\)](#VisualElement)  
  
-   [IP Address Resource Considerations](#ComponentsAndConcepts)  
  
-   [Client Recovery Latency During Failovers](#DNS)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="VisualElement"></a> SQL Server Multi\-Subnet Failover Cluster \(Two\-Nodes, Two\-Subnets\)  
 The following illustration represents a two node, two subnet failover cluster instance \(FCI\) in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 ![Multi-Subnet Architecture with MultiSubnetFailover](../../Images\Image\ImageNotContaina/Multi-Subnet_Architecture_withMultiSubnetFailoverParam.gif "Multi-Subnet_Architecture_withMultiSubnetFailoverParam")  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="Configurations"></a> Multi\-Subnet Failover Cluster Instance Configurations  
 The following are some examples of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCIs that use multiple subnets:  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCI SQLCLUST1 includes Node1 and Node2. Node1 is connected to Subnet1. Node2 is connected to Subnet2. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup sees this configuration as a multi\-subnet cluster and sets the IP address resource dependency to **OR**.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCI SQLCLUST1 includes Node1, Node2, and Node3. Node1 and Node2 are connected to Subnet1. Node 3 is connected to Subnet2. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup sees this configuration as a multi\-subnet cluster and sets the IP address resource dependency to **OR**. Because Node1 and Node2 are on the same subnet, this configuration provides additional local high availability.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCI SQLCLUST1 includes Node1 and Node2. Node1 is on Subnet1. Node2 is on Subnet1 and Subnet2. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup sees this configuration as a multi\-subnet cluster and sets the IP address resource dependency to **OR**.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCI SQLCLUST1 includes Node1 and Node2. Node1 is connected to Subnet1 and Subnet2. Node2 is also connected to Subnet1 and Subnet2. The IP address resource dependency is set to **AND** by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup.  
  
    > [!NOTE]  
    >  This configuration is not considered as a multi\-subnet failover cluster configuration because the clustered nodes are on the same set of subnets.  
  
##  <a name="ComponentsAndConcepts"></a> IP Address Resource Considerations  
 In a multi\-subnet failover cluster configuration, the IP addresses are not owned by all the nodes in the failover cluster, and may not be all online during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] startup. Beginning in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can set the IP address resource dependency to **OR**. This enables [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to be online when there is at least one valid IP address that it can bind to.  
  
> [!NOTE]  
>  In the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions earlier than [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], a stretch V\-LAN technology was used in multi\-site cluster configurations to expose a single IP address for failover across sites. With the new capability of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to cluster nodes across different subnets, you can now configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover clusters across multiple sites without implementing the stretch V\-LAN technology.  
  
### IP Address Resource OR Dependency Considerations  
 You may want to consider the following failover behavior if you set the IP address resource dependency is set to **OR**:  
  
-   When there is a failure of one of the IP addresses on the node that currently owns the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cluster resource group, a failover is not triggered automatically until all the IP addresses valid on that node fail.  
  
-   When a failover occurs, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will come online if it can bind to at least one IP address that is valid on the current node. The IP addresses that did not bind to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] at startup will be listed in the error log.  
  
 [&#91;Top&#93;](#Top)  
  
 When a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCI is installed side\-by\-side with a standalone instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], take care to avoid TCP port number conflicts on the IP addresses. Conflicts usually occur when two instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] are both configured to use the default TCP port \(1433\). To avoid conflicts, configure one instance to use a non\-default fixed port. Configuring a fixed port is usually easiest on the standalone instance. Configuring the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to use different ports will prevent an unexpected IP Address\/TCP port conflict that blocks an instance startup when a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FCI fails to the standby node.  
  
##  <a name="DNS"></a> Client Recovery Latency During Failover  
 A multi\-subnet FCI by default enables the RegisterAllProvidersIP cluster resource for its network name. In a multi\-subnet configuration, both the online and offline IP addresses of the network name will be registered at the DNS server. The client application then retrieves all registered IP addresses from the DNS server and attempts to connect to the addresses either in order or in parallel. This means that client recovery time in multi\-subnet failovers no longer depend on DNS update latencies. By default, the client tries the IP addresses in order. When the client uses the new optional **MultiSubnetFailover\=True** parameter in its connection string, it will instead try the IP addresses simultaneously and connects to the first server that responds. This can help minimize the client recovery latency when failovers occur. For more information, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](../Topic/AlwaysOn%20Client%20Connectivity%20\(SQL%20Server\).md) and [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md).  
  
 With legacy client libraries or third party data providers, you cannot use the **MultiSubnetFailover** parameter in your connection string. To help ensure that your client application works optimally with multi\-subnet FCI in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], try to adjust the connection timeout in the client connection string by 21 seconds for each additional IP address. This ensures that the client’s reconnection attempt does not timeout before it is able to cycle through all IP addresses in your multi\-subnet FCI.  
  
 The default client connection time\-out period for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Studio and **sqlcmd** is 15 seconds.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="RelatedContent"></a> Related Content  
  
|Content Description|Topic|  
|-------------------------|-----------|  
|Installing a SQL Server Failover Cluster|[Create a New SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Create%20a%20New%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md)|  
|In\-place upgrade of your existing SQL Server Failover Cluster|[Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](../Topic/Upgrade%20a%20SQL%20Server%20Failover%20Cluster%20Instance%20\(Setup\).md)|  
|Maintaining your existing SQL Server Failover Cluster|[Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Add%20or%20Remove%20Nodes%20in%20a%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md)|  
|Windows Failover Clustering|[Windows 2008 R2 Failover Multi\-Site Clustering](http://www.microsoft.com/windowsserver2008/en/us/failover-clustering-multisite.aspx)|  
|Use the Failover Cluster Management snap\-in to view WSFC events and logs|[View Events and Logs for a Failover Cluster](http://technet.microsoft.com/library/cc772342\(WS.10\).aspx)|  
|Use Windows PowerShell to create a log file for all nodes \(or a specific a node\) in a WSFC failover cluster|[Get\-ClusterLog Failover Cluster Cmdlet](http://technet.microsoft.com/library/ee461045.aspx)|  
  
 [&#91;Top&#93;](#Top)  
  
  