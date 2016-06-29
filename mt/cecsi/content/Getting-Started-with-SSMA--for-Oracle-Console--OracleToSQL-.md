---
title: Getting Started with SSMA  for Oracle Console (OracleToSQL)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.technology: 
  - sql-ssma
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
---
# Getting Started with SSMA  for Oracle Console (OracleToSQL)
This section describes the procedure to launch and get started with the Oracle console application. Also listed, herein, are the conventions used in a typical SSMA Console output window.  
  
## Launching SSMA Console  
Use the following steps to start the SSMA console application:  
  
1.  Go to **Start** and point to **All Programs**.  
  
2.  Click the **[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Migration Assistant for Oracle Command Prompt** shortcut.  
  
    It displays the SSMA Console usage menu and `(/? Help)`, to help you get started with the console application.  
  
## Procedure for Using the SSMA Console  
After the console is successfully launched on your Windows system, you could use the following steps to work on it:  
  
1.  Configure SSMA Console through the script files. For more information on this section, see [Creating Script Files &#40;OracleToSQL&#41;](../content/Creating-Script-Files--OracleToSQL-.md) .  
  
2.  [Creating Variable Value Files &#40;OracleToSQL&#41;](../content/Creating-Variable-Value-Files--OracleToSQL-.md)  
  
3.  [Creating the Server Connection Files &#40;OracleToSQL&#41;](../content/Creating-the-Server-Connection-Files--OracleToSQL-.md)  
  
4.  [Executing the SSMA Console &#40;OracleToSQL&#41;](../content/Executing-the-SSMA-Console--OracleToSQL-.md) based on your project needs  
  
Additional features:  
  
1.  [Specify a password](assetId:///8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c) and export\/ import it onto other Window machines  
  
2.  [Generate Reports](assetId:///ccad6262-01e1-447a-bd2b-c105154c80ce) to view the detailed xml output reports for assessment \/conversion and data migration. Detailed error reports can also be generated for refresh and synchronization commands.  
  
## SSMA Console Output Conventions  
Upon executing the SSMA script commands and options, the console program displays the results and messages (information, error, etc.) to the user on the console or if required, redirects to an xml output file. Each type of message in the output is signified by a unique color. For example, the text message in white color denotes script file commands; the one in green color represents a prompt for user\-input, and so on.  
  
![SSMA Console Output_Oracle](../content/media/SSMAConsoleOutput_Oracle.jpg "SSMAConsoleOutput_Oracle")  
  
Color\-interpretation of the console output in the following table:  
  
|Color|Description|  
|---------|---------------|  
|Red|Fatal error during execution|  
|Gray|Date and Time stamp, message to the user|  
|White|Script file commands, message type|  
|Yellow|Warning|  
|Green|Prompt for user\-input|  
|Cyan|Start, Finish and Result of an operation|  
  
## See Also  
[Installing SSMA for Oracle](assetId:///9211013a-ab24-4c52-9b26-87994b35e502)  
  
