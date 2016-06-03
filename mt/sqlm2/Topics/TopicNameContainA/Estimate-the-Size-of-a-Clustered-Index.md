---
title: Estimate the Size of a Clustered Index
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
---
# Estimate the Size of a Clustered Index
  You can use the following steps to estimate the amount of space that is required to store data in a clustered index:  
  
1.  Calculate the space used to store data in the leaf level of the clustered index.  
  
2.  Calculate the space used to store index information for the clustered index.  
  
3.  Total the calculated values.  
  
## Step 1. Calculate the Space Used to Store Data in the Leaf Level  
  
1.  Specify the number of rows that will be present in the table:  
  
     ***Num\_Rows***  \= number of rows in the table  
  
2.  Specify the number of fixed\-length and variable\-length columns and calculate the space that is required for their storage:  
  
     Calculate the space that each of these groups of columns occupies within the data row. The size of a column depends on the data type and length specification.  
  
     ***Num\_Cols***  \= total number of columns \(fixed\-length and variable\-length\)  
  
     ***Fixed\_Data\_Size***  \= total byte size of all fixed\-length columns  
  
     ***Num\_Variable\_Cols***  \= number of variable\-length columns  
  
     ***Max\_Var\_Size***  \= maximum byte size of all variable\-length columns  
  
3.  If the clustered index is nonunique, account for the *uniqueifier* column:  
  
     The uniqueifier is a nullable, variable\-length column. It will be nonnull and 4 bytes in size in rows that have nonunique key values. This value is part of the index key and is required to make sure that every row has a unique key value.  
  
     ***Num\_Cols***  \= ***Num\_Cols*** \+ 1  
  
     ***Num\_Variable\_Cols***  \= ***Num\_Variable\_Cols*** \+ 1  
  
     ***Max\_Var\_Size***  \= ***Max\_Var\_Size*** \+ 4  
  
     These modifications assume that all values will be nonunique.  
  
4.  Part of the row, known as the null bitmap, is reserved to manage column nullability. Calculate its size:  
  
     ***Null\_Bitmap***  \= 2 \+ \(\(***Num\_Cols*** \+ 7\) \/ 8\)  
  
     Only the integer part of the previous expression should be used; discard any remainder.  
  
5.  Calculate the variable\-length data size:  
  
     If there are variable\-length columns in the table, determine how much space is used to store the columns within the row:  
  
     ***Variable\_Data\_Size***  \= 2 \+ \(***Num\_Variable\_Cols*** x 2\) \+ ***Max\_Var\_Size***  
  
     The bytes added to ***Max\_Var\_Size*** are for tracking each variable column. This formula assumes that all variable\-length columns are 100 percent full. If you anticipate that a smaller percentage of the variable\-length column storage space will be used, you can adjust the ***Max\_Var\_Size*** value by that percentage to yield a more accurate estimate of the overall table size.  
  
    > [!NOTE]  
    >  You can combine **varchar**, **nvarchar**, **varbinary**, or **sql\_variant** columns that cause the total defined table width to exceed 8,060 bytes. The length of each one of these columns must still fall within the limit of 8,000 bytes for a **varchar**, **varbinary**, or **sql\_variant** column, and 4,000 bytes for **nvarchar** columns. However, their combined widths may exceed the 8,060 byte limit in a table.  
  
     If there are no variable\-length columns, set ***Variable\_Data\_Size*** to 0.  
  
6.  Calculate the total row size:  
  
     ***Row\_Size***  \= ***Fixed\_Data\_Size*** \+ ***Variable\_Data\_Size*** \+ ***Null\_Bitmap*** \+ 4  
  
     The value 4 is the row header overhead of a data row.  
  
7.  Calculate the number of rows per page \(8096 free bytes per page\):  
  
     ***Rows\_Per\_Page***  \= 8096 \/ \(***Row\_Size*** \+ 2\)  
  
     Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row. The value 2 in the formula is for the row's entry in the slot array of the page.  
  
8.  Calculate the number of reserved free rows per page, based on the [fill factor](../../Topics\TopicNameNotContainA/Specify-Fill-Factor-for-an-Index.md) specified:  
  
     ***Free\_Rows\_Per\_Page***  \= 8096 x \(\(100 \- ***Fill\_Factor***\) \/ 100\) \/ \(***Row\_Size*** \+ 2\)  
  
     The fill factor used in the calculation is an integer value instead of a percentage. Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row. As the fill factor grows, more data will be stored on each page and there will be fewer pages. The value 2 in the formula is for the row's entry in the slot array of the page.  
  
9. Calculate the number of pages required to store all the rows:  
  
     ***Num\_Leaf\_Pages***  \= ***Num\_Rows*** \/ \(***Rows\_Per\_Page*** \- ***Free\_Rows\_Per\_Page***\)  
  
     The number of pages estimated should be rounded up to the nearest whole page.  
  
10. Calculate the amount of space that is required to store the data in the leaf level \(8192 total bytes per page\):  
  
     ***Leaf\_space\_used***  \= 8192 x ***Num\_Leaf\_Pages***  
  
## Step 2. Calculate the Space Used to Store Index Information  
 You can use the following steps to estimate the amount of space that is required to store the upper levels of the index:  
  
1.  Specify the number of fixed\-length and variable\-length columns in the index key and calculate the space that is required for their storage:  
  
     The key columns of an index can include fixed\-length and variable\-length columns. To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row. The size of a column depends on the data type and length specification.  
  
     ***Num\_Key\_Cols***  \= total number of key columns \(fixed\-length and variable\-length\)  
  
     ***Fixed\_Key\_Size***  \= total byte size of all fixed\-length key columns  
  
     ***Num\_Variable\_Key\_Cols***  \= number of variable\-length key columns  
  
     ***Max\_Var\_Key\_Size***  \= maximum byte size of all variable\-length key columns  
  
2.  Account for any uniqueifier needed if the index is nonunique:  
  
     The uniqueifier is a nullable, variable\-length column. It will be nonnull and 4 bytes in size in rows that have nonunique index key values. This value is part of the index key and is required to make sure that every row has a unique key value.  
  
     ***Num\_Key\_Cols***  \= ***Num\_Key\_Cols*** \+ 1  
  
     ***Num\_Variable\_Key\_Cols***  \= ***Num\_Variable\_Key\_Cols*** \+ 1  
  
     ***Max\_Var\_Key\_Size***  \= ***Max\_Var\_Key\_Size*** \+ 4  
  
     These modifications assume that all values will be nonunique.  
  
3.  Calculate the null bitmap size:  
  
     If there are nullable columns in the index key, part of the index row is reserved for the null bitmap. Calculate its size:  
  
     ***Index\_Null\_Bitmap***  \= 2 \+ \(\(number of columns in the index row \+ 7\) \/ 8\)  
  
     Only the integer part of the previous expression should be used. Discard any remainder.  
  
     If there are no nullable key columns, set ***Index\_Null\_Bitmap*** to 0.  
  
4.  Calculate the variable\-length data size:  
  
     If there are variable\-length columns in the index, determine how much space is used to store the columns within the index row:  
  
     ***Variable\_Key\_Size***  \= 2 \+ \(***Num\_Variable\_Key\_Cols*** x 2\) \+ ***Max\_Var\_Key\_Size***  
  
     The bytes added to ***Max\_Var\_Key\_Size*** are for tracking each variable\-length column. This formula assumes that all variable\-length columns are 100 percent full. If you anticipate that a smaller percentage of the variable\-length column storage space will be used, you can adjust the ***Max\_Var\_Key\_Size*** value by that percentage to yield a more accurate estimate of the overall table size.  
  
     If there are no variable\-length columns, set ***Variable\_Key\_Size*** to 0.  
  
5.  Calculate the index row size:  
  
     ***Index\_Row\_Size***  \= ***Fixed\_Key\_Size*** \+ ***Variable\_Key\_Size*** \+ ***Index\_Null\_Bitmap*** \+ 1 \(for row header overhead of an index row\) \+ 6 \(for the child page ID pointer\)  
  
6.  Calculate the number of index rows per page \(8096 free bytes per page\):  
  
     ***Index\_Rows\_Per\_Page***  \= 8096 \/ \(***Index\_Row\_Size*** \+ 2\)  
  
     Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row. The 2 in the formula is for the row's entry in the page's slot array.  
  
7.  Calculate the number of levels in the index:  
  
     ***Non\-leaf\_Levels***  \= 1 \+ log \(Index\_Rows\_Per\_Page\) \(***Num\_Leaf\_Pages*** \/ ***Index\_Rows\_Per\_Page***\)  
  
     Round this value up to the nearest whole number. This value does not include the leaf level of the clustered index.  
  
8.  Calculate the number of non\-leaf pages in the index:  
  
     ***Num\_Index\_Pages \=*** ∑Level ***\(Num\_Leaf\_Pages \/ \(Index\_Rows\_Per\_Page***^Level***\)\)***  
  
     where 1 \<\= Level \<\= ***Non\-leaf\_Levels***  
  
     Round each summand up to the nearest whole number. As a simple example, consider an index where ***Num\_Leaf\_Pages*** \= 1000 and ***Index\_Rows\_Per\_Page*** \= 25. The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page. This means that 40 pages are required to store those 1000 index rows. The next level of the index has to store 40 rows. This means it requires 2 pages. The final level of the index has to store 2 rows. This means it requires 1 page. This gives 43 non\-leaf index pages. When these numbers are used in the previous formulas, the outcome is as follows:  
  
     ***Non\-leaf\_Levels***  \= 1 \+ log\(25\) \(1000 \/ 25\) \= 3  
  
     ***Num\_Index\_Pages*** \= 1000\/\(25^3\)\+ 1000\/\(25^2\) \+ 1000\/\(25^1\) \= 1 \+ 2 \+ 40 \= 43, which is the number of pages described in the example.  
  
9. Calculate the size of the index \(8192 total bytes per page\):  
  
     ***Index\_Space\_Used***  \= 8192 x ***Num\_Index\_Pages***  
  
## Step 3. Total the Calculated Values  
 Total the values obtained from the previous two steps:  
  
 Clustered index size \(bytes\) \= ***Leaf\_Space\_Used*** \+ ***Index\_Space\_used***  
  
 This calculation does not consider the following:  
  
-   Partitioning  
  
     The space overhead from partitioning is minimal, but complex to calculate. It is not important to include.  
  
-   Allocation pages  
  
     There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.  
  
-   Large object \(LOB\) values  
  
     The algorithm to determine exactly how much space will be used to store the LOB data types **varchar\(max\)**, **varbinary\(max\)**, **nvarchar\(max\)**, **text**, **ntext**, **xml**, and **image** values is complex. It is sufficient to just add the average size of the LOB values that are expected, multiply by ***Num\_Rows***, and add that to the total clustered index size.  
  
-   Compression  
  
     You cannot pre\-calculate the size of a compressed index.  
  
-   Sparse columns  
  
     For information about the space requirements of sparse columns, see [Use Sparse Columns](../../Topics\TopicNameNotContainA/Use-Sparse-Columns.md).  
  
## See Also  
 [Clustered and Nonclustered Indexes Described](../../Topics\TopicNameNotContainA/Clustered-and-Nonclustered-Indexes-Described.md)   
 [Estimate the Size of a Table](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Table.md)   
 [Create Clustered Indexes](../../Topics\TopicNameNotContainA/Create-Clustered-Indexes.md)   
 [Create Nonclustered Indexes](../../Topics\TopicNameNotContainA/Create-Nonclustered-Indexes.md)   
 [Estimate the Size of a Nonclustered Index](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Nonclustered-Index.md)   
 [Estimate the Size of a Heap](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Heap.md)   
 [Estimate the Size of a Database](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Database.md)  
  
  