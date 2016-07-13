---
title: Defect Multiple Target Servers from a Master Server
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
manager:jhubbard
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
# Defect Multiple Target Servers from a Master Server
This topic describes how to defect multiple target servers from a multiserver administration configuration in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. Run this procedure from the master server.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To defect multiple target servers from a master server  
  
1.  In **Object Explorer**, expand a server that is configured as a master server.  
  
2.  Right\-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.  
  
3.  Click **Post Instructions**, and then in the **Instruction type** list, select **Defect**.  
  
4.  Under **Recipients**, do one of the following:  
  
    -   Click **All target servers** to defect all target servers of this master server. Use this option if you want to completely uninstall the current multiserver administration configuration.  
  
    -   Click **These target servers**, and then click the corresponding **Select** box, to defect some, but not all, target servers of this master server.  
  
## See Also  
[Create a Multiserver Environment](../content/Create-a-Multiserver-Environment.md)  
[Automated Administration Across an Enterprise](../content/Automated-Administration-Across-an-Enterprise.md)  
[Defect a Target Server from a Master Server](../content/Defect-a-Target-Server-from-a-Master-Server.md)  
  
