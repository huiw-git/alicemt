---
title: Identity and Access Control (Replication)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
---
# Identity and Access Control (Replication)
  Authentication is the process by which an entity \(typically a computer in this context\) verifies that another entity, also called a *principal*, \(typically another computer or user\) is who or what it claims to be. Authorization is the process by which an authenticated principal is given access to resources, such as a file in the file system, or a table in a database.  
  
 Replication security uses authentication and authorization to control access to replicated database objects and to the computers and agents involved in replication processing. This is accomplished through three mechanisms:  
  
-   Agent security  
  
     The replication agent security model allows fine\-grained control over the accounts under which replication agents run and make connections. For detailed information about the agent security model, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md). For information about setting logins and passwords for agents, see [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md).  
  
-   Administration roles  
  
     Ensure that the correct server and database roles are used for replication setup, maintenance, and processing. For more information, see [Security Role Requirements for Replication](../../Topics\TopicNameNotContainA/Security-Role-Requirements-for-Replication.md).  
  
-   The publication access list \(PAL\)  
  
     Grant access to publications through the PAL. The PAL functions similarly to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows access control list. When a Subscriber connects to the Publisher or Distributor and requests access to a publication, the authentication information passed by the agent is checked against the PAL. For more information and best practices for the PAL, see [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md).  
  
## Filtering Published Data  
 In addition to using authentication and authorization to control access to replicated data and objects, replication includes two options to control what data is available at a Subscriber: column filtering and row filtering. For more information about filtering, see [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md).  
  
 When you define an article, you can publish only those columns that are necessary for the publication, and omit those that are unnecessary or contain sensitive data. For example, when publishing the **Customer** table from the Adventure Works database to sales representatives in the field, you can omit the **AnnualSales** column, which might be relevant only to executives at the company.  
  
 Filtering published data allows you to restrict access to data and allows you to specify the data that is available at the Subscriber. For example, you can filter the **Customer** table so that corporate partners only receive information about those customers whose **ShareInfo** column has a value of "yes." For merge replication, there are security considerations if you use a parameterized filter that includes HOST\_NAME\(\). For more, see the section "Filtering with HOST\_NAME\(\)" in [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
## See Also  
 [Security and Protection &#40;Replication&#41;](../Topic/Security%20and%20Protection%20\(Replication\).md)   
 [Security Overview &#40;Replication&#41;](../Topic/Security%20Overview%20\(Replication\).md)   
 [Threat and Vulnerability Mitigation &#40;Replication&#41;](../Topic/Threat%20and%20Vulnerability%20Mitigation%20\(Replication\).md)  
  
  