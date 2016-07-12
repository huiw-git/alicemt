---
title: Integrating Operations Manager with Development Processes in System Center 2012 R2
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 210b3726-182f-4b0e-bc7c-45f9042b57a6
manager:cfreeman
---
# Integrating Operations Manager with Development Processes in System Center 2012 R2
Streamlining the communications between development and information technology \(IT\) operations teams \(often called DevOps\) can help you decrease the time it takes for application maintenance and delivery into production, where your application delivers value to customers. To speed interactions between these teams, it is essential to quickly detect and fix problems that might need assistance from the engineering team.  
  
The topics in this section can help you integrate [!INCLUDE[omblue_1](../../om/manage//omblue_1_md.md)] with development tools, such as Team Foundation Server \(TFS\) and Visual Studio. This integration enables deep troubleshooting and provides greater efficiency between development and IT operations teams.  
  
## Integrating Operations Manager with Development Processes \(DevOps\) Topics  
  
-   [How to Configure Integration with TFS in System Center 2012 R2](../../om/manage/How-to-Configure-Integration-with-TFS-in-System-Center-2012-R2.md)  
  
    You can synchronize [!INCLUDE[omblue_1](../../om/manage//omblue_1_md.md)] alerts and TFS work items. When synchronization is enabled, IT operations can assign alerts to the engineering team.  
  
-   [How to Configure File Attachments for Operations Manager Alerts in System Center 2012 R2](../../om/manage/How-to-Configure-File-Attachments-for-Operations-Manager-Alerts-in-System-Center-2012-R2.md)  
  
    You will need to configure file attachments for [!INCLUDE[omblue_2](../../om/manage//omblue_2_md.md)] alerts. Proper configuration enables integration with TFS, IntelliTrace Historical Profiling, sharing Application Performance Monitoring events with developers, Global Service Monitor web tests, and any other scenarios that require files to be associated with [!INCLUDE[omblue_2](../../om/manage//omblue_2_md.md)] alerts.  
  
-   [How to Synchronize Alerts with TFS in System Center 2012 R2](../../om/manage/How-to-Synchronize-Alerts-with-TFS-in-System-Center-2012-R2.md)  
  
    TFS lets you configure engineering process templates. [!INCLUDE[omblue_2](../../om/manage//omblue_2_md.md)] integration with TFS introduces a new "Operational Issue" work item type definition that can be embedded into any of your organization’s engineering processes.  
  
-   [How to Configure Integration with IntelliTrace Historical Profiling in System Center 2012 R2](../../om/manage/How-to-Configure-Integration-with-IntelliTrace-Historical-Profiling-in-System-Center-2012-R2.md)  
  
    You can help developers to debug applications by collecting IntelliTrace snapshots directly from [!INCLUDE[omblue_2](../../om/manage//omblue_2_md.md)]. When TFS and [!INCLUDE[omblue_2](../../om/manage//omblue_2_md.md)] are integrated, these snapshots can be automatically attached to TFS work items.  
  
-   [How to Collect IntelliTrace Historical Profiling Traces from System Center 2012 R2](../../om/manage/How-to-Collect-IntelliTrace-Historical-Profiling-Traces-from-System-Center-2012-R2.md)  
  
    After configuring integration with IntelliTrace, you can collect and share IntelliTrace snapshots with developers.  
  
-   [Monitoring Integration between Operations Manager and TFS in System Center 2012 R2](../../om/manage/Monitoring-Integration-between-Operations-Manager-and-TFS-in-System-Center-2012-R2.md)  
  
    Depending on your environment, you can import TFS monitoring and management packs that give you real\-time visibility into the health of the TFS developer environment.  
  
-   [Integrating Operations Manager with Non-English Versions of Team Foundation Server &#40;TFS&#41; or a Customized Process Model in TFS](../../om/manage/Integrating-Operations-Manager-with-Non-English-Versions-of-Team-Foundation-Server--TFS--or-a-Customized-Process-Model-in-TFS.md)  
  
    When you need to synchronize Operations Manager alerts and TFS work items, and your development team is using a non\-English process template in TFS \(included in non\-English versions of TFS\), you must configure Operations Manager so that it can synchronize alerts with TFS work items.  
  
