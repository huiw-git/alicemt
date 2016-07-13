---
title: Descriptor Handles
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Descriptor Handles
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>descriptor</legacyItalic> is a collection of metadata that describes the parameters of an SQL statement or the columns of a result set, as seen by the application or driver (also known as the <legacyItalic>implementation</legacyItalic>). Thus, a descriptor can fill any of four roles:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Application Parameter Descriptor (APD).</legacyBold> Contains information about the application buffers bound to the parameters in an SQL statement, such as their addresses, lengths, and C data types.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Implementation Parameter Descriptor (IPD).</legacyBold> Contains information about the parameters in an SQL statement, such as their SQL data types, lengths, and nullability.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Application Row Descriptor (ARD).</legacyBold> Contains information about the application buffers bound to the columns in a result set, such as their addresses, lengths, and C data types.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Implementation Row Descriptor (IRD).</legacyBold> Contains information about the columns in a result set, such as their SQL data types, lengths, and nullability.</para>
      </listItem>
    </list>
    <para>Four descriptors (one filling each role) are allocated automatically when a statement is allocated. These are known as <legacyItalic>automatically allocated descriptors</legacyItalic> and are always associated with that statement. Applications can also allocate descriptors with <legacyBold>SQLAllocHandle</legacyBold>. These are known as <legacyItalic>explicitly allocated descriptors</legacyItalic>. They are allocated on a connection and can be associated with one or more statements on that connection to fulfill the role of an APD or ARD on those statements.</para>
    <para>Most operations in ODBC can be performed without explicit use of descriptors by the application. However, descriptors provide a convenient shortcut for some operations. For example, suppose an application wants to insert data from two different sets of buffers. To use the first set of buffers, it would repeatedly call <legacyBold>SQLBindParameter</legacyBold> to bind them to the parameters in an <legacyBold>INSERT</legacyBold> statement and then execute the statement. To use the second set of buffers, it would repeat this process. Alternatively, it could set up bindings to the first set of buffers in one descriptor and to the second set of buffers in another descriptor. To switch between the sets of bindings, the application would simply call <legacyBold>SQLSetStmtAttr</legacyBold> and associate the correct descriptor with the statement as the APD.</para>
    <para>For more information about descriptors, see <legacyLink xlink:href="ec20e446-e540-41ad-8559-d9c0a5b8358f">Types of Descriptors</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>