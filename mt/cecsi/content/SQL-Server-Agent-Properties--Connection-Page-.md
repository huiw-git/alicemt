---
title: "SQL Server Agent Properties (Connection Page)"
ms.custom: na
ms.date: 07/15/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: 3
manager: jhubbard
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
# SQL Server Agent Properties (Connection Page)
Use this page to view and modify the settings for the connection from the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
## Options  
**Alias local host server**  
Specifies the alias to use to connect to the local instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. If you cannot use the default connection options for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent, define an alias for the instance and specify the alias here.  
  
**Use Windows Authentication**  
Sets [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance. [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent connects as the account that the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service runs as.  
  
**Use SQL Server Authentication**  
Sets [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication is provided for backward compatibility. For improved security, use Windows Authentication if possible.  
  
**Login**  
Specifies the login name to use to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
**Password**  
Specifies the password to use to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
