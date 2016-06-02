---
title: Staging Stored Procedure (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
---
# Staging Stored Procedure (Master Data Services)
  When initiating the staging process from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you use one of three stored procedures.  
  
-   stg.udp\_\<name\>\_Leaf  
  
-   stg.udp\_\<name\>\_Consolidated  
  
-   stg.udp\_\<name\>\_Relationship  
  
 Where name is the name of the staging table that was specified when the entity was created.  
  
## Staging Process Stored Procedure Parameters  
 The following table lists the parameters of these stored procedures.  
  
|Parameter|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Required|The name of the version. This may or may not be case\-sensitive, depending on your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] collation setting.|  
|**LogFlag**<br /><br /> Required|Determines whether transactions are logged during the staging process. Possible values are:<br /><br /> **0**: Do not log transactions.<br /><br /> **1**: Log transactions.<br /><br /> <br /><br /> For more information about transactions, see [Transactions &#40;Master Data Services&#41;](../Topic/Transactions%20\(Master%20Data%20Services\).md).|  
|**BatchTag**<br /><br /> Required, except by web service|The **BatchTag** value as specified in the staging table.|  
|**Batch\_ID**<br /><br /> Required by web service only|The **Batch\_ID** value as specified in the staging table.|  
|**User Name**|Optional parameter|  
|**User ID**|Optional parameter|  
  
### Staging Process Stored Procedure Example  
 The following example shows how to start the staging process by using the staging stored procedure.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## See Also  
 [Validation Stored Procedure &#40;Master Data Services&#41;](../Topic/Validation%20Stored%20Procedure%20\(Master%20Data%20Services\).md)   
 [View Errors that Occur During Staging &#40;Master Data Services&#41;](../Topic/View%20Errors%20that%20Occur%20During%20Staging%20\(Master%20Data%20Services\).md)  
  
  