---
title: Configure Login Auditing (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
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
# Configure Login Auditing (SQL Server Management Studio)
This topic describes how to configure login auditing in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] to monitor [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)] login activity. Login auditing can be configured to write to the error log on the following events.  
  
-   Failed logins  
  
-   Successful logins  
  
-   Both failed and successful logins  
  
You must restart [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] before this option will take effect.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To configure login auditing  
  
1.  In [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)], connect to an instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)] with Object Explorer.  
  
2.  In Object Explorer, right\-click the server name, and then click **Properties**.  
  
3.  On the **Security** page, under **Login** auditing, click the desired option and close the **Server Properties** page.  
  
4.  In Object Explorer, right\-click the server name, and then click **Restart**.  
  
