---
title: "Groups and Users Append, ChangePassword Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
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
# Groups and Users Append, ChangePassword Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append</legacyLink> method of <legacyLink xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups</legacyLink>, as well as the <legacyLink xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append</legacyLink> method of <legacyLink xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users</legacyLink> by adding a new <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> and a new <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> to the system. The new <legacyBold>Group</legacyBold> is appended to the <legacyBold>Groups</legacyBold> collection of the new <legacyBold>User</legacyBold>. Consequently, the new <legacyBold>User</legacyBold> is added to the <legacyBold>Group</legacyBold>. Also, the <legacyLink xlink:href="d187fbc6-5fac-4abb-803d-bf344dcf0302">ChangePassword</legacyLink> method is used to specify the <legacyBold>User</legacyBold> password.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
    </alert>
  </introduction>
  <section>
    <content>
      <code>' BeginGroupVB
Sub Main()
    On Error GoTo GroupXError

    Dim cat As ADOX.Catalog
    Dim usrNew As ADOX.User
    Dim usrLoop As ADOX.User
    Dim grpLoop As ADOX.Group
    
    Set cat = New ADOX.Catalog
    
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';" &amp; _
        "jet oledb:system database=" &amp; _
        "'system.mdw'"

    With cat
        'Create and append new group with a string.
        .Groups.Append "Accounting"
       
        ' Create and append new user with an object.
        Set usrNew = New ADOX.User
        usrNew.Name = "Pat Smith"
        usrNew.ChangePassword "", "Password1"
        .Users.Append usrNew

        ' Make the user Pat Smith a member of the
        ' Accounting group by creating and adding the
        ' appropriate Group object to the user's Groups
        ' collection. The same is accomplished if a User
        ' object representing Pat Smith is created and
        ' appended to the Accounting group Users collection
        usrNew.Groups.Append "Accounting"
      
        ' Enumerate all User objects in the
        ' catalog's Users collection.
        For Each usrLoop In .Users
            Debug.Print "  " &amp; usrLoop.Name
            Debug.Print "    Belongs to these groups:"
            ' Enumerate all Group objects in each User
            ' object's Groups collection.
            If usrLoop.Groups.Count &lt;&gt; 0 Then
                For Each grpLoop In usrLoop.Groups
                    Debug.Print "    " &amp; grpLoop.Name
                Next grpLoop
            Else
                Debug.Print "    [None]"
            End If
        Next usrLoop

        ' Enumerate all Group objects in the default
        ' workspace's Groups collection.
        For Each grpLoop In .Groups
            Debug.Print "  " &amp; grpLoop.Name
            Debug.Print "    Has as its members:"
            ' Enumerate all User objects in each Group
            ' object's Users collection.
            If grpLoop.Users.Count &lt;&gt; 0 Then
                For Each usrLoop In grpLoop.Users
                    Debug.Print "    " &amp; usrLoop.Name
                Next usrLoop
            Else
                Debug.Print "    [None]"
            End If
        Next grpLoop
        
        ' Delete new User and Group objects because this
        ' is only a demonstration.
        ' These two line are commented out because the sub "OwnersX" uses
        ' the group "Accounting".
'        .Users.Delete "Pat Smith"
'        .Groups.Delete "Accounting"

    End With

    'Clean up
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Set usrNew = Nothing
    Exit Sub
    
GroupXError:
    
    Set cat = Nothing
    Set usrNew = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndGroupVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append Method (Groups)</link>
<link xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append Method (Users)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="d187fbc6-5fac-4abb-803d-bf344dcf0302">ChangePassword Method</link>
<link xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group Object</link>
<link xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups Collection</link>
<link xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User Object</link>
<link xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>