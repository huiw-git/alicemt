---
title: Web Service Task Editor (General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
---
# Web Service Task Editor (General Page)
  Use the **General** page of the **Web Services Task Editor** dialog box to specify an HTTP connection manager, specify the location of the Web Services Description Language \(WSDL\) file the Web Service task uses, describe the Web Services task, and download the WSDL file.  
  
 For more information about this task, see [Web Service Task](../../Topics\TopicNameNotContainA/Web-Service-Task.md).  
  
## Options  
 **HTTPConnection**  
 Select a connection manager in the list, or click \<**New connection…**\> to create a new connection manager.  
  
> [!IMPORTANT]  
>  The HTTP connection manager supports only anonymous authentication and basic authentication. It does not support Windows Authentication.  
  
 **Related Topics:**  [HTTP Connection Manager](../../Topics\TopicNameNotContainA/HTTP-Connection-Manager.md), [HTTP Connection Manager Editor &#40;Server Page&#41;](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Server%20Page\).md)  
  
 **WSDLFile**  
 Type the fully qualified path of a WSDL file that is local to the computer, or click the browse button **\(…\)** and locate this file.  
  
 If you have already manually downloaded the WSDL file to the computer, select this file. However, if the WSDL file has not yet been downloaded, follow these steps:  
  
-   Create an empty file that has the ".wsdl" file name extension.  
  
-   Select this empty file for the **WSDLFile** option.  
  
-   Set the value of **OverwriteWSDLFile** to **True** to enable the empty file to be overwritten with the actual WSDL file.  
  
-   Click **Download WSDL** to download the actual WSDL file and overwrite the empty file.  
  
    > [!NOTE]  
    >  The **Download WSDL** option is not enabled until you provide the name of an existing local file in the **WSDLFile** box.  
  
 **OverwriteWSDLFile**  
 Indicate whether the WSDL file for the Web Service task can be overwritten.  
  
 If you intend to download the WSDL file by using the **Download WSDL** button, set this value to **True**.  
  
 **Name**  
 Provide a unique name for the Web Service task. This name is used as the label in the task icon.  
  
> [!NOTE]  
>  Task names must be unique within a package.  
  
 **Description**  
 Type a description of the Web Service task.  
  
 **Download WSDL**  
 Download the WSDL file.  
  
 This button is not enabled until you provide the name of an existing local file in the **WSDLFile** box.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Web Service Task Editor &#40;Input Page&#41;](../Topic/Web%20Service%20Task%20Editor%20\(Input%20Page\).md)   
 [Web Service Task Editor &#40;Output Page&#41;](../Topic/Web%20Service%20Task%20Editor%20\(Output%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
  