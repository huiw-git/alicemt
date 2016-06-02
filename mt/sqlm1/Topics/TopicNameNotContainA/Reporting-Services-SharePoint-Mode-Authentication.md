---
title: Reporting Services SharePoint Mode Authentication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
---
# Reporting Services SharePoint Mode Authentication
  Use the **Reporting Services SharePoint Mode Authentication** page of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to specify the credentials of the service account that is used in the current [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation. The credentials will be used to create a new SharePoint application pool. Also, one new [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint service application will be created. The service application name will contain the name of the previous [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] instance name.  
  
## Options  
  
-   The **SSRS Application Pool Account Name:** option is read only. The value is automatically populated with the current value from the existing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation that you are upgrading.  
  
-   The **SSRS Application Pool Account Password:** option will be disabled if the application pool account does not require a password. For example, “NT Authority\\NetworkSerivce”. If the application pool account does require a password, you cannot continue with upgrade until you type the correct password.  
  
 For more information, see [Upgrade and Migrate Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=245628\).  
  
## See Also  
 [Upgrade and Migrate Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  