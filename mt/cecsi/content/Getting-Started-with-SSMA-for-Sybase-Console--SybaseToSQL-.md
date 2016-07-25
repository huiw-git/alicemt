---
title: "Getting Started with SSMA for Sybase Console (SybaseToSQL)"
ms.custom: na
ms.date: 07/18/2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
manager: lonnyb
---
# Getting Started with SSMA for Sybase Console (SybaseToSQL)
This section describes the procedure to launch and get started with the Sybase console application. Also listed, herein, are the conventions used in a typical SSMA Console output window.  
  
## Launching SSMA Console  
Use the following steps to start the SSMA console application:  
  
1.  Go to Start and point to All Programs.  
  
2.  Click the **SQL Server Migration Assistant for Sybase Command Prompt** shortcut.  
  
    It displays the SSMA Console usage menu and `(/? Help)`, to help you get started with the console application.  
  
## Procedure for Using the SSMA Console  
After the console is successfully launched on your Windows system, you could use the following steps to work on it:  
  
1.  Configure SSMA Console through the script files. For more information on this section, see [Creating Script Files &#40;SybaseToSQL&#41;](../content/Creating-Script-Files--SybaseToSQL-.md) .  
  
2.  [Creating Variable Value Files &#40;SybaseToSQL&#41;](../content/Creating-Variable-Value-Files--SybaseToSQL-.md)  
  
3.  [Creating the Server Connection Files &#40;SybaseToSQL&#41;](../content/Creating-the-Server-Connection-Files--SybaseToSQL-.md)  
  
4.  [Executing the SSMA Console &#40;SybaseToSQL&#41;](../content/Executing-the-SSMA-Console--SybaseToSQL-.md) based on your project needs  
  
Additional features:  
  
1.  [Specify a password](assetId:///9b6a70f9-6840-4140-a059-bb7bd7ccc67c) and export/ import it onto other Window machines  
  
2.  [Generate Reports](assetId:///19278f6a-6d58-4867-9d71-c6228040466e) to view the detailed xml output reports for assessment /conversion and data migration. Detailed error reports can also be generated for refresh and synchronization commands.  
  
## SSMA Console Output Conventions  
Upon executing the SSMA script commands and options, the console program displays the results and messages (information, error, etc.) to the user on the console or if required, redirects to an xml output file. Each type of message in the output is signified by a unique color. For example, the text message in white color denotes script file commands; the one in green color represents a prompt for user-input, and so on.  
  
![SSMAConsoleOutput_Sybase](../content/media/SSMAConsoleOutput_Sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Color-interpretation of the console output in the following table:  
  
|Color|Description|  
|---------|---------------|  
|Red|Fatal error during execution|  
|Gray|Date and Time stamp, message to the user|  
|White|Script file commands, message type|  
|Yellow|Warning|  
|Green|Prompt for user-input|  
|Cyan|Start, Finish and Result of an operation|  
  
## See Also  
[Installing SSMA  for Sybase &#40;SybaseToSQL&#41;](../content/Installing-SSMA--for-Sybase--SybaseToSQL-.md)  
  
