---
title: ODBC Driver Architecture
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Driver Architecture
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Driver writers must be aware that the driver architecture can affect whether an application can use DBMS-specific SQL.</para>
    <mediaLink>
      <image xlink:href="a7e36702-e367-4d10-803c-b6fa7e2dc4b9" />
    </mediaLink>
    <para>
      <legacyLink xlink:href="d92e0c5c-d176-4282-bbe1-d449e2223d50">File-based Drivers</legacyLink>
    </para>
    <para>When the driver accesses the physical data directly, the driver acts as both driver and data source. The driver must process both ODBC calls and SQL statements. Developers of file-based drivers must write their own database engines.</para>
    <para>
      <legacyLink xlink:href="e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330">DBMS-Based Drivers</legacyLink>
    </para>
    <para>When a separate database engine is used to access physical data, the driver processes only ODBC calls. It passes SQL statements to the database engine for processing. </para>
    <para>
      <legacyLink xlink:href="e14ae90f-87b3-4bcf-b69a-1773e2c2a1c5">Network Architecture</legacyLink>
    </para>
    <para>File and DBMS ODBC configurations can exist on a single network.</para>
    <para>
      <legacyLink xlink:href="1cad06ee-5940-4361-8d01-7d850db1dd66">Other Driver Architectures</legacyLink>
    </para>
    <para>When a driver is required to work with a variety of data sources, it can be used as middleware. Heterogeneous join engine architecture can make the driver appear as a driver manager. Drivers can also be installed on servers, where they can be shared by a series of clients.</para>
    <para>For more information about driver architecture, see <legacyLink xlink:href="559e4de1-16c9-4998-94f5-6431122040cd">Driver Manager</legacyLink> and <legacyLink xlink:href="c5003413-0cc1-4f41-b877-a64e2f5ab118">Driver Architecture</legacyLink> in the section on <link xlink:href="2604f492-587b-4a51-9876-59a7870b3ef2">ODBC Architecture</link>. </para>
    <para>More information about driver issues can be found in the locations described in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Issue</para>
          </TD>
          <TD>
            <para>Topic</para>
          </TD>
          <TD>
            <para>Location</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Compatibility issues with applications and drivers</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="23ed7f5e-e945-4c36-9dbc-e0f93b6d23c5">Application/Driver Compatibility</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="6a1b7b7e-5d08-4df8-aa4a-688da7da1b30">Programming Considerations</link>, in the ODBC Programmer's Reference</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Writing ODBC drivers</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="9b75f59b-623f-4711-9ca2-e751b3622e00">Writing ODBC 3.x Drivers</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="6a1b7b7e-5d08-4df8-aa4a-688da7da1b30">Programming Considerations</link>, in the ODBC Programmer's Reference</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Driver guidelines for backward compatibility</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="911cd335-f2c0-4d03-9739-1078308a678a">Driver Guidelines for Backward Compatibility</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="911cd335-f2c0-4d03-9739-1078308a678a">Appendix G: Driver Guidelines for Backward Compatibility</link>, in the ODBC Programmer's Reference</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Connecting to a driver</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="e93027ab-9e60-47b7-ba96-8289dae32a22">Connecting to a Data Source or Driver</link>, in the ODBC Programmer's Reference</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Identifying drivers</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="6d43ae52-c6f8-4f07-8911-4d5278dd439e">Viewing Drivers</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="6d43ae52-c6f8-4f07-8911-4d5278dd439e">Viewing Drivers</link>, in the Microsoft ODBC Data Source Administrator online Help</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Enabling connection pooling </para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="ee95ffdb-5aa1-49a3-beb2-7695b27c3df9">ODBC Connection Pooling</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="e93027ab-9e60-47b7-ba96-8289dae32a22">Connecting to a Data Source or Driver</link>, in the ODBC Programmer's Reference</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Unicode/ANSI driver and connection issues</para>
          </TD>
          <TD>
            <para>
              <legacyLink xlink:href="3b4742d5-74fb-4aff-aa21-d83a0064d73d">Unicode Drivers</legacyLink>
            </para>
          </TD>
          <TD>
            <para>
              <link xlink:href="6a1b7b7e-5d08-4df8-aa4a-688da7da1b30">Programming Considerations</link>, in the ODBC Programmer's Reference</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
  </relatedTopics>
</developerConceptualDocument>