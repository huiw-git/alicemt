---
title: Subscriber Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
---
# Subscriber Properties
  The **Subscriber Properties** dialog box contains information relevant to Subscribers running versions of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)].  
  
## Options  
 **Agent Connection to the Subscriber**  
 The context under which the Distribution Agent and Merge Agent connect from the Distributor to the Subscriber This applies only to versions before [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)].  
  
 Select **Impersonate agent process account** to make connections to the Subscriber using the context of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent account at the Distributor, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you select **Impersonate agent process account**.  
  
 For [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions, connection information is specified for each subscription in the New Subscription Wizard and can be changed in the **Subscription Properties** dialog box.  
  
 **Default Agent Schedules**  
 The default schedule used in the New Subscription Wizard for Subscribers running versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] before [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)].  
  
 **Miscellaneous**  
 Includes information on the Subscriber and Subscriber type.  
  
## See Also  
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [Properties Reference &#40;Replication&#41;](../Topic/Properties%20Reference%20\(Replication\).md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  