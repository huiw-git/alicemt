---
title: Microsoft ODBC Desktop Database Drivers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e505c65-a8dd-4283-ae28-313d8a3aa046
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Microsoft ODBC Desktop Database Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC is an API that uses Structured Query Language (SQL) as the database access language. You can access a wide variety of database management systems (DBMSs) with the same ODBC source code that is directly incorporated into an application's source code. With the Microsoft ODBC Desktop Database Drivers, a user of an ODBC-enabled application can open, query, and update a desktop database through the ODBC interface.</para>
    <para>The Microsoft ODBC Desktop Database Drivers are a Microsoft Jet-based set of ODBC drivers. Whereas Microsoft ODBC Desktop Database Drivers 2.0 include both 16-bit and 32-bit drivers, versions 3.0 and later include only 32-bit drivers that work on Windows 95 or later, Windows NT Workstation or Server version 4.0, Windows 2000 Professional, or Windows 2000 Server. These drivers provide access to the following types of data sources:  </para>
    <list class="bullet">
      <listItem>
        <para>Microsoft Access</para>
      </listItem>
      <listItem>
        <para>Microsoft Excel</para>
      </listItem>
      <listItem>
        <para>Paradox</para>
      </listItem>
      <listItem>
        <para>dBASE</para>
      </listItem>
      <listItem>
        <para>Text</para>
      </listItem>
    </list>
    <para>See <legacyLink xlink:href="27359133-dd41-478f-8902-996022deb845">Visual FoxPro ODBC Driver</legacyLink> for detailed documentation about the Microsoft Visual FoxPro® ODBC Driver. </para>
    <alert class="note">
      <para>Access to other data sources, such as Lotus 1-2-3, Microsoft Exchange, and HTML, is enabled by installable ISAM (IISAM) drivers. For more information about these drivers, see "Accessing External Data" in the <legacyItalic>Microsoft Jet Database Engine Programmer's Reference</legacyItalic>. ODBC Desktop Database Drivers 4.0 do not support Btrieve and EMS data formats.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="8b4d13f7-ab37-40b4-a9c6-145e7385352f">Desktop Database Drivers Architecture</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b4a2aff8-bde7-4bd5-8580-bc50f27311c8">History of the Desktop Database Drivers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="585c41c6-5c5a-437e-a4b4-e32a346b478d">Product Support</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a8bf304b-eff1-447c-887c-dabdb5353a2d">Implementing Desktop Database Drivers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="2d2f09c0-18ef-45a4-a72a-d7a3bdcef646">Microsoft Access Driver Programming Considerations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="d3cf324c-aa52-47a6-b44a-a59a778fad23">Microsoft Excel Driver Programming Considerations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="327e952b-e7d5-4209-9423-f4b49cea272f">Paradox Driver Programming Considerations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ce5e8efc-6a2d-40d5-a658-8dd35cd1dd09">dBASE Driver Programming Considerations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="aabff9d9-20ea-4b68-b8fd-1e33061bd0ef">Text File Driver Programming Considerations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="2ead7727-3245-4c2b-91f5-ed946ef4edf5">Additional Supported ODBC SQL Grammar</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b8d71c2a-23c8-4e9b-b5f7-aca51c5a4721">Limitations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="33542afe-4dc7-4db8-b625-fec51a4718d3">ODBC Errors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b28a8ed6-09b1-4acf-bf3e-f90bb32422de">Supported ODBC API Functions</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>