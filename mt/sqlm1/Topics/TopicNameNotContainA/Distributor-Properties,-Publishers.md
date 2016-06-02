---
title: Distributor Properties, Publishers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
---
# Distributor Properties, Publishers
  The **Publishers** page of the **Distributor Properties** dialog box allows you to enable Publishers to use this Distributor. You can also set properties associated with those Publishers. Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher. You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor. You can configure the Publisher and choose a Distributor through the New Publication Wizard.  
  
## Options  
 **Publishers**  
 Select the servers that are allowed to use this Distributor. Click the Properties button **\(...\)** next to a Publisher to view and set additional properties.  
  
 **Add**  
 If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Publisher or Oracle Publisher to the list of available Publishers. If the server you add is the first server to use this Distributor as a remote Distributor, you are prompted to provide an administrative link password.  
  
 **Administrative link password**  
 Use to specify or update the password for the connection replication makes between the Publisher and the remote Distributor using the **distributor\_admin** login:  
  
-   If the Distributor serves only as a local Distributor, this password is randomly generated and automatically configured.  
  
-   If the Distributor already has a remote Publisher, a password was initially supplied on this page or the **Distributor Password** page of the Configure Distribution Wizard.  
  
-   If you enable the first remote Publisher for this Distributor, you are prompted to enter a password.  
  
 For more information on security for Distributors, see [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md).  
  
## See Also  
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md)   
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)  
  
  