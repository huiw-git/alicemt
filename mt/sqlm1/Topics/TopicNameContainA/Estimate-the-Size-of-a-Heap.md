---
title: Estimate the Size of a Heap
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81fd5ec9-ce0f-4c2c-8ba0-6c483cea6c75
---
# Estimate the Size of a Heap
  You can use the following steps to estimate the amount of space that is required to store data in a heap:  
  
1.  Specify the number of rows that will be present in the table:  
  
     ***Num\_Rows***  \= number of rows in the table  
  
2.  Specify the number of fixed\-length and variable\-length columns and calculate the space that is required for their storage:  
  
     Calculate the space that each of these groups of columns occupies within the data row. The size of a column depends on the data type and length specification.  
  
     ***Num\_Cols***  \= total number of columns \(fixed\-length and variable\-length\)  
  
     ***Fixed\_Data\_Size***  \= total byte size of all fixed\-length columns  
  
     ***Num\_Variable\_Cols***  \= number of variable\-length columns  
  
     ***Max\_Var\_Size***  \= maximum total byte size of all variable\-length columns  
  
3.  Part of the row, known as the null bitmap, is reserved to manage column nullability. Calculate its size:  
  
     ***Null\_Bitmap***  \= 2 \+ \(\(***Num\_Cols*** \+ 7\) \/ 8\)  
  
     Only the integer part of this expression should be used. Discard any remainder.  
  
4.  Calculate the variable\-length data size:  
  
     If there are variable\-length columns in the table, determine how much space is used to store the columns within the row:  
  
     ***Variable\_Data\_Size***  \= 2 \+ \(***Num\_Variable\_Cols*** x 2\) \+ ***Max\_Var\_Size***  
  
     The bytes added to ***Max\_Var\_Size*** are for tracking each variable\-length column. This formula assumes that all variable\-length columns are 100 percent full. If you anticipate that a smaller percentage of the variable\-length column storage space will be used, you can adjust the ***Max\_Var\_Size*** value by that percentage to yield a more accurate estimate of the overall table size.  
  
    > [!NOTE]  
    >  You can combine **varchar**, **nvarchar**, **varbinary**, or **sql\_variant** columns that cause the total defined table width to exceed 8,060 bytes. The length of each one of these columns must still fall within the limit of 8,000 bytes for a **varchar**, **nvarchar,****varbinary**, or **sql\_variant** column. However, their combined widths may exceed the 8,060 byte limit in a table.  
  
     If there are no variable\-length columns, set ***Variable\_Data\_Size*** to 0.  
  
5.  Calculate the total row size:  
  
     ***Row\_Size***  \= ***Fixed\_Data\_Size*** \+ ***Variable\_Data\_Size*** \+ ***Null\_Bitmap*** \+ 4  
  
     The value 4 in the formula is the row header overhead of the data row.  
  
6.  Calculate the number of rows per page \(8096 free bytes per page\):  
  
     ***Rows\_Per\_Page***  \= 8096 \/ \(***Row\_Size*** \+ 2\)  
  
     Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row. The value 2 in the formula is for the row's entry in the slot array of the page.  
  
7.  Calculate the number of pages required to store all the rows:  
  
     ***Num\_Pages***  \= ***Num\_Rows*** \/ ***Rows\_Per\_Page***  
  
     The number of pages estimated should be rounded up to the nearest whole page.  
  
8.  Calculate the amount of space that is required to store the data in the heap \(8192 total bytes per page\):  
  
     Heap size \(bytes\) \= 8192 x ***Num\_Pages***  
  
 This calculation does not consider the following:  
  
-   Partitioning  
  
     The space overhead from partitioning is minimal, but complex to calculate. It is not important to include.  
  
-   Allocation pages  
  
     There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.  
  
-   Large object \(LOB\) values  
  
     The algorithm to determine exactly how much space will be used to store the LOB data types **varchar\(max\)**, **varbinary\(max\)**, **nvarchar\(max\)**, **text**, **ntextxml**, and **image** values is complex. It is sufficient to just add the average size of the LOB values that are expected and add that to the total heap size.  
  
-   Compression  
  
     You cannot pre\-calculate the size of a compressed heap.  
  
-   Sparse columns  
  
     For information about the space requirements of sparse columns, see [Use Sparse Columns](../../Topics\TopicNameNotContainA/Use-Sparse-Columns.md).  
  
## See Also  
 [Heaps &#40;Tables without Clustered Indexes&#41;](../Topic/Heaps%20\(Tables%20without%20Clustered%20Indexes\).md)   
 [Clustered and Nonclustered Indexes Described](../../Topics\TopicNameNotContainA/Clustered-and-Nonclustered-Indexes-Described.md)   
 [Create Clustered Indexes](../../Topics\TopicNameNotContainA/Create-Clustered-Indexes.md)   
 [Create Nonclustered Indexes](../../Topics\TopicNameNotContainA/Create-Nonclustered-Indexes.md)   
 [Estimate the Size of a Table](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Table.md)   
 [Estimate the Size of a Clustered Index](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Clustered-Index.md)   
 [Estimate the Size of a Nonclustered Index](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Nonclustered-Index.md)   
 [Estimate the Size of a Database](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Database.md)  
  
  