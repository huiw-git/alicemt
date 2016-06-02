---
title: Disconnect Users and Sessions on Analysis Services Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
---
# Disconnect Users and Sessions on Analysis Services Server
  An administrator of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] may want to end user activity as part of workload management. You do this by canceling sessions and connections. Sessions can be formed automatically when a query is run \(implicit\), or named at the time of creation by the administrator \(explicit\). Connections are open conduits over which queries can be run. Both sessions and connections can be ended while they are active. For example, an administrator may want to end processing for a session if the processing is taking too long or if some doubt has arisen as to whether the command being executed was written correctly.  
  
## Ending Sessions and Connections  
 To manage sessions and connections, you can use Dynamic Management Views \(DMVs\) and XMLA:  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to an Analysis Services instance.  
  
2.  Paste any one of the following DMV queries in an MDX query window to get a list of all sessions, connections, and commands that are currently executing:  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  Press F5 to execute the query.  
  
     The DMV query returns session and connection information in a tabular result set that is easier read and copy from.  
  
 Keep the query window open. In the next step, you will want to return to this page to copy the SPIDs of the session you want to disconnect.  
  
 To end a session, open a second XMLA query window.  
  
1.  Paste the following syntax into an MDX query window, replacing the ConnectionID, SessionID, or SPID placeholder with a valid value copied from the previous step.  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Press F5 to execute the cancel command.  
  
 Ending a connection cancels all sessions and SPIDs, closing the host session.  
  
 Ending a session stops all commands \(SPIDs\) that are running as part of that session.  
  
 Ending a SPID cancels a particular commend.  
  
 In rare cases, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] will not close a connection if it cannot track all the sessions and SPIDs associated with the connection \(for example, when multiple sessions are open in an HTTP scenario\).  
  
 For more information about the XMLA referenced in this topic, see [Execute Method &#40;XMLA&#41;](../Topic/Execute%20Method%20\(XMLA\).md) and [Cancel Element &#40;XMLA&#41;](../Topic/Cancel%20Element%20\(XMLA\).md).  
  
## See Also  
 [Managing Connections and Sessions &#40;XMLA&#41;](../Topic/Managing%20Connections%20and%20Sessions%20\(XMLA\).md)   
 [BeginSession Element &#40;XMLA&#41;](../Topic/BeginSession%20Element%20\(XMLA\).md)   
 [EndSession Element &#40;XMLA&#41;](../Topic/EndSession%20Element%20\(XMLA\).md)   
 [Session Element &#40;XMLA&#41;](../Topic/Session%20Element%20\(XMLA\).md)  
  
  