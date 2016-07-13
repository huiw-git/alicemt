---
title: ODBC Functions Not Executed by the Cursor Library
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2941522-75eb-4db9-9468-4800b884dac2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Functions Not Executed by the Cursor Library
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The cursor library does not execute the following functions. When an application calls one of these functions, the Driver Manager invokes the driver, not the cursor library.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLGetEnvAttr</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SQLGetConnectAttr</legacyBold> </para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLSetDescRec</legacyBold> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SQLGetDiagField</legacyBold>
              </para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLSetEnvAttr</legacyBold> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SQLGetDiagRec</legacyBold> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>