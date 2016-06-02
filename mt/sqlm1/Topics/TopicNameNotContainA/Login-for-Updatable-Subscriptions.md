---
title: Login for Updatable Subscriptions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
---
# Login for Updatable Subscriptions
  If you selected **Replicate** on the **Updatable Subscriptions** page of this wizard, you must specify an account at the Subscriber under which connections to the Publisher are made for immediate updating subscriptions. Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher. This account is required even if you selected **Queue changes and commit when possible** on the **Updatable Subscriptions** page, because by default the New Subscription Wizard configures queued updating with the ability to switch to immediate updating if required.  
  
> [!IMPORTANT]  
>  The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions. Grant permissions on views in the publication database that are named in the form **syncobj\_***\<HexadecimalNumber\>* to the account you configured at each Subscriber.  
  
 There are three options available for the type of connection:  
  
-   A linked server or remote server that you have already defined.  
  
-   A linked server that replication creates; the connection is made with the credentials you specify in this wizard.  
  
-   A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.  
  
 The first two options can be specified in this wizard. The last option can only be specified using [sp_link_publication &#40;Transact-SQL&#41;](../Topic/sp_link_publication%20\(Transact-SQL\).md); specify a value of **1** for the parameter **@security\_mode**.  
  
## Options  
 **Create a linked server that connects using the following SQL Server Authentication login:**  
 Replication creates a linked server using the credentials specified in the **Login** and **Password** fields.  
  
 **Login**  
 Enter a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login that has only the permissions described in this topic.  
  
 **Password**  
 Enter a strong password for the login specified in **Login**.  
  
 **Confirm Password**  
 Re\-enter the password to confirm that it was entered correctly.  
  
 **Use a linked server or remote server that you have already defined.**  
 This option requires a linked server or remote server that you have already defined. For more information, see [Linked Servers &#40;Database Engine&#41;](../Topic/Linked%20Servers%20\(Database%20Engine\).md) and [Remote Servers](../../Topics\TopicNameNotContainA/Remote-Servers.md). Ensure that the login used for the linked server or remote server has a strong password and has only the permissions described in this topic.  
  
## See Also  
 [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md)   
 [View and Modify Replication Security Settings](../../Topics\TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md)   
 [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  