---
title: "ObjectTypeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 10
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
# ObjectTypeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the type of database object for which to set permissions or ownership.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
            <TD>
              <para>Value</para>
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
                <legacyBold>adPermObjColumn</legacyBold>             </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>The object is a column.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adPermObjDatabase</legacyBold>             </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>The object is a database.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adPermObjProcedure</legacyBold>             </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>The object is a procedure.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adPermObjProviderSpecific</legacyBold>             </para>
            </TD>
            <TD>
              <para>-1</para>
            </TD>
            <TD>
              <para>The object is a type defined by the provider. An error will occur if the <legacyItalic>ObjectType</legacyItalic> parameter is <legacyBold>adPermObjProviderSpecific</legacyBold> and an <legacyItalic>ObjectTypeId</legacyItalic> is not supplied.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adPermObjTable</legacyBold>             </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>The object is a table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adPermObjView</legacyBold>             </para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para>The object is a view.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="8965adf0-9075-4125-8142-73eb700029c3">GetObjectOwner Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions Method</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="e5170a37-9d6e-43db-bfb6-9b6631fa3048">SetObjectOwner Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions Method</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>