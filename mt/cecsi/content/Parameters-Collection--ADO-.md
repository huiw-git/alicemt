---
title: "Parameters Collection (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 497cae10-3913-422a-9753-dcbb0a639b1b
caps.latest.revision: 19
manager: sonalm
translation.priority.ht: 
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
# Parameters Collection (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all the <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> objects of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>Command</legacyBold> object has a <legacyBold>Parameters</legacyBold> collection made up of <legacyBold>Parameter</legacyBold> objects.</para>
      <para>Using the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method on a <legacyBold>Command</legacyBold> object's <legacyBold>Parameters</legacyBold> collection retrieves provider parameter information for the stored procedure or parameterized query specified in the <legacyBold>Command</legacyBold> object. Some providers do not support stored procedure calls or parameterized queries; calling the <legacyBold>Refresh</legacyBold> method on the <legacyBold>Parameters</legacyBold> collection when using such a provider will return an error.</para>
      <para>If you have not defined your own <legacyBold>Parameter</legacyBold> objects and you access the <legacyBold>Parameters</legacyBold> collection before calling the <legacyBold>Refresh</legacyBold> method, ADO will automatically call the method and populate the collection for you.</para>
      <para>You can minimize calls to the provider to improve performance if you know the properties of the parameters associated with the stored procedure or parameterized query you wish to call. Use the <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink> method to create <legacyBold>Parameter</legacyBold> objects with the appropriate property settings and use the <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> method to add them to the <legacyBold>Parameters</legacyBold> collection. This lets you set and return parameter values without having to call the provider for the parameter information. If you are writing to a provider that does not supply parameter information, you must manually populate the <legacyBold>Parameters</legacyBold> collection using this method to be able to use parameters at all. Use the <legacyLink xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete</legacyLink> method to remove <legacyBold>Parameter</legacyBold> objects from the <legacyBold>Parameters</legacyBold> collection if necessary.</para>
      <para>The objects in the <legacyBold>Parameters</legacyBold> collection of a <legacyBold>Recordset</legacyBold> go out of scope (therefore becoming unavailable) when the <legacyBold>Recordset</legacyBold> is closed.</para>
      <para>When calling a stored procedure with <legacyBold>Command</legacyBold>, the return value/output parameter of a stored procedure is retrieved as follows:</para>
      <list class="ordered">
        <listItem>
          <para>When calling a stored procedure that has no parameters, the <legacyBold>Refresh</legacyBold> method on the <legacyBold>Parameters</legacyBold> collection should be called before calling the <legacyBold>Execute</legacyBold> method on the <legacyBold>Command</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>When calling a stored procedure with parameters and explicitly appending a parameter to the <legacyBold>Parameters</legacyBold> collection with <legacyBold>Append</legacyBold>, the return value/output parameter should be appended to the <legacyBold>Parameters</legacyBold> collection. The return value must first be appended to the <legacyBold>Parameters</legacyBold> collection. Use <legacyBold>Append</legacyBold> to add the other parameters into the <legacyBold>Parameters</legacyBold> collection in the order of definition. For example, the stored procedure SPWithParam has two parameters. The first parameter, <parameterReference>InParam</parameterReference>, is an input parameter defined as adVarChar (20), and the second parameter, <parameterReference>OutParam</parameterReference>, is an output parameter defined as adVarChar (20). You can retrieve the return value/output parameter with the following code.</para>
          <code>' Open Connection Conn
set ccmd = CreateObject("ADODB.Command")
ccmd.Activeconnection= Conn

ccmd.CommandText="SPWithParam"
ccmd.commandType = 4 'adCmdStoredProc

ccmd.parameters.Append ccmd.CreateParameter(, adInteger, adParamReturnValue, , NULL)   ' return value
ccmd.parameters.Append ccmd.CreateParameter("InParam", adVarChar, adParamInput, 20, "hello world")   ' input parameter
ccmd.parameters.Append ccmd.CreateParameter("OutParam", adVarChar, adParamOuput, 20, NULL)   ' output parameter

ccmd.execute()

' Access ccmd.parameters(0) as return value of this stored procedure
' Access ccmd.parameters("OutParam") as the output parameter of this stored procedure.
</code>
        </listItem>
        <listItem>
          <para>When calling a stored procedure with parameters and configuring the parameters by calling the <legacyBold>Item</legacyBold> method on the <legacyBold>Parameters</legacyBold> collection, the return value/output parameter of the stored procedure can be retrieved from the <legacyBold>Parameters</legacyBold> collection. For example, the stored procedure SPWithParam has two parameters. The first parameter, <parameterReference>InParam</parameterReference>, is an input parameter defined as adVarChar (20), and the second parameter, <parameterReference>OutParam</parameterReference>, is an output parameter defined as adVarChar (20). You can retrieve the return value/output parameter with the following code.</para>
          <code>' Open Connection Conn
set ccmd = CreateObject("ADODB.Command")
ccmd.Activeconnection= Conn

ccmd.CommandText="SPWithParam"
ccmd.commandType = 4 'adCmdStoredProc

ccmd.parameters.Item("InParam").value = "hello world" ' input parameter
ccmd.execute()

' Access ccmd.parameters(0) as return value of stored procedure
' Access ccmd.parameters(2) or ccmd.parameters("OutParam") as the output parameter.</code>
        </listItem>
      </list>
      <para>This section contains the following topic.</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="63b3f9a3-1c36-4d06-a6b0-49b5eb5adf06">Parameters Collection Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
<link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>