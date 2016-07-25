---
title: "Removing SSMA for Sybase Components (SybaseToSQL)"
ms.custom: na
ms.date: 07/18/2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
caps.latest.revision: 6
manager: lonnyb
---
# Removing SSMA for Sybase Components (SybaseToSQL)
When you have finished migrating databases from Sybase Adaptive Server Enterprise (ASE) to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you might want to uninstall SSMA components. You can uninstall the client components at any time, but you should not uninstall the extension pack from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] unless you are sure that your migrated databases no longer use functions in the **ssma_syb** schema of the **sysdb** database.  
  
## Uninstalling the SSMA for Sybase Client  
You can uninstall SSMA by using **Add or Remove Programs**.  
  
**To uninstall SSMA**  
  
1.  In Control Panel, open **Add or Remove Programs**.  
  
2.  Select **Microsoft SQL Server Migration Assistant for Sybase**, and then click **Remove**.  
  
3.  To confirm that you want to uninstall SSMA, click **Yes**.  
  
## Uninstalling the Extension Pack  
If you are sure your migrated databases do not use objects in the **sysdb.ssma_syb** schema, you can remove the extension pack by using **Add or Remove Programs**.  
  
To uninstall the extension pack  
  
1.  In Control Panel, open **Add or Remove Programs**.  
  
2.  Select **Microsoft SQL Server Migration Assistant for Sybase Extension Pack**, and then click **Remove**.  
  
3.  To confirm that you want to uninstall the extension pack, click **Yes**.  
  
4.  On the Instances with Utilities Database Scripts page, click **Next**.  
  
5.  On the Connection Parameters page, select the authentication method, and then click **Next**.  
  
    Windows Authentication will use your Windows credentials to try to log on to the instance of SQL Server. If you select SQL Server Authentication, you must enter a SQL Server login name and password.  
  
6.  On the Operation Completed page, click **OK**.  
  
7.  On the Finish page, click **Exit**.  
  
After uninstalling, you can confirm that the **sysdb.ssma_syb** schema, and possibly the whole **sysdb** database, has been removed by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. However, if you use other SSMA products, they also use the **sysdb** database. If the database exists and you are sure that no other databases reference objects in this database, you can detach the database.  
  
## See Also  
[Installing SSMA  for Sybase Client &#40;SybaseToSQL&#41;](../content/Installing-SSMA--for-Sybase-Client--SybaseToSQL-.md)  
[Installing SSMA Components on SQL Server &#40;SybaseToSQL&#41;](../content/Installing-SSMA-Components-on-SQL-Server--SybaseToSQL-.md)  
  
