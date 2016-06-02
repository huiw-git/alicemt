---
title: Symmetric Keys on User Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
---
# Symmetric Keys on User Databases
  This rule checks whether keys that have a length of less than 128 bytes do not use the RC2 or RC4 encryption algorithm.  
  
## Best Practices Recommendations  
 Use AES 128 bit or larger to create symmetric keys for data encryption. If AES is not supported by your operating system, use 3DES.  
  
## For More Information  
 [Choose an Encryption Algorithm](../../Topics\TopicNameNotContainA/Choose-an-Encryption-Algorithm.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  