---
title: "InheritTypeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
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
# InheritTypeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies how objects will inherit permissions set with <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink>.</para>
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
                <legacyBold>adInheritBoth</legacyBold>             </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Both objects and other containers contained by the primary object inherit the entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adInheritContainers</legacyBold>             </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Other containers that are contained by the primary object inherit the entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adInheritNone</legacyBold>             </para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>Default. No inheritance occurs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adInheritNoPropagate</legacyBold>             </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>The <legacyBold>adInheritObjects</legacyBold> and <legacyBold>adInheritContainers</legacyBold> flags are not propagated to an inherited entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adInheritObjects</legacyBold>             </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Non-container objects in the container inherit the permissions.</para>
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
        <link xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions Method (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>