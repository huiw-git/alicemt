---
title: "JScript Code Example to Return a Recordset"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74aad8a6-06cc-4a2c-811a-d78f9b741d84
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
# JScript Code Example to Return a Recordset
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>JScript Code (rs.js)</title>
    <content>
      <code>main();

function main()
{
  DP = "SQLOLEDB";
  DS = "MySQLServer";
  DB = "NORTHWIND";

  adOpenForwardOnly = 0;
  adLockReadOnly = 1;
  adCmdText = 1;
  try 
  {
    var objRs = new ActiveXObject("ADODB.Recordset");
  }
  catch (e)
  {
    alert("ADODB namespace not found.");
    exit(0);
  }

  strConn =  "Provider="         +DP+
            ";Initial Catalog="  +DB+
            ";Data Source="      +DS+
            ";Integrated Security=SSPI;"
  strComm = "SELECT ProductID,ProductName,UnitPrice "+
            "FROM Products " + 
            "WHERE CategoryID = 7"  // select Produce

  objRs.open(strComm, 
             strConn, 
             adOpenForwardOnly,
             adLockReadOnly,
             adCmdText);

  objRs.MoveFirst();
  while (objRs.EOF != true) 
  {
    alert(objRs("ProductID")+"\t"
         +objRs("ProductName")+"\t"
         +objRs("UnitPrice"));
    objRs.MoveNext();
  }

  objRs.Close
  objRs = null;
}


function alert(str)
{
  WScript.Echo(str);
}</code>
      <procedure>
        <title>Try It!</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Save the code above into a text file. Save the file as rs.js.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Open a command prompt and cd to the directory where you have saved the JScript file (rs.js).</para>
            </content>
          </step>
          <step>
            <content>
              <para>Type <codeInline>CScript rs.js</codeInline> from the command prompt.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>