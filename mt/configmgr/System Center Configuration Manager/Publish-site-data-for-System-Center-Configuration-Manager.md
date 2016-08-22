---
title: "Publish site data for System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 17cf034f-eaff-43ce-bc8e-917213c1db74
caps.latest.revision: 8
---
# Publish site data for System Center Configuration Manager
After you extend the Active Directory schema for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you can publish [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites to Active Directory Domain Services (AD DS) so that Active Directory computers can securely retrieve site information from a trusted source. Although publishing site information to AD DS is not required for basic [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] functionality, this configuration can reduce administrative overhead.  
  
-   **When a site is configured to publish to AD DS**, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients can automatically find management points through Active Directory publishing using an LDAP query to a global catalog server.  
  
-   **When a site does not publish to AD DS**, clients must have an alternative mechanism to locate their default management point.  
  
 For information about how clients find a management point see [Understand how clients find site resources and services for System Center Configuration Manager](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md).  
  
## Configure sites to publish to AD DS  
 The following are the high-level steps:  
  
-   You must [Extend the Active Directory schema for System Center Configuration Manager](../System Center Configuration Manager/Extend-the-Active-Directory-schema-for-System-Center-Configuration-Manager.md) in each forest where you will publish site data, and ensure the **System Management** container is present.  
  
-   You must grant the computer account of each primary site that will publish data   **full control** to the **System Management** container and all of its child objects.  
  
#### To enable a Configuration Manager site to publish site information to Active Directory forest:  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Site Configuration** and click **Sites**. Select the site that you want to configure to have publish its site data, and then on the **Home** tab, in the **Properties** group, click **Properties**.  
  
3.  On the **Publishing** tab of the sites properties, select the forests to which this site will publish site data.  
  
4.  Click **Ok** to save the configuration.  
  
 Use the following procedure to configure an Active Directory forest for publishing:  
  
#### To configure Active Directory forests for publishing:  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, click **Active Directory Forests**. If Active Directory Forest Discovery has previously run, you see each discovered forest in the results pane. The local forest and any trusted forests are discovered when Active Directory Forest Discovery runs. Only untrusted forests must be manually added.  
  
    -   To configure a previously discovered forest, select the forest in the results pane, and then on the **Home** tab, in the **Properties** group, click **Properties** to open the forest properties. Continue with step 3.  
  
    -   To configure a new forest that is not listed, on the **Home** tab, in the **Create** group, click **Add Forest** to open the **Add Forests** dialog box. Continue with step 3.  
  
3.  On the **General** tab, complete configurations for the forest that you want to discover and specify the **Active Directory Forest Account**.  
  
    > [!NOTE]  
    >  Active Directory Forest Discovery requires a global account to discover and publish to untrusted forests. If you do not use the computer account of the site server, you can only select a global account.  
  
4.  If you plan to allow sites to publish site data to this forest, on the **Publishing** tab, complete configurations for publishing to this forest.  
  
    > [!NOTE]  
    >  If you enable sites to publish to a forest, you must extend the Active Directory schema of that forest for Configuration Manager, and the Active Directory Forest Account must have Full Control permissions to the System container in that forest.  
  
5.  When you complete the configuration of this forest for use with Active Directory Forest Discovery, click **OK** to save the configuration.  
  
## See Also  
 [Configure sites and hierarchies for System Center Configuration Manager](../System Center Configuration Manager/Configure-sites-and-hierarchies-for-System-Center-Configuration-Manager.md)