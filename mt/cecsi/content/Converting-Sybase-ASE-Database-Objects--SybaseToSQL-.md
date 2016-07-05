---
title: Converting Sybase ASE Database Objects (SybaseToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
---
# Converting Sybase ASE Database Objects (SybaseToSQL)
After you have connected to Sybase Adaptive Server Enterprise (ASE), connected to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure, and set project and data mapping options, you can convert Sybase Adaptive Server Enterprise (ASE) database objects to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure database objects.  
  
## The Conversion Process  
Converting database objects takes the object definitions from ASE, converts them to similar [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure objects, and then loads this information into the SSMA metadata. It does not load the information into the instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure. You can then view the objects and their properties by using the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure Metadata Explorer.  
  
During the conversion, SSMA prints output messages to the Output pane and error messages to the Error List pane. Use the output and error information to determine whether you have to modify your ASE databases or your conversion process to obtain the desired conversion results.  
  
## Setting Conversion Options  
Before converting objects, review the project conversion options in the **Project Settings** dialog box. By using this dialog box, you can set how SSMA converts functions and global variables. For more information, see [Project Settings &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../content/Project-Settings--Conversion---SybaseToSQL-.md).  
  
## Converting ASE Database Objects  
To convert ASE database objects, you first select the objects that you want to convert, and then have SSMA perform the conversion. To view output messages during the conversion, on the **View** menu, select **Output**.  
  
**To convert ASE objects to SQL Server or SQL Azure syntax**  
  
1.  In Sybase Metadata Explorer, expand the ASE server, and then expand **Databases**.  
  
2.  Select objects to convert:  
  
    -   To convert all databases, select the check box next to **Databases**.  
  
    -   To convert or omit a database, select or clear the check box next to the database name.  
  
    -   To convert or omit individual schemas, expand the database, expand **Schemas**, and then select or clear the check box next to the schema.  
  
    -   To convert or omit a category of objects, expand the schema, and then select or clear the check box next to the category.  
  
    -   To convert or omit individual objects, expand the category folder, and then select or clear the check box next to the object.  
  
3.  To convert all selected objects, right\-click **Databases** and select **Convert Schema**.  
  
    You can also convert individual objects or categories of objects by right\-clicking the object or its containing folder, and then selecting **Convert Schema**.  
  
> [!NOTE]  
> Some of the Sybase system functions do not exactly match the equivalent SQL Server system functions in behavior. To emulate the Sybase ASE behavior, SSMA generates User Defined functions in the converted SQL Server database under a schema called ‘s2ss’. Depending on the Project Settings, some of the SQL Server system functions are replaced with these emulated functions. SSMA creates the following user\-defined functions:  
  
||||  
|-|-|-|  
|**char\_length\_nvarchar**|**index\_colorder**|**ssma\_datepart**|  
|**char\_length\_varchar**|**inttohex**|**substring\_nvarchar**|  
|**charindex\_nvarchar**|**ssma\_datediff**|**substring\_varbinary**|  
|**charindex\_varchar**|**hextoint**|**substring\_varchar**|  
|**ulowsurr**|**to\_unichar**|**ssma\_current\_time**|  
|**uhighsurr**|||  
  
## Objects not supported in SQL Azure  
The following T\-SQL keywords are used by SSMA for Sybase during conversion to regular SQL Server but these keywords are not supported by SQL Azure T\-SQL syntax:  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE\/ALTER\/DROP DEFAULT|CREATE\/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|GRANT\/REVOKE\/DENY ALL|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## Viewing Conversion Problems  
Some ASE objects might not convert. You can determine the conversion success rates by viewing the summary conversion report.  
  
**To view a summary report**  
  
1.  In Sybase Metadata Explorer, select **Databases**.  
  
2.  In the right pane, select the **Report** tab.  
  
    This report shows the summary assessment report for all database objects that have been assessed or converted. You can also view a summary report for individual objects:  
  
    -   To view the report for an individual database, select the database in Sybase Metadata Explorer.  
  
    -   To view the report for an individual database object, select the object in Sybase Metadata Explorer. Objects that have conversion problems have a red error icon.  
  
For objects that failed conversion, you can view the syntax that resulted in the conversion failure.  
  
**To view individual conversion problems**  
  
1.  In Sybase Metadata Explorer, expand **Databases**.  
  
2.  Expand the database that shows a red error icon.  
  
3.  Expand the **Schemas** folder, and then expand the schema that shows a red error icon.  
  
4.  Under the schema, expand a folder that has a red error icon.  
  
5.  Select the object that has a red error icon.  
  
6.  In the right pane, click the **Report** tab.  
  
7.  At the top of the **Report** tab is a drop\-down list. If the list shows **Statistics**, change the selection to **Source**.  
  
    SSMA will display the source code and several buttons immediately above the code.  
  
8.  Click the **Next Problem** button. This is a red error icon with an arrow pointing to the right.  
  
    SSMA for ASE will highlight the first problematic source code it finds in the current object.  
  
For each item that could not be converted, you have to determine what you want to do with that object:  
  
-   You can edit the source code for procedures and triggers on the **SQL** tab.  
  
-   You can alter the ASE object to remove or revise problematic code. To load the updated code into SSMA, you will have to update the metadata. For more information, see [Connecting to Sybase ASE &#40;SybaseToSQL&#41;](../content/Connecting-to-Sybase-ASE--SybaseToSQL-.md).  
  
-   You can exclude the object from migration. In [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure Metadata Explorer and Sybase Metadata Explorer, clear the check box next to the item before loading the objects into [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] or SQL Azure and migrating data from ASE.  
  
## Next Step  
The next step in the migration process is to [Loading Converted Database Objects into SQL Server/ SQL Azure (SybaseToSQL)](assetId:///4c59256f-99a8-4351-9559-a455813dbd06).  
  
## See Also  
[Migrating Sybase ASE Databases to SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../content/Migrating-Sybase-ASE-Databases-to-SQL-Server---Azure-SQL-DB--SybaseToSQL-.md)  
  
