---
title: "System Center Configuration Manager privacy statement - Microsoft Operations Management Suite addendum"
ms.custom: na
ms.date: 2016-07-22
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa91afee-45b5-46eb-ad8a-e9c7d3122b38
caps.latest.revision: 4
author: barlanmsft
---
# System Center Configuration Manager privacy statement - Microsoft Operations Management Suite addendum
This privacy statement should be read in conjunction with the [System Center Configuration Manager privacy statement](https://www.microsoft.com/en-us/privacystatement/SystemCenterConfigurationManager/Default.aspx) as the provisions in that document are applicable. This privacy statement covers the features for the [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)] Connector within [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)]. This disclosure focuses on high-level aspects of the Connector, and is not intended to be an exhaustive list. 

### **What this feature does:** 
The [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)] Connector syncs data such as collections from [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)] to [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)] Suite. Collections are used in [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)] to organize resources into manageable units. This enables system administrators to create an organized structure that can be used to perform various management tasks on multiple resources, such as computers and servers, at one time. 

### Information collected, processed, or transmitted:
The Microsoft Azure subscription ID and secret key are stored in the [!INCLUDE[cmshort_md](../System Center Configuration Manager/itokens/cmshort_md.md)] database when an administrator configures the feature. Both the Azure Active Directory client secret and the [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)] workspace shared key are stored in the on-premise [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)] database. 

During configuration, a list of collections within [!INCLUDE[cmshortname_md](../System Center Configuration Manager/itokens/cmshortname_md.md)] appears. The administrator can select from these collections to allow them to be monitored from [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)]. All communications between [!INCLUDE[cm6long_md](../System Center Configuration Manager/itokens/cm6long_md.md)] and [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)] use HTTPS. No additional information about the collections are provided to Microsoft outside of randomized telemetry data. For details about what information is collected by [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)], see more [here about log analytics data security](https://azure.microsoft.com/en-us/documentation/articles/log-analytics-security/).

### Choice/control: 
It is your choice to use the [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)] Connector. This feature is not enabled by default, and requires the use of Microsoft web-based services. Additionally, the administrator is able to select which collections are synced, and can be terminated at any time. This will remove all synced data from [!INCLUDE[omslong](../System Center Configuration Manager/itokens/omslong.md)]. 
