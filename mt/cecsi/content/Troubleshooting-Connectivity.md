---
title: "Troubleshooting Connectivity"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
caps.latest.revision: 23
manager: jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# Troubleshooting Connectivity
  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] requires that TCP/IP be installed and running to communicate with your [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database. You can use the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Configuration Manager to verify which network library protocols are installed.  
  
 A database connection attempt might fail for many reasons. These can include the following:  
  
-   TCP/IP is not enabled for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], or the server or port number specified is incorrect. Verify that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is listening with TCP/IP on the specified server and port. This might be reported with an exception similar to: "The login has failed. The TCP/IP connection to the host has failed." This indicates one of the following:  
  
    -   [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is installed but TCP/IP has not been installed as a network protocol for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] by using the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Network Utility for [!INCLUDE[ssVersion2000](../content/includes/ssVersion2000_md.md)], or the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Configuration Manager for [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)] and later.  
  
    -   TCP/IP is installed as a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] protocol, but it is not listening on the port specified in the JDBC connection URL. The default port is 1433, but [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] can be configured at product installation to listen on any port. Make sure that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is listening on port 1433. Or, if the port has been changed, make sure that the port specified in the JDBC connection URL matches the changed port. For more information about JDBC connection URLs, see [Building the Connection URL](../content/Building-the-Connection-URL.md).  
  
    -   The address of the computer that is specified in the JDBC connection URL does not refer to a server where [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is installed and started.  
  
    -   The networking operation of TCP/IP between the client and server running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is not operable. You can check TCP/IP connectivity to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] by using telnet. For example, at the command prompt, type `telnet 192.168.0.0 1433` where 192.168.0.0 is the address of the computer that is running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and 1433 is the port it is listening on. If you receive a message that states "Telnet cannot connect," TCP/IP is not listening on that port for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] connections. Use the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Network Utility for [!INCLUDE[ssVersion2000](../content/includes/ssVersion2000_md.md)], or the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Configuration Manager for [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)] and later to make sure that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is configured to use TCP/IP on port 1433.  
  
    -   The port that is used by the server has not been opened in the firewall. This includes the port that is used by the server or optionally, the port associated with a named instance of the server.  
  
-   The specified database name is incorrect. Make sure that you are logging on to an existing [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
-   The user name or password is incorrect. Make sure that you have the correct values.  
  
-   When you use [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, the JDBC driver requires that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is installed with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, which is not the default. Make sure that this option is included when you install or configure your instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
## See Also  
 [Diagnosing Problems with the JDBC Driver](../content/Diagnosing-Problems-with-the-JDBC-Driver.md)   
 [Connecting to SQL Server with the JDBC Driver](../content/Connecting-to-SQL-Server-with-the-JDBC-Driver.md)  
  
  