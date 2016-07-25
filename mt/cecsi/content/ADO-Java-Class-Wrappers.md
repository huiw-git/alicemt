---
title: "ADO Java Class Wrappers"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
caps.latest.revision: 9
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
# ADO Java Class Wrappers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This code declares an instance of the ADO <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> class wrapper and initializes it, all on the same line of code. Further, it declares variables for each of the arguments in the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method, especially for <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> and <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> (because Java doesn't support enumerated types). It opens and closes the <legacyBold>Recordset</legacyBold> object. Setting Rs1 to NULL merely schedules that variable to be released when Java performs its systematic and intermittent release of unused objects.</para>
    <code>public static void main( String args[])
{
   msado15._Recordset   Rs1 = new msado15.Recordset();
   Variant Source     = new Variant( "SELECT * FROM Authors" );
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;
   int     Options    = -1;

   Rs1.Open( Source, Connect, LockType,  CursorType, Options );
   Rs1.Close();
   Rs1 = null;

   System.out.println( "Success!\n" );
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="f9737a65-4b2f-47fa-b026-1494dca158eb">Using ADO with the Java Type Library Wizard</link>
<link xlink:href="2d7cb5b5-8307-49dd-b07e-c07069bb1626">Using ADO with the Microsoft SDK for Java</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>