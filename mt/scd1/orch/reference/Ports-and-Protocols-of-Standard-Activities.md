---
title: Ports and Protocols of Standard Activities
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - orchestrator
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 306056fe-02cc-44e9-8cd2-9df390660915
---
# Ports and Protocols of Standard Activities
[!INCLUDE[orchshort](../../om/manage/includes/orchshort_md.md)] standard activities can communicate between the runbook servers where the runbook is deployed and any resource. If you have firewalls in your environment, when you use a standard activity, you must enable the ports between the runbook servers and resource as indicated in the following table.  
  
|Standard activity|Port on runbook server|Port on resource server|Notes|  
|---------------------|--------------------------|---------------------------|---------|  
|[Query Database](../../orch/reference/Query-Database.md)||Any port the target database requires.||  
|[Write to Database](../../orch/reference/Write-to-Database.md)||Any port the target database requires.||  
|[Invoke Web Services](../../orch/reference/Invoke-Web-Services.md)|HTTP or HTTPS|HTTP or HTTPS||  
|[Map Network Path](../../orch/reference/Map-Network-Path.md)|||Activity uses Microsoft Windows file sharing.|  
|[Set SNMP Variable](../../orch/reference/Set-SNMP-Variable.md)|SNMP|SNMP||  
|[Get SNMP Variable](../../orch/reference/Get-SNMP-Variable.md)|SNMP|SNMP||  
|[Monitor SNMP Trap](../../orch/reference/Monitor-SNMP-Trap.md)|SNMP|SNMP||  
|[Send SNMP Trap](../../orch/reference/Send-SNMP-Trap.md)|SNMP|SNMP||  
|[Run Program](../../orch/reference/Run-Program.md)|||Activity uses Microsoft Windows file sharing and I\/O pipes.|  
|[Send Email](../../orch/reference/Send-Email.md)|SMTP|SMTP||  
|[Monitor Internet Application](../../orch/reference/Monitor-Internet-Application.md)|HTTP\/SMTP\/POP3\/FTP\/DNS|HTTP\/SMTP\/POP3\/FTP\/DNS||  
|[Get Internet Application Status](../../orch/reference/Get-Internet-Application-Status.md)|HTTP\/SMTP\/POP3\/FTP\/DNS\/Custom|HTTP\/SMTP\/POP3\/FTP\/DNS\/Custom|Custom can be anything.|  
|[Send Syslog Message](../../orch/reference/Send-Syslog-Message.md)|syslog|syslog||  
  
## Other resources for this product  
  
-   TechNet Library main page for [Orchestrator_1](../Topic/Orchestrator_1.md)  
  
-   [Runbook Activity Reference for System Center 2012 - Orchestrator](../../orch/reference/Runbook-Activity-Reference-for-System-Center-2012---Orchestrator.md)  
  
-   [Alphabetical List of Standard Activities](../../orch/reference/Alphabetical-List-of-Standard-Activities.md)  
  
## See Also  
[TCP Port Requirements](assetId:///dc879c86-4855-4fd0-808d-06f64a9657ca)  
  
