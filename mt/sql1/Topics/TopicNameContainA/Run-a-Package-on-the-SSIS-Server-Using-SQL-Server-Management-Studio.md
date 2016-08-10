---
title: "Run a Package on the SSIS Server Using SQL Server Management Studio"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Run a Package on the SSIS Server Using SQL Server Management Studio
After you deploy your project to the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] server, you can run the package on the server.  
  
 You can use operations reports to view information about packages that have run, or are currently running, on the server. For more information, see [Reports for the Integration Services Server](../../Topics/TopicNameNotContainA/Reports-for-the-Integration-Services-Server.md).  
  
### To run a package on the server using SQL Server Management Studio  
  
1.  Open [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and connect to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that contains the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] catalog.  
  
2.  In Object Explorer, expand the **Integration Services Catalogs** node, expand the **SSISDB** node, and navigate to the package contained in the project you deployed.  
  
3.  Right-click the package name and select **Execute**.  
  
4.  Configure the package execution by using the settings on the **Parameters**, **Connection Managers**, and **Advanced** tabs in the **Execute Package** dialog box.  
  
5.  Click **OK** to run the package.  
  
     -or-  
  
     Use stored procedures to run the package. Click **Script** to generate the Transact-SQL statement that creates an instance of the execution and starts an instance of the execution. The statement includes a call to the catalog.create_execution, catalog.set_execution_parameter_value, and catalog.start_execution stored procedures. For more information about these stored procedures, see [catalog.create_execution (SSISDB Database)](assetId:///45d0c2f6-1f38-445f-ac06-e2a01f6ac600), [catalog.set_execution_parameter_value (SSISDB Database)](assetId:///055d86c9-befd-4e63-acb1-6dfe833549d2), and [catalog.start_execution (SSISDB Database)](assetId:///f8663ff3-aa98-4dd8-b850-b21efada0b87).