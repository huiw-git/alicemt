---
title: Error Configuration (Mining Structure Dialog Box) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
---
# Error Configuration (Mining Structure Dialog Box) (Analysis Services - Multidimensional Data)
  Use the **Error Configuration** page of the **Mining Structure Properties** dialog box in **SQL Server Management Studio** to set the error configuration properties of a mining structure in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database.  
  
## Options  
 **Use default error configuration**  
 Select to use the default error configuration for objects in the processing operation.  
  
 **Key error action**  
 Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:  
  
-   **Convert to unknown** aggregates the information for the record into the unknown member.  
  
-   **Discard record** excludes the information for the record from being processed with the object.  
  
 **Ignore errors count**  
 Click to ignore any errors that occur when processing.  
  
 **Stop on error**  
 Click to stop processing when errors occur. This option enables the **Number of errors** and the **On error action** options.  
  
 **Number of errors**  
 Type the number of errors that are ignored before processing stops.  
  
 **On error action**  
 Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:  
  
-   **Stop processing** ends the processing operation.  
  
-   **Stop logging** stops logging errors, but continues the processing operation.  
  
 **Key not found**  
 Specify one of the following actions to be taken when a key is not found when an object is processed:  
  
-   **Ignore error** ignores the error  
  
-   **Report and continue** reports the error and continues the processing operation  
  
-   **Report and stop** reports the error and stops the processing operation.  
  
 **Duplicate key**  
 Specify one of the following actions to be taken if a duplicate key is found when an object is processed:  
  
-   **Ignore error** ignores the error  
  
-   **Report and continue** reports the error and continues the processing operation  
  
-   **Report and stop** reports the error and stops the processing operation.  
  
 **Null key converted to unknown**  
 Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed.  
  
-   **Ignore error** ignores the error  
  
-   **Report and continue** reports the error and continues the processing operation  
  
-   **Report and stop** reports the error and stops the processing operation.  
  
 **Null key not allowed**  
 Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed.  
  
-   **Ignore error** ignores the error  
  
-   **Report and continue** reports the error and continues the processing operation  
  
-   **Report and stop** reports the error and stops the processing operation.  
  
 **Error log path**  
 Type the full path and file name for the error log file.  
  
## See Also  
 [Mining Structure Properties Dialog &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structure%20Properties%20Dialog%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [General &#40;Mining Structure Dialog Box&#41; &#40;Analysis Services - Data Mining&#41;](../Topic/General%20\(Mining%20Structure%20Dialog%20Box\)%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
  