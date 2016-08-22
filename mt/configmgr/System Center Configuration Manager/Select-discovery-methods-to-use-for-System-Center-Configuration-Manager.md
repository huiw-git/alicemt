---
title: "Select discovery methods to use for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-04-28
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 127ce713-d085-430f-ac7b-2701637fe126
caps.latest.revision: 9
---
# Select discovery methods to use for System Center Configuration Manager
To successfully and efficiently use discovery for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you must consider which methods to use and at which sites to run them.  
  
 Because discovery can generate a large volume of network traffic, and the resultant discovery data records (DDRs) can result in a significant use of CPU resources during processing, use only those discovery methods that you require to meet your goals. You might start by using  only one or two discovery methods, and then later enable additional methods in a controlled manner to extend the level of discovery in your environment. The information in this topic can help you make informed decisions.  
  
 For information about the different discovery methods, see [About discovery methods for System Center Configuration Manager](../System Center Configuration Manager/About-discovery-methods-for-System-Center-Configuration-Manager.md).  
  
## Select methods to discover different things  
 To discover potential [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client computers or user resources, you must enable the appropriate discovery methods. You can use different combinations of discovery methods to locate different resources and to discover additional information about those resources. The discovery methods that you use determine the type of resources that are discovered and which [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services and agents are used in the discovery process. They also determine the type of information about resources that you can discover.  
  
 **Discover Computers**   
When you want to discover computers, you can use Active Directory System Discovery or Network Discovery.  
  
 As an example, if you want to discover resources that can install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client before you use client push installation, you might run Active Directory System Discovery. Alternately you could run Network Discovery and use its options to discover the operating system of resources (required to later use client push installation). However, by using Active Directory System Discovery, you not only discover the resource, but discover basic information and can discover extended information about it from Active Directory Domain Services. This information might be useful in building complex queries and collections to use for the assignment of client settings or content deployment. Network Discovery, on the other hand, provides you with information about your network topology that you are not able to acquire with other discovery methods, but Network Discovery does not provide you any information about your Active Directory environment.  
  
 It is also possible to use only Heartbeat Discovery to force the discovery of clients that you installed by methods other than client push installation. However, unlike other discovery methods, Heartbeat Discovery cannot discover computers that do not have an active [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, and returns a limited set of information. It is intended to maintain an existing database record and not to be the basis of that record. Information submitted by Heartbeat Discovery might not be sufficient to build complex queries or collections.  
  
 If you use Active Directory Group Discovery to discover the membership of a specified group, you can discover limited system or computer information. This does not replace a full discovery of computers but can provide basic information. This basic information is insufficient for client push installation.  
  
 **Discover Users**   
When you want to discover information about users, you can use Active Directory User Discovery. Similar to Active Directory System Discovery, this method discovers users from Active Directory and includes basic information in addition to extended Active Directory information. You can use this information to build complex queries and collections similar to those for computers.  
  
 **Discover Group information**   
When you want to discover information about groups and group memberships, use Active Directory Group Discovery. This discovery method creates resource records for security groups.  
  
 You can use this method to search a specific Active Directory group to identify the members of that group in addition to any nested groups within that group. You can also use this method to search an Active Directory location for groups, and recursively search each child container of that location in Active Directory Domain Services.  
  
 This discovery method can also search the membership of distribution groups. This can identify the group relationships of both users and computers.  
  
 When you discover a group, you can also discover limited information about its members. This does not replace Active Directory System or User Discovery and is usually insufficient to build complex queries and collections or serve as the bases of a client push installation.  
  
 **Discover infrastructure**   
There are two methods that you can use to discover network infrastructure, Active Directory Forest Discovery and Network Discovery.  
  
 You can use Active Directory Forest Discovery to search an Active Directory forest for information about subnets and Active Directory site configurations. These configurations can then be automatically entered into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] as boundary locations.  
  
 When you want to discover your network topology, use Network Discovery. While other discovery methods return information related to Active Directory Domain Services and can identify the current network location of a client, they do not provide infrastructure information based on the subnets and router topology of your network.  
  
##  <a name="bkmk_shared"></a> Discovery data is shared between sites  
 After [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] adds discovery data to a database, it is quickly shared between all sites in the hierarchy. Because there is typically no benefit to discovering the same information at multiple sites in your hierarchy, consider configuring a single instance of each discovery method that you use to run at a single site instead of running multiple instances of a single method at different sites.  
  
 However, for some environments it might be useful to assign the same discovery method to run at multiple sites, each with a separate configuration and schedule. This is because configurations to run a discovery method are specific to a single site. This enables you to have discovery run at one site and then share the results with other sites, or use the same method at two different sites where discovery runs against a local resource and does not try to discover information from locations across a WAN.  For example, this is often useful when using Network Discovery where you direct each site to discover its local network instead of attempting to run discover of all network location across a WAN. If you do configure multiple instances of the same discovery methods to run at different sites, plan the configuration of each site carefully to avoid having two or more sites discover the same resources form your network or Active Directory. Discovering the same locations and resources at multiple sites can consume additional network bandwidth and create duplicate discovery data records (DDRs) for resources that add no value but which  must still be processed by your site servers.  
  
 The following table identifies at which sites you can configure the different discovery methods.  
  
|Discovery method|Supported locations|  
|----------------------|-------------------------|  
|Active Directory Forest Discovery|Central administration site<br /><br /> Primary Site|  
|Active Directory Group Discovery|Primary site|  
|Active Directory System Discovery|Primary site|  
|Active Directory User Discovery|Primary site|  
|Heartbeat Discovery<sup>1</sup>|Primary site|  
|Network Discovery|Primary site<br /><br /> Secondary site|  
  
 <sup>1</sup> Secondary sites cannot configure Heartbeat Discovery but can receive the Heartbeat DDR from a client.  
  
 When secondary sites run Network Discovery, or receive Heartbeat Discovery DDRs, they transfer the DDR by file-based replication to their parent primary site. This is because only primary sites and central administration sites can process DDRs. For more information about how DDRs are processed, see [About discovery data records](../System Center Configuration Manager/Run-discovery-for-System-Center-Configuration-Manager.md#BKMK_DDRs).  
  
## Considerations for different discovery methods  
 Because each site server and network environment is different, limit your initial configurations for discovery and then closely monitor each site server for its ability to process the discovery data that is generated.  
  
-   When you use an Active Directory Discovery method for systems, users, or groups:  
  
    -   Run discovery at a site that has a fast network connection to your domain controllers.  
  
    -   Consider the Active Directory replication topology to ensure discovery can access the latest information.  
  
    -   Consider the scope of the discovery configuration and limit discovery to only those Active Directory locations and groups that you have to discover.  
  
-   If you use Network Discovery:  
  
    -   Use a limited initial configuration to identify your network topography.  
  
    -   After you identify your network topography, configure Network Discovery to run at specific sites that are central to the network areas that you want to more fully discover.  
  
-   Because Heartbeat Discovery does not run at a specific site, you do not have to consider it in general planning for where to run discovery.  
  
-   Because each site server and network environment is different, limit your initial discovery configurations and closely monitor each site server for its ability to process the discovery data that is generated.  
  
##  <a name="bkmk_best"></a> Best practices for discovery  
 **Run Active Directory System Discovery and Active Directory User Discovery before you run Active Directory Group Discovery:**  
  
 When Active Directory Group Discovery identifies a previously undiscovered user or computer as a member of a group, it attempts to discover basic details for the user or computer. Because Active Directory Group Discovery is not optimized for this type of discovery, this process can cause Active Directory Group Discovery to run slow. Additionally, Active Directory Group Discovery identifies only the basic details about users and computers is discovers, and does not create a complete user or computer discovery record. When you run Active Directory System Discovery and Active Directory User Discovery, the additional Active Directory attributes for each object type are available, and as a result, Active Directory Group Discovery runs more efficiently.  
  
 **When you configure Active Directory Group Discovery, only specify groups that you use with Configuration Manager:**  
  
 To help control the use of resources by Active Directory Group Discovery, specify only those groups that you use with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. This is because Active Directory Group Discovery recursively searches each group it discovers for users, computers, and nested groups. The search of each nested group can expand the scope of Active Directory Group Discovery and reduce performance. Additionally, when you configure delta discovery for Active Directory Group Discovery, the discovery method monitors each group for changes. This further reduces performance when the method must search unnecessary groups.  
  
 **Configure discovery methods with a longer interval between full discovery, and a more frequent period of delta discovery:**  
  
 Because delta discovery uses fewer resources than a full discovery cycle, and can identify new or modified resources in Active Directory, when you use delta discovery you can reduce the frequency of full discovery cycles to run one per week or less. Delta discovery for Active Directory System Discovery, Active Directory User Discovery and Active Directory Group Discovery identifies almost all the changes of Active Directory objects and can maintain accurate discovery data for resources.  
  
 **Run Active Directory Discovery methods at primary site that has a network location that is closest to your Active Directory domain controller:**  
  
 To improve the performance of Active Directory discovery, it is recommended to run discover at a primary site that has a fast network connection to your domain controllers. If you run the same Active Directory discovery method at multiple sites, it is recommended to configure each discovery method to avoid overlap. Unlike past versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], discovery data is shared between sites. Therefore, it is not necessary to discovery the same information at multiple sites. For more information, see [Discovery data is shared between sites](../System Center Configuration Manager/Select-discovery-methods-to-use-for-System-Center-Configuration-Manager.md#bkmk_shared).  
  
 **Run Active Directory Forest Discovery at  only one site when you plan to automatically create boundaries from the discovery data:**  
  
 If you run Active Directory Forest Discovery at more than one site in a hierarchy, it is recommended to only enable options to automatically create boundaries at a single site. This is because when Active Directory Forest Discovery runs at each site and creates boundaries, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot merge those boundaries into a single boundary object. When you configure Active Directory Forest Discovery to automatically create boundaries at multiple sites, the result can be duplicated boundary objects in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
## See Also  
 [Run discovery for System Center Configuration Manager](../System Center Configuration Manager/Run-discovery-for-System-Center-Configuration-Manager.md)