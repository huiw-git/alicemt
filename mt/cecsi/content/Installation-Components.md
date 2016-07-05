---
title: Installation Components
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
translation.priority.ht: 
  - en-gb
---
# Installation Components
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>The installation process starts when the user runs the setup program. The setup program works in conjunction with the <legacyItalic>installer DLL</legacyItalic> and a <legacyItalic>driver setup DLL</legacyItalic> for each driver. Both the setup program and the installer DLL use the arguments in the <legacyBold>SQLInstallDriverEx</legacyBold> and <legacyBold>SQLInstallTranslatorEx</legacyBold> functions to determine which files to copy or delete for each component. The following illustration shows the relationship between these installation components.</para>
    <mediaLink>
      <image xlink:href="21782d1d-7819-40da-be3c-0027ca351cb2" />
    </mediaLink>
    <alert class="important">
      <para>The Odbc.inf file that was used in ODBC 2.<legacyItalic>x</legacyItalic> to describe the files required by each ODBC component is not used in ODBC 3<legacyItalic>.x</legacyItalic>. Drivers that ship ODBC 3<legacyItalic>.x</legacyItalic> components do not need to create an Odbc.inf file. The removal of <legacyBold>SQLInstallDriver</legacyBold> and <legacyBold>SQLInstallODBC</legacyBold>, and the deprecation of <legacyBold>SQLInstallTranslator</legacyBold>, have rendered Odbc.inf unnecessary. The driver information that used to be in the Driver Keyword sections of Odbc.inf is now provided in the <legacyItalic>lpszDriver</legacyItalic> argument in <legacyBold>SQLInstallDriverEx</legacyBold>. The translator information that used to be in the [ODBC Translator] and Translator Specification sections of Odbc.inf is now provided in the <legacyItalic>lpszTranslator</legacyItalic> argument of <legacyBold>SQLInstallTranslatorEx</legacyBold>. These changes allow the ODBC Installer to be more portable across platforms.</para>
    </alert>
    <para>For more information about these components, see the following topics at the end of this section.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="9cc5d75d-b293-41e5-927c-10f4af2e7af1">Setup Program</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e2b92afb-64ce-4ce0-84ad-6a4276646e68">Installer DLL</legacyLink> </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="49bab021-81fa-402e-b7a4-a5214f1fadc4">Driver Setup DLL</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>