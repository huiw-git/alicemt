---
title: Look Up RFC Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
---
# Look Up RFC Destination
  Use the **Look Up RFC Destination** dialog box to look up an RFC destination that is defined in the SAP Netweaver BW system. When the list of available RFC destinations appears, select the destination that you want, and the component will populate the associated options with the required values.  
  
 Both the SAP BW source and the SAP BW destination use the **Look Up RFC Destination** dialog box. For more information about these components of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](../../Topics\TopicNameNotContainA/SAP-BW-Source.md) and [SAP BW Destination](../../Topics\TopicNameNotContainA/SAP-BW-Destination.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
 **To open the Look Up RFC Destination dialog box**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that contains the SAP BW source or destination.  
  
2.  On the **Data Flow** tab, double\-click the SAP BW source or destination.  
  
3.  In the **SAP BW Source Editor** or the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.  
  
4.  On the **Connection Manager** page, in the **RFC Destination** group box, click **Look up** to display the **Look Up RFC Destination** dialog box.  
  
     In the **SAP BW Source Editor**, the **RFC Destination** group box appears only if the value for **Execution mode** is **P \- Trigger process chain** or **W \- Wait for notify**.  
  
## Options  
 **Destination**  
 View the name of the RFC destination that is defined in the SAP Netweaver BW system.  
  
 **Gateway Host**  
 View the server name or IP address of the gateway host. Usually, the name or IP address is the same as the SAP application server.  
  
 **Gateway Service**  
 View the name of the gateway service, in the format **sapgwNN**, where **NN** is the system number.  
  
 **Program ID**  
 View the Program ID that is associated with the RFC destination.  
  
## See Also  
 [SAP BW Source Editor &#40;Connection Manager Page&#41;](../Topic/SAP%20BW%20Source%20Editor%20\(Connection%20Manager%20Page\).md)   
 [SAP BW Destination Editor &#40;Connection Manager Page&#41;](../Topic/SAP%20BW%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics\TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)  
  
  