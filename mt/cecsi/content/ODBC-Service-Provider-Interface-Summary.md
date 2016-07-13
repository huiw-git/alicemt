---
title: ODBC Service Provider Interface Summary
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Service Provider Interface Summary
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table describes ODBC Service Provider interface functions. For more information about the syntax and semantics for each function, see <legacyLink xlink:href="cdeffb4a-f344-4abe-97f3-be2ede1c8e59">ODBC Service Provider Interface (SPI) Reference</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function name</para>
          </TD>
          <TD>
            <para>Purpose</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLSetConnectAttrForDbcInfo</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Same as <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>, but it sets the attribute on the connection information token instead of on the connection handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0de28eb5-8aa9-43e4-a87f-7dbcafe800dc">SQLSetDriverConnectInfo</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Sets the connection string into the connection info token for an application’s <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> call.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLSetConnectInfo</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Sets the data source, user ID, and password into the connection info token for an application’s <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> call.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLGetPoolID</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Retrieves the pool ID.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLRateConnection</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Determines if a driver can reuse an existing connection in the connection pool.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLPoolConnect</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Create a new connection if no connection in the pool can be reused.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0d87fcac-30a0-4303-ad8f-a5b53f4b428d">SQLCleanupConnectionPoolID</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Informs a driver that a pool ID was timed out.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>