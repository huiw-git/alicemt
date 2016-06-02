---
title: Plugin Algorithms
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
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
---
# Plugin Algorithms
  In addition to the algorithms that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides, there are many other algorithms that you can use for data mining. Accordingly, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides a mechanism for "plugging in" algorithms that are created by third parties. As long as the algorithms follow certain standards, you can use them within [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] just as you use the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] algorithms. Plugin algorithms have all the capabilities of algorithms that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides.  
  
 For a full description of the interfaces that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] uses to communicate with plugin algorithms, see the samples for creating a custom algorithm and custom model viewer that are published on [CodePlex](http://go.microsoft.com/fwlink/?LinkID=87843) Web site.  
  
## Algorithm Requirements  
 To plug an algorithm into [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], you must implement the following COM interfaces:  
  
 **IDMAlgorithm**  
 Implements an algorithm that produces models, and implements the prediction operations of the resulting models.  
  
 **IDMAlgorithmNavigation**  
 Enables browsers to access the content of the models.  
  
 **IDMPersist**  
 Enables the models that the algorithm trains to be saved and loaded by [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
 **IDMAlgorithmMetadata**  
 Describes the capabilities and input parameters of the algorithm.  
  
 **IDMAlgorithmFactory**  
 Creates instances of the objects that implement the algorithm interface, and provides [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] with access to the algorithm\-metadata interface.  
  
 [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] uses these COM interfaces to communicate with plugin algorithms. Although plugin algorithms that you use must support the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] OLE DB for Data Mining specification, they do not have to support all the data mining options in the specification. You can use the [MINING\_SERVICES](../Topic/DMSCHEMA_MINING_SERVICES%20Rowset.md) schema rowset to determine the capabilities of an algorithm. This schema rowset lists the data mining support options for each plugin algorithm provider.  
  
 You must register new algorithms before you use them with [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. To register an algorithm, include the following information in the .ini file of the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on which you want to include the algorithms:  
  
-   The algorithm name  
  
-   ProgID \(this is optional and will only be included for plugin algorithms\)  
  
-   A flag that indicates whether the algorithm is enabled or not  
  
 The following code sample illustrates how to register a new algorithm:  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [DMSCHEMA_MINING_SERVICES Rowset](../Topic/DMSCHEMA_MINING_SERVICES%20Rowset.md)  
  
  