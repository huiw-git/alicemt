---
title: Environment Handles
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
translation.priority.ht: 
  - en-gb
---
# Environment Handles
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An <legacyItalic>environment</legacyItalic> is a global context in which to access data; associated with an environment is any information that is global in nature, such as:  </para>
    <list class="bullet">
      <listItem>
        <para>The environment's state</para>
      </listItem>
      <listItem>
        <para>The current environment-level diagnostics</para>
      </listItem>
      <listItem>
        <para>The handles of connections currently allocated on the environment</para>
      </listItem>
      <listItem>
        <para>The current settings of each environment attribute</para>
      </listItem>
    </list>
    <para>Within a piece of code that implements ODBC (the Driver Manager or a driver), an environment handle identifies a structure to contain this information.</para>
    <para>Environment handles are not frequently used in ODBC applications. They are always used in calls to <legacyBold>SQLDataSources</legacyBold> and <legacyBold>SQLDrivers</legacyBold> and sometimes used in calls to <legacyBold>SQLAllocHandle</legacyBold>, <legacyBold>SQLEndTran</legacyBold>, <legacyBold>SQLFreeHandle</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, and <legacyBold>SQLGetDiagRec</legacyBold>.</para>
    <para>Each piece of code that implements ODBC (the Driver Manager or a driver) contains one or more environment handles. For example, the Driver Manager maintains a separate environment handle for each application that is connected to it. Environment handles are allocated with <legacyBold>SQLAllocHandle</legacyBold> and freed with <legacyBold>SQLFreeHandle</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>