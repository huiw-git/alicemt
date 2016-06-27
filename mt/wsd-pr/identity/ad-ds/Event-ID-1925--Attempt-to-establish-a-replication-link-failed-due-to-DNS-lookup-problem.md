---
title: Event ID 1925: Attempt to establish a replication link failed due to DNS lookup problem
ms.custom: 
  - x
ms.prod: windows-server-threshold
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - active-directory-domain-services
ms.tgt_pltfrm: na
ms.assetid: 6460101a-f188-47c7-aa53-172422d48606
---
# Event ID 1925: Attempt to establish a replication link failed due to DNS lookup problem
This problem typically occurs when an attempt to establish a replication link fails as a result of a Domain Name System \(DNS\) lookup problem. If you receive Event ID 1925 with the error message that DNS lookup failed, inbound replication of a directory partition has failed on the destination domain controller, and you must fix the DNS problem.  
  
 The following is an example of the event text:  
  
```  
Log Name: Directory Service  
Source: Microsoft-Windows-ActiveDirectory_DomainService  
Date: 3/12/2008  8:14:13 AM  
Event ID: 1925  
Task Category: Knowledge Consistency Checker   
Level: Warning  
Keywords: Classic  
User: ANONYMOUS LOGON  
Computer: DC3.contoso.com  
Description:  
The attempt to establish a replication link for the following   
writable directory partition failed.   
  
Directory partition:   
CN=Configuration,DC=contoso,DC=com   
Source directory service:   
CN=NTDS Settings,CN=DC1,CN=Servers,CN=Default-First-Site-Name,  
CN=Sites,CN=Configuration,DC=contoso,DC=com   
Source domain controller address:   
f8786828-ecf5-4b7d-ad12-8ab60178f7cd._msdcs.contoso.com   
Intersite transport (if any): CN=IP,CN=Inter-Site Transports,  
CN=Sites,CN=Configuration,DC=constoso,DC=com  
  
This domain controller will be unable to replicate with the   
source domain controller until this problem is corrected.    
  
User Action   
Verify if the source domain controller is accessible or   
network connectivity is available.   
  
Additional Data   
Error value:   
8524 The DSA operation is unable to proceed because of a DNS   
lookup failure.  
  
```  
  
## Resolution  
 Proceed with DNS testing as described in "[Event ID 2087: DNS lookup failure caused replication to fail](../Topic/Event%20ID%202087:%20DNS%20lookup%20failure%20caused%20replication%20to%20fail.md)."