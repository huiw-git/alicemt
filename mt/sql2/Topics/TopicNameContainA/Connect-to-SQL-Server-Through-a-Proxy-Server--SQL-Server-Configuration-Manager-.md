---
title: Connect to SQL Server Through a Proxy Server (SQL Server Configuration Manager)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
---
# Connect to SQL Server Through a Proxy Server (SQL Server Configuration Manager)
  This topic describes how to connect to SQL Server through a proxy server in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] by using SQL Server Configuration Manager. To listen remotely by way of Remote WinSock (RWS), define the local address table (LAT) for the proxy server so that the listening node address is outside the range of LAT entries.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To enable connections to SQL Server through Microsoft Proxy Server  
  
1.  Follow the steps in [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameContainA/Configure-a-Server-to-Listen-on-a-Specific-TCP-Port--SQL-Server-Configuration-Manager-.md) to determine which TCP/IP ports are used by the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)], or to configure the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] to use a desired port.  
  
2.  In your proxy server define the local address table (LAT) for the proxy server so that the listening node address is outside the range of LAT entries. For more information, see your proxy server documentation.  
  
  