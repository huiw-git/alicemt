---
title: "Specify an Interval of Change Data"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
caps.latest.revision: 31
manager: jhubbard
---
# Specify an Interval of Change Data
In the control flow of an [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package that performs an incremental load of change data, the first task is to calculate the endpoints of the change interval. These endpoints are **datetime** values and will be stored in package variables for use later in the package.  
  
> [!NOTE]  
>  For a description of the overall process of designing the control flow, see [Change Data Capture (SSIS)](../../Topics/TopicNameNotContainA/Change-Data-Capture--SSIS-.md).  
  
## Set Up Package Variables for the Endpoints  
 Before configuring the Execute SQL task to calculate the endpoints, the package variables that will store the endpoints have to be defined.  
  
#### To set up package variables  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open a new [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] project.  
  
2.  In the **Variables** window, create the following variables:  
  
    1.  Create a variable with the **datetime** data type to hold the starting point for the interval.  
  
         This example uses the variable name, ExtractStartTime.  
  
    2.  Create another variable with the **datetime** data type to hold the ending point for the interval.  
  
         This example uses the variable name, ExtractEndTime.  
  
 If you calculate the endpoints in a master package that executes multiple child packages, you can use Parent Package Variable configurations to pass the values of these variables to each child package. For more information, see [Execute Package Task](../../Topics/TopicNameNotContainA/Execute-Package-Task.md) and [Use the Values of Variables and Parameters in a Child Package](../../Topics/TopicNameContainA/Use-the-Values-of-Variables-and-Parameters-in-a-Child-Package.md).  
  
## Calculate a Starting Point and an Ending Point for Change Data  
 After you set up the package variables for the interval endpoints, you can calculate the actual values for those endpoints and map those values to the corresponding package variables. Because those endpoints are **datetime** values, you will have to use functions that can calculate or work with **datetime** values. Both the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] expression language and Transact-SQL have functions that work with **datetime** values:  
  
 Functions in the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] expression language that work with **datetime** values  
 -   [DATEADD (SSIS Expression)](../../Topics/TopicNameNotContainA/DATEADD--SSIS-Expression-.md)  
  
-   [DATEDIFF (SSIS Expression)](../../Topics/TopicNameNotContainA/DATEDIFF--SSIS-Expression-.md)  
  
-   [DATEPART (SSIS Expression)](../../Topics/TopicNameNotContainA/DATEPART--SSIS-Expression-.md)  
  
-   [DAY (SSIS Expression)](../../Topics/TopicNameNotContainA/DAY--SSIS-Expression-.md)  
  
-   [GETDATE (SSIS Expression)](../../Topics/TopicNameNotContainA/GETDATE--SSIS-Expression-.md)  
  
-   [GETUTCDATE (SSIS Expression)](../../Topics/TopicNameNotContainA/GETUTCDATE--SSIS-Expression-.md)  
  
-   [MONTH (SSIS Expression)](../../Topics/TopicNameNotContainA/MONTH--SSIS-Expression-.md)  
  
-   [YEAR (SSIS Expression)](../../Topics/TopicNameNotContainA/YEAR--SSIS-Expression-.md)  
  
 Functions in Transact-SQL that work with **datetime** values  
 [Date and Time Data Types and Functions (Transact-SQL)](assetId:///83e378a2-6e89-4c80-bc4f-644958d9e0a9).  
  
 Before you use any one of these **datetime** functions to calculate the endpoints, you have to determine whether the interval is fixed and occurs on a regular schedule. Typically, you want to apply changes that have occurred in source tables to destination tables on a regular schedule. For example, you might want to apply those changes on an hourly, daily, or weekly basis.  
  
 After you understand whether your change interval is fixed or is more random, you can calculate the endpoints:  
  
-   **Calculating the starting date and time**. You use the ending date and time from the previous load as the current starting date and time. If you use a fixed interval for incremental loads, you can calculate this value by using the **datetime** functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] expression language. Otherwise, you might have to persist the endpoints between executions, and use an Execute SQL task or a Script task to load the previous endpoint.  
  
-   **Calculating the ending date and time**. If you use a fixed interval for incremental loads, calculate the current ending date and time as an offset from the starting date and time. Again, you can calculate this value by using the **datetime** functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] expression language.  
  
 In the following procedure, the change interval uses a fixed interval and assumes that the incremental load package is run daily without exception. Otherwise, change data for missed intervals would be lost. The starting point for the interval is midnight the day before yesterday, that is, between 24 and 48 hours ago. The ending point for the interval is midnight yesterday, that is, the previous night, between 0 and 24 hours ago.  
  
#### To calculate the starting point and ending point for the capture interval  
  
1.  On the **Control Flow** tab of [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, add an Execute SQL Task to the package.  
  
2.  Open the **Execute SQL Task Editor**, and on the **General** page of the editor, select the following options:  
  
    1.  For **ResultSet**, select **Single row**.  
  
    2.  Configure a valid connection to the source database.  
  
    3.  For **SQLSourceType**, select **Direct input**.  
  
    4.  For **SQLStatement**, enter the following SQL statement:  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  On the **Result Set** page of the **Execute SQL Task Editor**, map the ExtractStartTime result to the ExtractStartTime package variable, and map the ExtractEndTime result to the ExtractEndTime package variable.  
  
    > [!NOTE]  
    >  When you use an expression to set the value of an [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] variable, the expression is evaluated every time that that the value of the variable is accessed.  
  
## Next Step  
 After you calculate the starting point and ending point for a range of changes, the next step is to determine whether the change data is ready.  
  
 **Next topic:** [Determine Whether the Change Data Is Ready](../../Topics/TopicNameNotContainA/Determine-Whether-the-Change-Data-Is-Ready.md)  
  
## See Also  
 [Use Variables in Packages](../../Topics/TopicNameNotContainA/Use-Variables-in-Packages.md)   
 [Integration Services (SSIS) Expressions](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Expressions.md)   
 [Execute SQL Task](../../Topics/TopicNameNotContainA/Execute-SQL-Task.md)   
 [Script Task](../../Topics/TopicNameNotContainA/Script-Task.md)