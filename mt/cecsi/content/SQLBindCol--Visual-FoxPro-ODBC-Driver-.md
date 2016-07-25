---
title: "SQLBindCol (Visual FoxPro ODBC Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 984d6605-39ba-4d33-ac94-22625bfa6107
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBindCol (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Assigns storage space for a result column and specifies the type of the result. When <legacyLink xlink:href="6198a006-6f25-4328-8403-2aba29b7041f">SQLFetch</legacyLink> or <legacyLink xlink:href="b28af112-fb47-4143-b11e-3b743b2ae1b8">SQLExtendedFetch</legacyLink> is called, the driver places the data for all bound columns in the assigned locations. See <legacyLink xlink:href="5f25e20b-a4ef-42da-aeb6-00e0510fb1cc">SQLGetTypeInfo</legacyLink> for the mapping between ODBC and Visual FoxPro data types.</para>
    <para>For more information, see <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>