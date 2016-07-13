---
title: Installer DLL API Reference Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47fcadc3-f102-4989-9ee7-a1c65233142a
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Installer DLL API Reference Function
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section describes the syntax of the functions in the installer DLL API. The installer DLL API consists of 20 functions. Three of these functions, <legacyBold>SQLGetTranslator</legacyBold>, <legacyBold>SQLRemoveDSNFromIni</legacyBold>, and <legacyBold>SQLWriteDSNToIni</legacyBold>, are called only by setup DLLs. The other functions are called by the setup and administration programs.</para>
    <para>Each function is labeled with the version of ODBC in which it was introduced.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>           <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="4f681961-ac9f-4d88-b065-5258ba112642">SQLConfigDriver Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="76ee851a-dca9-40cc-8e9e-eb3f74e560ee">SQLCreateDataSource Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="b96ab3b8-08d5-4fea-9ffe-e03043efbf2d">SQLGetConfigMode Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="a1983a2e-0edf-422e-bd1b-ec5db40a34bc">SQLGetInstalledDrivers Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="b72ca065-4d67-48df-baac-e18379a8320a">SQLGetPrivateProfileString Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="33879db3-5ef9-4585-9be5-69376157e017">SQLGetTranslator Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="1dd74544-f4e9-46e1-9b5f-c11d84fdab4c">SQLInstallDriverEx Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="aebc439b-fffd-4d98-907a-0163f79aee8d">SQLInstallDriverManager Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="e6474b79-4d55-458f-81ce-abfafe357f83">SQLInstallerError Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="453b21ff-3c2b-4069-8ff7-5c727f062d89">SQLInstallTranslator Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="a0630602-53c1-4db0-98ce-70d160aedf8d">SQLInstallTranslatorEx Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="ac6d186f-b394-406c-94c4-c6331d1ca468">SQLManageDataSources Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="4c60d827-b2d2-4f27-b220-daa9e1fcdd8d">SQLPostInstallerError Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="ead464aa-cdc3-47dd-a0c0-997711205d31">SQLReadFileDSN Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="db803266-57df-4864-a41b-901247549c1f">SQLRemoveDefaultDataSource Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="9a3b4f8b-982b-44b9-ade6-754ff026dc90">SQLRemoveDriver Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="3a41511f-6603-4b81-a815-7883874023c4">SQLRemoveDriverManager Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="bb2e8273-7b61-4113-bfc8-f7ccc607c811">SQLRemoveDSNFromIni Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="c6feda49-0359-4224-8de9-77125cf2397b">SQLRemoveTranslator Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="09eb88ea-b6f6-4eca-b19d-0951cebc6c0a">SQLSetConfigMode Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="930d1d89-337a-4429-85a2-84ee10555ac9">SQLValidDSN Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="dc7018b2-18d4-4657-96d0-086479a47474">SQLWriteDSNToIni Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="9e18f56f-1061-416b-83d4-ffeec42ab5a9">SQLWriteFileDSN Function</legacyLink>         </para>
      </listItem>
      <listItem>
        <para>           <legacyLink xlink:href="526f36a4-92ed-4874-9725-82d27c0b86f9">SQLWritePrivateProfileString Function</legacyLink>         </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerOrientationDocument>