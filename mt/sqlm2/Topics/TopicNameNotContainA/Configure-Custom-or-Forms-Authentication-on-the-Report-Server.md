---
title: Configure Custom or Forms Authentication on the Report Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
---
# Configure Custom or Forms Authentication on the Report Server
  Reporting Services provides an extensible architecture that allows you to plug in custom or forms\-based authentication modules. You might consider implementing a custom authentication extension if deployment requirements do not include Windows integrated security or Basic authentication. The most common scenario for using custom authentication is to support Internet or extranet access to a Web application. Replacing the default Windows Authentication extension with a custom authentication extension gives you more control over how external users are granted access to the report server.  
  
 In practice, deploying a custom authentication extension requires multiple steps that include copying assemblies and application files, modifying configuration files, and testing. This topic focuses on just the authentication settings that you specify in the configuration files.  
  
> [!NOTE]  
>  Creating a custom authentication extension requires custom code and expertise in [!INCLUDE[vstecasp](../../Token\Other/vstecasp_md.md)] security. If you do not want to create a custom authentication extension, you can use [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Active Directory groups and accounts, but you should greatly reduce the scope of a report server deployment. For more information about custom authentication, see [Implementing a Security Extension](../Topic/Implementing%20a%20Security%20Extension.md).  
  
 Additionally, if you want to use Forms authentication or a custom authentication extension in a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] environment that is integrated with a SharePoint product, you must configure the SharePoint site to use the authentication method that you choose. For more information about configuring authentication in SharePoint, see [Authentication Samples](http://go.microsoft.com/fwlink/?LinkId=115575) on [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Developer Network \(MSDN\).  
  
### To configure a report server to use Custom authentication  
  
1.  Open RSReportServer.config in a text editor.  
  
2.  Find \<**Authentication**\>.  
  
3.  Copy the following XML structure:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  Paste it over the existing entries for \<**Authentication**\>.  
  
     Note that you cannot use **Custom** with other authentication types.  
  
5.  Save the file.  
  
6.  Open the Web.config file for the report server. By default, it is located at \\Program Files\\Microsoft SQL Server\\MSRS10\_50.MSSQLSERVER\\ReportServer.  
  
7.  Find **authentication mode** and set it **Forms**.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  Find **identity impersonate** and set it to **False**.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. Open the Web.config file for Report Manager. By default, it is located at \\Program Files\\Microsoft SQL Server\\MSRS10\_50.MSSQLSERVER\\ReportManager.  
  
10. Find **authentication mode** and set it **Forms**.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. Find **identity impersonate** and set it to **False**.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. Add the **PassThroughCookies** element structure to the configuration file. For more information, see [Configure Report Manager to Pass Custom Authentication Cookies](../../Topics\TopicNameNotContainA/Configure-Report-Manager-to-Pass-Custom-Authentication-Cookies.md).  
  
13. Save the file.  
  
14. If you configured a scale\-out deployment, repeat all of the previous steps for other report servers in the deployment.  
  
15. Restart the report server to clear any sessions that are currently open.  
  
## See Also  
 [Implementing a Security Extension](../Topic/Implementing%20a%20Security%20Extension.md)   
 [Authentication with the Report Server](../../Topics\TopicNameNotContainA/Authentication-with-the-Report-Server.md)   
 [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md)   
 [Configure Basic Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Basic-Authentication-on-the-Report-Server.md)   
 [Configure Windows Authentication on the Report Server](../../Topics\TopicNameNotContainA/Configure-Windows-Authentication-on-the-Report-Server.md)  
  
  