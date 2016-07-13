---
title: Behavioral Changes and ODBC 3.x Drivers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Behavioral Changes and ODBC 3.x Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The environment attribute SQL_ATTR_ODBC_VERSION indicates to the driver whether it needs to exhibit ODBC 2.<legacyItalic>x </legacyItalic>behavior or ODBC 3<legacyItalic>.x</legacyItalic> behavior. How the SQL_ATTR_ODBC_VERSION environment attribute is set depends on the application. ODBC 3<legacyItalic>.x</legacyItalic> applications must call <legacyBold>SQLSetEnvAttr</legacyBold> to set this attribute after they call <legacyBold>SQLAllocHandle</legacyBold> to allocate an environment handle and before they call <legacyBold>SQLAllocHandle</legacyBold> to allocate a connection handle. If they fail to do this, the Driver Manager returns SQLSTATE HY010 (Function sequence error) on the latter call to <legacyBold>SQLAllocHandle</legacyBold>.</para>
    <alert class="note">
      <para>For more information on behavioral changes and how an application acts, see <legacyLink xlink:href="a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67">Behavioral Changes</legacyLink>.</para>
    </alert>
    <para>ODBC 2.<legacyItalic>x</legacyItalic> applications and ODBC 2.<legacyItalic>x</legacyItalic> applications recompiled with the ODBC 3<legacyItalic>.x</legacyItalic> header files do not call <legacyBold>SQLSetEnvAttr</legacyBold>. However, they call <legacyBold>SQLAllocEnv</legacyBold> instead of <legacyBold>SQLAllocHandle</legacyBold> to allocate an environment handle. Therefore, when the application calls <legacyBold>SQLAllocEnv</legacyBold> in the Driver Manager, the Driver Manager calls <legacyBold>SQLAllocHandle</legacyBold> and <legacyBold>SQLSetEnvAttr</legacyBold> in the driver. Thus, ODBC 3<legacyItalic>.x</legacyItalic> drivers can always count on this attribute being set.</para>
    <para>If a standards-compliant application compiled with the ODBC_STD compile flag calls <legacyBold>SQLAllocEnv</legacyBold> (which may occur because <legacyBold>SQLAllocEnv</legacyBold> is not deprecated in ISO), the call is mapped to <legacyBold>SQLAllocHandleStd</legacyBold> at compile time. At run time, the application calls <legacyBold>SQLAllocHandleStd</legacyBold>. The Driver Manager sets the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC3. A call to <legacyBold>SQLAllocHandleStd</legacyBold> is equivalent to a call to <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV and a call to <legacyBold>SQLSetEnvAttr</legacyBold> to set SQL_ATTR_ODBC_VERSION to SQL_OV_ODBC3. </para>
    <para>In certain driver architectures, there is a need for the driver to appear as either an ODBC 2.<legacyItalic>x</legacyItalic> driver or an ODBC 3<legacyItalic>.x</legacyItalic> driver, depending on the connection. The driver in this case might not actually be a driver but a layer that resides between the Driver Manager and another driver. For example, it might mimic a driver, like ODBC Spy. In another example, it might act as a gateway, like EDA/SQL. To appear as an ODBC 3<legacyItalic>.x</legacyItalic> driver, such a driver must be able to export <legacyBold>SQLAllocHandle</legacyBold>, and to appear as an ODBC 2.<legacyItalic>x</legacyItalic> driver, must be able to export <legacyBold>SQLAllocConnect</legacyBold>, <legacyBold>SQLAllocEnv</legacyBold>, and <legacyBold>SQLAllocStmt</legacyBold>. When an environment, connection, or statement is to be allocated, the Driver Manager checks to see if this driver exports <legacyBold>SQLAllocHandle</legacyBold>. Since the driver does, the Driver Manager calls <legacyBold>SQLAllocHandle</legacyBold> in the driver. If the driver is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, the driver must map the call to <legacyBold>SQLAllocHandle</legacyBold> to <legacyBold>SQLAllocConnect</legacyBold>, <legacyBold>SQLAllocEnv</legacyBold>, or <legacyBold>SQLAllocStmt</legacyBold>, as appropriate. It must also do nothing with the <legacyBold>SQLSetEnvAttr</legacyBold> call when behaving as an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="6b9363c9-04bf-4492-a210-7aa15dea4af8">Datetime Data Types</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b1453a65-ae03-4061-b0cf-a8434d8bc40b">Backward Compatibility of C Data Types</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cbd8185e-fb03-408f-b80b-1a2e164534fd">Fixed-Length Bookmarks</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="57326f57-daba-46b6-b0be-6c97213b9ef1">SQLGetInfo Support</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="deed0163-9d1a-4e9b-9342-3f82e64477d2">Returning SQL_NO_DATA</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="03e5c4d0-2bb3-4649-9781-89cab73f78eb">Calling SQLSetPos to Insert Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="337d90ab-68eb-4940-a2f3-f7d5693ee766">Loading by Ordinal</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>