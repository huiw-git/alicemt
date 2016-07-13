---
title: Appendix G: Driver Guidelines for Backward Compatibility
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Appendix G: Driver Guidelines for Backward Compatibility
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This appendix provides information for driver writers working on ODBC 3.<legacyItalic>x</legacyItalic> drivers that need to support ODBC 2.<legacyItalic>x</legacyItalic> applications. For more information about backward compatibility, see <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>This section contains the following topics.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility for ODBC 3.x Drivers</legacyLink>
					— New features are features that exist in ODBC 3.<legacyItalic>x</legacyItalic> and not in ODBC 2.<legacyItalic>x</legacyItalic>. ODBC 3.<legacyItalic>x</legacyItalic> drivers generally do not have to worry about backward compatibility with new features because ODBC 2.<legacyItalic>x</legacyItalic> applications never use them. The sole exceptions to this are features related to <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLSetPos</legacyBold>, and <legacyBold>SQLExtendedFetch</legacyBold>; for more information, see , later in this appendix.</para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="ee462617-1d79-4c88-afeb-b129cff34cc6">Mapping Deprecated Functions</legacyLink>
					— Duplicated features are features that are implemented differently in ODBC 3.<legacyItalic>x</legacyItalic> and ODBC 2.<legacyItalic>x</legacyItalic>. ODBC 3.<legacyItalic>x</legacyItalic> drivers do not have to worry about backward compatibility with duplicated features because the Driver Manager always maps ODBC 2.<legacyItalic>x</legacyItalic> features to ODBC 3.<legacyItalic>x</legacyItalic> features when calling an ODBC 3.<legacyItalic>x</legacyItalic> driver. Thus, an ODBC 3.<legacyItalic>x</legacyItalic> driver sees only ODBC 3.<legacyItalic>x</legacyItalic> features. For more information about these mappings, see , later in this appendix.</para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="88a503cc-bff7-42d9-83ff-8e232109ed06">Behavioral Changes and ODBC 3.x Drivers</legacyLink>
					— Behavior changes are features that are handled differently in ODBC 3.<legacyItalic>x</legacyItalic> and ODBC 2.<legacyItalic>x</legacyItalic>. ODBC 3.<legacyItalic>x</legacyItalic> drivers have to worry about behavior changes and act in response to the SQL_ATTR_ODBC_VERSION environment attribute set by the application. </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>