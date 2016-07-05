---
title: Types of Changes
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
translation.priority.ht: 
  - en-gb
---
# Types of Changes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Three types of changes are made in ODBC 3.<legacyItalic>x</legacyItalic> (and any version of ODBC). Each of these affects backward compatibility differently and is handled in a different way. These changes are described in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Type of change</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>New features</para>
          </TD>
          <TD>
            <para>These are features that are new to ODBC 3.<legacyItalic>x</legacyItalic>, such as out-of-line binding or descriptors. These are implemented only when the application and driver, as well as the Driver Manager, are of version 3<legacyItalic>.x</legacyItalic>, so there is no attempt to make these backward compatible.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Duplicated features</para>
          </TD>
          <TD>
            <para>These are features that exist in ODBC 2<legacyItalic>.x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic> but are implemented in different ways in each. The functions <legacyBold>SQLAllocHandle</legacyBold> and <legacyBold>SQLAllocStmt</legacyBold> are an example. Backward compatibility issues for these and other duplicated features are mostly handled by mappings in the Driver Manager.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Behavioral changes</para>
          </TD>
          <TD>
            <para>These are features that are handled differently in ODBC 2<legacyItalic>.x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic>. A datetime <legacyBold>#define</legacyBold> is an example. These features are handled by the ODBC 3.<legacyItalic>x</legacyItalic> driver based on an environment attribute setting. (See <legacyLink xlink:href="a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67">Behavioral Changes</legacyLink> for more information.)</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>