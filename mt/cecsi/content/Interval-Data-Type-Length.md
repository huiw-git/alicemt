---
title: "Interval Data Type Length"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Interval Data Type Length
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following rules are used to determine the length of an interval data type in characters. Length is expressed in number of characters. The number of bytes depends upon the character set. The length includes the following values added together:  </para>
    <list class="bullet">
      <listItem>
        <para>Two characters for every field in the interval that is not the leading field.</para>
      </listItem>
      <listItem>
        <para>For the leading field, the number of characters that is the express or implicit leading precision. If the leading precision is not specified, the default value is 2.</para>
      </listItem>
      <listItem>
        <para>One character for the separator between the fields.</para>
      </listItem>
      <listItem>
        <para>One plus the express or implied seconds precision. If the seconds precision is not specified, the default value is 6.</para>
      </listItem>
    </list>
    <para>Specific column length values for each interval data type are contained in <legacyLink xlink:href="541b83ab-b16d-4714-bcb2-3c3daa9a963b">Column Size</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>