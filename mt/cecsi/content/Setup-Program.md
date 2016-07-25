---
title: "Setup Program"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setup Program
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>The user runs the setup program to start the setup process. The setup program is written by the application or driver developer. In addition to installing ODBC components, it can install other software. For example, application developers might use the same setup program both to install ODBC components and to install their applications.</para>
    <para>Developers can write the setup program from scratch, using the Microsoft® Windows® SDK setup utilities or setup software from other vendors. This gives those developers complete control over the setup program's look and feel. The setup program can be written to install additional software, such as an ODBC application. For more information on the Windows SDK setup utilities, see the Windows SDK documentation.</para>
    <para>How much of the installation is actually done by the setup program depends on what functions it calls in the installer DLL. The installer DLL contains functions to install individual ODBC components. The setup program simply calls <legacyBold>SQLInstallDriverManager</legacyBold>, <legacyBold>SQLInstallDriverEx</legacyBold>, or <legacyBold>SQLInstallTranslatorEx</legacyBold> in the installer DLL to retrieve the path of the directory in which the component is to be installed and to add information about the component to the registry. These functions do not actually copy files; the setup program does this using the information in the arguments of these functions.</para>
    <para>The installer DLL also contains functions to remove ODBC components. The setup program calls <legacyBold>SQLRemoveDriverManager</legacyBold>, <legacyBold>SQLRemoveDriver</legacyBold>, or <legacyBold>SQLRemoveTranslator</legacyBold> in the installer DLL to decrement a component's usage count in the registry and, if the component's new usage count falls to 0, remove all information about the component from the registry. These functions do not actually remove the files for the component; the setup program does this if the new usage count falls to 0.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>