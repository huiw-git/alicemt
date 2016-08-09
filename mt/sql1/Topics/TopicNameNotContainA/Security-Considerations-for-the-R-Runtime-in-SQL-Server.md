---
title: "Security Considerations for the R Runtime in SQL Server"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-04-01
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 16
caps.handback.revision: 0
manager: paulettm
---
# Security Considerations for the R Runtime in SQL Server
This topic provides an overview of security considerations for working with [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
 For more information about managing the service, and about how to provision the user accounts used to execute R scripts, see [Configure and Manage Advanced Analytics Extensions](../../Topics/TopicNameNotContainA/Configure-and-Manage-Advanced-Analytics-Extensions.md).  
  
## Use Firewall to Restrict Network Access by R  
 In the suggested installation method, a Windows Firewall rule is used to block all outbound network access from the R runtime processes. Firewall rules should be created to prevent the R runtime process from downloading packages or from making other network calls that could potentially be malicious.  
  
 We strongly recommend that you turn on Windows Firewall (or another firewall of your choice) to block network access by the R runtime.  
  
 If you are using a different firewall program, you can also create rules to block outbound network connection for the R runtime, by setting rules for the local user accounts or for the group represented by the user account pool.   
For more information, see [Configure and Manage Advanced Analytics Extensions](../../Topics/TopicNameNotContainA/Configure-and-Manage-Advanced-Analytics-Extensions.md).  
  
## Windows Authentication. Mixed Mode Authentication, and Implied Authentication  
 In early release versions of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], use of Windows Integrated Authentication was not supported for connections between [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and the R runtime if the data scientist is working from a remote client.  
  
 The previous workaround was to enable SQL logins (Mixed Mode authentication) when installing the instance, and provide the data scientist with the login and password.  
  
 However, this restriction has been partially removed as of RC1 and will be fully removed in RTM. You can use Windows authentication for all remote and local R execution.  
  
 In general the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] starts the R runtime and executes R scripts under its own account, including commands sent from a remote data science client, using the **rx** functions. However, if the R script makes an ODBC call, the call would be  issued under the name of the BxlServer user, not the actual user, and typically fail.  
  
 To enable script execution without such errors, the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] will impersonate the credentials of the user that sent the command. This is called *implied authentication*. For implied authentication to succeed, the **SQLRUser** group must have a login in the master database. The only permissions required are Connect.  
  
## No Support for Encryption at Rest  
 Transparent Data Encryption is not supported for data sent to or received from the R runtime. As a consequence, encryption at rest **will not** be applied to any data that you use in R scripts, any data saved to disk, or any persisted intermediate results.