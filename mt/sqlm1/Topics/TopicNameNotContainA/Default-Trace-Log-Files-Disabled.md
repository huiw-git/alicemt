---
title: Default Trace Log Files Disabled
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
---
# Default Trace Log Files Disabled
  This rule checks the value of the sp\_configure stored procedure default trace enabled option to determine whether default trace is set ON \(1\) or OFF \(0\). When this option is enabled, default tracing provides information about configuration and DDL changes to the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. In some cases, this information can be helpful for customers and [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Customer Service and Support when they troubleshooting issues with the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
## Best Practices Recommendations  
 Use the sp\_configure stored procedure to enable tracing by setting the value of default trace enabled to 1.  
  
## For More Information  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  