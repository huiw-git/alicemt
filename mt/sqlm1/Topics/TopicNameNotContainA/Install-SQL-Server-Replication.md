---
title: Install SQL Server Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
---
# Install SQL Server Replication
  Replication components can be installed by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard or at a command prompt. Install replication when you install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or when you modify an existing instance.  
  
 After replication components are installed, you must configure the server before you can use replication. For more information, see [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
> [!IMPORTANT]  
>  If you install replication components when you modify an existing instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you must stop and restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent after the installation is completed. This action helps ensure that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent recognizes the replication agent subsystems and can call replication agents from job steps.  
  
## Installing Replication by Using Setup  
 **To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]**  
  
-   To install replication components, including Replication Management Objects \(RMO\), select **SQL Server Replication** on the **Feature Selection** page of the Installation Wizard.  
  
## Installing Replication from the Command Prompt  
 **To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]**  
  
-   See [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
## See Also  
 [Install SQL Server 2016](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016.md)   
 [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)   
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  
  
  