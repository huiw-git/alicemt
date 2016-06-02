---
title: Union All Transformation Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
---
# Union All Transformation Editor
  Use the **Union All Transformation Editor** dialog box to merge several input rowsets into a single output rowset. By including the Union All transformation in a data flow, you can merge data from multiple data flows, create complex datasets by nesting Union All transformations, and re\-merge rows after you correct errors in the data.  
  
 To learn more about the Union All transformation, see [Union All Transformation](../../Topics\TopicNameNotContainA/Union-All-Transformation.md).  
  
## Options  
 **Output Column Name**  
 Type an alias for each column. The default is the name of the input column from the first \(reference\) input; however, you can choose any unique, descriptive name.  
  
 **Union All Input 1**  
 Select from the list of available input columns in the first \(reference\) input. The metadata of mapped columns must match.  
  
 **Union All Input n**  
 Select from the list of available input columns in the second and additional inputs. The metadata of mapped columns must match.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Merge Data by Using the Union All Transformation](../../Topics\TopicNameNotContainA/Merge-Data-by-Using-the-Union-All-Transformation.md)   
 [Merge Transformation](../../Topics\TopicNameNotContainA/Merge-Transformation.md)   
 [Merge Join Transformation](../../Topics\TopicNameNotContainA/Merge-Join-Transformation.md)  
  
  