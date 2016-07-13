---
title: Standards-Compliant Applications and Drivers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Standards-Compliant Applications and Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A standards-compliant application or driver is one that conforms to the Open Group CAE Specification "Data Management: SQL Call-Level Interface (CLI)," and the ISO/IEC 9075-3:1995 (E) Call-Level Interface (SQL/CLI).</para>
    <para>ODBC 3<legacyItalic>.x</legacyItalic> guarantees the following features:  </para>
    <list class="bullet">
      <listItem>
        <para>An application written to the Open Group and ISO CLI specifications will work with an ODBC 3<legacyItalic>.x</legacyItalic> driver or a standards-compliant driver when it is compiled with the ODBC 3<legacyItalic>.x</legacyItalic> header files and linked with ODBC 3<legacyItalic>.x</legacyItalic> libraries, and when it gains access to the driver through the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager.</para>
      </listItem>
      <listItem>
        <para>A driver written to the Open Group and ISO CLI specifications will work with an ODBC 3<legacyItalic>.x</legacyItalic> application or a standards-compliant application when it is compiled with the ODBC 3<legacyItalic>.x</legacyItalic> header files and linked with ODBC 3<legacyItalic>.x</legacyItalic> libraries, and when the application gains access to the driver through the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager.</para>
      </listItem>
    </list>
    <para>Standards-compliant applications and drivers are compiled with the ODBC_STD compile flag.</para>
    <para>Standards-compliant applications exhibit the following behavior:  </para>
    <list class="bullet">
      <listItem>
        <para>If a standards-compliant application calls <legacyBold>SQLAllocEnv</legacyBold> (which can occur because <legacyBold>SQLAllocEnv</legacyBold> is a valid function in the Open Group and ISO CLI), the call is mapped to <legacyBold>SQLAllocHandleStd</legacyBold> at compile time. As a result, at run time, the application calls <legacyBold>SQLAllocHandleStd</legacyBold>. During the course of processing this call, the Driver Manager sets the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC3. A call to <legacyBold>SQLAllocHandleStd</legacyBold> is equivalent to a call to <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and a call to <legacyBold>SQLSetEnvAttr</legacyBold> to set SQL_ATTR_ODBC_VERSION to SQL_OV_ODBC3.</para>
      </listItem>
      <listItem>
        <para>If a standards-compliant application calls <legacyBold>SQLBindParam</legacyBold> (which can occur because <legacyBold>SQLBindParam</legacyBold> is a valid function in the Open Group and ISO CLI), the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager maps the call to the equivalent call in <legacyBold>SQLBindParameter</legacyBold>. (See <legacyLink xlink:href="375f8f24-36de-4946-916e-c75abc6f070d">SQLBindParam Mapping</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.)</para>
      </listItem>
      <listItem>
        <para>To align with the ISO CLI, the ODBC 3<legacyItalic>.x</legacyItalic> header files contain aliases for information types used in calls to <legacyBold>SQLGetInfo</legacyBold>. A standards-compliant application can use these aliases instead of the ODBC 3<legacyItalic>.x</legacyItalic> information types. For more information, see the next topic, <legacyLink xlink:href="b4a03273-5e30-4d7b-826e-02f8f28ba078">Header Files</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>A standards-compliant application must verify that all features it supports are supported in the driver it will work with. Setting the SQL_ATTR_CURSOR_SCROLLABLE statement attribute to SQL_SCROLLABLE and setting the SQL_ATTR_CURSOR_SENSITIVITY statement attribute to SQL_INSENSITIVE or SQL_SENSITIVE are capabilities that are available as optional features in the standards but are not included in the ODBC 3<legacyItalic>.x</legacyItalic> Core level and therefore might not be supported by all ODBC 3<legacyItalic>.x</legacyItalic> drivers. If a standards-compliant application uses these capabilities, it should verify that the driver that it will work with supports them.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>