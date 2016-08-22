---
title: "Extend the Active Directory schema for System Center Configuration Manager"
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
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: 17
caps.handback.revision: 0
---
# Extend the Active Directory schema for System Center Configuration Manager
When you extend the Active Directory schema for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] you introduce new structures to Active Directory that are used by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites to publish key information in a secure location where clients can easily access it.  
  
 We recommend that you use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] with an extended Active Directory schema when you manage on-premises clients. An extended schema can simplify the process of deploying and configuring clients, and enables clients to efficiently locate resources such as content servers and additional services provided by the various [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system roles.  
  
-   If you’re not familiar with what extended schema provides a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] deployment,  you can read about [Schema extensions for System Center Configuration Manager](../System Center Configuration Manager/Schema-extensions-for-System-Center-Configuration-Manager.md) to help you make this decision.  
  
-   When you don’t use an extended schema, you can configure other methods like DNS and WINS to locate services and site system servers. These methods of service location require additional configurations and are not the preferred method for service location by clients. To learn more about this, read [Understand how clients find site resources and services for System Center Configuration Manager](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md),  
  
-   If your Active Directory schema was extended for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] 2007 or [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], then you don’t need to do more. The schema extensions are unchanged, and will already be in place.  
  
 Extending the schema is a one-time action for any forest. To extend, and then make use of the extended Active Directory schema involves the following:  
  
## Step 1. Extend the schema  
 Extending the schema for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] requires you to:  
  
-   Use an account that is a member of the Schema Admins security group  
  
-   Be logged into the schema master domain controller  
  
-   Run the **Extadsch.exe** tool, or use the LDIFDE command-line utility with the **ConfigMgr_ad_schema.ldf** file. Both the tool and file are in the **SMSSETUP\BIN\X64** folder on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installation media.  
  
#### Option A: Use Extadsch.exe  
  
1.  Run **extadsch.exe** to add the new classes and attributes to the Active Directory schema.  
  
    > [!TIP]  
    >  Run this tool from a command line to view feedback while it runs.  
  
2.  Verify that the schema extension was successful by reviewing the extadsch.log located in the root of the system drive.  
  
#### Option B: Use the LDIF file  
  
1.  Edit the **ConfigMgr_ad_schema.ldf** file to define the Active Directory root domain you want to extend:  
  
    -   All instances of the text **DC=x** in the file must be replaced with the full name of the domain to extend  
  
    -   For example, if the full name of the domain to extend is named widgets.microsoft.com, change all instances of DC=x in the file to **DC=widgets, DC=microsoft, DC=com**.  
  
2.  Use the LDIFDE command-line utility to import the contents of the **ConfigMgr_ad_schema.ldf** file into Active Directory Domain Services:  
  
    -   For example, the following command line imports the schema extensions into Active Directory Domain Services, turns on verbose logging, and creates a log file during the import process: **ldifde -i -f ConfigMgr_ad_schema.ldf -v -j <location to store log file\>**  
  
3.  You can verify the schema extension was successful by reviewing a log file created by the command line used in the previous step.  
  
## Step 2.  Create the System Management container and grant sites permissions to the container  
 After extending the schema, you must create a container named **System Management** in Active Directory Domain Services (AD DS):  
  
-   You create this container one time in each domain that has a primary or secondary site that will publish data to Active Directory  
  
-   For each container, you grant permissions to the computer account of each primary and secondary site server that will publish data that domain. Each account needs **Full Control** to the container with the advanced permission **Apply onto** equal to **This object and all descendant objects**  
  
#### To add the container  
  
1.  Use an account that has the **Create All Child Objects** permission on the **System** container in Active Directory Domain Services.  
  
2.  Run **ADSI Edit** (adsiedit.msc), and connect to the site server’s domain.  
  
3.  Create the container:  
  
    -   Expand **Domain** <computer fully qualified domain name\>, expand <distinguished name\>, right-click **CN=System**, click **New**, and then click **Object**.  
  
    -   In the **Create Object** dialog box, select **Container**, and then click **Next**.  
  
    -   In the **Value** box, type **System Management**, and then click **Next**.  
  
4.  Assign permissions:  
  
    > [!NOTE]  
    >  If you prefer, you can use other tools like the Active Directory Users and Computers administrative tool (dsa.msc) to add permissions to the container.  
  
    -   Right-click **CN=System Management**, and then click **Properties**.  
  
    -   Select the **Security** tab, click **Add**, and then add the site server computer account with the  
        **Full Control** permission.  
  
    -   Click **Advanced**, select the site server’s computer account, and then click **Edit**.  
  
    -   In the **Apply onto** list, select **This object and all descendant objects**.  
  
5.  Click **OK** to close the console and save the configuration.  
  
## Step 3. Configure Sites to Publish to Active Directory Domain Services  
 After the container is configured and permissions are granted, and you have installed a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] primary site, you can configure that site to publish data to Active Directory.  
  
 For information about publishing, see [Publish site data for System Center Configuration Manager](../System Center Configuration Manager/Publish-site-data-for-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Prepare your network environment for System Center Configuration Manager](../System Center Configuration Manager/Prepare-your-network-environment-for-System-Center-Configuration-Manager.md)