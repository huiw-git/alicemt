---
title: Affected ODBC Components
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Affected ODBC Components
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Backward compatibility describes how applications, the Driver Manager, and drivers are affected by the introduction of a new version of the Driver Manager. This affects applications and driver when either or both of them remain in the old version. There are, therefore, three types of backward compatibility to consider, as shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Type</para>
          </TD>
          <TD>
            <para>Version of DM</para>
          </TD>
          <TD>
            <para>Version of application</para>
          </TD>
          <TD>
            <para>Version of driver</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Backward Compatibility of Driver Manager</para>
          </TD>
          <TD>
            <para>3<legacyItalic>.x</legacyItalic></para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic></para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Backward Compatibility of Driver[1]</para>
          </TD>
          <TD>
            <para>3<legacyItalic>.x</legacyItalic></para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic></para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Backward Compatibility of Application</para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic></para>
          </TD>
          <TD>
            <para>3.<legacyItalic>x</legacyItalic></para>
          </TD>
          <TD>
            <para>2.<legacyItalic>x</legacyItalic></para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   The backward compatibility of drivers is primarily discussed in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    <alert class="note">
      <para>A standards-compliant application — for example, an application that has been written in accordance with the Open Group or ISO CLI standards — is guaranteed to work with an ODBC 3<legacyItalic>.x</legacyItalic> driver through the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager. It is assumed that the functionality that the application is using is available in the driver. It is also assumed that the standards-compliant application has been compiled with the ODBC 3<legacyItalic>.x</legacyItalic> header files.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>