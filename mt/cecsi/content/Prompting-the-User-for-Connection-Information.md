---
title: "Prompting the User for Connection Information"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Prompting the User for Connection Information
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If the application uses <legacyBold>SQLConnect</legacyBold> and needs to prompt the user for any connection information, such as a user name and password, it must do so itself. While this allows the application to control its "look and feel," it might force the application to contain driver-specific code. This occurs when the application needs to prompt the user for driver-specific connection information. This presents an impossible situation for generic applications, which are designed to work with any and all drivers, including drivers that do not exist when the application is written.</para>
    <para>
      <legacyBold>SQLDriverConnect</legacyBold> can prompt the user for connection information. For example, the custom program mentioned earlier could pass the following connection string to <legacyBold>SQLDriverConnect</legacyBold>:</para>
    <code>DSN=XYZ Corp;</code>
    <para>The driver might then display a dialog box that prompts for user IDs and passwords, similar to the following illustration.</para>
    <mediaLink>
      <image xlink:href="9aaa6908-7840-4b7d-8037-e06060a60547" />
    </mediaLink>
    <para>That the driver can prompt for connection information is particularly useful to generic and vertical applications. These applications should not contain driver-specific information, and having the driver prompt for the information it needs keeps that information out of the application. This is shown by the previous two examples. When the application passed only the data source name to the driver, the application did not contain any driver-specific information and was therefore not tied to a particular driver. When the application passed a complete connection string to the driver, it was tied to the driver that could interpret that string.</para>
    <para>A generic application might take this one step further and not even specify a data source. When <legacyBold>SQLDriverConnect</legacyBold> receives an empty connection string, the Driver Manager displays the following dialog box.</para>
    <mediaLink>
      <image xlink:href="ce2f3908-5617-4dee-8f8a-226de019bae0" />
    </mediaLink>
    <para>After the user selects a data source, the Driver Manager constructs a connection string specifying that data source and passes it to the driver. The driver can then prompt the user for any additional information it needs.</para>
    <para>The conditions under which the driver prompts the user are controlled by the <legacyItalic>DriverCompletion</legacyItalic> flag; there are options to always prompt, prompt if necessary, or never prompt. For a complete description of this flag, see the <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>