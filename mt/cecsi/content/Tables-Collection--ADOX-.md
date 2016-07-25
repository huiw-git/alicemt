---
title: "Tables Collection (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
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
# Tables Collection (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> objects of a catalog.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append</legacyLink> method for a <legacyBold>Tables</legacyBold> collection is unique for ADOX. You can:  </para>
      <list class="bullet">
        <listItem>
          <para>Add a new table to the collection with the <unmanagedCodeEntityReference>Append</unmanagedCodeEntityReference> method.</para>
        </listItem>
      </list>
      <para>The remaining properties and methods are standard to ADO collections. You can:  </para>
      <list class="bullet">
        <listItem>
          <para>Access a table in the collection with the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the number of tables contained in the collection with the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Remove a table from the collection with the <legacyLink xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Update the objects in the collection to reflect the current database schema with the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method.</para>
        </listItem>
      </list>
      <para>Some providers may return other schema objects, such as a view, in the <unmanagedCodeEntityReference>Tables</unmanagedCodeEntityReference> collection. Therefore, some ADOX collections may contain multiple references to the same object. Should you delete the object from one collection, the change will not be visible in another collection that references the deleted object until the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method is called on the collection. For example, with the OLE DB Provider for Microsoft Jet, views are returned with the <unmanagedCodeEntityReference>Tables</unmanagedCodeEntityReference> collection. If you drop a view, you must refresh the <unmanagedCodeEntityReference>Tables</unmanagedCodeEntityReference> collection before the collection will reflect the change.</para>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="98101a52-53a6-4287-a8d9-2a7c76c3e0b9">Tables Collection Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="bb3274b1-764d-43a7-a49f-ef55680ecd26">Catalog ActiveConnection Property Example (VB)</link>
<link xlink:href="678e5546-df5d-4cd0-bfe9-6cf13cb385c0">Columns and Tables Append Methods, Name Property Example (VB)</link>
<link xlink:href="f88e7a3b-19ed-46e2-b2ce-3b611d9b8166">Connection Close Method, Table Type Property Example (VB)</link>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>