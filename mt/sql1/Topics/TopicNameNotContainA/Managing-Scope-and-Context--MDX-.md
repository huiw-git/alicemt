---
title: "Managing Scope and Context (MDX)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
caps.latest.revision: 33
caps.handback.revision: 0
manager: mblythe
---
# Managing Scope and Context (MDX)
In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], a Multidimensional Expressions (MDX) script can apply to the entire cube, or to specific portions of the cube, at specific points within the execution of the script. The MDX script can take a layered approach to calculations within a cube through the use of calculation passes.  
  
> [!NOTE]  
>  For more information on how calculation passes can affect calculations, see [Understanding Pass Order and Solve Order (MDX)](../../Topics/TopicNameNotContainA/Understanding-Pass-Order-and-Solve-Order--MDX-.md).  
  
 To control the calculation pass, scope, and context within an MDX script, you specifically use the CACULATE statement, the **This** function, and the SCOPE statement.  
  
## Using the CALCULATE Statement  
 The CALCULATE statement populates each cell in the cube with aggregated data. For example, the default MDX script has a single CALCULATE statement at the beginning of the script.  
  
 For more information on the syntax of the CALCULATE statement, see [CALCULATE Statement (MDX)](assetId:///41e196a1-d49e-487b-a42a-73e5d441ed1b).  
  
> [!NOTE]  
>  If the script contains a SCOPE statement that contains a CALCULATE statement, MDX evaluates the CALCULATE statement within the context of the subcube defined by the SCOPE statement, not against the whole cube.  
  
## Using the This Function  
 The **This** function lets you retrieve the current subcube within an MDX script. You can use the **This** function to quickly set the value of cells within the current subcube to an MDX expression. You often use the **This** function in conjunction with the SCOPE statement to change the contents of a specific subcube during a specific calculation pass.  
  
> [!NOTE]  
>  If the script contains a SCOPE statement that contains a **This** function, MDX evaluates the **This** function within the context of the subcube defined by the SCOPE statement, not against the whole cube.  
  
### This Function Example  
 The following MDX script command example uses the **This** function to increase the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../Topics/TopicNameNotContainA/tokens/ssAWDWsp_md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension:  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 For more information on the syntax of the **This** function, see [This](assetId:///87acddee-ae54-49ee-8923-1b760606e8b7).  
  
## Using the SCOPE Statement  
 The SCOPE statement defines the current subcube that contains, and specifies the scope of, other MDX expressions and statements within an MDX script. MDX evaluates this other MDX expressions and statements, including the **This** function and the CALCULATE statement, within the context of the subcube.  
  
 A SCOPE statement is dynamic, but not iterative in nature. The statements contained within a SCOPE statement run once, but the subcube itself can be dynamically determined. For example, you have a cube named SampleCube. Against the SampleCube cube, you apply the following SCOPE statement to define a subcube the defines the context as the ALLMEMBERS within the Measures dimension:  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 The statements and expressions within this SCOPE statement run once.  
  
 Now, a business user runs the following MDX query that contains one measure, named ExistingMeasure, against the SampleCube cube:  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 The cellset returned from the query resembles the output shown in the following table.  
  
||[ExistingMeasure]|[NewMeasure]|  
|-|-------------------------|--------------------|  
|[Customer].[All]|2|2|  
  
 Looking at the returned cellset, notice how the ExistingMeasure value, included in the SCOPE statement within the MDX script, is dynamically updated after the measure NewMeasure was defined.  
  
 A SCOPE statement can be nested within another SCOPE statement. However, as the SCOPE statement is not iterative, the primary purpose for nesting SCOPE statements is to further subdivide a subcube for special treatment.  
  
### SCOPE Statement Example  
 The following MDX script example uses a SCOPE statement to sets the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../Topics/TopicNameNotContainA/tokens/ssAWDWsp_md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension. However, another SCOPE statement changes the subcube to include the Amount measure for the children of the 2002 calendar year. Finally, the Amount measure is then aggregated only for that subcube, leaving the aggregated values for the Amount measure in other calendar years unchanged.  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 For more information on the syntax of the SCOPE statement, see [SCOPE Statement (MDX)](assetId:///ceab459d-b601-4468-b3fc-4f5bb4a1805f).  
  
## See Also  
 [MDX Language Reference (MDX)](assetId:///8ceaedd3-7679-4300-83a5-4809243cdc5d)   
 [The Basic MDX Script (MDX)](../../Topics/TopicNameNotContainA/The-Basic-MDX-Script--MDX-.md)   
 [MDX Query Fundamentals (Analysis Services)](../../Topics/TopicNameNotContainA/MDX-Query-Fundamentals--Analysis-Services-.md)