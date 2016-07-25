---
title: "AllowNullsEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: 11
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
# AllowNullsEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether records with null values are indexed.</para>
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
                <legacyBold>adIndexNullsAllow</legacyBold>             </para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>The index does allow entries in which the key columns are null. If a null value is entered in a key column, the entry is inserted into the index.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adIndexNullsDisallow</legacyBold>             </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Default. The index does not allow entries in which the key columns are null. If a null value is entered in a key column, an error will occur.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adIndexNullsIgnore</legacyBold>             </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>The index does not insert entries containing null keys. If a null value is entered in a key column, the entry is ignored and no error occurs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adIndexNullsIgnoreAny</legacyBold>             </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>The index does not insert entries where some key column has a null value. For an index having a multi-column key, if a null value is entered in some column, the entry is ignored and no error occurs.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="313b0bf7-3f37-4823-8fca-bd9c80e078a7">IndexNulls Property (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>