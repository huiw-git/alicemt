---
title: "GetPermissions and SetPermissions Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa366d98-8c7a-4189-bdd8-1d663b243d33
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
# GetPermissions and SetPermissions Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions</legacyLink> and <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink> methods. The following code gives full access for the Orders table to the Admin user.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginGrantPermissionsVB
Sub GrantPermissions()
    On Error GoTo GrantPermissionsError
    
    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim lngPerm As Long

    ' Opens a connection to the northwind database
    ' using the Microsoft Jet 4.0 provider
    cnn.Provider = "Microsoft.Jet.OLEDB.4.0"
    cnn.Open "Data Source='Northwind.mdb';" &amp; _
        "jet oledb:system database=" &amp; _
        "'system.mdw'"

    Set cat.ActiveConnection = cnn

    ' Retrieve original permissions
    lngPerm = cat.Users("admin").GetPermissions("Orders", adPermObjTable)
    Debug.Print "Original permissions: " &amp; Str(lngPerm)
    
    ' Revoke all permissions
    cat.Users("admin").SetPermissions "Orders", adPermObjTable, _
        adAccessRevoke, adRightFull
    
    ' Display permissions
    Debug.Print "Revoked permissions: " &amp; _
        Str(cat.Users("admin").GetPermissions("Orders", adPermObjTable))
    
    ' Give the Admin user full rights on the orders object
    cat.Users("admin").SetPermissions "Orders", adPermObjTable, _
        adAccessSet, adRightFull

    ' Display permissions
    Debug.Print "Full permissions: " &amp; _
        Str(cat.Users("admin").GetPermissions("Orders", adPermObjTable))

    ' Restore original permissions
    cat.Users("admin").SetPermissions "Orders", adPermObjTable, _
        adAccessSet, lngPerm

    ' Display permissions
    Debug.Print "Final permissions: " &amp; _
        Str(cat.Users("admin").GetPermissions("Orders", adPermObjTable))
    
    'Clean up
    cnn.Close
    Set cat = Nothing
    Set cnn = Nothing
    Exit Sub
    
GrantPermissionsError:
    
    Set cat = Nothing
    
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndGrantPermissionsVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions Method</link>
<link xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions Method</link>
<link xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User Object</link>
<link xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>