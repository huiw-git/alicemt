---
title: "Set Trace Definition Defaults (SQL Server Profiler)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab9fc570-797d-411e-814f-1c46d2d5feae
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Set Trace Definition Defaults (SQL Server Profiler)
The trace definition default is the default trace template that is used for each provider or server. You can set default trace templates for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] or for [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)].  
  
### To set trace definition defaults  
  
1.  On the **File** menu, select **Templates**, and then click **Edit Template.**  
  
2.  In the **Trace Template Properties** dialog box, on the **General**tab, select a server type from the **Select server type**list.  
  
3.  In the **Select template name**list, select the name of the template that you want to use as the trace definition default.  
  
4.  Select **Use as a default template for selected server type**.  
  
5.  If necessary, click the **Events Selection**tab to modify the template.  
  
6.  Click **Save**.  
  
## See Also  
 [SQL Server Profiler Templates](../../Topics/TopicNameNotContainA/SQL-Server-Profiler-Templates.md)   
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md)