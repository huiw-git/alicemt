---
title: "Translator Setup DLLs"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Translator Setup DLLs
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>The translator setup DLL contains the <legacyBold>ConfigTranslator</legacyBold> function, which returns the default option for a translator. If necessary, it prompts the user for this information. For a complete description of this function, see <legacyLink xlink:href="f9d03f17-1c0d-4e7c-9c04-8c316e07ef25">Setup DLL API Reference</legacyLink>.</para>
    <para>The translator setup DLL is written by the translator developer. It can be part of the translator DLL or a separate DLL.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>