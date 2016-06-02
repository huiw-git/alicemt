---
title: Switch an Analysis Services database between ReadOnly and ReadWrite modes
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
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
---
# Switch an Analysis Services database between ReadOnly and ReadWrite modes
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database administrators can change the read\/write mode of a Tabular or Multidimensional database as part of larger effort that distributes a query workload among multiple query\-only servers.  
  
 A database mode can be switched in several ways. This document explains the following common scenarios:  
  
-   Interactively using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]  
  
-   Programmatically using AMO  
  
-   Script using XMLA or TMSL  
  
## Switch the read\/write mode of a database interactively using Management Studio  
  
1.  In Object Explorer, right\-click  the database and select **Properties**.  
  
     Note the location. An empty database storage location indicates that the database folder is located in the server data folder.  
  
2.  Right\-click the database and select **Detach…**  
  
3.  Assign a password to the database to be detached, and then click **OK** to execute the detach command.  
  
4.  In Object Explorer, right\-click the **Databases** folder and select **Attach…**  
  
5.  In the **folder** text box, type the original location of the database folder. Alternatively, you can use the browse button \(**…**\) to locate the database folder.  
  
6.  Select the read\/write mode for the database.  
  
7.  Type the password and click **OK** to execute the attach command.  
  
## Switch the read\/write mode to a database programmatically using AMO  
 In your C\# application, invoke `SwitchReadWrite()` with the necessary parameters. Compile and execute your code to move the database.  
  
```  
private void SwitchReadWrite(Server server, string dbName, ReadWriteMode dbReadWriteMode)  
{  
    if (server.Databases.ContainsName(dbName))  
    {  
        Database db;  
        string databaseLocation;  
        db = server.Databases[dbName];  
        databaseLocation = db.DbStorageLocation;  
  
	          if (databaseLocation == null)  
            {  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
  
    String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);  
  
   if (possibleFolders.Length > 1)  
         {  
         List<String> sortedFolders = new List<string>(possibleFolders.Length);  
         sortedFolders.AddRange(possibleFolders);  
         sortedFolders.Sort();  
         databaseLocation = sortedFolders[sortedFolders.Count - 1];  
         }  
         else  
         {  
         databaseLocation = possibleFolders[0];  
          }  
        }  
    db.Detach();  
    server.Attach(databaseLocation, dbReadWriteMode);  
    }  
}  
  
```  
  
## Switch the read\/write mode to a database by script using XMLA  
 The following instructions apply to Multidimensional databases and Tabular databases at compatibility mode 1050, 1100, or 1103.  
  
1.  In Object Explorer, right\-click  the database and select **Properties**.  
  
     Note the location. An empty database storage location indicates that the database folder is located in the server data folder.  
  
2.  Right\-click the database and select **Detach…**  
  
3.  Open a new XMLA tab in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)].  
  
4.  Copy the following script template for XMLA:  
  
    ```  
    <Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Object>  
          <DatabaseID>%dbName%</DatabaseID>  
          <Password>%password%</Password>  
       </Object>  
    </Detach>  
    ```  
  
5.  Replace `%dbName%` with the name of the database and `%password%` with the password. The % characters are part of the template and must be removed.  
  
6.  Execute the XMLA command.  
  
7.  Copy the following script template for XMLA in a new XMLA tab  
  
    ```  
    <Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Folder>%dbFolder%</Folder>  
       <ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>  
    </Attach>  
    ```  
  
8.  Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value **ReadOnly** or **ReadWrite**, and `%password%` with the password. The % characters are part of the template and must be removed.  
  
9. Execute the XMLA command.  
  
## See Also  
 [Detach](assetId:///M:Microsoft.AnalysisServices.Database.Detach)   
 [High availability and Scalability in Analysis Services](../../Topics\TopicNameNotContainA/High-availability-and-Scalability-in-Analysis-Services.md)   
 [Attach and Detach Analysis Services Databases](../../Topics\TopicNameNotContainA/Attach-and-Detach-Analysis-Services-Databases.md)   
 [Database Storage Location](../../Topics\TopicNameNotContainA/Database-Storage-Location.md)   
 [Database ReadWriteModes](../../Topics\TopicNameNotContainA/Database-ReadWriteModes.md)   
 [Attach Element](../Topic/Attach%20Element.md)   
 [Detach Element](../Topic/Detach%20Element.md)   
 [ReadWriteMode Element](../Topic/ReadWriteMode%20Element.md)   
 [DbStorageLocation Element](../Topic/DbStorageLocation%20Element.md)  
  
  