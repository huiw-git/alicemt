---
title: Deploy and Execute SSIS Packages using Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
---
# Deploy and Execute SSIS Packages using Stored Procedures
  When you configure an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project to use the project deployment model, you can use stored procedures in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] catalog to deploy the project and execute the packages. For information about the project deployment model, see [Deployment of Projects and Packages](../../Topics\TopicNameNotContainA/Deployment-of-Projects-and-Packages.md).  
  
 You can also use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to deploy the project and execute the packages. For more information, see the topics in the **See Also** section.  
  
> [!TIP]  
>  You can easily generate the Transact\-SQL statements for the stored procedures listed in the procedure below, with the exception of catalog.deploy\_project, by doing the following:  
>   
>  1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], expand the **Integration Services Catalogs** node in Object Explorer and navigate to the package you want to execute.  
> 2.  Right\-click the package, and then click **Execute**.  
> 3.  As needed, set parameters values, connection manager properties, and options in the **Advanced** tab such as the logging level.  
>   
>      For more information about logging levels, see [Enable Logging for Package Execution on the SSIS Server](../../Topics\TopicNameNotContainA/Enable-Logging-for-Package-Execution-on-the-SSIS-Server.md).  
> 4.  Before clicking **OK** to execute the package, click **Script**. The Transact\-SQL appears in a Query Editor window in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
## To deploy and execute a package using stored procedures  
  
1.  Call [catalog.deploy_project &#40;SSISDB Database&#41;](../Topic/catalog.deploy_project%20\(SSISDB%20Database\).md) to deploy the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the package to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server.  
  
     To retrieve the binary contents of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project deployment file, for the *@project\_stream* parameter, use a SELECT statement with the OPENROWSET function and the BULK rowset provider. The BULK rowset provider enables you to read data from a file. The SINGLE\_BLOB argument for the BULK rowset provider returns the contents of the data file as a single\-row, single\-column rowset of type varbinary\(max\). For more information, see [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md).  
  
     In the following example, the SSISPackages\_ProjectDeployment project is deployed to the SSIS Packages folder on the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server. The binary data is read from the project file \(SSISPackage\_ProjectDeployment.ispac\) and is stored in the *@ProjectBinary* parameter of type varbinary\(max\). The *@ProjectBinary* parameter value is assigned to the *@project\_stream* parameter.  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  Call [catalog.create_execution &#40;SSISDB Database&#41;](../Topic/catalog.create_execution%20\(SSISDB%20Database\).md) to create an instance of the package execution, and optionally call [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](../Topic/catalog.set_execution_parameter_value%20\(SSISDB%20Database\).md) to set runtime parameter values.  
  
     In the following example, catalog.create\_execution creates an instance of execution for package.dtsx that is contained in the SSISPackage\_ProjectDeployment project. The project is located in the SSIS Packages folder. The execution\_id returned by the stored procedure is used in the call to catalog.set\_execution\_parameter\_value. This second stored procedure sets the LOGGING\_LEVEL parameter to 3 \(verbose logging\) and sets a package parameter named Parameter1 to a value of 1.  
  
     For parameters such as LOGGING\_LEVEL the object\_type value is 50. For package parameters the object\_type value is 30.  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  Call [catalog.start_execution &#40;SSISDB Database&#41;](../Topic/catalog.start_execution%20\(SSISDB%20Database\).md) to execute the package.  
  
     In the following example, a call to catalog.start\_execution is added to the Transact\-SQL to start the package execution. The execution\_id returned by the catalog.create\_execution stored procedure is used.  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## To deploy a project from server to server using stored procedures  
 You can deploy a project from server to server by using the [catalog.get_project &#40;SSISDB Database&#41;](../Topic/catalog.get_project%20\(SSISDB%20Database\).md) and [catalog.deploy_project &#40;SSISDB Database&#41;](../Topic/catalog.deploy_project%20\(SSISDB%20Database\).md) stored procedures.  
  
 You need to do the following before running the stored procedures.  
  
-   Create a linked server object. For more information, see [Create Linked Servers &#40;SQL Server Database Engine&#41;](../Topic/Create%20Linked%20Servers%20\(SQL%20Server%20Database%20Engine\).md).  
  
     On the **Server Options** page of the **Linked Server Properties** dialog box, set **RPC** and **RPC Out** to **True**. Also, set **Enable Promotion of Distributed Transactions for RPC** to **False**.  
  
-   Enable dynamic parameters for the provider you selected for the linked server, by expanding the **Providers** node under **Linked Servers** in Object Explorer, right\-clicking the provider, and then clicking **Properties**. Select **Enable** next to **Dynamic parameter.**  
  
-   Confirm that the Distributed Transaction Coordinator \(DTC\) is started on both servers.  
  
 Call catalog.get\_project to return the binary for the project, and then call catalog.deploy\_project. The value returned by catalog.get\_project is inserted into a table variable of type varbinary\(max\). The linked server can’t return results that are varbinary\(max\).  
  
 In the following example, catalog.get\_project returns a binary for the SSISPackages project on the linked server. The catalog.deploy\_project deploys the project to the local server, to the folder named DestFolder.  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## See Also  
 [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md)   
 [Run a Package in SQL Server Data Tools](../../Topics\TopicNameContainA/Run-a-Package-in-SQL-Server-Data-Tools.md)   
 [Run a Package on the SSIS Server Using SQL Server Management Studio](../../Topics\TopicNameContainA/Run-a-Package-on-the-SSIS-Server-Using-SQL-Server-Management-Studio.md)  
  
  