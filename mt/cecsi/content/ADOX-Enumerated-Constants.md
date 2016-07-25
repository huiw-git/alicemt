---
title: "ADOX Enumerated Constants"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
caps.latest.revision: 8
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
# ADOX Enumerated Constants
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To assist debugging, the ADOX enumerated constants list a value for each constant. However, this value is purely advisory, and may change from one release of ADOX to another. Your code should only depend on the name, not the actual value, of enumerated constants.</para>
  </introduction>
  <section>
    <content>
      <para>The following enumerated constants are defined.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Enumeration</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="f948febd-c885-4621-823b-421e116fec4e">ActionEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the type of action to be performed when <legacyBold>SetPermissions</legacyBold> is called.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="6acf3689-1a7f-4379-9d7f-df452ccbac27">AllowNullsEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies whether records with null values are indexed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="cd0db27a-1080-40af-a491-3893e7bef9cd">ColumnAttributesEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies characteristics of a <legacyBold>Column</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the data type of a <legacyBold>Field</legacyBold>, <legacyBold>Parameter</legacyBold>, or <legacyBold>Property</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="c2f6ce79-c4b3-4d40-ac95-21025208f991">InheritTypeEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies how objects will inherit permissions set with <legacyBold>SetPermissions</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="3e597c52-caf4-4341-8471-d1ade563dbf7">KeyTypeEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the type of <legacyBold>Key</legacyBold>: primary, foreign, or unique.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="3fdecfca-aa91-4596-ad98-610f1b7f840b">ObjectTypeEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the type of database object for which to set permissions or ownership.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="55ee67c7-a583-42aa-849a-78264b4cb614">RightsEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the rights or permissions for a group or user on an object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="738fd3ff-3daf-483d-a0b9-88bef1be54c1">RuleEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the rule to follow when a <legacyBold>Key</legacyBold> is deleted.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyLink xlink:href="0b9d46e7-29d9-4ca1-a23a-056403106a71">SortOrderEnum</legacyLink>
            </para>
            </TD>
            <TD>
              <para>Specifies the sort sequence for an indexed column.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ef700465-2e97-46e8-8213-2d662501e540">ADOX API Reference</link>
<link xlink:href="c6579b5b-a93e-48c5-8847-743fc4590cd2">Microsoft ADOX Programmer's Reference</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>