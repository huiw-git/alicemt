---
title: "ParentCatalog Property (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
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
# ParentCatalog Property (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the parent catalog of a Table, User, or Column object to provide access to provider-specific properties.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets and returns a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink> object. Setting <unmanagedCodeEntityReference>ParentCatalog</unmanagedCodeEntityReference> to an open <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> allows access to provider-specific properties prior to appending a table or column to a <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> collection.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Some data providers allow provider-specific property values to be written only at creation: that is, when a table or column is appended to its <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> collection. To access these properties before appending these objects to a <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference>, specify the <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> in the <unmanagedCodeEntityReference>ParentCatalog</unmanagedCodeEntityReference> property first.</para>
      <para>An error occurs when the table or column is appended to a different <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> than the <unmanagedCodeEntityReference>ParentCatalog</unmanagedCodeEntityReference>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User Object (ADOX)</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="448bc850-7584-4c5f-89f3-5f4fee88b259">ParentCatalog Property Example (VB)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>