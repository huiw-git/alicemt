---
title: Execute Package Task Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
---
# Execute Package Task Editor
  Use the Execute Package Task Editor to configure the Execute Package Task. The Execute Package task extends the enterprise capabilities of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] by letting packages run other packages as part of a workflow.  
  
 **What do you want to do?**  
  
-   [Open the Execute Package Task Editor](#open)  
  
-   [Set the Options on the General Page](#general)  
  
-   [Set the Options on the Package Page](#package)  
  
-   [Set the Options on the Parameter Bindings Page](#parameter)  
  
##  <a name="open"></a> Open the Execute Package Task Editor  
  
1.  Open an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project in [!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] that contains an Execute Package task.  
  
2.  Right\-click the task in the SSIS Designer, and then click **Edit**.  
  
##  <a name="general"></a> Set the Options on the General Page  
 **Name**  
 Provide a unique name for the Execute Package task. This name is used as the label in the task icon.  
  
> [!NOTE]  
>  Task names must be unique within a package.  
  
 **Description**  
 Type a description of the Execute Package task.  
  
##  <a name="package"></a> Set the Options on the Package Page  
 **ReferenceType**  
 Select **Project Reference** for child packages that are in the project. Select **External Reference** for child packages that are located outside the package  
  
> [!NOTE]  
>  The **ReferenceType** option is ready\-only and set to **External Reference** if the project that contains the package has not been converted to the project deployment model. For more information about conversion, see [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md).  
  
 **Password**  
 If the child package is password protected, provide the password for the child package, or click the ellipsis button \(…\) and create a new password for the child package.  
  
 **ExecuteOutOfProcess**  
 Specify whether the child package runs in the process of the parent package or in a separate process. By default, the ExecuteOutOfProcess property of the Execute Package task is set to **False**, and the child package runs in the same process as the parent package. If you set this property to **true**, the child package runs in a separate process. This may slow down the launching of the child package. In addition, if set the property to **true**, you cannot debug the package in a tools\-only install; you must install the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] product. For more information, see [Install Integration Services](../../Topics\TopicNameNotContainA/Install-Integration-Services.md).  
  
### ReferenceType Dynamic Options  
  
#### ReferenceType \= External Reference  
 **Location**  
 Select the location of the child package. This property has the options listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|**SQL Server**|Set the location to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|**File system**|Set the location to the file system.|  
  
 **Connection**  
 Select the type of storage location for the child package.  
  
 **PackageNameReadOnly**  
 Displays the package name.  
  
#### ReferenceType \= Project Reference  
 **PackageNameFromProjectReference**  
 Select a package contained in the project, to be the child package.  
  
### Location Dynamic Options  
  
#### Location \= SQL Server  
 **Connection**  
 Select an OLE DB connection manager in the list, or click \<**New connection...**\> to create a new connection manager.  
  
 **Related Topics:** [OLE DB Connection Manager](../../Topics\TopicNameNotContainA/OLE-DB-Connection-Manager.md), [Configure OLE DB Connection Manager](../../Topics\TopicNameNotContainA/Configure-OLE-DB-Connection-Manager.md)  
  
 **PackageName**  
 Type the name of the child package, or click the ellipsis \(…\) and then locate the package.  
  
#### Location \= File system  
 **Connection**  
 Select a File connection manager in the list, or click \<**New connection...**\> to create a new connection manager.  
  
 **Related Topics:** [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md), [File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md)  
  
 **PackageNameReadOnly**  
 Displays the package name.  
  
##  <a name="parameter"></a> Set the Options on the Parameter Bindings Page  
 You can pass values from the parent package or the project, to the child package. The project must use the project deployment model and the child package must be contained in the same project that contains the parent package.  
  
 For information about converting projects to the project deployment model, see [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md).  
  
 **Child package parameter**  
 Enter or select a name for the child package parameter.  
  
 **Binding parameter or variable**  
 Select the parameter or variable that contains the value that you want to pass to the child package.  
  
 **Add**  
 Click to map a parameter or variable to a child package parameter.  
  
 **Remove**  
 Click to remove a mapping between a parameter or variable and a child package parameter.  
  
  