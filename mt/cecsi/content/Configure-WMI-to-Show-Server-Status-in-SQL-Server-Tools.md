---
title: "Configure WMI to Show Server Status in SQL Server Tools"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 4
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Configure WMI to Show Server Status in SQL Server Tools
This topic describes how to configure WMI to show the server status in SQL Server tools in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)]. When connecting to servers, both the Registered Servers and Object Explorer components of [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], as well as [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Configuration Manager, use Windows Management Instrumentation (WMI) to obtain the status of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] (MSSQLSERVER) and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent (MSSQLSERVER) services. To display the status of the service, the user must have rights to remotely access the WMI object. The server must have WMI installed to configure this permission.  
  
## <a name="SSMSProcedure"></a>To configure WMI permission  
  
1.  On the **Start** menu on the remote server, click **Run**.  
  
2.  In the **Open** box type **wmimgmt.msc**, and then click **OK**.  
  
3.  In the **Windows Management Infrastructure** program, right-click **WMI Control (Local)**, and then click **Properties**.  
  
4.  In the **WMI Control (Local) Properties** dialog box, on the **Security** tab, expand **Root**, and then click **CIMV2**.  
  
5.  Click **Security** to open the **Security for ROOT\CIMV2** dialog box.  
  
6.  Add a group or user to the **Group or user names** box and select it.  
  
7.  In the **Permissions for***<group or user>* box, select the **Allow** column, for the **Remote Enable** permission, for users whom you wish to remotely detect the service status.  
  
## See Also  
[Start, Stop, or Pause the SQL Server Agent Service](../content/Start--Stop--or-Pause-the-SQL-Server-Agent-Service.md)  
  
