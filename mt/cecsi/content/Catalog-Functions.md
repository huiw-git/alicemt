---
title: "Catalog Functions"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Catalog Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All databases have a structure that outlines how data will be stored in the database. For example, a simple sales order database might have the structure shown in the following illustration, in which the ID columns are used to link the tables.</para>
    <mediaLink>
      <image xlink:href="e59b759e-5d3b-4b86-ae10-b208f766908b" />
    </mediaLink>
    <para>This structure, along with other information such as privileges, is stored in a set of system tables called the database's <legacyItalic>catalog,</legacyItalic> which is also known as a <legacyItalic>data dictionary</legacyItalic>.</para>
    <para>An application can discover this structure through calls to the <legacyItalic>catalog functions</legacyItalic>. The catalog functions return information in result sets and are usually implemented through <legacyBold>SELECT</legacyBold> statements against the tables in the catalog. For example, an application might request a result set containing information about all the tables on the system or all the columns in a particular table.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="d5915d0c-eec3-4382-850e-bd863763c99a">Uses of Catalog Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para> <legacyLink xlink:href="4f28f557-7eca-4905-aa6d-45a6cf501a66">Catalog Functions in ODBC</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>