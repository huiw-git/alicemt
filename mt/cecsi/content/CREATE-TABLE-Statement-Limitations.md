---
title: "CREATE TABLE Statement Limitations"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# CREATE TABLE Statement Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the Microsoft Access, Microsoft Excel, or Paradoxdriver is used, and the length of a text or binary column is not specified (or is specified as 0), the column length will be set to 255.</para>
    <para>When the dBASE driver is used, and the length of a text or binary column is not specified (or is specified as 0), the column length will be set to 254.</para>
    <para>A maximum of 255 columns is supported.</para>
    <para>When the Microsoft Excel driver is used on a MicrosoftExcel 5.0, 7.0, or 97 data source, a worksheet cannot be created with the same name as a worksheet that was previously dropped. When the Microsoft Excel driver is used to access a version 5.0, 7.0, or 97 worksheet, a DROP TABLE statement clears the worksheet, but does not delete the worksheet name.</para>
    <para>When the Paradox driver is used, columns cannot be added once an index has been defined on a table. If the first column of the argument list of a CREATE TABLE statement creates an index, a second column cannot be included in the argument list.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>