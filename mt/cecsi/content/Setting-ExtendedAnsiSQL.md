---
title: Setting ExtendedAnsiSQL
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting ExtendedAnsiSQL
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The attribute can be controlled in the connection string by adding the ExtendedAnsiSQL attribute: </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Value</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>ExtendedAnsiSQL=0 (default)</para>
          </TD>
          <TD>
            <para>This setting does not enable the new features.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ExtendedAnsiSQL=1</para>
          </TD>
          <TD>
            <para>This setting enables the new features.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The attribute can also be set in a DSN through the <legacyBold>Advanced Options</legacyBold> dialog box when configuring a DSN through Control Panel.</para>
    <para>Setting the attribute to 0 disables the new features; setting it to 1 enables the new features.</para>
    <para>The attribute can also be set using SQLSetConnectAttr(). The attribute value is 65501 and is set to a SQLINTEGER value of 1 or 0, as documented in the preceding table. It can be called before or after connecting, but it is better to call it after connecting because of the order in which the driver processes cached connection attributes and connection strings.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>