---
title: Block Cursors, Scrollable Cursors, and Backward Compatibility
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
translation.priority.ht: 
  - en-gb
---
# Block Cursors, Scrollable Cursors, and Backward Compatibility
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The existence of both <legacyBold>SQLFetchScroll</legacyBold> and <legacyBold>SQLExtendedFetch</legacyBold> represents the first clear split in ODBC between the Application Programming Interface (API), which is the set of functions the application calls, and the Service Provider Interface (SPI), which is the set of functions the driver implements. This split is necessary so that ODBC 3.<legacyItalic>x</legacyItalic>, which uses <legacyBold>SQLFetchScroll</legacyBold>,bealigned with the standards and also be compatible with ODBC 2.<legacyItalic>x</legacyItalic>, which uses <legacyBold>SQLExtendedFetch</legacyBold>.</para>
  </introduction>
  <section>
    <content>
      <para>The ODBC 3<legacyItalic>.x</legacyItalic> API, which is the set of functions the application calls, includes <legacyBold>SQLFetchScroll</legacyBold> and related statement attributes. The ODBC 3<legacyItalic>.x</legacyItalic> SPI, which is the set of functions the driver implements, includes <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLExtendedFetch</legacyBold>, and related statement attributes. Because ODBC does not formally enforce this split between the API and the SPI, it is possible for ODBC 3<legacyItalic>.x</legacyItalic> applications to call <legacyBold>SQLExtendedFetch</legacyBold> and related statement attributes. However, there is no reason for ODBC 3<legacyItalic>.x</legacyItalic> application to do this. For more information about APIs and SPIs, see the introduction to <legacyLink xlink:href="2604f492-587b-4a51-9876-59a7870b3ef2">ODBC Architecture</legacyLink>.</para>
      <para>For information about what functions and statement attributes an ODBC 3.<legacyItalic>x</legacyItalic> application should use with block and scrollable cursors, see <legacyLink xlink:href="82f6cf68-cfde-4417-9788-d6382ca14bf8">Block Cursors, Scrollable Cursors, and Backward Compatibility for ODBC 3.x Applications</legacyLink>.</para>
      <para>This section contains the following topics.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="57f65c38-d9ee-46c8-9051-128224a582c6">What the Driver Manager Does</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6">What the Driver Does</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>