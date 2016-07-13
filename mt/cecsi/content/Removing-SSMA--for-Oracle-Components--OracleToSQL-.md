---
title: Removing SSMA  for Oracle Components (OracleToSQL)
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
manager: b-tomb
---
# Removing SSMA  for Oracle Components (OracleToSQL)
When you have finished migrating databases from Oracle to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you might want to uninstall SSMA components. You can uninstall the client components at any time. However, you should not uninstall the extension pack from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] unless your migrated databases no longer use functions in the **ssma\_oracle** schema of the **sysdb** database.  
  
## Uninstalling the SSMA for Oracle Client  
You can uninstall SSMA by using **Add or Remove Programs**.  
  
**To uninstall SSMA**  
  
1.  In Control Panel, open **Add or Remove Programs**.  
  
2.  Select **[!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Migration Assistant for Oracle**, and then click **Remove**.  
  
3.  To confirm that you want to uninstall SSMA, click **Yes**.  
  
## Uninstalling the Extension Pack  
If you are sure your migrated databases do not use objects in the **sysdb.ssma\_oracle** schema, you can remove the extension pack by using **Add or Remove Programs**.  
  
**To uninstall the extension pack**  
  
1.  In Control Panel, open **Add or Remove Programs**.  
  
2.  Select **Microsoft SQL Server Migration Assistant for Oracle Extension Pack**, and then click **Remove**.  
  
3.  To confirm that you want to uninstall the extension pack, click **Yes**.  
  
4.  On the Instances with Utilities Database Scripts page, select an instance and then click **Next**.  
  
5.  On the Connection Parameters page, select the authentication method, and then click **Next**.  
  
    Windows Authentication will use your Windows credentials to try to log on to the instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. If you select [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, you must enter a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] login name and password.  
  
6.  On the Operation Completed page, click **OK**.  
  
7.  On the Finish page, click **Exit**.  
  
After the uninstall, you can confirm that objects in the **sysdb.ssma\_oracle** schema, and possibly the whole **sysdb** database, has been removed by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)]. However, if you use other SSMA products, they also use the **sysdb** database. If the database exists and you are sure that no other databases reference objects in this database, you can detach the database.  
  
## See Also  
[Installing SSMA for Oracle Client &#40;OracleToSQL&#41;](../content/Installing-SSMA-for-Oracle-Client--OracleToSQL-.md)  
[Installing SSMA Components on SQL Server &#40;OracleToSQL&#41;](../content/Installing-SSMA-Components-on-SQL-Server--OracleToSQL-.md)  
  
