---
title: "Manage Logins in the Publication Access List"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
caps.latest.revision: 45
caps.handback.revision: 0
manager: jhubbard
---
# Manage Logins in the Publication Access List
This topic describes how to manage logins in the Publication Access List in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. Access to a publication is controlled by the publication access list (PAL). Logins and groups can be added and removed from the PAL.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
-   **To manage logins in the Publication Access List, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must associate the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login with a database user in the publication database before you add the login to the PAL.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 You use the publication access list (PAL) on the **Publication Access List** page of the **Publication Properties - <Publication\>** dialog box to manage logins. For more information about how to access this dialog box, see [View and Modify Publication Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To manage logins in the PAL  
  
1.  On the **Publication Access List** page of the **Publication Properties - <Publication\>** dialog box, use the **Add**, **Remove**, and **Remove All** buttons to add and remove logins and groups from the PAL. Do not remove **distributor_admin** from the PAL. This account is used by replication.  
  
    > [!NOTE]  
    >  If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor. The account must be either a domain account or a local account that is defined at both servers. The passwords that are associated with both logins must be the same.  
  
2.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view groups and logins that belong to the PAL  
  
1.  At the Publisher on the publication database, execute [sp_help_publication_access](assetId:///9408fa13-54a0-4cb1-8fb0-845e5536ef50). For **@publication**, specify the publication name. This displays information about the groups and logins in the PAL.  
  
#### To add groups and logins to the PAL  
  
1.  At the Publisher on the publication database, execute [sp_grant_publication_access](assetId:///17993952-def6-4a16-b1c1-323ec42967f8). For **@publication**, specify the publication name; and for **@login**, specify the name of the login or group that is being added.  
  
#### To remove groups and logins from the PAL  
  
1.  At the Publisher on the publication database, execute [sp_revoke_publication_access](assetId:///84ed9e77-991f-4fa5-a21f-7c6bfec1b3e3). For **@publication**, specify the publication name; and for **@login**, specify the name of the login or group that is being removed.  
  
## See Also  
 [Manage Logins in the Publication Access List](../../Topics/TopicNameNotContainA/Manage-Logins-in-the-Publication-Access-List.md)   
 [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md)   
 [Secure a Replication Topology](../../Topics/TopicNameContainA/Secure-a-Replication-Topology.md)   
 [Secure the Publisher](../../Topics/TopicNameNotContainA/Secure-the-Publisher.md)