---
title: New Agent Profile
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
---
# New Agent Profile
  Use the **New Agent Profile** dialog box to create a new profile. New profiles are always based on existing profiles, but they can be modified to meet application requirements. After a profile has been created, it can be applied to existing and future agent jobs in the **Agent Profiles** dialog box. Agent parameter values can be edited in the \<**AgentProfileName\> Properties** dialog box.  
  
## Options  
 **Name**  
 Enter a name for the profile.  
  
 **Description**  
 Enter a description for the profile.  
  
 **Parameter**  
 The agent parameters included in the profile. The profile on which the new profile is based does not necessarily specify a value for each parameter. To see all parameters that are valid for a given agent, clear the **Show only parameters used in this profile** check box. For descriptions of each parameter, see:  
  
-   [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md)  
  
-   [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md)  
  
-   [Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md)  
  
-   [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md)  
  
-   [Replication Queue Reader Agent](../../Topics\TopicNameNotContainA/Replication-Queue-Reader-Agent.md)  
  
 **Default Value**  
 The default value for each agent parameter.  
  
 **Value**  
 The value specified for the parameter in the profile on which the new profile is based. Edit this field for any parameter values you want to change.  
  
 **Show only parameters used in this profile**  
 Clear to show all valid parameters for a given agent.  
  
## See Also  
 [Work with Replication Agent Profiles](../../Topics\TopicNameNotContainA/Work-with-Replication-Agent-Profiles.md)   
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)   
 [Replication Agent Profiles](../../Topics\TopicNameNotContainA/Replication-Agent-Profiles.md)  
  
  