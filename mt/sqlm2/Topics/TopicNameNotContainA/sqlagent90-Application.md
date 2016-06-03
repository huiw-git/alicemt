---
title: sqlagent90 Application
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
---
# sqlagent90 Application
  The **sqlagent90** application starts [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent from the command prompt. Usually, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent should be run from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or by using SQL\-SMO methods in an application. Only run **sqlagent90** from the command prompt when you are diagnosing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, or when you are directed to it by your primary support provider.  
  
## Syntax  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## Arguments  
 **\-c**  
 Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is running from the command prompt and is independent of the Microsoft Windows Services Control Manager. When **\-c** is used, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent cannot be controlled from either the Services application in Administrative Tools or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager. This argument is mandatory.  
  
 **\-v**  
 Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent runs in verbose mode and writes diagnostic information to the command\-prompt window. The diagnostic information is the same as the information written to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent error log.  
  
 **\-i** *instance\_name*  
 Indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent connects to the named [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance specified by *instance\_name*.  
  
## Remarks  
 After displaying a copyright message, **sqlagent90** displays output in the command prompt window only when the **\-v** switch is specified. To stop **sqlagent90**, press CTRL\+C at the command prompt. Do not close the command\-prompt window before stopping **sqlagent90**.  
  
## See Also  
 [Automated Administration Tasks &#40;SQL Server Agent&#41;](../Topic/Automated%20Administration%20Tasks%20\(SQL%20Server%20Agent\).md)  
  
  