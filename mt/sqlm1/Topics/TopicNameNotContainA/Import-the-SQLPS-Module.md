---
title: Import the SQLPS Module
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
---
# Import the SQLPS Module
  The recommended way to manage [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from PowerShell is to import the **sqlps** module into a Windows PowerShell environment. The module loads and registers the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] snap\-ins and manageability assemblies.  
  
1.  **Before You Begin:**  [Security](#Security)  
  
2.  **To load the module:**  [Load the sqlps Module](#LoadSqlps)  
  
## Before You Begin  
 After importing the **sqlps** module into Windows PowerShell, you can then:  
  
-   Interactively run Windows PowerShell commands.  
  
-   Run Windows PowerShell script files.  
  
-   Run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cmdlets.  
  
-   Use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.  
  
-   Use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] manageability object models \(such as Microsoft.SqlServer.Management.Smo\) to manage [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.  
  
> [!NOTE]  
>  The verbs used in the names of two SQL Server cmdlets \(**Encode\-Sqlname** and **Decode\-Sqlname**\) do not match the approved verbs for Windows PowerShell. This has no effect on their operation, but Windows PowerShell raises a warning when the **sqlps** module is imported to a session.  
  
###  <a name="Security"></a> Security  
 By default, Windows PowerShell runs with the scripting execution policy set to **Restricted**, which prevents running any Windows PowerShell scripts. To load the **sqlps** module, you can use the **Set\-ExecutionPolicy** cmdlet to enable running signed scripts, or any scripts. Only run scripts from trusted sources, and secure all input and output files using the appropriate NTFS permissions. For more information about enabling Windows PowerShell scripts, see [Running Windows PowerShell Scripts](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx).  
  
##  <a name="LoadSqlps"></a> Load the sqlps Module  
 **To load the sqlps module in Windows PowerShell**  
  
1.  Use the **Set\-ExecutionPolicy** cmdlet to set the appropriate script execution policy.  
  
2.  Use the **Import\-Module** cmdlet to import the sqlps module. Specify the **DisableNameChecking** parameter if you want to suppress the warning about **Encode\-Sqlname** and **Decode\-Sqlname**.  
  
### Example \(PowerShell\)  
 This example loads the **sqlps** module with name checking turned off.  
  
```  
## Import the SQL Server Module.  
  
Import-Module “sqlps” -DisableNameChecking  
  
```  
  
> [!NOTE]  
>  If the **sqlps** module is not in your path, change to the location of the module or use the full path in the script \(using double\-quotes of folders in your path have spaces\). The **sqlps** module is located in the Tools\\Powershell folder for your SQL Server instance.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [&#91;Top&#93;](#Intro)  
  
## See Also  
 [SQL Server PowerShell](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell.md)   
 [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)   
 [Use the Database Engine cmdlets](../../Topics\TopicNameNotContainA/Use-the-Database-Engine-cmdlets.md)  
  
  