---
title: Interface Conformance Levels
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
translation.priority.ht: 
  - en-gb
---
# Interface Conformance Levels
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The purpose of leveling is to inform the application what features are available to it from the driver. A leveling scheme based on functions does not sufficiently achieve this goal. In ODBC 3.<legacyItalic>x</legacyItalic>, drivers are classified based on the features they possess. Supporting the feature can include supporting the function; it can also include supporting a descriptor field, a statement attribute, a "Y" value for an information type returned by <legacyBold>SQLGetInfo</legacyBold>, and so on.</para>
    <para>To simplify specification of interface conformance, ODBC defines three conformance levels. To meet a particular conformance level, a driver must satisfy all of the requirements of that conformance level. Conformance with a given level implies complete conformance with all lower levels.</para>
    <para>Conformance levels do not always divide neatly into support for a specific list of ODBC functions, but specify supported features as listed in the following sections. To provide support for a feature, a driver must support some or all forms of calls to certain ODBC functions (for more information, see <legacyLink xlink:href="bb5d68cf-d238-481e-babc-2e9401b4700e">Function Conformance</legacyLink>), setting certain attributes (see <legacyLink xlink:href="34fea100-10f9-46d5-bc50-3aa867b70f24">Attribute Conformance</legacyLink>), and certain descriptor fields (see <legacyLink xlink:href="6c29d93b-696c-4960-bff3-4d6bc41bc513">Descriptor Field Conformance</legacyLink>).</para>
    <para>The application discovers a driver's interface conformance level by connecting to a data source and calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_ODBC_INTERFACE_CONFORMANCE option.</para>
    <para>Drivers are free to implement features beyond the level to which they claim complete conformance. Applications discover any such additional capabilities by calling <legacyBold>SQLGetFunctions</legacyBold> (to determine which ODBC functions are present) and <legacyBold>SQLGetInfo</legacyBold> (to query various other ODBC capabilities).</para>
    <para>There are three ODBC interface conformance levels: Core, Level 1, and Level 2.</para>
    <alert class="note">
      <para>These conformance levels have different requirements than the ODBC API conformance levels of the same name in ODBC 2<legacyItalic>.x</legacyItalic>. In particular, all the features implied by ODBC 2<legacyItalic>.x</legacyItalic> API conformance Level 1 are now part of the Core interface conformance level. As a result, many ODBC drivers may report Core-level interface conformance.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="aaaa864a-6477-45ff-a50a-96d8db66a252">Core Interface Conformance</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ee3f5c08-0583-4f3b-8354-ef71b6086a7e">Level 1 Interface Conformance</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="2dc87840-f2fe-43dd-9d7b-bd95523081d9">Level 2 Interface Conformance</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="bb5d68cf-d238-481e-babc-2e9401b4700e">Function Conformance</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="34fea100-10f9-46d5-bc50-3aa867b70f24">Attribute Conformance</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6c29d93b-696c-4960-bff3-4d6bc41bc513">Descriptor Field Conformance</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>