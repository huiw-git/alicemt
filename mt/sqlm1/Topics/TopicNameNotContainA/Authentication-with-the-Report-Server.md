---
title: Authentication with the Report Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 753c2542-0e97-4d8f-a5dd-4b07a5cd10ab
---
# Authentication with the Report Server
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] \(SSRS\) offers several configurable options for authenticating users and client applications against the report server. By default, the report server uses Windows Integrated authentication and assumes trusted relationships where client and network resources are in the same domain or in a trusted domain. Depending on your network topology and the needs of your organization, you can customize the authentication protocol that is used for Windows Integrated authentication, use Basic authentication, or use a custom forms\-based authentication extension that you provide. Each of the authentication types can be turned on or off individually. You can enable more than one authentication type if you want the report server to accept requests of multiple types.  
  
> [!NOTE]  
>  In previous versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], all authentication support was provided by IIS. Starting with the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] release, IIS is no longer used. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] handles all authentication requests internally.  
  
 All users or applications who request access to report server content or operations must be authenticated before access is allowed.  
  
## Authentication Types  
 All users or applications who request access to report server content or operations must be authenticated using the authentication type configured on the report server before access is allowed. The following table describes the authentication types supported by [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
|AuthenticationType Name|HTTP Authentication Layer value|Used by default|Description|  
|-----------------------------|-------------------------------------|---------------------|-----------------|  
|RSWindowsNegotiate|Negotiate|Yes|Attempts to use Kerberos for Windows Integrated authentication first, but falls back to NTLM if Active Directory cannot grant a ticket for the client request to the report server. Negotiate will only fall back to NTLM if the ticket is not available. If the first attempt results in an error rather than a missing ticket, the report server does not make a second attempt.|  
|RSWindowsNTLM|NTLM|Yes|Uses NTLM for Windows Integrated authentication.<br /><br /> The credentials will not be delegated or impersonated on other requests. Subsequent requests will follow a new challenge\-response sequence. Depending on network security settings, a user might be prompted for credentials or the authentication request will be handled transparently.|  
|RSWindowsKerberos|Kerberos|No|Uses Kerberos for Windows Integrated authentication. You must configure Kerberos by setting up setup service principle names \(SPNs\) for your service accounts, which requires domain administrator privileges. If you set up identity delegation with Kerberos, the token of the user who is requesting a report can also be used on an additional connection to the external data sources that provide data to reports.<br /><br /> Before you specify RSWindowsKerberos, be sure that the browser type you are using actually supports it. If you are using Internet Explorer, Kerberos authentication is only supported through Negotiate. Internet Explorer will not formulate an authentication request that specifies Kerberos directly.|  
|RSWindowsBasic|Basic|No|Basic authentication is defined in the HTTP protocol and can only be used to authenticate HTTP requests to the report server.<br /><br /> Credentials are passed in the HTTP request in base64 encoding. If you use Basic authentication, use Secure Sockets Layer \(SSL\) to encrypt user account information before it is sent across the network. SSL provides an encrypted channel for sending a connection request from the client to the report server over an HTTP TCP\/IP connection. For more information, see [Using SSL to Encrypt Confidential Data](http://go.microsoft.com/fwlink/?LinkId=71123) on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] TechNet Web site.|  
|Custom|\(Anonymous\)|No|Anonymous authentication directs the report server to ignore authentication header in an HTTP request. The report server accepts all requests, but call on a custom [!INCLUDE[vstecasp](../../Token\Other/vstecasp_md.md)] Forms authentication that you provide to authenticate the user.<br /><br /> Specify **Custom** only if you are deploying a custom authentication module that handles all authentication requests on the report server. You cannot use the Custom authentication type with the default Windows Authentication extension.|  
  
## Unsupported Authentication Methods  
 The following authentication methods and requests are not supported.  
  
|Authentication method|Explanation|  
|---------------------------|-----------------|  
|Anonymous|The report server will not accept unauthenticated requests from an anonymous user, except for those deployments that include a custom authentication extension.<br /><br /> Report Builder will accept unauthenticated requests if you enable Report Builder access on a report server that is configured for Basic authentication.<br /><br /> For all other cases, anonymous requests are rejected with an HTTP Status 401 Access Denied error before the request reaches [!INCLUDE[vstecasp](../../Token\Other/vstecasp_md.md)]. Clients receiving 401 Access Denied must reformulate the request with a valid authentication type.|  
|Single sign\-on technologies \(SSO\)|There is no native support for single sign\-on technologies in [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. If you want to use a single sign\-on technology, you must create a custom authentication extension.<br /><br /> The report server hosting environment does not support ISAPI filters. If the SSO technology you are using is implemented as an ISAPI filter, consider using the ISA Server built\-in support for RSASecueID or the RADIUS protocol. Otherwise, you can create an ISA Server ISAPI or an HTTPModule for RS, but it is recommended you use ISA Server directly.|  
|Passport|Not supported in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|  
|Digest|Not supported in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|  
  
## Configuration of Authentication Settings  
 Authentication settings are configured for default security when the report server URL is reserved. If you modify these settings incorrectly, the report server will return HTTP 401 Access Denied errors for HTTP requests that cannot be authenticated. Choosing an authentication type requires that you already know how Windows Authentication is supported in your network. At least one authentication type must be specified. Multiple authentication types can be specified for RSWindows. RSWindows authentication types \(that is, **RSWindowsBasic**, **RSWindowsNTLM**, **RSWindowsKerberos**, and **RSWindowsNegotiate**\) are mutually exclusive with Custom.  
  
> [!IMPORTANT]  
>  Reporting Services does not validate the settings you specify to determine whether they are correct for your computing environment. It is possible that default security will not work for your installation, or that you will specify configuration settings that are not valid for your security infrastructure. For this reason, it is important that you carefully test your report server deployment in controlled test environment before making it available to your larger organization.  
  
 The Report Server Web service and Report Manager always use the same authentication type. You cannot configure different authentication types for the feature areas of the Report Server service. If you have a scale\-out deployment, be sure to duplicate all of your changes on all nodes in the deployment. You cannot configure different nodes in the same scale\-out to use different authentication types.  
  
 Background processing does not accept requests from end\-users, however it does authenticate all requests for unattended execution purposes. It always uses Windows Authentication and it authenticates requests using the Report Server service or the unattended execution account if it is configured.  
  
## In This Section  
  
-   [Configure Windows Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Windows-Authentication-on-the-Report-Server.md)  
  
-   [Configure Basic Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Basic-Authentication-on-the-Report-Server.md)  
  
-   [Configure Custom or Forms Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Custom-or-Forms-Authentication-on-the-Report-Server.md)  
  
## Related Tasks  
  
|Task Descriptions|Links|  
|-----------------------|-----------|  
|Configure the Windows Integrated authentication type.|[Configure Windows Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Windows-Authentication-on-the-Report-Server.md)|  
|Configure the Basic authentication type.|[Configure Basic Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Basic-Authentication-on-the-Report-Server.md)|  
|Configure forms authentication or otherwise a Custom authentication type.|[Configure Custom or Forms Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Custom-or-Forms-Authentication-on-the-Report-Server.md)|  
|Enable the report manager to handle the custom authentication scenario.|[Configure Report Manager to Pass Custom Authentication Cookies](../../Topics\TopicNameNotContainA/Configure-Report-Manager-to-Pass-Custom-Authentication-Cookies.md)|  
  
## See Also  
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)   
 [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md)   
 [Create and Manage Role Assignments](../../Topics\TopicNameNotContainA/Create-and-Manage-Role-Assignments.md)   
 [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Implementing a Security Extension](../Topic/Implementing%20a%20Security%20Extension.md)   
 [Configure SSL Connections on a Native Mode Report Server](../../Topics\TopicNameContainA/Configure-SSL-Connections-on-a-Native-Mode-Report-Server.md)   
 [Configure Report Builder Access](../../Topics\TopicNameNotContainA/Configure-Report-Builder-Access.md)   
 [Security Extensions Overview](../Topic/Security%20Extensions%20Overview.md)   
 [Authentication in Reporting Services](../Topic/Authentication%20in%20Reporting%20Services.md)   
 [Authorization in Reporting Services](../Topic/Authorization%20in%20Reporting%20Services.md)  
  
  