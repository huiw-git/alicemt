---
title: "EXISTING Keyword (MDX)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 39
caps.handback.revision: 0
manager: mblythe
---
# EXISTING Keyword (MDX)
Forces a specified set to be evaluated within the current context.  
  
## Syntax  
  
```  
  
Existing Set_Expression  
```  
  
## Arguments  
 *Set_Expression*  
 A valid Multidimensional Expressions (MDX) set expression.  
  
## Remarks  
 By default, sets are evaluated within the context of the cube that contains the members of the set. The **Existing** keyword forces a specified set to be evaluated within the current context instead.  
  
## Example  
 The following example returns the count of the resellers whose sales have declined over the previous time period, based on user-selected State-Province member values evaluated using the **Aggregate** function. The [Hierarchize (MDX)](assetId:///e9795003-70e7-4b4c-9074-45b5b9b817fa) and [DrilldownLevel (MDX)](assetId:///47531ce5-1ac0-4aa9-a85c-824fb5d21e7c) functions are used to return values for declining sales for product categories in the Product dimension. The **Existing** keyword forces the the set in the **Filter** function to be evaluated in the current context - that is, for the Washington and Oregon members of the State-Province attribute hierarchy.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## See Also  
 [Count (Set) (MDX)](assetId:///22f530e9-f8e1-4608-affa-9a2bc0821591)   
 [AddCalculatedMembers (MDX)](assetId:///c676cf70-7c24-46ea-b88c-d4a389a71d48)   
 [Aggregate (MDX)](assetId:///9d5e0966-74d1-4cc8-b9f9-47e4dc65d165)   
 [Filter (MDX)](assetId:///f2df51c8-6acb-4300-b71c-2a480c9fbdf8)   
 [Properties (MDX)](assetId:///2d8442c5-30c4-4fd1-99ea-9845b6533e41)   
 [DrilldownLevel (MDX)](assetId:///47531ce5-1ac0-4aa9-a85c-824fb5d21e7c)   
 [Hierarchize (MDX)](assetId:///e9795003-70e7-4b4c-9074-45b5b9b817fa)   
 [MDX Function Reference (MDX)](assetId:///e363722a-3e5b-40a9-a0b5-399dd2d93f6d)