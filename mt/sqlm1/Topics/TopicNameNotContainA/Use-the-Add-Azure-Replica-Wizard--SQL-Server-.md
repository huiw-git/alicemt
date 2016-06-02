---
title: Use the Add Azure Replica Wizard (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
---
# Use the Add Azure Replica Wizard (SQL Server)
  Use the Add Azure Replica Wizard to help you create a new Windows Azure VM in hybrid IT and configure it as a secondary replica for a new or existing Always On availability group.  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To add a replica, using:**  [Add Azure Replica Wizard \(SQL Server Management Studio\)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must be connected to the server instance that hosts the current primary replica.  
  
-   You must have a hybrid\-IT environment where your on\-premise subnet has a site\-to\-site VPN with Windows Azure. For more information, see [Configure a Site\-to\-Site VPN in the Management Portal](https://azure.microsoft.com/en-us/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Your availability group must contain on\-premise availability replicas.  
  
-   Clients to the availability group listener must have connectivity to the Internet if they want to maintain connectivity with the listener when the availability group is failed over to a Windows Azure replica.  
  
-   **Prerequisites for using full initial data synchronization** You will need to specify a network share in order for the wizard to create and access backups. For the primary replica, the account used to start the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] must have read and write file\-system permissions on a network share. For secondary replicas, the account must have read permission on the network share.  
  
     If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually. You can do this before or after running the wizard. For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 See [Security](../Topic/Use%20the%20Add%20Replica%20to%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md#Security)  
  
##  <a name="SSMSProcedure"></a> Using the Add Azure Replica Wizard \(SQL Server Management Studio\)  
 The Add Azure Replica Wizard can be launched from the [Specify Replicas Page](../Topic/Specify%20Replicas%20Page%20\(New%20Availability%20Group%20Wizard:%20Add%20Replica%20Wizard\).md). There are two ways to reach this page:  
  
-   [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Add%20Replica%20to%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
 Once you have launched the Add Azure Replica Wizard, follow the steps below:  
  
1.  First, download a management certificate for your Windows Azure subscription. Click **Download** to open the sign\-in page.  
  
2.  Sign in to Microsoft Azure with your Microsoft account or your organizational account. Your Microsoft or organizational account is in the format of an email address, such as  HYPERLINK "mailto:patc@contoso.com" patc@contoso.com. For more information about Azure credentials, see [Microsoft Account for Organizations FAQ](http://technet.microsoft.com/jj592903) and [Troubleshooting sign\-in problems with your organizational account](https://support.microsoft.com/kb/2756852).  
  
3.  Next, connect to your subscription by clicking **Connect**. Once you are connected, the drop\-down lists are populated with your Windows Azure parameters, such as **Virtual Network** and **Virtual Network Subnet**.  
  
4.  Specify the settings for the Windows Azure VM that will host the new secondary replica:  
  
     Image  
     The name of the SQL Server image to use for the Windows Azure VM  
  
     VM Size  
     The size of the Windows Azure VM  
  
     VM Name  
     The DNS name of the Windows Azure VM  
  
     VM Username  
     The username of the default administrator for the Windows Azure VM  
  
     VM Administrator Password \(and Confirm Password\)  
     The password for the default administrator for the Windows Azure VM  
  
     Virtual Network  
     The virtual network in which to place the Windows Azure VM  
  
     Virtual Network Subnet  
     The virtual network subnet in which to place the Windows Azure VM  
  
     Domain  
     The Active Directory \(AD\) domain to join the Windows Azure VM  
  
     Domain Username  
     The AD username used to join the Windows Azure VM to the domain  
  
     Password  
     The password used to join the Windows Azure VM to the domain  
  
5.  Click **OK** to commit your settings and exit the Add Azure Replica Wizard.  
  
6.  Continue with the rest of the configuration steps for [Specify Replicas Page](../Topic/Specify%20Replicas%20Page%20\(New%20Availability%20Group%20Wizard:%20Add%20Replica%20Wizard\).md) as you do for any new replica.  
  
     Once you are finished with the Availability Group Wizard or the Add Replica to Availability Group Wizard, the configuration process performs all operations in Windows Azure to create the new VM, join it to the AD domain, add it to the Windows cluster, enable Always On High Availability, and add the new replica to the availability group.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  