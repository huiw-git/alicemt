---
title: Estimate the Size of a Nonclustered Index
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
---
# Estimate the Size of a Nonclustered Index
  Follow these steps to estimate the amount of space that is required to store a nonclustered index:  
  
1.  Calculate variables for use in steps 2 and 3.  
  
2.  Calculate the space used to store index information in the leaf level of the nonclustered index.  
  
3.  Calculate the space used to store index information in the non\-leaf levels of the nonclustered index.  
  
4.  Total the calculated values.  
  
## Step 1. Calculate Variables for Use in Steps 2 and 3  
 You can use the following steps to calculate variables that are used to estimate the amount of space that is required to store the upper levels of the index.  
  
1.  Specify the number of rows that will be present in the table:  
  
     ***Num\_Rows***  \= number of rows in the table  
  
2.  Specify the number of fixed\-length and variable\-length columns in the index key and calculate the space that is required for their storage:  
  
     The key columns of an index can include fixed\-length and variable\-length columns. To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row. The size of a column depends on the data type and length specification.  
  
     ***Num\_Key\_Cols***  \= total number of key columns \(fixed\-length and variable\-length\)  
  
     ***Fixed\_Key\_Size***  \= total byte size of all fixed\-length key columns  
  
     ***Num\_Variable\_Key\_Cols***  \= number of variable\-length key columns  
  
     ***Max\_Var\_Key\_Size***  \= maximum byte size of all variable\-length key columns  
  
3.  Account for the data row locator that is required if the index is nonunique:  
  
     If the nonclustered index is nonunique, the data row locator is combined with the nonclustered index key to produce a unique key value for every row.  
  
     If the nonclustered index is over a heap, the data row locator is the heap RID. This is a size of 8 bytes.  
  
     ***Num\_Key\_Cols***  \= ***Num\_Key\_Cols*** \+ 1  
  
     ***Num\_Variable\_Key\_Cols***  \= ***Num\_Variable\_Key\_Cols*** \+ 1  
  
     ***Max\_Var\_Key\_Size***  \= ***Max\_Var\_Key\_Size*** \+ 8  
  
     If the nonclustered index is over a clustered index, the data row locator is the clustering key. The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.  
  
     ***Num\_Key\_Cols***  \= ***Num\_Key\_Cols*** \+ number of clustering key columns not in the set of nonclustered index key columns \(\+ 1 if the clustered index is nonunique\)  
  
     ***Fixed\_Key\_Size***  \= ***Fixed\_Key\_Size*** \+ total byte size of fixed\-length clustering key columns not in the set of nonclustered index key columns  
  
     ***Num\_Variable\_Key\_Cols***  \= ***Num\_Variable\_Key\_Cols*** \+ number of variable\-length clustering key columns not in the set of nonclustered index key columns \(\+ 1 if the clustered index is nonunique\)  
  
     ***Max\_Var\_Key\_Size***  \= ***Max\_Var\_Key\_Size*** \+ maximum byte size of variable\-length clustering key columns not in the set of nonclustered index key columns \(\+ 4 if the clustered index is nonunique\)  
  
4.  Part of the row, known as the null bitmap, may be reserved to manage column nullability. Calculate its size:  
  
     If there are nullable columns in the index key, including any necessary clustering key columns as described in Step 1.3, part of the index row is reserved for the null bitmap.  
  
     ***Index\_Null\_Bitmap***  \= 2 \+ \(\(number of columns in the index row \+ 7\) \/ 8\)  
  
     Only the integer part of the previous expression should be used. Discard any remainder.  
  
     If there are no nullable key columns, set ***Index\_Null\_Bitmap*** to 0.  
  
5.  Calculate the variable length data size:  
  
     If there are variable\-length columns in the index key, including any necessary clustered index key columns, determine how much space is used to store the columns within the index row:  
  
     ***Variable\_Key\_Size***  \= 2 \+ \(***Num\_Variable\_Key\_Cols*** x 2\) \+ ***Max\_Var\_Key\_Size***  
  
     The bytes added to ***Max\_Var\_Key\_Size*** are for tracking each variable column.This formula assumes that all variable\-length columns are 100 percent full. If you anticipate that a smaller percentage of the variable\-length column storage space will be used, you can adjust the ***Max\_Var\_Key\_Size*** value by that percentage to yield a more accurate estimate of the overall table size.  
  
     If there are no variable\-length columns, set ***Variable\_Key\_Size*** to 0.  
  
6.  Calculate the index row size:  
  
     ***Index\_Row\_Size***  \= ***Fixed\_Key\_Size*** \+ ***Variable\_Key\_Size*** \+ ***Index\_Null\_Bitmap*** \+ 1 \(for row header overhead of an index row\) \+ 6 \(for the child page ID pointer\)  
  
7.  Calculate the number of index rows per page \(8096 free bytes per page\):  
  
     ***Index\_Rows\_Per\_Page***  \= 8096 \/ \(***Index\_Row\_Size*** \+ 2\)  
  
     Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row. The 2 in the formula is for the row's entry in the page's slot array.  
  
## Step 2. Calculate the Space Used to Store Index Information in the Leaf Level  
 You can use the following steps to estimate the amount of space that is required to store the leaf level of the index. You will need the values preserved from Step 1 to complete this step.  
  
1.  Specify the number of fixed\-length and variable\-length columns at the leaf level and calculate the space that is required for their storage:  
  
    > [!NOTE]  
    >  You can extend a nonclustered index by including nonkey columns in addition to the index key columns. These additional columns are only stored at the leaf level of the nonclustered index. For more information, see [Create Indexes with Included Columns](../../Topics\TopicNameNotContainA/Create-Indexes-with-Included-Columns.md).  
  
    > [!NOTE]  
    >  You can combine **varchar**, **nvarchar**, **varbinary**, or **sql\_variant** columns that cause the total defined table width to exceed 8,060 bytes. The length of each one of these columns must still fall within the limit of 8,000 bytes for a **varchar**, **varbinary**, or **sql\_variant** column, and 4,000 bytes for **nvarchar** columns. However, their combined widths may exceed the 8,060 byte limit in a table. This also applies to nonclustered index leaf rows that have included columns.  
  
     If the nonclustered index does not have any included columns, use the values from Step 1, including any modifications determined in Step 1.3:  
  
     ***Num\_Leaf\_Cols***  \= ***Num\_Key\_Cols***  
  
     ***Fixed\_Leaf\_Size***  \= ***Fixed\_Key\_Size***  
  
     ***Num\_Variable\_Leaf\_Cols***  \= ***Num\_Variable\_Key\_Cols***  
  
     ***Max\_Var\_Leaf\_Size***  \= ***Max\_Var\_Key\_Size***  
  
     If the nonclustered index does have included columns, add the appropriate values to the values from Step 1, including any modifications in Step 1.3. The size of a column depends on the data type and length specification. For more information, see [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md).  
  
     ***Num\_Leaf\_Cols***  \= ***Num\_Key\_Cols*** \+ number of included columns  
  
     ***Fixed\_Leaf\_Size***  \= ***Fixed\_Key\_Size*** \+ total byte size of fixed\-length included columns  
  
     ***Num\_Variable\_Leaf\_Cols***  \= ***Num\_Variable\_Key\_Cols*** \+ number of variable\-length included columns  
  
     ***Max\_Var\_Leaf\_Size***  \= ***Max\_Var\_Key\_Size*** \+ maximum byte size of variable\-length included columns  
  
2.  Account for the data row locator:  
  
     If the nonclustered index is nonunique, the overhead for the data row locator has already been considered in Step 1.3 and no additional modifications are required. Go to the next step.  
  
     If the nonclustered index is unique, the data row locator must be accounted for in all rows at the leaf level.  
  
     If the nonclustered index is over a heap, the data row locator is the heap RID \(size 8 bytes\).  
  
     ***Num\_Leaf\_Cols***  \= ***Num\_Leaf\_Cols*** \+ 1  
  
     ***Num\_Variable\_Leaf\_Cols***  \= ***Num\_Variable\_Leaf\_Cols*** \+ 1  
  
     ***Max\_Var\_Leaf\_Size***  \= ***Max\_Var\_Leaf\_Size*** \+ 8  
  
     If the nonclustered index is over a clustered index, the data row locator is the clustering key. The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.  
  
     ***Num\_Leaf\_Cols***  \= ***Num\_Leaf\_Cols*** \+ number of clustering key columns not in the set of nonclustered index key columns \(\+ 1 if the clustered index is nonunique\)  
  
     ***Fixed\_Leaf\_Size***  \= ***Fixed\_Leaf\_Size*** \+ number of fixed\-length clustering key columns not in the set of nonclustered index key columns  
  
     ***Num\_Variable\_Leaf\_Cols***  \= ***Num\_Variable\_Leaf\_Cols*** \+ number of variable\-length clustering key columns not in the set of nonclustered index key columns \(\+ 1 if the clustered index is nonunique\)  
  
     ***Max\_Var\_Leaf\_Size***  \= ***Max\_Var\_Leaf\_Size*** \+ size in bytes of the variable\-length clustering key columns not in the set of nonclustered index key columns \(\+ 4 if the clustered index is nonunique\)  
  
3.  Calculate the null bitmap size:  
  
     ***Leaf\_Null\_Bitmap***  \= 2 \+ \(\(***Num\_Leaf\_Cols*** \+ 7\) \/ 8\)  
  
     Only the integer part of the previous expression should be used. Discard any remainder.  
  
4.  Calculate the variable length data size:  
  
     If there are variable\-length columns in the index key, including any necessary clustering key columns as described previously in Step 2.2, determine how much space is used to store the columns within the index row:  
  
     ***Variable\_Leaf\_Size***  \= 2 \+ \(***Num\_Variable\_Leaf\_Cols*** x 2\) \+ ***Max\_Var\_Leaf\_Size***  
  
     The bytes added to ***Max\_Var\_Key\_Size*** are for tracking each variable column.This formula assumes that all variable\-length columns are 100 percent full. If you anticipate that a smaller percentage of the variable\-length column storage space will be used, you can adjust the ***Max\_Var\_Leaf\_Size*** value by that percentage to yield a more accurate estimate of the overall table size.  
  
     If there are no variable\-length columns, set ***Variable\_Leaf\_Size*** to 0.  
  
5.  Calculate the index row size:  
  
     ***Leaf\_Row\_Size***  \= ***Fixed\_Leaf\_Size*** \+ ***Variable\_Leaf\_Size*** \+ ***Leaf\_Null\_Bitmap*** \+ 1 \(for row header overhead of an index row\) \+ 6 \(for the child page ID pointer\)  
  
6.  Calculate the number of index rows per page \(8096 free bytes per page\):  
  
     ***Leaf\_Rows\_Per\_Page***  \= 8096 \/ \(***Leaf\_Row\_Size*** \+ 2\)  
  
     Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row. The 2 in the formula is for the row's entry in the page's slot array.  
  
7.  Calculate the number of reserved free rows per page, based on the [fill factor](../../Topics\TopicNameNotContainA/Specify-Fill-Factor-for-an-Index.md) specified:  
  
     ***Free\_Rows\_Per\_Page***  \= 8096 x \(\(100 \- ***Fill\_Factor***\) \/ 100\) \/ \(***Leaf\_Row\_Size*** \+ 2\)  
  
     The fill factor used in the calculation is an integer value instead of a percentage. Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row. As the fill factor grows, more data will be stored on each page and there will be fewer pages. The 2 in the formula is for the row's entry in the page's slot array.  
  
8.  Calculate the number of pages required to store all the rows:  
  
     ***Num\_Leaf\_Pages***  \= ***Num\_Rows*** \/ \(***Leaf\_Rows\_Per\_Page*** \- ***Free\_Rows\_Per\_Page***\)  
  
     The number of pages estimated should be rounded up to the nearest whole page.  
  
9. Calculate the size of the index \(8192 total bytes per page\):  
  
     ***Leaf\_Space\_Used***  \= 8192 x ***Num\_Leaf\_Pages***  
  
## Step 3. Calculate the Space Used to Store Index Information in the Non\-leaf Levels  
 Follow these steps to estimate the amount of space that is required to store the intermediate and root levels of the index. You will need the values preserved from steps 2 and 3 to complete this step.  
  
1.  Calculate the number of non\-leaf levels in the index:  
  
     ***Non\-leaf Levels***  \= 1 \+ log\( Index\_Rows\_Per\_Page\) \(***Num\_Leaf\_Pages*** \/ ***Index\_Rows\_Per\_Page***\)  
  
     Round this value up to the nearest whole number. This value does not include the leaf level of the nonclustered index.  
  
2.  Calculate the number of non\-leaf pages in the index:  
  
     ***Num\_Index\_Pages***  \= ∑Level \(***Num\_Leaf\_Pages\/Index\_Rows\_Per\_Page***^Level\)where 1 \<\= Level \<\= ***Levels***  
  
     Round each summand up to the nearest whole number. As a simple example, consider an index where ***Num\_Leaf\_Pages*** \= 1000 and ***Index\_Rows\_Per\_Page*** \= 25. The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page. This means that 40 pages are required to store those 1000 index rows. The next level of the index has to store 40 rows. This means that it requires 2 pages. The final level of the index has to store 2 rows. This means that it requires 1 page. This yields 43 non\-leaf index pages. When these numbers are used in the previous formulas, the result is as follows:  
  
     ***Non\-leaf\_Levels***  \= 1 \+ log\(25\) \(1000 \/ 25\) \= 3  
  
     ***Num\_Index\_Pages*** \= 1000\/\(25^3\)\+ 1000\/\(25^2\) \+ 1000\/\(25^1\) \= 1 \+ 2 \+ 40 \= 43, which is the number of pages described in the example.  
  
3.  Calculate the size of the index \(8192 total bytes per page\):  
  
     ***Index\_Space\_Used***  \= 8192 x ***Num\_Index\_Pages***  
  
## Step 4. Total the Calculated Values  
 Total the values obtained from the previous two steps:  
  
 Nonclustered index size \(bytes\) \= ***Leaf\_Space\_Used*** \+ ***Index\_Space\_used***  
  
 This calculation does not consider the following:  
  
-   Partitioning  
  
     The space overhead from partitioning is minimal, but complex to calculate. It is not important to include.  
  
-   Allocation pages  
  
     There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.  
  
-   Large object \(LOB\) values  
  
     The algorithm to determine exactly how much space will be used to store the LOB data types **varchar\(max\)**, **varbinary\(max\)**, **nvarchar\(max\)**, **text**, **ntext**, **xml**, and **image** values is complex. It is sufficient to just add the average size of the LOB values expected, multiply by ***Num\_Rows***, and add that to the total nonclustered index size.  
  
-   Compression  
  
     You cannot pre\-calculate the size of a compressed index.  
  
-   Sparse columns  
  
     For information about the space requirements of sparse columns, see [Use Sparse Columns](../../Topics\TopicNameNotContainA/Use-Sparse-Columns.md).  
  
## See Also  
 [Clustered and Nonclustered Indexes Described](../../Topics\TopicNameNotContainA/Clustered-and-Nonclustered-Indexes-Described.md)   
 [Create Nonclustered Indexes](../../Topics\TopicNameNotContainA/Create-Nonclustered-Indexes.md)   
 [Create Clustered Indexes](../../Topics\TopicNameNotContainA/Create-Clustered-Indexes.md)   
 [Estimate the Size of a Table](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Table.md)   
 [Estimate the Size of a Clustered Index](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Clustered-Index.md)   
 [Estimate the Size of a Heap](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Heap.md)   
 [Estimate the Size of a Database](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Database.md)  
  
  