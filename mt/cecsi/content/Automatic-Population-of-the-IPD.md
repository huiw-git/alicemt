---
title: Automatic Population of the IPD
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Automatic Population of the IPD
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Some drivers are capable of setting the fields of the IPD after a parameterized query has been prepared. The descriptor fields are automatically populated with information about the parameter, including the data type, precision, scale, and other characteristics. This is equivalent to supporting <legacyBold>SQLDescribeParam</legacyBold>. This information can be particularly valuable to an application when it has no other way to discover it, such as when an ad hoc query is performed with parameters that the application does not know about.</para>
    <para>An application determines whether the driver supports automatic population by calling <legacyBold>SQLGetConnectAttr</legacyBold> with an <legacyItalic>Attribute</legacyItalic> of SQL_ATTR_AUTO_IPD. If SQL_TRUE is returned, the driver supports it and the application can enable it by setting the SQL_ATTR_ENABLE_AUTO_IPD statement attribute to SQL_TRUE.</para>
    <para>When automatic population is supported and enabled, the driver populates the fields of the IPD after an SQL statement containing parameter markers has been prepared by a call to <legacyBold>SQLPrepare</legacyBold>. An application can retrieve this information by calling <legacyBold>SQLGetDescField</legacyBold> or <legacyBold>SQLGetDescRec</legacyBold>, or <legacyBold>SQLDescribeParam</legacyBold>. The application can use the information to bind the most appropriate application buffer for a parameter or to specify a data conversion for it.</para>
    <para>Automatic population of the IPD might produce a performance penalty. An application can turn it off by resetting the SQL_ATTR_ENABLE_AUTO_IPD statement attribute to SQL_FALSE (the default value).</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>