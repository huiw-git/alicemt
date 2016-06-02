---
title: Consolidated Member Staging Table (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 070681ed-be99-49ae-93bd-6402f2134ace
---
# Consolidated Member Staging Table (Master Data Services)
  Use the consolidated members staging table \(stg.name\_Consolidated\) in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database to create, update, deactivate, and delete consolidated members. You can also use it to update attribute values for consolidated members.  
  
##  <a name="TableColumns"></a> Table Columns  
 The following table explains what each of the fields in the Consolidated staging table are used for.  
  
|Column Name|Description|  
|-----------------|-----------------|  
|**ID**|An automatically assigned identifier. Do not enter a value in this field. If the batch has not been processed, this field is blank.|  
|**ImportType**<br /><br /> Required|Determines what to do when staged data matches data that already exists in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.<br /><br /> **0**: Create new members. Replace existing MDS data with staged data, but only if the staged data isn’t NULL. NULL values are ignored. To change an attribute value to NULL, use **~NULL~**.<br /><br /> **1**: Create new members only. Any updates to existing MDS data fail.<br /><br /> **2**: Create new members. Replace existing MDS data with staged data. If you import NULL values, they will overwrite existing MDS values.<br /><br /> **3**: Deactivate the member, based on the Code value. All attributes, hierarchy and collection memberships, and transactions are maintained but no longer available in the UI. If the member is used as a domain\-based attribute value of another member, the deactivation will fail.<br /><br /> **4**: Permanently delete the member, based on the Code value. All attributes, hierarchy and collection memberships, and transactions are permanently deleted. If the member is used as a domain\-based attribute value of another member, the deletion will fail.|  
|**ImportStatus\_ID**<br /><br /> Required|The status of the import process. Possible values are:<br /><br /> **0**, which you specify to indicate that the record is ready for staging.<br /><br /> **1**, which is automatically assigned and indicates that the staging process for the record has succeeded.<br /><br /> **2**, which is automatically assigned and indicates that the staging process for the record has failed.|  
|**Batch\_ID**<br /><br /> Required by web service only|An automatically assigned identifier that groups records for staging. All members in the batch are assigned this identifier, which is displayed in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface in the **ID** column.<br /><br /> If the batch has not been processed, this field is blank.|  
|**BatchTag**<br /><br /> Required, except by web service|A unique name for the batch, up to 50 characters.|  
|**HierarchyName**<br /><br /> Required|The explicit hierarchy name. Each consolidated member can belong to one hierarchy only.|  
|**ErrorCode**|Displays an error code. For all records with a **ImportStatus\_ID** of **2**, see [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md).|  
|**Code**<br /><br /> Required, except when codes are generated automatically for **ImportType1** or **2**; see [Automatic Code Creation &#40;Master Data Services&#41;](../Topic/Automatic%20Code%20Creation%20\(Master%20Data%20Services\).md) for more information|A unique code for the member.|  
|**Name**<br /><br /> Optional|A name for the member.|  
|**NewCode**|Use only if you are changing the member code.|  
|\<Attribute name\>|A column exists for each attribute in the entity. Use this with an **ImportType** of **0** or **2**. For free\-form attributes, specify the new text or string value for the attribute. For domain\-based attributes, specify the code for the member that will be the attribute. For link attributes, the URL must start with **http:\/\/**.<br /><br /> <br /><br /> Note: You cannot stage file attributes.|  
  
## See Also  
 [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [View Errors that Occur During Staging &#40;Master Data Services&#41;](../Topic/View%20Errors%20that%20Occur%20During%20Staging%20\(Master%20Data%20Services\).md)   
 [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md)  
  
  