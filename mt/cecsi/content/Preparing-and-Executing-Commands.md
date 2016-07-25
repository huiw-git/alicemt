---
title: "Preparing and Executing Commands"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7448d9ee-7f4b-47e3-be54-2df8c9bbac32
caps.latest.revision: 10
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
# Preparing and Executing Commands
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Commands are instructions issued to a provider to perform some operations against the underlying data source. An SQL statement, for example, is a command to the Microsoft SQL Data Provider. In ADO, commands are typically represented by <legacyBold>Command</legacyBold> objects, although simple commands can also be issued through <legacyBold>Connection</legacyBold> or <legacyBold>Recordset</legacyBold> objects.</para>
    <para>You can use the <legacyBold>Command</legacyBold> object to request any supported type of operation from the provider, assuming that the provider can interpret the command string properly. A common operation for data providers is to query a database and return records in a <legacyBold>Recordset</legacyBold> object, which that can be thought of as a container to hold the result and a tool to view the result. As with many ADO objects, some <legacyBold>Command</legacyBold> object collections, methods, or properties might generate errors when referenced, depending on the functionality of the provider.</para>
    <para>In addition to using <legacyBold>Command</legacyBold> objects, you can use the <legacyBold>Execute</legacyBold> method on the <legacyBold>Connection</legacyBold> object or the <legacyBold>Open</legacyBold> method on the <legacyBold>Recordset</legacyBold> object to issue a command and have it executed. However, you should use a <legacyBold>Command</legacyBold> object if you need to reuse a command in your code, or if you need to pass detailed parameter information with your command. These scenarios are covered in more detail later in this section.</para>
    <alert class="note">
      <para>Certain <legacyBold>Command</legacyBold>s can return a result set as a binary stream or as a single <legacyBold>Record</legacyBold> rather than as a <legacyBold>Recordset</legacyBold>, if this is supported by the provider. Also, some <legacyBold>Command</legacyBold>s are not intended to return any result set at all (for example, a SQL Update query). This section will cover the most typical scenario, however: executing <legacyBold>Command</legacyBold>s that return results as a <legacyBold>Recordset</legacyBold> object. For more information about returning results into <legacyBold>Record</legacyBold>s or <legacyBold>Stream</legacyBold>s, see <legacyLink xlink:href="4d68868e-2611-4b5c-9a89-7caa5f753151">Records and Streams</legacyLink>.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="e84a14b1-3c2a-4f7d-a966-9e08a93948df">Command Object Overview</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0b81af6f-b9ae-4f7c-b59b-b5bdd775036f">Creating and Executing a Simple Command</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="10e7ef4a-78bf-4e91-931e-cbc6c065dd4c">Command Object Parameters</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="685f7652-2271-4ede-b552-2eeb8c756b4c">Calling a Stored Procedure with a Command</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="35ffdb79-a931-4271-a3bb-0cd804cf173e">Calling a Stored Procedure as a Method on a Connection Object</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="5a0ec8f9-5ba3-4f9f-b80d-2073aa049586">Named Commands</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="36e0cdbe-7f50-40f5-af0d-700f5d8dc75a">Passing Parameters to a Named Command</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>