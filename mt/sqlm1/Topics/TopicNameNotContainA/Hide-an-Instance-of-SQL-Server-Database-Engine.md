---
title: Hide an Instance of SQL Server Database Engine
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 392de21a-57fa-4a69-8237-ced8ca86ed1d
---
# Hide an Instance of SQL Server Database Engine
  This topic describes how to hide an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using SQL Server Configuration Manager. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service to enumerate instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] installed on the computer. This enables client applications to browse for a server, and helps clients distinguish between multiple instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on the same computer. You can use the following procedure to prevent the SQL Server Browser service from exposing an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to client computers that try to locate the instance by using the **Browse** button.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To hide an instance of the SQL Server Database Engine  
  
1.  In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right\-click **Protocols for** *\<server instance\>*, and then select **Properties**.  
  
2.  On the **Flags** tab, in the **HideInstance** box, select **Yes**, and then click **OK** to close the dialog box. The change takes effect immediately for new connections.  
  
## Remarks  
 If you hide a named instance, you will need to provide the port number in the connection string to connect to the hidden instance, even if the browser service is running. We recommend that you use a static port instead of a dynamic port for the named hidden instance.  
  For more information, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20a%20Server%20to%20Listen%20on%20a%20Specific%20TCP%20Port%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
### Clustering  
 If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This will cause the cluster instance’s **IsAlive** check to fail and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will go offline. We recommend that you create an alias in all the nodes of the clustered instance to reflect the static port that you configured for the instance.  
 For more information, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](../Topic/Create%20or%20Delete%20a%20Server%20Alias%20for%20Use%20by%20a%20Client%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
 If you hide a clustered named instance, cluster service may not be able to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] if the **LastConnect** registry key \(**HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSSQLServer\\Client\\SNI11.0\\LastConnect**\) has a different port than the port that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is listening on. If the cluster service is unable to make a connection to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you might see an error similar to the following:  
**Event ID: 1001: Event Name: Failover clustering resource deadlock.**  
  
## See Also  
 [Server Network Configuration](../../Topics\TopicNameNotContainA/Server-Network-Configuration.md)   
 [Description of SQL Virtual Server client connections](https://support.microsoft.com/kb/273673)   
 [How to assign a static port to a SQL Server named instance \- and avoid a common pitfall](http://blogs.msdn.com/b/arvindsh/archive/2012/09/08/how-to-assign-a-static-port-to-a-sql-server-named-instance-and-avoid-a-common-pitfall.aspx)  
  
  