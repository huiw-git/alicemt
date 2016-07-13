---
title: ODBC Visual FoxPro Setup Dialog Box
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Visual FoxPro Setup Dialog Box
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>ODBC Visual FoxPro Setup</legacyBold> dialog box enables you to add or change a Visual FoxPro data source.</para>
    <para>To download the driver, see <externalLink><linkText>the Visual FoxPro ODBC Driver download site</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=121318</linkUri></externalLink>.</para>
  </introduction>
  <section>
    <title>Dialog Box Options</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyBold>Data Source Name</legacyBold> </definedTerm>
        <definition>
          <para>Type the name you want to use for the data source.</para>
        </definition>
        <definedTerm> <legacyBold>Description</legacyBold> </definedTerm>
        <definition>
          <para>Type a description for the data source.</para>
        </definition>
        <definedTerm> <legacyBold>Database type</legacyBold> </definedTerm>
        <definition>
          <para>Lets you choose the type of database you want your data source to connect to.</para>
        </definition>
        <definedTerm> <legacyBold>Visual FoxPro database (.DBC)</legacyBold> </definedTerm>
        <definition>
          <para>Specifies that the data source connects to a Visual FoxPro <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink> (.dbc file) and to all the tables and local views in the database.</para>
        </definition>
        <definedTerm> <legacyBold>Free Table directory</legacyBold> </definedTerm>
        <definition>
          <para>Specifies that the data source connects to a directory of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>. Any <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink> tables in the same directory are ignored by ODBC catalog functions such as <legacyLink xlink:href="b588a875-0153-43a0-9b76-f89e728cfa65">SQLColumns</legacyLink> or <legacyLink xlink:href="69e2a038-5def-423f-91aa-8756e069dd2a">SQLTables</legacyLink>. Database tables can be accessed by using SQL SELECT statements sent through <legacyLink xlink:href="cce0c25f-fa85-4cf5-bfee-4b7a9401f585">SQLExecute</legacyLink> and <legacyLink xlink:href="5004060f-8510-4018-87a4-d41789e69d3e">SQLExecDirect</legacyLink>.</para>
        </definition>
        <definedTerm> <legacyBold>Path</legacyBold> </definedTerm>
        <definition>
          <para>Displays the path and name for the database or the directory of free tables to which the data source connects.</para>
        </definition>
        <definedTerm> <legacyBold>Browse</legacyBold> </definedTerm>
        <definition>
          <para>Enables you to search your system and network for the database or directory to which you want to connect the data source.</para>
        </definition>
        <definedTerm> <legacyBold>Options</legacyBold> </definedTerm>
        <definition>
          <para>Expands the dialog box so that you can set Visual FoxPro ODBC Driver options.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Driver</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyBold>Collating sequence</legacyBold> </definedTerm>
        <definition>
          <para>The sequence in which fields are sorted. The default sequences reflect the sequences supported by your language version of the operating system. For a list of supported collating sequences, see <legacyLink xlink:href="00efbcd4-fea8-4061-86a5-82de413cb753">SET COLLATE</legacyLink>.</para>
        </definition>
        <definedTerm> <legacyBold>Exclusive</legacyBold> </definedTerm>
        <definition>
          <para>When this check box is selected, the driver opens the Visual FoxPro database exclusively when you access data using the data source. Other users cannot access the database or the tables in the database while the database is opened exclusively. Tables within the exclusively opened database are opened as SHARED. To open a table exclusively, use the <legacyLink xlink:href="d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2">SET EXCLUSIVE</legacyLink> command. This check box is disabled when <legacyBold>Database type</legacyBold> is set to <legacyBold>Free Table directory</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyBold>Null</legacyBold> </definedTerm>
        <definition>
          <para>Determines whether columns created with ALTER TABLE and CREATE TABLE allow null values. If you set Null ON, INSERT – SQL inserts a null value into any column not included in an INSERT – SQL... VALUE clause. A blank is inserted if Null is OFF. You can also control this option through a passed connection string as in the following code:  </para>
          <code>strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"</code>
        </definition>
        <definedTerm> <legacyBold>Deleted</legacyBold> </definedTerm>
        <definition>
          <para>Determines whether rows marked as deleted are returned. You can also control this option through a passed connection string as in the following code:  </para>
          <code>strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;
DELETED=YES"</code>
        </definition>
        <definedTerm> <legacyBold>Fetch data in background</legacyBold> </definedTerm>
        <definition>
          <para>Determines whether records will be fetched in the background (progressive fetching) or your application will wait until all records in the result set are fetched.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>