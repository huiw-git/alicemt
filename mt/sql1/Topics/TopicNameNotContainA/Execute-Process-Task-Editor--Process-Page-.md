---
title: "Execute Process Task Editor (Process Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
caps.latest.revision: 32
manager: jhubbard
---
# Execute Process Task Editor (Process Page)
Use the **Process** page of the **Execute Process Task Editor** dialog box to configure the options that execute the process. These options include the executable to run, its location, command prompt arguments, and the variables that provide input and capture output.  
  
 To learn about this task, see [Execute Process Task](../../Topics/TopicNameNotContainA/Execute-Process-Task.md).  
  
## Options  
 **RequireFullFileName**  
 Indicate whether the task should fail if the executable is not found at the specified location.  
  
 **Executable**  
 Type the name of the executable to run.  
  
 **Arguments**  
 Provide command prompt arguments.  
  
 **WorkingDirectory**  
 Type the path of the folder that contains the executable, or click the browse button **(…)** and locate the folder.  
  
 **StandardInputVariable**  
 Select a variable to provide the input to the process, or click <**New variable...**> to create a new variable:  
  
 **Related Topics:** [Add Variable](../../Topics/TopicNameNotContainA/Add-Variable.md)  
  
 **StandardOutputVariable**  
 Select a variable to capture the output of the process, or click <**New variable...**> to create a new variable.  
  
 **StandardErrorVariable**  
 Select a variable to capture the error output of the processor, or click <**New variable...**> to create a new variable.  
  
 **FailTaskIfReturnCodeIsNotSuccessValue**  
 Indicate whether the task fails if the process exit code is different from the value specified in **SuccessValue**.  
  
 **SuccessValue**  
 Specify the value returned by the executable to indicate success. By default this value is set to **0**.  
  
 **TimeOut**  
 Specify the number of seconds that the process can run. A value of **0** indicates that no time-out value is used, and the process runs until it is completed or until an error occurs.  
  
 **TerminateProcessAfterTimeOut**  
 Indicate whether the process is forced to end after the time-out period specified by the **TimeOut** option. This option is available only if **TimeOut** is not **0**.  
  
 **WindowStyle**  
 Specify the window style in which to run the process.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Expressions Page](../../Topics/TopicNameNotContainA/Expressions-Page.md)