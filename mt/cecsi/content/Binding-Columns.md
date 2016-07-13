---
title: Binding Columns
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Binding Columns
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data fetched from the data source is returned to the application in variables that the application has allocated for this purpose. Before this can be done, the application must associate, or <legacyItalic>bind</legacyItalic>, these variables to the columns of the result set; conceptually, this process is the same as binding application variables to statement parameters. When the application binds a variable to a result set column, it describes that variable — address, data type, and so on — to the driver. The driver stores this information in the structure it maintains for that statement and uses the information to return the value from the column when the row is fetched.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="4bc9c30f-83ae-4766-a746-032953c187ad">Binding Result Set Columns</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="17277ab3-33ad-44d3-a81c-a26b5e338512">Using SQLBindCol</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>