---
title: "Schema extensions for System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: 8
caps.handback.revision: 0
robots: noindex
---
# Schema extensions for System Center Configuration Manager
You can extend the Active Directory schema to support [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. This edits a forests Active Directory schema  to add a new container and several attributes that are used by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites to publish key information in Active Directory where clients can securely access it.  This information can simplify the deployment and configuration of clients, and helps clients locate site resources like servers with deployed content or that provide various services to clients.  
  
-   Extending the Active Directory schema is not required, but is recommended.  
  
 Before you [extend the Active Directory schema](https://msdnstage.redmond.corp.microsoft.com/en-US/library/mt345589\(TechNet.10\).aspx), you should be familiar with Active Directory Domain Services and comfortable with [modifying the Active Directory schema](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx).  
  
## Considerations for Extending the Active Directory Schema for Configuration Manager  
  
-   The Active Directory schema extensions for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] are unchanged from those used by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2012. If you previously extended the schema for either version, you do not have to extend the schema again.  
  
-   Extending the schema is forest-wide, one-time, irreversible action.  
  
-   Extending the schema can only be done by a user who is a member of the Schema Admins Group or who has been delegated sufficient permissions to modify the schema.  
  
-   Although you can extend the schema before or after running [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup, we recommend doing so before you start configuring your sites and hierarchy settings.  This can simplify many of the later configuration steps.  
  
-   After you extend the schema,  the Active Directory global catalog is replicated throughout the forest. Therefore, plan to extend the schema when the replication traffic will not adversely affect other network-dependent processes:  
  
    -   In Windows 2000 forests, extending the schema causes a full synchronization of the whole global catalog  
  
    -   Beginning with Windows 2003 forests, only the newly added attributes are replicated  
  
 **Devices and clients that do not use the Active Directory schema:**  
  
-   Mobile devices that are managed by the Exchange Server connector  
  
-   The client for Mac computers  
  
-   The client for Linux and UNIX servers  
  
-   Mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
-   Mobile devices that are enrolled by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)]  
  
-   Mobile device legacy clients  
  
-   Windows clients that are configured for Internet-only client management  
  
-   Windows clients that are detected by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to be on the Internet  
  
## Capabilities that benefit from extending the schema  
 **Client computer installation and site assignment** - When a new client installs on a Windows computer, the client searches Active Directory Domain Services for installation properties.  
  
-   **Workarounds:** If you do not extend the schema, use one of the following options to provide configuration details that computers require to install:  
  
    -   **Use client push installation**. Before you use client installation method, make sure that all prerequisites are met. For more information, see the section “Installation Method Dependencies” in Prerequisites for Computer Clients.  
  
    -   **Install clients manually** and provide client installation properties by using CCMSetup installation command-line properties. This must include the following:  
  
        -   Specify a management point or source path from which the computer can download the installation files by using the CCMSetup property **/mp:=<management point name computer name\>** or **/source:<path to client source files\>** on the CCMSetup command line during client installation.  
  
        -   Specify a list of initial management points for the client to use so that it can assign to the site and then download client policy and site settings. Use the CCMSetup Client.msi property SMSMP to do this.  
  
    -   **Publish the management point in DNS or WINS** and configure clients to use this service location method.  
  
 **Port configuration for client-to-server communication** - When a client installs, it is configured with port information stored in Active Directory. If you later change the client-to-server communication port for a site, a client can get this new port setting from Active Directory Domain Services.  
  
-   **Workarounds:** If you do not extend the schema, use one of the following options to provide new port configurations to existing clients:  
  
    -   **Reinstall clients** using options that configure the new port.  
  
    -   **Deploy a custom script to clients that updates the port information**. If clients cannot communicate with a site because of a port change, you cannot use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to  deploy this script. For example, you could use Group Policy.  
  
 **Content deployment scenarios** - When you create content at one site and then deploy that content to another site in the hierarchy, the receiving site must be able to verify the signature of the signed content data. This requires access to the public key of the source site where you create this data. When you extend the Active Directory schema for Configuration Manager, a site’s public key is made available to all sites in the hierarchy.  
  
-   **Workaround:** If you do not extend the schema, use the hierarchy maintenance tool, **preinst.exe**, to exchange the secure key information between sites.  
  
     For example, if you plan to create content at a primary site and deploy that content to a secondary site below a different primary site, you must either extend the Active Directory schema to enable the secondary site to obtain the source primary sites public key, or use preinst.exe to share keys between the two sites directly.  
  
## Active Directory Attributes and Classes  
 When you extend the schema for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], the following classes and attributes are added to the schema and made available to all [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites in that Active Directory forest.  
  
-   Attributes:  
  
    -   cn=mS-SMS-Assignment-Site-Code  
  
    -   cn=mS-SMS-Capabilities  
  
    -   cn=MS-SMS-Default-MP  
  
    -   cn=mS-SMS-Device-Management-Point  
  
    -   cn=mS-SMS-Health-State  
  
    -   cn=MS-SMS-MP-Address  
  
    -   cn=MS-SMS-MP-Name  
  
    -   cn=MS-SMS-Ranged-IP-High  
  
    -   cn=MS-SMS-Ranged-IP-Low  
  
    -   cn=MS-SMS-Roaming-Boundaries  
        on  
  
    -   cn=MS-SMS-Site-Boundaries  
  
    -   cn=MS-SMS-Site-Code  
  
    -   cn=mS-SMS-Source-Forest  
  
    -   cn=mS-SMS-Version  
  
-   Classes:  
  
    -   cn=MS-SMS-Management-Point  
  
    -   cn=MS-SMS-Roaming-Boundary-Range  
  
    -   cn=MS-SMS-Server-Locator-Point  
  
    -   cn=MS-SMS-Site  
  
> [!NOTE]  
>  The  schema extensions might include attributes and classes that are carried forward from previous versions of the product but not used by Configuration Manager 2015. For example:  
>   
>  -   Attribute: cn=MS-SMS-Site-Boundaries  
> -   Class: cn=MS-SMS-Server-Locator-Point  
  
 You can ensure the preceding lists are current by viewing the **ConfigMgr_ad_schema.LDF** file from the **\SMSSETUP\BIN\x64** folder of the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] installation media.  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)