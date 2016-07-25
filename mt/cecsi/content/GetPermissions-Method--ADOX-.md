---
title: "GetPermissions Method (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
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
# GetPermissions Method (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns the permissions for a <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">group</legacyLink> or <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">user</legacyLink> on an object or object container.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>ReturnValue</parameterReference><legacyBold>=</legacyBold><parameterReference>GroupOrUser</parameterReference><legacyBold>.GetPermissions(</legacyBold><parameterReference>Name</parameterReference><legacyBold>,</legacyBold><parameterReference> ObjectType    </parameterReference>[<legacyBold>,</legacyBold><parameterReference>ObjectTypeId</parameterReference>]<legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> value that specifies a bitmask containing the permissions that the group or user has on the object. This value can be one or more of the <legacyLink xlink:href="55ee67c7-a583-42aa-849a-78264b4cb614">RightsEnum</legacyLink> constants.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>Name </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>Variant</languageKeyword> value that specifies the name of the object for which to set permissions. Set <parameterReference>Name</parameterReference> to a null value if you want to get the permissions for the object container.</para>
        </definition>
        <definedTerm> <parameterReference>ObjectType </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value which can be one of the <legacyLink xlink:href="3fdecfca-aa91-4596-ad98-610f1b7f840b">ObjectTypeEnum</legacyLink> constants, that specifies the type of the object for which to get permissions.</para>
        </definition>
        <definedTerm> <parameterReference>ObjectTypeId </parameterReference></definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> value that specifies the GUID for a provider object type not defined by the OLE DB specification. This parameter is required if <parameterReference>ObjectType</parameterReference> is set to <legacyBold>adPermObjProviderSpecific</legacyBold>; otherwise, it is not used.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group Object (ADOX)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User Object (ADOX)</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="aa366d98-8c7a-4189-bdd8-1d663b243d33">GetPermissions and SetPermissions Methods Example (VB)</link>
<link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property</link>
<link xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>