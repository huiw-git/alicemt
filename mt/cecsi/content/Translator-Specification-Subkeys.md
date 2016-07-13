---
title: Translator Specification Subkeys
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Translator Specification Subkeys
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each translator listed in the ODBC Translators subkey has a subkey of its own. This subkey has the same name as the corresponding value under the ODBC Translators subkey. The values under this subkey list the full paths of the translator and translator setup DLLs and the usage count. The formats of the values are as shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Data</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Translator</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>translator-DLL-path</legacyItalic>
            </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Setup</para>
          </TD>
          <TD>
            <para>REG_SZ</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>setup-DLL-path</legacyItalic>
            </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UsageCount</para>
          </TD>
          <TD>
            <para>REG_DWORD</para>
          </TD>
          <TD>
            <para>
              <legacyItalic>count</legacyItalic>
            </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For information about usage counts, see <legacyLink xlink:href="0678aee9-8256-463c-89dd-77b1a0dfdd60">Usage Counting</legacyLink> earlier in this section.</para>
    <para>Applications should not set the usage count. ODBC will maintain this count.</para>
    <para>For example, suppose the Microsoft Code Page Translator has a translation DLL named Mscpxl32.dll, that the translator setup functions are in the same DLL, and that the translator has been installed three times. The values under the Microsoft Code Page Translator subkey might be as follows:</para>
    <code>Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL
UsageCount : REG_DWORD : 0x3</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>