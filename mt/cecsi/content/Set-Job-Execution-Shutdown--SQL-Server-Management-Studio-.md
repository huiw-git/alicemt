---
title: Set Job Execution Shutdown (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Set Job Execution Shutdown (SQL Server Management Studio)
This topic describes how to set the time that [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent itself finishes in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
**In This Topic**  
  
-   **Before you begin:**  
  
    [Security](#Security)  
  
-   **To set a shutdown time for a SQL Server Agent job, using:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Before You Begin  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
By default, members of the **sysadmin** fixed server role can set the time that [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent itself finishes. Other users must be granted one of the following [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent fixed database roles in the **msdb** database:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To set job execution shutdown  
  
1.  In **Object Explorer,** , click the plus sign to expand the server where you want to set a job execution shutdown interval.  
  
2.  Right\-click **SQL Server Agent** and select **Properties**.  
  
3.  Under **Select a page**, select **Job System**.  
  
4.  Set the **Shutdown time\-out interval** in seconds to increase or decrease the shutdown time\-out interval. This determines how long [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent itself finishes.  
  
