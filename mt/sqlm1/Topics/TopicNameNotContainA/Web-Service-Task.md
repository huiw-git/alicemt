---
title: Web Service Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
---
# Web Service Task
  The Web Service task executes a Web service method. You can use the Web Service task for the following purposes:  
  
-   Writing to a variable the values that a Web service method returns. For example, you could obtain the highest temperature of the day from a Web service method, and then use that value to update a variable that is used in an expression that sets a column value.  
  
-   Writing to a file the values that a Web service method returns. For example, a list of potential customers can be written to a file and the file then used as a data source in a package that cleans the data before it is written to a database.  
  
## WSDL File  
 The Web Service task uses an HTTP connection manager to connect to the Web service. The HTTP connection manager is configured separately from the Web Service task, and is referenced in the task. The HTTP connection manager specifies the server proxy settings such as the server URL, credentials for accessing the Web services server, and time\-out length. For more information, see [HTTP Connection Manager](../../Topics\TopicNameNotContainA/HTTP-Connection-Manager.md).  
  
> [!IMPORTANT]  
>  The HTTP connection manager supports only anonymous authentication and basic authentication. It does not support Windows Authentication.  
  
 The HTTP connection manager can point to a Web site or to a Web Service Description Language \(WSDL\) file. The URL of the HTTP connection manager that points to a WSDL file includes the `?WSDL` parameter: for example, `http://MyServer/MyWebService/MyPage.asmx?WSDL`.  
  
 The WSDL file must be available locally to configure the Web Service task using the **Web Service Task Editor** dialog box that [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer provides.  
  
-   If the HTTP connection manager points to a Web site, the WSDL file must be copied manually to a local computer.  
  
-   If the HTTP connection manager points to a WSDL file, the file can be downloaded from the Web site to a local file by the Web Service task.  
  
 The WSDL file lists the methods that the Web service offers, the input parameters that the methods require, the responses that the methods return, and how to communicate with the Web service.  
  
 If the method uses input parameters, the Web Service task requires parameter values. For example, a Web service method that recommends the length of skis you should purchase based on your height requires that your height be submitted in an input parameter. The parameter values can be provided either by strings that are defined in the task, or by variables defined in the scope of the task or a parent container. The advantage of using variables is that they let you dynamically update the parameter values by using package configurations or scripts. For more information, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md) and [Package Configurations](../../Topics\TopicNameNotContainA/Package-Configurations.md).  
  
 Many Web service methods do not use input parameters. For example, a Web service method that gets the names of presidents who were born in the current month would not require an input parameter because the Web service can determine the current month locally.  
  
 The results of the Web service method can be written to a variable or to a file. You use the File connection manager either to specify the file or to provide the name of the variable to write the results to. For more information, see [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md) and [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md).  
  
## Custom Logging Messages Available on the Web Service Task  
 The following table lists the custom log entries that you can enable for the Web Service task. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md) and [Custom Messages for Logging](../../Topics\TopicNameNotContainA/Custom-Messages-for-Logging.md).  
  
|Log entry|Description|  
|---------------|-----------------|  
|**WSTaskBegin**|The task began to access a Web service.|  
|**WSTaskEnd**|The task completed a Web service method.|  
|**WSTaskInfo**|Descriptive information about the task.|  
  
## Configuration of the Web Service Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [Web Service Task Editor &#40;General Page&#41;](../Topic/Web%20Service%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Web Service Task Editor &#40;Input Page&#41;](../Topic/Web%20Service%20Task%20Editor%20\(Input%20Page\).md)  
  
-   [Web Service Task Editor &#40;Output Page&#41;](../Topic/Web%20Service%20Task%20Editor%20\(Output%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
## Programmatic Configuration of the Web Service Task  
 For more information about programmatically setting these properties, click one of the following topics:  
  
-   [WebServiceTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask)  
  
## Related Content  
 Video, [How to: Call a Web Service by Using the Web Service Task \(SQL Server Video\)](http://go.microsoft.com/fwlink/?LinkId=259642), on technet.microsoft.com.  
  
 Curated Answer, [Consume Web Services in SSIS using Scripts](http://go.microsoft.com/fwlink/?LinkId=321996), on curatedviews.cloudapp.net.  
  
  