---
title: Analysis Services PowerShell Reference
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
---
# Analysis Services PowerShell Reference
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] includes a PowerShell provider \(SQLAS\) and cmdlets \(SQLASCMDLETS\) so that you can use Windows PowerShell to navigate, administer, and query [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects. For more information about loading and using the provider and cmdlets, see [PowerShell scripting in Analysis Services](../../Topics\TopicNameNotContainA/PowerShell-scripting-in-Analysis-Services.md). For an example of how to use AMO types in PowerShell to create a Tabular database, see [AMO PowerShell Example](../../Topics\TopicNameNotContainA/AMO-PowerShell-Example.md).  
  
##  <a name="bkmk_cmdlets"></a> Analysis Services Cmdlets  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides cmdlets correspond to methods in the **Microsoft.AnalysisServices** namespace. The following table describes each cmdlet and provides a link to the corresponding AMO method.  
  
 If you want to use PowerShell to perform a task that is not represented in the following list \(for example to create or synchronize a database\), you can write TMSL or XMLA script for that action, and then execute it using the **Invoke\-ASCmd** cmdlet.  
  
|Cmdlet|Description|Equivalent AMO Methods|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember cmdlet](../../Topics\TopicNameNotContainA/Add-RoleMember-cmdlet.md)|Add a member to a database role.|[Add](assetId:///M:Microsoft.AnalysisServices.RoleMemberCollection.Add(Microsoft.AnalysisServices.RoleMember))|  
|[Backup-ASDatabase cmdlet](../../Topics\TopicNameNotContainA/Backup-ASDatabase-cmdlet.md)|Backup an Analysis Services database.|[Backup](assetId:///M:Microsoft.AnalysisServices.Database.Backup(System.String))|  
|[Invoke-ASCmd cmdlet](../../Topics\TopicNameNotContainA/Invoke-ASCmd-cmdlet.md)|Execute a query or script in XMLA or TSML \(JSON\) format.|[Execute](assetId:///M:Microsoft.AnalysisServices.Server.Execute(System.String))|  
|[Invoke-ProcessASDatabase](../../Topics\TopicNameNotContainA/Invoke-ProcessASDatabase.md)|Process a database.|[Process](assetId:///M:Microsoft.AnalysisServices.IProcessable.Process)|  
|[Invoke-ProcessCube cmdlet](../../Topics\TopicNameNotContainA/Invoke-ProcessCube-cmdlet.md)|Process a cube.|[Process](assetId:///M:Microsoft.AnalysisServices.IProcessable.Process)|  
|[Invoke-ProcessDimension cmdlet](../../Topics\TopicNameNotContainA/Invoke-ProcessDimension-cmdlet.md)|Process a dimension.|[Process](assetId:///M:Microsoft.AnalysisServices.IProcessable.Process)|  
|[Invoke-ProcessPartition cmdlet](../../Topics\TopicNameNotContainA/Invoke-ProcessPartition-cmdlet.md)|Process a partition.|[Process](assetId:///M:Microsoft.AnalysisServices.IProcessable.Process)|  
|[Invoke-ProcessTable cmdlet](../../Topics\TopicNameNotContainA/Invoke-ProcessTable-cmdlet.md)|Process a table in a Tabular model, compatibility model 1200 or later.|[Process](assetId:///M:Microsoft.AnalysisServices.IProcessable.Process)|  
|[Merge-Partition cmdlet](../../Topics\TopicNameNotContainA/Merge-Partition-cmdlet.md)|Merge a partition.|[Merge](assetId:///M:Microsoft.AnalysisServices.Partition.Merge(System.Collections.IEnumerable))|  
|[New-RestoreFolder cmdlet](../../Topics\TopicNameNotContainA/New-RestoreFolder-cmdlet.md)|Create a folder to contain a database backup.|[RestoreFolder](assetId:///T:Microsoft.AnalysisServices.RestoreFolder)|  
|[New-RestoreLocation cmdlet](../../Topics\TopicNameNotContainA/New-RestoreLocation-cmdlet.md)|Specify one or more remote servers on which to restore the database.|[RestoreLocation](assetId:///T:Microsoft.AnalysisServices.RestoreLocation)|  
|[Remove-RoleMember cmdlet](../../Topics\TopicNameNotContainA/Remove-RoleMember-cmdlet.md)|Remove a member from a database role.|[Remove](assetId:///M:Microsoft.AnalysisServices.RoleMemberCollection.Remove(Microsoft.AnalysisServices.RoleMember))|  
|[Restore-ASDatabase cmdlet](../../Topics\TopicNameNotContainA/Restore-ASDatabase-cmdlet.md)|Restore a database on a server instance.|[Restore](assetId:///M:Microsoft.AnalysisServices.Server.Restore(System.String))|  
  
## See Also  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference](../Topic/Tabular%20Model%20Scripting%20Language%20\(TMSL\)%20Reference.md)   
 [Compatibility Level for Tabular models in Analysis Services](../../Topics\TopicNameNotContainA/Compatibility-Level-for-Tabular-models-in-Analysis-Services.md)   
 [Analysis Services Scripting Language &#40;ASSL for XMLA&#41;](../Topic/Analysis%20Services%20Scripting%20Language%20\(ASSL%20for%20XMLA\).md)   
 [PowerShell scripting in Analysis Services](../../Topics\TopicNameNotContainA/PowerShell-scripting-in-Analysis-Services.md)  
  
  