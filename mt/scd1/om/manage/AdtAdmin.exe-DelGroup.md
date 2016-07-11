---
title: AdtAdmin.exe DelGroup
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f933313-7927-477f-a048-1296869a2c41
manager:cfreeman
---
# AdtAdmin.exe DelGroup
The *\/DelGroup* parameter deletes a group from an ACS collector by using its name or group identification number. When a group is deleted, the forwarders that belong to the group are not deleted. Any forwarders assigned to a group when it is deleted are added to or still belong to the default top\-level groups.  
  
No output is generated from this command. You can use the *\/ListGroups* parameter to verify that the group was created and also to determine a group’s assigned identification number.  
  
## Syntax  
`AdtAdmin.exe /DelGroup [/Collector:<CollectorName>] {[/Group:<GroupName>] | [/GroupID:<IdentificationNumber>]}`  
  
|Subparameter|Description|  
|----------------|---------------|  
|\/Collector:CollectorName|Specifies the ACS collector on which the group was created. If this subparameter is omitted, the local ACS collector is assumed.|  
|\/Group:GroupName|Specifies an ACS group to delete by the group’s name.|  
|\/GroupID:IdentificationNumber|Specifies an ACS group to delete by the group’s identification number. An identification number is assigned to a group when it is first created.|  
  
## Example  
Use the following example to delete an ACS group that has the name "Accounting Computers":  
  
`adtadmin /delgroup /group:"Accounting Computers"`  
  
## See Also  
[Audit Collection Services Administration &#40;AdtAdmin.exe&#41;](../../om/manage/Audit-Collection-Services-Administration--AdtAdmin.exe-.md)  
[AdtAdmin.exe AddGroup](../../om/manage/AdtAdmin.exe-AddGroup.md)  
[AdtAdmin.exe Disconnect](../../om/manage/AdtAdmin.exe-Disconnect.md)  
[AdtAdmin.exe GetDBAuth](../../om/manage/AdtAdmin.exe-GetDBAuth.md)  
[AdtAdmin.exe GetQuery](../../om/manage/AdtAdmin.exe-GetQuery.md)  
[AdtAdmin.exe ListForwarders](../../om/manage/AdtAdmin.exe-ListForwarders.md)  
[AdtAdmin.exe ListGroups](../../om/manage/AdtAdmin.exe-ListGroups.md)  
[AdtAdmin.exe SetDBAuth](../../om/manage/AdtAdmin.exe-SetDBAuth.md)  
[AdtAdmin.exe SetQuery](../../om/manage/AdtAdmin.exe-SetQuery.md)  
[AdtAdmin.exe Stats](../../om/manage/AdtAdmin.exe-Stats.md)  
[AdtAdmin.exe UpdForwarder](../../om/manage/AdtAdmin.exe-UpdForwarder.md)  
[AdtAdmin.exe UpdGroup](../../om/manage/AdtAdmin.exe-UpdGroup.md)  
  
