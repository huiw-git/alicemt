---
title: "Specify a connection string (SSAS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# Specify a connection string (SSAS)
This page of the **Table Import Wizard** enables you to specify a connection string to connect to an OLE DB or ODBC data source. To access the wizard from the [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)], on the **Model** menu, click **Import from Data Source**.  
  
 To connect to a data source, you must have the appropriate provider installed on your computer. For more information about supported data sources and providers, see [Data Sources Supported (SSAS Tabular)](../../Topics/TopicNameNotContainA/Data-Sources-Supported--SSAS-Tabular-.md).  
  
## UIElement List  
 **Friendly name for this connection**  
 Type a unique name for this data source connection. This is a required field.  
  
 **Connection String**  
 Type a connection string to connect to an OLE DB or ODBC data source.  
  
 **Build**  
 Specify the properties for a connection string by using the **Data Link Properties** dialog box. For more information, see the Microsoft Data Link Help, which is available from that dialog box.  
  
 **Test Connection**  
 Attempt to establish a connection to the data source using the specified connection string. A message is displayed indicating whether the connection is successful.