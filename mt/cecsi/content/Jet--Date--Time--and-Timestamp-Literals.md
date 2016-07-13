---
title: Jet: Date, Time, and Timestamp Literals
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Jet: Date, Time, and Timestamp Literals
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>For maximum interoperability, applications should pass date literals in the ODBC canonical format using escape-clause syntax: 

</para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>For date literals, {d '<legacyItalic>value</legacyItalic>'}, where <legacyItalic>valu</legacyItalic>e is in the form "yyyy-mm-dd"</para>
        </listItem>
        <listItem>
          <para>For time literals, {t '<legacyItalic>value</legacyItalic>'}, where <legacyItalic>valu</legacyItalic>e is in the form "hh:mm:ss"</para>
        </listItem>
      </list>
      <para>For timestamp literals {ts '<legacyItalic>value</legacyItalic>'}, where <legacyItalic>valu</legacyItalic>e is in the form "yyyy-mm-dd hh:mm:ss[.f...]". </para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>