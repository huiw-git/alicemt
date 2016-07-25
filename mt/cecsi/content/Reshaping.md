---
title: "Reshaping"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
caps.latest.revision: 13
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
# Reshaping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyBold>Recordset</legacyBold> created by a clause of a shape command may be assigned an <legacyItalic>alias</legacyItalic> name (typically with the AS keyword). The alias of a shaped <legacyBold>Recordset</legacyBold> can be referenced in a completely different command. That is, you can reuse, or <legacyItalic>reshape</legacyItalic>, a previously shaped <legacyBold>Recordset</legacyBold> in a new shape command. To support this feature, ADO provides a property, <legacyLink xlink:href="690229d1-46cc-42e6-a57d-4438251fe248">Reshape Name</legacyLink>.</para>
    <para>Reshaping has two main functions. The first is to associate an existing <legacyBold>Recordset</legacyBold> with a new parent <legacyBold>Recordset</legacyBold>.</para>
  </introduction>
  <codeExample>
    <code>rs1.Open "SHAPE {select * from Customers} " &amp; _
         "APPEND ({select * from Orders} AS <codeFeaturedElement>chapOrders</codeFeaturedElement> " &amp; _
         "RELATE CustomerID to CustomerID)", cn

rs2.Open "SHAPE {select * from Employees} " &amp; _
         "APPEND (<codeFeaturedElement>chapOrders</codeFeaturedElement> RELATE EmployeeID to EmployeeID)", cn</code>
    <comments>
      <content>
        <para>The second function is to enable non-chaptered access to existing child <legacyBold>Recordset</legacyBold> objects, using the syntax "SHAPE &lt;recordset reshape name&gt;".</para>
        <alert class="note">
          <para>You cannot append columns to an existing <legacyBold>Recordset</legacyBold>, reshape a parameterized <legacyBold>Recordset</legacyBold> or the <legacyBold>Recordset</legacyBold> objects in any intervening COMPUTE clause, or perform aggregate operations on any <legacyBold>Recordset</legacyBold> descendant from the <legacyBold>Recordset</legacyBold> being reshaped. The <legacyBold>Recordset</legacyBold> being reshaped and the new shape command must both use the same <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>.</para>
        </alert>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="1bfdcad4-52e1-45bc-ad21-783657ef0a44">Data Shaping</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>