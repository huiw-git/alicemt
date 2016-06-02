---
title: Execute Process Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aca5a0b5-34a9-45bc-a234-8e63ea51a1ee
---
# Execute Process Task
  The Execute Process task runs an application or batch file as part of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package workflow. Although you can use the Execute Process task to open any standard application, such as [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)] or [!INCLUDE[ofprword](../../Token\Other/ofprword_md.md)], you typically use it to run business applications or batch files that work against a data source. For example, you can use the Execute Process task to expand a compressed text file. Then the package can use the text file as a data source for the data flow in the package. As another example, you can use the Execute Process task to run a custom [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] application that generates a daily sales report. Then you can attach the report to a Send Mail task and forward the report to a distribution list.  
  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes other tasks that perform workflow operations such as executing packages. For more information, see [Execute Package Task](../../Topics\TopicNameNotContainA/Execute-Package-Task.md)  
  
## Custom Log Entries Available on the Execute Process Task  
 The following table lists the custom log entries for the Execute Process task. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md) and [Custom Messages for Logging](../../Topics\TopicNameNotContainA/Custom-Messages-for-Logging.md).  
  
|Log entry|Description|  
|---------------|-----------------|  
|**ExecuteProcessExecutingProcess**|Provides information about the process that the task is configured to run.<br /><br /> Two log entries are written. One contains information about the name and location of the executable that the task runs, and the other entry records the exit from the executable.|  
|**ExecuteProcessVariableRouting**|Provides information about which variables are routed to the input and outputs of the executable. Log entries are written for stdin \(the input\), stdout \(the output\), and stderr \(the error output\).|  
  
## Configuration of the Execute Process Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Execute Process Task Editor &#40;General Page&#41;](../Topic/Execute%20Process%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Execute Process Task Editor &#40;Process Page&#41;](../Topic/Execute%20Process%20Task%20Editor%20\(Process%20Page\).md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
### Property Settings  
 When the Execute Process task runs a custom application, the task provides input to the application through one or both of the following methods:  
  
-   A variable that you specify in the **StandardInputVariable** property setting. For more information about variables, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md) and [Use Variables in Packages](../../Topics\TopicNameNotContainA/Use-Variables-in-Packages.md).  
  
-   An argument that you specify in the **Arguments** property setting. \(For example, if the task opens a document in Word, the argument can name the .doc file.\)  
  
 To pass multiple arguments to a custom application in one Execute Process task, use spaces to delimit the arguments. An argument cannot include a space; otherwise, the task will not run. You can use an expression to pass a variable value as the argument. In the following example, the expression passes two variable values as arguments, and uses a space to delimit the arguments:  
  
 `@variable1 + " " + @variable2`  
  
 You can use an expression to set various Execute Process task properties.  
  
 When you use the **StandardInputVariable** property to configure the Execute Process task to provide input, call the **Console.ReadLine** method from the application to read the input. For more information, see [Console.ReadLine Method](http://go.microsoft.com/fwlink/?LinkId=129201)the topic, , in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] Class Library.  
  
 When you use the **Arguments** property to configure the Execute Process task to provide input, do one of the following steps to obtain the arguments:  
  
-   If you use Microsoft Visual Basic to write the application, set the **My.Application.CommandLineArgs** property. The following example sets the **My.Application.CommandLineArgs** property is to retrieve two arguments:  
  
    ```  
    Dim variable1 As String = My.Application.CommandLineArgs.Item(0)  
    Dim variable2 As String = My.Application.CommandLineArgs.Item(1)   
    ```  
  
     For more information, see the topic, [My.Application.CommandLineArgs Property](http://go.microsoft.com/fwlink/?LinkId=129200), in the [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] reference.  
  
-   If you use Microsoft Visual C\# to write the applicate, use the **Main** method.  
  
     For more information, see the topic, [Command\-Line Arguments \(C\# Programming Guide\)](http://go.microsoft.com/fwlink/?LinkId=129406), in the C\# Programming Guide.  
  
 The Execute Process task also includes the **StandardOutputVariable** and **StandardErrorVariable** properties for specifying the variables that consume the standard output and error output of the application, respectively.  
  
 Additionally, you can configure the Execute Process task to specify a working directory, a time\-out period, or a value to indicate that the executable ran successfully. The task can also be configured to fail if the return code of the executable does not match the value that indicates success, or if the executable is not found at the specified location.  
  
## Programmatic Configuration of the Execute Process Task  
 For more information about programmatically setting these properties, click the following topic:  
  
-   [ExecuteProcess](assetId:///T:Microsoft.SqlServer.Dts.Tasks.ExecuteProcess.ExecuteProcess)  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  