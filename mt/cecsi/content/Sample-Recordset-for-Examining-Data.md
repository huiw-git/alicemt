---
title: "Sample Recordset for Examining Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
caps.latest.revision: 12
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
# Sample Recordset for Examining Data
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>First, let's look at the <legacyBold>Recordset</legacyBold> object as returned using the following SQL query, executed against the Northwind sample data base in Microsoft SQL Server. </para>
    <code>SELECT ProductID,ProductName,UnitPrice 
FROM Products 
WHERE CategoryID = 7  </code>
    <para>The resultant <legacyBold>Recordset</legacyBold> object contains all the produces in the database shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ProductID</para>
          </TD>
          <TD>
            <para> ProductName </para>
          </TD>
          <TD>
            <para> UnitPrice</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>7</para>
          </TD>
          <TD>
            <para>Uncle Bob's Organic Dried Pears</para>
          </TD>
          <TD>
            <para>30.0000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>14</para>
          </TD>
          <TD>
            <para>Tofu</para>
          </TD>
          <TD>
            <para>23.2500</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>28</para>
          </TD>
          <TD>
            <para>Rssle Sauerkraut</para>
          </TD>
          <TD>
            <para>45.6000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>51</para>
          </TD>
          <TD>
            <para>Manjimup Dried Apples</para>
          </TD>
          <TD>
            <para>53.0000</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>74</para>
          </TD>
          <TD>
            <para>Longlife Tofu</para>
          </TD>
          <TD>
            <para>10.0000</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>If you are interested in getting these results yourself, try the following JScript example:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="74aad8a6-06cc-4a2c-811a-d78f9b741d84">JScript Example to Return a Recordset</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>