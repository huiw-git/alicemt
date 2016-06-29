---
title: Types of Descriptors
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec20e446-e540-41ad-8559-d9c0a5b8358f
translation.priority.ht: 
  - en-gb
---
# Types of Descriptors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A descriptor is used to describe one of the following:  </para>
    <list class="bullet">
      <listItem>
        <para>A set of zero or more parameters. A parameter descriptor can be used to describe: </para>
        <list class="bullet">
          <listItem>
            <para>The <legacyItalic>application parameter buffer,</legacyItalic> which contains either the input dynamic arguments as set by the application or the output dynamic arguments following the execution of a <legacyBold>CALL</legacyBold> statement of SQL.</para>
          </listItem>
          <listItem>
            <para>The <legacyItalic>implementation parameter buffer</legacyItalic>. For input dynamic arguments, this contains the same arguments as the application parameter buffer, after any data conversion the application may specify. For output dynamic arguments, this contains the returned arguments, before any data conversion that the application may specify.</para>
          </listItem>
        </list>
        <para>For input dynamic arguments, the application must operate on an application parameter descriptor before executing any SQL statement that contains dynamic parameter markers. For both input and output dynamic arguments, the application can specify different data types from those in the implementation parameter descriptor to achieve data conversion. </para>
      </listItem>
      <listItem>
        <para>A single row of database data. A row descriptor can be used to describe: </para>
        <list class="bullet">
          <listItem>
            <para>The <legacyItalic>implementation row buffer,</legacyItalic> which contains the row from the database. (These buffers conceptually contain data as written to or read from the database. However, the stored form of database data is not specified. A database could perform additional conversion on the data from its form in the implementation buffer.)</para>
          </listItem>
          <listItem>
            <para>The <legacyItalic>application row buffer,</legacyItalic> which contains the row of data as presented to the application, following any data conversion that the application may specify.</para>
          </listItem>
        </list>
        <para>The application operates on the application row descriptor in any case where column data from the database must appear in application variables. To achieve data conversion of column data, the application can specify different data types from those in the implementation row descriptor. </para>
      </listItem>
    </list>
    <para>The descriptor types are summarized in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Buffer type</para>
          </TD>
          <TD>
            <para>Rows</para>
          </TD>
          <TD>
            <para>Dynamic parameters</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>Application buffer</legacyBold>             </para>
          </TD>
          <TD>
            <para>Application row descriptor (ARD)</para>
          </TD>
          <TD>
            <para>Application parameter descriptor (APD)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>Implementation buffer</legacyBold>             </para>
          </TD>
          <TD>
            <para>Implementation row descriptor (IRD)</para>
          </TD>
          <TD>
            <para>Implementation parameter descriptor (IPD)</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For either the parameter or the row buffers, if the application specifies different data types in corresponding records of the implementation and application descriptors, the driver performs data conversion when it uses the descriptors. For example, it may convert numeric and datetime values to character-string format. (For valid conversions, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.)</para>
    <para>A descriptor can perform different roles. Different statements can share any descriptor that the application explicitly allocates. A row descriptor in one statement can serve as a parameter descriptor in another statement.</para>
    <para>It is always known whether a given descriptor is an application descriptor or an implementation descriptor, even if the descriptor has not yet been used in a database operation. For the descriptors that the implementation implicitly allocates, the implementation records the predefined row relative to the statement handle. Any descriptor that the application allocates by calling <legacyBold>SQLAllocHandle</legacyBold> is an application descriptor.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>