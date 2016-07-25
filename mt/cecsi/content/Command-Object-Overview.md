---
title: "Command Object Overview"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: 9
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
# Command Object Overview
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>With a <legacyBold>Command</legacyBold> object, you can do the following:  </para>
    <list class="bullet">
      <listItem>
        <para>Define the executable text of the command (for example, a SQL statement or a stored procedure) by using the <legacyBold>CommandText</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>Define parameterized queries or stored procedure arguments by using <legacyBold>Parameter</legacyBold> objects and the <legacyBold>Parameters</legacyBold> collection.</para>
      </listItem>
      <listItem>
        <para>Execute a command and return a <legacyBold>Recordset</legacyBold> object, if appropriate, by using the <legacyBold>Execute</legacyBold> method.</para>
      </listItem>
      <listItem>
        <para>Specify the type of command by using the <legacyBold>CommandType</legacyBold> property prior to execution to optimize performance.</para>
      </listItem>
      <listItem>
        <para>Specify specific information about the command text by using the <legacyBold>Dialect</legacyBold> property of the <legacyBold>Command</legacyBold> object.</para>
      </listItem>
      <listItem>
        <para>Control whether the provider saves a prepared (or compiled) version of the command prior to execution by using the <legacyBold>Prepared</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>Set the number of seconds that a provider will wait for a command to execute by using the <legacyBold>CommandTimeout</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>Associate an open connection with a <legacyBold>Command</legacyBold> object by setting its <legacyBold>ActiveConnection</legacyBold> property.</para>
      </listItem>
      <listItem>
        <para>Set the <legacyBold>Name</legacyBold> property to identify the <legacyBold>Command</legacyBold> object as a method on the associated <legacyBold>Connection</legacyBold> object.</para>
      </listItem>
      <listItem>
        <para>Pass a <legacyBold>Command</legacyBold> object to the <legacyBold>Source</legacyBold> property of a <legacyBold>Recordset</legacyBold> in order to obtain data.</para>
      </listItem>
      <listItem>
        <para>Pass a <legacyBold>Stream</legacyBold> object containing a command (for example, an XML command) to a provider that supports it.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>