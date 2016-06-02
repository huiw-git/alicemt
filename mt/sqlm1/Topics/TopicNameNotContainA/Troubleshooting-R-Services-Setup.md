---
title: Troubleshooting R Services Setup
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce6b902b-a4fa-4b0a-ac0d-be47a59c2a78
robots: noindex,nofollow
---
# Troubleshooting R Services Setup
  This topic provides answers to some common questions about installation of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].  
  
## Changes in Setup  
 In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC2, the process for setup has changed and you can install all related features, including the R  components, by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup Wizard. You can also install the R packages and tools on a data science workstation \(no [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] required\) to connect to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and deploy R solutions.  
  
 If you have an early preview version of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and do not wish to upgrade, you can still install the R components used by the previous versions. For more information, see [Installing Previous Versions of SQL Server R Services](../../Topics\TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md).  
  
 However, be sure to verify the build of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that you are running and choose a compatible version of the R components. For a compatibility chart, see [Install R Packages and Providers for SQL Server R Services](../../Topics\TopicNameNotContainA/Install-R-Packages-and-Providers-for-SQL-Server-R-Services.md).  
  
## Setting up SQL Server R Services in an Azure Virtual Machine  
 If you install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on an Azure virtual machine by using one of the images that includes [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], some additional steps are needed.  
  
-   The [!INCLUDE[rsql_extensions](../../Token\Other/rsql_extensions_md.md)] feature is not installed by default. Therefore, after you have created the virtual machine, you will need to re\-run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, add the feature on the **Server Configuration** page of the wizard, and restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
-   You will also need to make some additional changes to the firewall on the virtual machine, and verify that you can access the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance from your data science client.  
  
#### To add Advanced Analytics Extensions to the SQL Server instance  
  
1.  **Connect to the virtual machine**  
  
     After the virtual machine has been provisioned, use Remote Desktop to connect to the image. From the Azure portal, you can click **CONNECT** to get an RDP file to use in opening the connection. Provide the user name and password that you used when you created the virtual machine.  
  
2.  **Locate and then run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup utility**  
  
     The default location for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup utility is C:\\SQLServer\_13.0\_Full.  Double\-click the **Setup** application to run the setup wizard.  
  
3.  **Add options needed for R Services**  
  
     In **SQL Server Installation Center**, click the **Installation** tab, and click **New SQL Server standalone installation or add features to an existing installation**. When the rules check completes, click **Next**.  
  
     On the **Installation Type** page, determine whether you want to add R Services to the existing instance, or if you want to add a new instance just for R.  
  
    -   **Add features to an existing instance of SQL Server 2016**. Using the default instance is the easiest option to manage, particularly if you don't intend to make heavy use of most features, or if you are only using R integration and not the other features installed by default.  
  
    -   **Perform a new installation of SQL Server 2016**. We recommend this option if you intend to make heavy use of R, or if you want to keep R services and related logins in a separate instance.  
  
         However, if you create a new instance, note the name of the instance. Later on you will have to specify the instance name for R configuration.  
  
4.  Run the Setup wizard.  
  
     Complete other selections for R Services as described in [Installing R Services \(In\-Database\)](../../Topics\TopicNameNotContainA/Troubleshooting-R-Services-Setup.md). On the **Ready to Install** page, click Install to add the R Services components and complete setup.  
  
5.  **Enable R scripts**  
  
     When installation is complete, run the following statement on the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance to enable external scripts, and restart the instance.  
  
    ```  
    sp_configure 'external scripts enabled',1'  
    reconfigure with override  
    ```  
  
6.  **Unblock firewall**  
  
     If you have installed [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on a Windows Azure virtual machine, you might not be able to use compute contexts that require use of the virtual machine's workspace. The reason is that, by default, the firewall on the Azure virtual machine includes a rule that blocks network access for local R user accounts.  
  
     As a workaround, on the virtual machine, open Windows Firewall with Advanced Security, select **Outbound Rules**, and disable the following rule:  
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`  
  
7.  **Install required network protocols**  
  
     Currently, [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] uses the Named Pipes protocol for connections between the client and server computers. If Named Pipes is not enabled, you must install and enable it on both the client and server.  
  
8.  **Create database and logins used for R tasks**  
  
     It is not required that R code be run as administrator; however, depending on which packages you are using, your R user might need to create new tables, run SELECT statements, or delete \(DROP\) tables. Therefore, we recommend that you create a login that can be used for running R code, and assign it to the appropriate role in the database that stores your data, or in the database where you will store the results of your R jobs.  
  
     The post\-installation configuration script should create one login that you can use. However, if you want to create additional logins for specific tasks, and are new to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security, we recommend this article to better understand the relationship between users and logins, and how to assign permissions for individual databases.  
  
     [Basic SQL Server Security Concepts \(MSDN\)](http://blogs.msdn.com/b/lcris/archive/2007/03/23/basic-sql-server-security-concepts-logins-users-and-principals.aspx)  
  
9. On the virtual machine, run the post\-installation configuration steps as described here: [Post-Installation Server Configuration &#40;SQL Server R Services&#41;](../Topic/Post-Installation%20Server%20Configuration%20\(SQL%20Server%20R%20Services\).md)  
  
    > [!NOTE]  
    >  If you installed two instances of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on the virtual machine, be sure to specify the instance includes the R extensions. If the instance is not the default instance, when you run the script to register the R extensions \(in Step 3\), use the syntax for registering a named instance.  
  
## Other Issues  
  
-   Error during setup because I cannot install R components  
  
     [Installing R Components without Internet Access](../../Topics\TopicNameNotContainA/Installing-R-Components-without-Internet-Access.md)  
  
-   I installed [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on an Azure virtual machine and cannot run R  
  
     [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md)  
  
-   Migration and upgrade issues  
  
     [Upgrade and Installation FAQ &#40;SQL Server R Services&#41;](../Topic/Upgrade%20and%20Installation%20FAQ%20\(SQL%20Server%20R%20Services\).md)  
  
     [Installing Previous Versions of SQL Server R Services](../../Topics\TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md)  
  
## See Also  
 [SQL Server R Services Tutorials](../Topic/SQL%20Server%20R%20Services%20Tutorials.md)   
 [SQL Server R Services Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-R-Services-Features-and-Tasks.md)  
  
  