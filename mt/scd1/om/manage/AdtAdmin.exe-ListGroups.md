---
title: AdtAdmin.exe ListGroups
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14a02a1a-0a40-4f23-809b-11f6fb9ac5ba
---
# AdtAdmin.exe ListGroups
The output of the *\/ListGroups* parameter is a comma\-separated list of groups that is maintained by an ACS collector. If no subparameters are used, all groups from this ACS collector are listed. None of the subparameters that specify individual ACS forwarders apply to the *\/ListGroups* parameter.  
  
## Syntax  
`AdtAdmin.exe /ListGroups [/Collector:<CollectorName>] {[/Group:<GroupName>] | [/GroupID:<IdentificationNumber>] | [/Value:<ValueNumber>]}`  
  
|Subparameter|Definition|  
|----------------|--------------|  
|\/Collector:CollectorName|Specifies an ACS collector whose groups you want to list. If this subparameter is omitted, the local ACS collector is assumed.|  
|\/Group:GroupName|Specifies a group of ACS forwarders by the group’s name.|  
|\/GroupID: IdentificationNumber|Specifies a group of ACS forwarders by the group’s identification number. An identification number is assigned to a group when it is first created.|  
|\/Value:ValueNumber|Specifies an ACS forwarder or ACS group by its assigned connection value. The ACS collector prioritizes connections from ACS forwarders using connection values. Connection values range from \-1 through 99. A value of \-1 means the forwarder is part of an ACS group and that the group's value is used to determine the forwarder's priority. A value of 0 means the ACS collector ignores data from that ACS forwarder or group. If event saturation is detected, a collector will disconnect forwarders or a group of forwarders with lower values before disconnecting forwarders with higher values.|  
  
## Example  
Use the following example to list all ACS groups defined on this ACS collector:  
  
`adtadmin /listgroups`  
  
## See Also  
[Audit Collection Services Administration &#40;AdtAdmin.exe&#41;](../../om/manage/Audit-Collection-Services-Administration--AdtAdmin.exe-.md)  
[AdtAdmin.exe AddGroup](../../om/manage/AdtAdmin.exe-AddGroup.md)  
[AdtAdmin.exe DelGroup](../../om/manage/AdtAdmin.exe-DelGroup.md)  
[AdtAdmin.exe Disconnect](../../om/manage/AdtAdmin.exe-Disconnect.md)  
[AdtAdmin.exe GetDBAuth](../../om/manage/AdtAdmin.exe-GetDBAuth.md)  
[AdtAdmin.exe GetQuery](../../om/manage/AdtAdmin.exe-GetQuery.md)  
[AdtAdmin.exe ListForwarders](../../om/manage/AdtAdmin.exe-ListForwarders.md)  
[AdtAdmin.exe SetDBAuth](../../om/manage/AdtAdmin.exe-SetDBAuth.md)  
[AdtAdmin.exe SetQuery](../../om/manage/AdtAdmin.exe-SetQuery.md)  
[AdtAdmin.exe Stats](../../om/manage/AdtAdmin.exe-Stats.md)  
[AdtAdmin.exe UpdForwarder](../../om/manage/AdtAdmin.exe-UpdForwarder.md)  
[AdtAdmin.exe UpdGroup](../../om/manage/AdtAdmin.exe-UpdGroup.md)  
  
