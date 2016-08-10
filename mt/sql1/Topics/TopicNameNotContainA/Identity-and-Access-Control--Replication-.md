---
title: "Identity and Access Control (Replication)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Identity and Access Control (Replication)
Authentication is the process by which an entity (typically a computer in this context) verifies that another entity, also called a *principal*, (typically another computer or user) is who or what it claims to be. Authorization is the process by which an authenticated principal is given access to resources, such as a file in the file system, or a table in a database.  
  
 Replication security uses authentication and authorization to control access to replicated database objects and to the computers and agents involved in replication processing. This is accomplished through three mechanisms:  
  
-   Agent security  
  
     The replication agent security model allows fine-grained control over the accounts under which replication agents run and make connections. For detailed information about the agent security model, see [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md). For information about setting logins and passwords for agents, see [Manage Logins and Passwords in Replication](../../Topics/TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md).  
  
-   Administration roles  
  
     Ensure that the correct server and database roles are used for replication setup, maintenance, and processing. For more information, see [Security Role Requirements for Replication](../../Topics/TopicNameNotContainA/Security-Role-Requirements-for-Replication.md).  
  
-   The publication access list (PAL)  
  
     Grant access to publications through the PAL. The PAL functions similarly to a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows access control list. When a Subscriber connects to the Publisher or Distributor and requests access to a publication, the authentication information passed by the agent is checked against the PAL. For more information and best practices for the PAL, see [Secure the Publisher](../../Topics/TopicNameNotContainA/Secure-the-Publisher.md).  
  
## Filtering Published Data  
 In addition to using authentication and authorization to control access to replicated data and objects, replication includes two options to control what data is available at a Subscriber: column filtering and row filtering. For more information about filtering, see [Filter Published Data](../../Topics/TopicNameNotContainA/Filter-Published-Data.md).  
  
 When you define an article, you can publish only those columns that are necessary for the publication, and omit those that are unnecessary or contain sensitive data. For example, when publishing the **Customer** table from the Adventure Works database to sales representatives in the field, you can omit the **AnnualSales** column, which might be relevant only to executives at the company.  
  
 Filtering published data allows you to restrict access to data and allows you to specify the data that is available at the Subscriber. For example, you can filter the **Customer** table so that corporate partners only receive information about those customers whose **ShareInfo** column has a value of "yes." For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME(). For more, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](../../Topics/TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
## See Also  
 [Security and Protection (Replication)](../../Topics/TopicNameNotContainA/Security-and-Protection--Replication-.md)   
 [Security Overview (Replication)](../../Topics/TopicNameNotContainA/Security-Overview--Replication-.md)   
 [Threat and Vulnerability Mitigation (Replication)](../../Topics/TopicNameNotContainA/Threat-and-Vulnerability-Mitigation--Replication-.md)