---
title: Driver Version Scheme
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Version Scheme
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The following table lists all released versions of the Microsoft ODBC Driver for Oracle.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Driver version</para>
          </TD>
          <TD>
            <para>Build number    </para>
          </TD>
          <TD>
            <para>Availability history</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>1.0</para>
          </TD>
          <TD>
            <para>2.00.6235</para>
          </TD>
          <TD>
            <para>Visual C++ 4.2 and Visual Basic 5.0, Enterprise Edition</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.0</para>
          </TD>
          <TD>
            <para>2.73.7269       </para>
          </TD>
          <TD>
            <para>Visual Studio 97 and MDAC 1.5a</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.0 updated    </para>
          </TD>
          <TD>
            <para>2.73.7283.01    </para>
          </TD>
          <TD>
            <para>IIS 4.0</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.0 updated    </para>
          </TD>
          <TD>
            <para>2.73.7283.03    </para>
          </TD>
          <TD>
            <para>MDAC 1.5b and 1.5c</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.0 updated    </para>
          </TD>
          <TD>
            <para>2.73.7356       </para>
          </TD>
          <TD>
            <para>ODBC 3.5 SDK</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.5            </para>
          </TD>
          <TD>
            <para>2.573.2927      </para>
          </TD>
          <TD>
            <para>Visual Studio 6.0 and MDAC 2.0</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.5 updated</para>
          </TD>
          <TD>
            <para>2.573.3513</para>
          </TD>
          <TD>
            <para>SQL Server 7.0</para>
            <para>SQL Server 6.5 SP5</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Build 2.00.6235 (version 1) was the first release of the Microsoft ODBC Driver for Oracle. After the release of the first version, a new naming convention was adopted.</para>
    <para>For example, 2.73.7283.03 can be divided into the following distinct components:  </para>
    <list class="bullet">
      <listItem>
        <para>2 = The version number.</para>
      </listItem>
      <listItem>
        <para>73 = The version of Oracle Server for which the driver was designed.</para>
      </listItem>
      <listItem>
        <para>7283.03 = The build number of the driver.</para>
      </listItem>
    </list>
    <alert class="note">
      <para>With release 2.573.2973, the naming convention has led to some confusion that 2.573 is an earlier release than 2.73, but each section of the build number should be considered individually. The number 573 is larger than 73, so it is a newer version. Also, "2.5" indicates the driver's version number.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>