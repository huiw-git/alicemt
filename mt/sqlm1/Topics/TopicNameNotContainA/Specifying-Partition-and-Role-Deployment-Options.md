---
title: Specifying Partition and Role Deployment Options
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
---
# Specifying Partition and Role Deployment Options
  The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard reads the partition and role deployment options from the \<*project name*\>.deploymentoptions file. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] creates this file when you build the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] uses the partition and role deployment options of the current project when the \<*project name*\>.deploymentoptions file is created. For more information about configuration settings, see [Understanding the Input Files Used to Create the Deployment Script](../../Topics\TopicNameNotContainA/Understanding-the-Input-Files-Used-to-Create-the-Deployment-Script.md).  
  
## Reviewing the Partition and Role Deployment Options  
 The deployment options in the \<*project name*\>.deploymentoptions file include the following:  
  
 **Partition deployment options**  
 The \<*project name*\>.deploymentoptions file specifies whether existing partitions in the destination database are retained or overwritten \(default\). If existing partitions are retained, only new partitions will be deployed, and the partitions and aggregation designs on all existing measure groups are left unchanged.  
  
> [!NOTE]  
>  If the measure group in which the partition exists is deleted, the partition is automatically deleted.  
  
 **Role deployment options**  
 The \<*project name*\>.deploymentoptions file specifies one of the following role deployment options:  
  
-   Existing roles and role members in the destination database are retained, and only new roles and role members are deployed.  
  
-   All existing roles and members in the destination database are replaced by the roles and members being deployed.  
  
-   Existing roles and role members in the destination database are retained, and no new roles are deployed.  
  
-   **Note** When existing roles and members are retained, the permissions associated with those roles are reset to none. Security permissions are contained by the objects they secure, not by the security roles with which they are associated. For more information about how to work with this behavior by using the Analysis Service Deployment Wizard, see ‘Retain Roles and Members’ in the Microsoft Knowledge Base.  
  
## Modifying the Partition and Role Deployment Options  
 You may have to deploy the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project using different partition and role options than those stored in the \<*project name*\>.deploymentoptions file. For example, you may want to retain existing partitions, roles, and role members, instead of replacing all existing partitions, roles, and members as indicated in the \<*project name*\>.deploymentoptions file.  
  
 To modify the deployment of partitions and roles in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, you cannot change the partition and roles settings within the project because the *\<project name\>* **Properties Pages** dialog box in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] does not display these options. If you want to change the deployment options for roles and partitions, you must change this information within the \<*project name*\>.deploymentoptions file itself. The following procedure describes how to change the partition and role deployment options within the \<*project name*\>.deploymentoptions file.  
  
#### To change the deployment of partitions or roles after the input files have been generated  
  
-   Run the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard interactively, and on the **Partition and Role Deployment Options** page, specify new deployment options for the partitions and roles.  
  
     —or—  
  
-   Run the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard at the command prompt, and set the wizard to run in answer file mode. \(For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](../../Topics\TopicNameNotContainA/Running-the-Analysis-Services-Deployment-Wizard.md).\)  
  
     —or—  
  
-   Open the \<*project name*\>.deploymentoptions in any text editor and manually change the options.  
  
## See Also  
 [Specifying the Installation Target](../../Topics\TopicNameNotContainA/Specifying-the-Installation-Target.md)   
 [Specifying Configuration Settings for Solution Deployment](../../Topics\TopicNameNotContainA/Specifying-Configuration-Settings-for-Solution-Deployment.md)   
 [Specifying Processing Options](../../Topics\TopicNameNotContainA/Specifying-Processing-Options.md)  
  
  