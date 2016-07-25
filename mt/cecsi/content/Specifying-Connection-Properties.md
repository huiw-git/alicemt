---
title: "Specifying Connection Properties"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 14
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Specifying Connection Properties
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can supply much of the information specified by a <legacyLink xlink:href="14eae122-2d1e-40c8-b88e-b7cb8dfbc93b">connection string</legacyLink> by setting properties of the <legacyBold>Connection</legacyBold> object before opening the connection. For example, you could achieve the same effect as the connection string discussed in <link xlink:href="14eae122-2d1e-40c8-b88e-b7cb8dfbc93b">Creating a Connection string</link> by using the following code.</para>
    <code>With objConn
.Provider = "SQLOLEDB"
.Properties("Data Source") = "MySqlServer"
   .Properties("Integrated Security") = "SSPI"
.Open
.DefaultDatabase = "Northwind"
End With</code>
    <para>DefaultDatabase is set only after you open the connection.</para>
    <alert class="note">
      <para>In ADO you must not use a password containing semicolons (";") unless the password is enclosed in single quotation marks.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>