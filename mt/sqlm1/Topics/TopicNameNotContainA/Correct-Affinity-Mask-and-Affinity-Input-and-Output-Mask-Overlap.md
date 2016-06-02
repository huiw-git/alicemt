---
title: Correct Affinity Mask and Affinity Input and Output Mask Overlap
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
---
# Correct Affinity Mask and Affinity Input and Output Mask Overlap
  This rule checks whether the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has one or more processors that are assigned to be used with both the affinity mask and the affinity I\/O mask options. On a computer that has more than one processor, the affinity mask and the affinity I\/O mask options are used to designate which CPUs are used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Enabling a CPU with both the affinity mask and the affinity I\/O mask can slow performance by forcing the processor to be overused.  
  
## Best Practices Recommendations  
 When you specify either the affinity mask or the affinity I\/O mask options, you should specify both, but only enable each CPU no more than once.  
  
 Do not enable the same CPU in both the affinity mask option and the affinity I\/O mask option. The bits that correspond to each CPU should be in one of the following states:  
  
-   0 in both the affinity mask option and the affinity I\/O mask option  
  
-   0 in the affinity mask option and 1 in the affinity I\/O mask option  
  
-   1 in the affinity mask option and 0 in the affinity I\/O mask option  
  
## For More Information  
 [affinity mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md)  
  
 [affinity Input-Output mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-Input-Output-mask-Server-Configuration-Option.md)  
  
 [affinity64 mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity64-mask-Server-Configuration-Option.md)  
  
 [affinity64 Input-Output mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity64-Input-Output-mask-Server-Configuration-Option.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  