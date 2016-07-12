---
title: How to Install the Orchestrator Web Service
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - orchestrator
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec1737c6-b1eb-4ce9-8ef2-ae1e3e28ce23
manager:cfreeman
---
# How to Install the Orchestrator Web Service
Use the following steps to install the [!INCLUDE[orchlong](../../orch/deploy//orchlong_md.md)] web service.  
  
### To install the [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] web service  
  
1.  On the server where you want to install the [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] web service, start the **[!INCLUDE[orchlong](../../orch/deploy//orchlong_md.md)] Setup Wizard**.  
  
    To start the **[!INCLUDE[orchlong](../../orch/deploy//orchlong_md.md)] Setup Wizard**, on your product media or network share, double\-click **SetupOrchestrator.exe**.  
  
    > [!NOTE]  
    > Before you begin the installation of the [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] web service, close any open programs and ensure that there are no pending restarts on the computer. For example, if you have installed a server role by using [!INCLUDE[smshort](../../orch/deploy//smshort_md.md)] or have applied a security update, you might have to restart the computer, and then log on to the computer with the same user account to finish the installation of the server role or the security update.  
  
2.  On the main **[!INCLUDE[orchlong](../../orch/deploy//orchlong_md.md)] Setup Wizard** page, click **Install**.  
  
    > [!WARNING]  
    > If Microsoft .NET Framework 3.5 Service Pack 1 is not installed on your computer, a dialog box appears asking if you want to install .NET Framework 3.5 SP1. Click **Yes** to proceed with the installation.  
  
3.  On the **Product registration** page, provide the name and company for the product registration, and then click **Next**.  
  
    > [!NOTE]  
    > For this evaluation release, a product key is not required.  
  
4.  On the **Please read this license agreement** page, review and accept the Microsoft Software License Terms, and then click **Next**.  
  
5.  Your computer is checked for required hardware and software. If your computer meets all of the requirements, the **All prerequisites are installed** page appears. Click **Next** and proceed to the next step.  
  
    If a prerequisite is not met, a page displays information about the prerequisite that has not been met and how to resolve the issue. Use the following steps to resolve the failed prerequisite check:  
  
    1.  Review the items that did not pass the prerequisite check. For some requirements, such as Microsoft .NET Framework 4, you can use the link provided in the Setup Wizard to install the missing requirement. The Setup Wizard can install or configure other prerequisites, such as the Internet Information Services \(IIS\) role.  
  
        > [!WARNING]  
        > If you enable prerequisites during setup, such as Microsoft .NET Framework 4, your computer can require a restart. If you restart your computer, you must run setup again from the beginning.  
  
    2.  After you resolve the missing prerequisites, click **Verify prerequisites again**.  
  
    3.  Click **Next** to continue.  
  
6.  On the **Configure the service account** page, enter the user name and password for the [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] service account. Click **Test** to verify the account credentials. If the credentials are accepted, click **Next**.  
  
7.  On the **Configure the database server** page, enter the name of the database server associated with your [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] management server. You can also specify whether to use Windows Authentication or SQL Server Authentication, and whether to create a new database or use an existing database. Click **Test Database Connection** to verify the account credentials. If the credentials are accepted, click **Next**.  
  
8.  On the **Configure the database** page, select the [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] database for your deployment, and then click **Next**.  
  
9. On the **Configure the port for the web service** page, verify the port numbers for the [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)] web service and the Orchestration console, and then click **Next**.  
  
10. On the **Select the installation location** page, verify the installation location for [!INCLUDE[orchshort](../../om/manage//orchshort_md.md)], and then click **Next**.  
  
11. On the **Microsoft Update** page, optionally indicate whether you want to use the Microsoft Update services to check for updates, and then click **Next**.  
  
12. On the **Help improve Microsoft System Center Orchestrator** page, optionally indicate whether you want to participate in the **Customer Experience Improvement Program** or **Error Reporting**, and then click **Next**.  
  
13. Review the **Installation summary** page, and then click **Install**.  
  
    The **Installing features** page appears and displays the installation progress.  
  
14. On the **Setup completed successfully** page, optionally indicate whether you want to start the Runbook Designer, and then click **Close** to complete the installation.  
  
## See Also  
[Install Individual Orchestrator Features](../../orch/deploy/Install-Individual-Orchestrator-Features.md)  
  
