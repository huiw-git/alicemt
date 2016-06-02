---
title: Oracle Publisher
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
---
# Oracle Publisher
  Beginning with [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] allows you to publish data from an Oracle database using snapshot and transactional replication. For more information, see [Oracle Publishing Overview](../../Topics\TopicNameNotContainA/Oracle-Publishing-Overview.md).  
  
 The Oracle Publisher must use a remote [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor; this wizard must be run on that server after the necessary Oracle networking software has been installed and tested. For more information, see [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md).  
  
> [!IMPORTANT]  
>  If another administrator configured the Oracle database as a Publisher, after clicking **Next** you will be prompted to enter the password for the replication login used to connect to the Oracle database. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will then create a mapping between your login and the linked server connection to the Oracle database. You will not be required to enter a password for subsequent connections to the Oracle database.  
  
## Options  
 **Oracle Publishers**  
 Select an Oracle Publisher from the list. This list contains Oracle Publishers that have previously been configured to use the server against which the wizard is running as their Distributor. If the list is empty, or the Oracle Publisher you want to use is not in the list, click **Add Oracle Publisher**.  
  
 **Add Oracle Publisher**  
 Click to launch the **Distributor Properties** dialog box. In this dialog box, click **Add**, and then click **Add Oracle Publisher**. In the **Connect to Server** dialog box, specify the Oracle server name, and the login and password for the replication administrative user schema. For more information, see [Connect to Server &#40;Oracle&#41;, Login](../Topic/Connect%20to%20Server%20\(Oracle\),%20Login.md).  
  
> [!NOTE]  
>  If the server against which the wizard is running has not yet been configured as a Distributor, you are prompted to configure it now.  
  
## See Also  
 [Create a Publication from an Oracle Database](../../Topics\TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md)   
 [Properties Reference &#40;Replication&#41;](../Topic/Properties%20Reference%20\(Replication\).md)  
  
  