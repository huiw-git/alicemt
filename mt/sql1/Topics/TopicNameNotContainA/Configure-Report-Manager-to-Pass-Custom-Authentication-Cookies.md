---
title: "Configure Report Manager to Pass Custom Authentication Cookies"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
caps.handback.revision: 0
manager: mblythe
---
# Configure Report Manager to Pass Custom Authentication Cookies
If you are using a custom authentication extension, you should configure Report Manager to transmit custom authentication cookies. Otherwise, Report Manager will only transmit cookies through HTTP requests specific to the report server. If you want to transmit additional cookies, you must modify the RSReportServer.Config file.  
  
## Modifying the RSReportServer.Config File  
 You can enable Report Manager to transmit additional cookies through to the report server by adding a <**PassThroughCookies**> element to the Report Manager configuration settings in the RSReportServer.config file. Transmitting additional cookies is helpful in a single sign-on authentication solution that requires not only the report server authentication cookies, but also cookies from a third-party authentication system.  
  
 To enable additional cookies to be transmitted through HTTP requests when using Report Manager, set the following elements in the RSReportServer.config file:  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## See Also  
 [Authentication with the Report Server](../../Topics/TopicNameNotContainA/Authentication-with-the-Report-Server.md)   
 [RsReportServer.config Configuration File](../../Topics/TopicNameNotContainA/RsReportServer.config-Configuration-File.md)   
 [Introducing Reporting Services Security Extensions](assetId:///24ccd795-6506-457c-93ac-6a9dd6bb9a46)   
 [Configure and Administer a Report Server (SSRS Native Mode)](../../Topics/TopicNameContainA/Configure-and-Administer-a-Report-Server--SSRS-Native-Mode-.md)