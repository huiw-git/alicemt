---
title: "Client Protocols - Named Pipes Properties (Protocol Tab)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Client Protocols - Named Pipes Properties (Protocol Tab)
In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager use the **Protocol** tab on the **Named Pipes Properties** dialog box to view or modify the description of default pipe. To connect to a different pipe, type the pipe in the **Default Pipe** box. For more information about connection strings, see [Creating a Valid Connection String Using Named Pipes](assetId:///90930ff2-143b-4651-8ae3-297103600e4f).  
  
## Options  
 **Default Pipe**  
 Specifies the default pipe the Named Pipes Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. By default, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] listens on: `\\.\pipe\sql\query`  
  
 To connect to the default pipe, enter `sql\query`  
  
 **Enabled**  
 Possible values are **Yes** and **No**.  
  
## See Also  
 [Choosing a Network Protocol](assetId:///6565fb7d-b076-4447-be90-e10d0dec359a)