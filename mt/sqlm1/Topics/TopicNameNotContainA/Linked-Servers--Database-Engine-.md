---
title: Linked Servers (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
---
# Linked Servers (Database Engine)
  Configure a linked server to enable the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] to execute commands against OLE DB data sources outside of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Typically linked servers are configured to enable the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to execute a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that includes tables in another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or another database product such as Oracle. Many types OLE DB data sources can be configured as linked servers, including [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Access and Excel. Linked servers offer the following advantages:  
  
-   The ability to access data from outside of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   The ability to issue distributed queries, updates, commands, and transactions on heterogeneous data sources across the enterprise.  
  
-   The ability to address diverse data sources similarly.  
  
 You can configure a linked server by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or by using the [sp_addlinkedserver &#40;Transact-SQL&#41;](../Topic/sp_addlinkedserver%20\(Transact-SQL\).md) statement. OLE DB providers vary greatly in the type and number of parameters required. For example some providers require you to provide a security context for the connection using [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../Topic/sp_addlinkedsrvlogin%20\(Transact-SQL\).md). Some OLE DB providers allow [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to update data on the OLE DB source. Others provide only read\-only data access. For information about each OLE DB provider, consult documentation for that OLE DB provider.  
  
## Linked Server Components  
 A linked server definition specifies the following objects:  
  
-   An OLE DB provider  
  
-   An OLE DB data source  
  
 An *OLE DB provider* is a DLL that manages and interacts with a specific data source. An *OLE DB data source* identifies the specific database that can be accessed through OLE DB. Although data sources queried through linked server definitions are ordinarily databases, OLE DB providers exist for a variety of files and file formats. These include text files, spreadsheet data, and the results of full\-text content searches.  
  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client OLE DB Provider \(PROGID: SQLNCLI11\) is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] distributed queries are designed to work with any OLE DB provider that implements the required OLE DB interfaces. However, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has been tested against only the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client OLE DB Provider and certain other providers.  
  
## Linked Server Details  
 The following illustration shows the basics of a linked server configuration.  
  
 ![Client tier, server tier, and database server tier](../../Images\Image\ImageNotContaina/lsvr.gif "lsvr")  
  
 Typically, linked servers are used to handle distributed queries. When a client application executes a distributed query through a linked server, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] parses the command and sends requests to OLE DB. The rowset request may be in the form of executing a query against the provider or opening a base table from the provider.  
  
 For a data source to return data through a linked server, the OLE DB provider \(DLL\) for that data source must be present on the same server as the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 When a third\-party OLE DB provider is used, the account under which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service runs must have read and execute permissions for the directory, and all subdirectories, in which the provider is installed.  
  
## Managing Providers  
 There is a set of options that control how [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] loads and uses OLE DB providers that are specified in the registry.  
  
## Managing Linked Server Definitions  
 When you are setting up a linked server, register the connection information and data source information with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. After registered, that data source can be referred to with a single logical name.  
  
 You can use stored procedures and catalog views to manage linked server definitions:  
  
-   Create a linked server definition by running **sp\_addlinkedserver**.  
  
-   View information about the linked servers defined in a specific instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by running a query against the **sys.servers** system catalog views.  
  
-   Delete a linked server definition by running **sp\_dropserver**. You can also use this stored procedure to remove a remote server.  
  
 You can also define linked servers by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. In the Object Explorer, right\-click **Server Objects**, select **New**, and select **Linked Server**. You can delete a linked server definition by right\-clicking the linked server name and selecting **Delete**.  
  
 When you execute a distributed query against a linked server, include a fully qualified, four\-part table name for each data source to query. This four\-part name should be in the form *linked\_server\_name.catalog***.***schema***.***object\_name*.  
  
> [!NOTE]  
>  Linked servers can be defined to point back \(loop back\) to the server on which they are defined. Loopback servers are most useful when testing an application that uses distributed queries on a single server network. Loopback linked servers are intended for testing and are not supported for many operations, such as distributed transactions.  
  
## Related Tasks  
 [Create Linked Servers &#40;SQL Server Database Engine&#41;](../Topic/Create%20Linked%20Servers%20\(SQL%20Server%20Database%20Engine\).md)  
  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../Topic/sp_addlinkedserver%20\(Transact-SQL\).md)  
  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../Topic/sp_addlinkedsrvlogin%20\(Transact-SQL\).md)  
  
 [sp_dropserver &#40;Transact-SQL&#41;](../Topic/sp_dropserver%20\(Transact-SQL\).md)  
  
## Related Content  
 [sys.servers &#40;Transact-SQL&#41;](../Topic/sys.servers%20\(Transact-SQL\).md)  
  
 [sp_linkedservers &#40;Transact-SQL&#41;](../Topic/sp_linkedservers%20\(Transact-SQL\).md)  
  
  