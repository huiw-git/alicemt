---
title: "RightsEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
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
# RightsEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the rights or permissions for a group or user on an object.</para>
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
                <legacyBold>adRightCreate</legacyBold>             </para>
            </TD>
            <TD>
              <para>16384 (&amp;H4000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to create new objects of this type.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightDelete</legacyBold>             </para>
            </TD>
            <TD>
              <para>65536 (&amp;H10000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to delete data from an object. For objects such as <legacyBold>Tables</legacyBold>, the user has permission to delete data values from records.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightDrop</legacyBold>             </para>
            </TD>
            <TD>
              <para>256 (&amp;H100)</para>
            </TD>
            <TD>
              <para>The user or group has permission to remove objects from the catalog. For example, <legacyBold>Tables</legacyBold> can be deleted by a DROP TABLE SQL command.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightExclusive</legacyBold>             </para>
            </TD>
            <TD>
              <para>512 (&amp;H200)</para>
            </TD>
            <TD>
              <para>The user or group has permission to access the object exclusively.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightExecute</legacyBold>             </para>
            </TD>
            <TD>
              <para>536870912 (&amp;H20000000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to execute the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightFull</legacyBold>             </para>
            </TD>
            <TD>
              <para>268435456 (&amp;H10000000)</para>
            </TD>
            <TD>
              <para>The user or group has all permissions on the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightInsert</legacyBold>             </para>
            </TD>
            <TD>
              <para>32768 (&amp;H8000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to insert the object. For objects such as <legacyBold>Tables</legacyBold>, the user has permission to insert data into the table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightMaximumAllowed</legacyBold>             </para>
            </TD>
            <TD>
              <para>33554432 (&amp;H2000000)</para>
            </TD>
            <TD>
              <para>The user or group has the maximum number of permissions allowed by the provider. Specific permissions are provider-dependent.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightNone</legacyBold>             </para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>The user or group has no permissions for the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightRead</legacyBold>             </para>
            </TD>
            <TD>
              <para>-2147483648 (&amp;H80000000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to read the object. For objects such as <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Tables</legacyLink>, the user has permission to read the data in the table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightReadDesign</legacyBold>             </para>
            </TD>
            <TD>
              <para>1024 (&amp;H400)</para>
            </TD>
            <TD>
              <para>The user or group has permission to read the design for the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightReadPermissions</legacyBold>             </para>
            </TD>
            <TD>
              <para>131072 (&amp;H20000)</para>
            </TD>
            <TD>
              <para>The user or group can view, but not change, the specific permissions for an object in the catalog.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightReference</legacyBold>             </para>
            </TD>
            <TD>
              <para>8192 (&amp;H2000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to reference the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightUpdate</legacyBold>             </para>
            </TD>
            <TD>
              <para>1073741824 (&amp;H40000000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to update the object. For objects such as <legacyBold>Tables</legacyBold>, the user has permission to update the data in the table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightWithGrant</legacyBold>             </para>
            </TD>
            <TD>
              <para>4096 (&amp;H1000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to grant permissions on the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightWriteDesign</legacyBold>             </para>
            </TD>
            <TD>
              <para>2048 (&amp;H800)</para>
            </TD>
            <TD>
              <para>The user or group has permission to modify the design for the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightWriteOwner</legacyBold>             </para>
            </TD>
            <TD>
              <para>524288 (&amp;H80000)</para>
            </TD>
            <TD>
              <para>The user or group has permission to modify the owner of the object.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRightWritePermissions</legacyBold>             </para>
            </TD>
            <TD>
              <para>262144 (&amp;H40000)</para>
            </TD>
            <TD>
              <para>The user or group can modify the specific permissions for an object in the catalog.</para>
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
                <link xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions Method</link>
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