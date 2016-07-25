---
title: "ADOX Methods"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8de11ef7-034c-4613-91df-2244171f0b9a
caps.latest.revision: 9
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
# ADOX Methods
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append (Columns)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>Column</legacyBold> object to the <legacyBold>Columns</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append (Groups)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>Group</legacyBold> object to the <legacyBold>Groups</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="6695769f-275b-4b70-81bd-1a5f7d74926c">Append (Indexes)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>Index</legacyBold> object to the <legacyBold>Indexes</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="215a5391-f422-42ec-99ea-4e6fbb5d3d64">Append (Keys)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>Key</legacyBold> object to the <legacyBold>Keys</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="38e3492c-c1e1-42e3-a71a-befdc90204db">Append (Procedures)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>Procedure</legacyBold> object to the <legacyBold>Procedures</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append (Tables)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>Table</legacyBold> object to the <legacyBold>Tables</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append (Users)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>User</legacyBold> object to the <legacyBold>Users</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="6070fd58-3237-4c77-a966-5b39ce5d57e4">Append (Views)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Adds a new <legacyBold>View</legacyBold> object to the <legacyBold>Views</legacyBold> collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="d187fbc6-5fac-4abb-803d-bf344dcf0302">ChangePassword</legacyLink>           </para>
          </TD>
          <TD>
            <para>Changes the password for a user account.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="64f5c21c-b581-42d8-bdc7-c4f1bebaf105">Create</legacyLink>           </para>
          </TD>
          <TD>
            <para>Creates a new catalog.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Removes an object from a collection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="8965adf0-9075-4125-8142-73eb700029c3">GetObjectOwner</legacyLink>           </para>
          </TD>
          <TD>
            <para>Returns the owner of an object in a catalog.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions</legacyLink>           </para>
          </TD>
          <TD>
            <para>Returns the permissions for a group or user on an object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="e5170a37-9d6e-43db-bfb6-9b6631fa3048">SetObjectOwner</legacyLink>           </para>
          </TD>
          <TD>
            <para>Specifies the owner of an object in a catalog.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink>           </para>
          </TD>
          <TD>
            <para>Specifies the permissions for group or user on an object.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="ef700465-2e97-46e8-8213-2d662501e540">ADOX API Reference</link>
<link xlink:href="c6579b5b-a93e-48c5-8847-743fc4590cd2">Microsoft ADOX Programmer's Reference</link>
</relatedTopics>
</developerOrientationDocument>