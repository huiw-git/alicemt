---
title: Delete a Table (SSAS Tabular)
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
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
---
# Delete a Table (SSAS Tabular)
  In the model designer, you can delete tables in your model workspace database that you no longer need. Deleting a table does not affect the original source data, only the data that you imported and were working with. You cannot undo the deletion of a table.  
  
### To delete a table  
  
-   Right\-click the tab at the bottom of the model designer for the table that you want to delete, and then click **Delete**.  
  
## Considerations when Deleting Tables  
  
-   When you delete a table, the entire tab that the table was on is deleted.  
  
-   If any measures were associated with that table, the definition of the measure will also be deleted.  
  
-   If you created any calculated columns using that table, columns in that table are also deleted; any calculated columns in other tables that use columns from the deleted table will display an error.  
  
## See Also  
 [Tables and Columns &#40;SSAS Tabular&#41;](../Topic/Tables%20and%20Columns%20\(SSAS%20Tabular\).md)  
  
  