---
title: "Setting Options Programmatically for the Paradox Driver"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Options Programmatically for the Paradox Driver
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Option</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para>Method</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Directory</para>
          </TD>
          <TD>
            <para>Sets the targeted directory.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Collating Sequence</para>
          </TD>
          <TD>
            <para>The sequence in which the fields are sorted.</para>
            <para>The sequence can be ASCII (the default), International, Swedish-Finnish, or Norwegian-Danish.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>COLLATINGSEQUENCE</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para>An optional description of the data in the data source; for example, "Hire date, salary history, and current review of all employees."</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DESCRIPTION</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Exclusive</para>
          </TD>
          <TD>
            <para>If the <legacyBold>Exclusive</legacyBold> box is selected, the database will be opened in Exclusive mode and can be accessed by only one user at a time. Performance is enhanced when running in Exclusive mode.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>EXCLUSIVE</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Net Style</para>
          </TD>
          <TD>
            <para>The network access style to use when accessing Paradox data: either "3.<legacyItalic>x</legacyItalic>" for Paradox 3.<legacyItalic>x</legacyItalic> or "4.<legacyItalic>x</legacyItalic>" for Paradox 4.<legacyItalic>x</legacyItalic> or 5.<legacyItalic>x</legacyItalic>. Can be set to "3.<legacyItalic>x</legacyItalic>" or "4.<legacyItalic>x</legacyItalic>" if the version is Paradox 4.<legacyItalic>x</legacyItalic> or 5.<legacyItalic>x</legacyItalic>; if the version is Paradox 3.<legacyItalic>x</legacyItalic>, the style must be "3.<legacyItalic>x</legacyItalic>".</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>PARADOXNETSTYLE</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Page Timeout</para>
          </TD>
          <TD>
            <para>Specifies the period of time, in tenths of a second, that a page (if not used) remains in the buffer before being removed. The default is 600 tenths of a second (60 seconds). This option applies to all data sources that use the ODBC driver.</para>
            <para>The page timeout cannot be 0 because of an inherent delay. The page timeout cannot be less than the inherent delay, even if the page timeout option is set below that value.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>PAGETIMEOUT</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Read Only</para>
          </TD>
          <TD>
            <para>Designates the database as read-only.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>READONLY</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Select Directory</para>
          </TD>
          <TD>
            <para>Displays a dialog box where you can select a directory containing the files you want to access.</para>
            <para>When defining a data source directory specify the directory where your most commonly used files are located. The ODBC driver uses this directory as the default directory. Copy other files into this directory if they are used frequently. Alternatively, you can qualify file names in a SELECT statement with the directory name:</para>
            <para>SELECT * FROM C:\MYDIR\EMP</para>
            <para>Or, you can specify a new default directory by using the <legacyBold>SQLSetConnectOption</legacyBold> function with the SQL_CURRENT_QUALIFIER option.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Select Network Directory</para>
          </TD>
          <TD>
            <para>The full path of the directory containing a Paradox lock database, because it contains either the Pdoxusrs.net file (in Paradox 4.<legacyItalic>x</legacyItalic>) or the Paradox.net file (in Paradox 5.<legacyItalic>x</legacyItalic>). If the directory does not contain one of these files, the Paradox driver creates one. For information about these files, see the Paradox documentation.</para>
            <para>Before you can select a network directory, you must enter your Paradox user name in the <legacyBold>User Name</legacyBold> text box. Click <legacyBold>Select Network Directory</legacyBold> to select a network directory.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>PARADOXNETPATH</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>User Name</para>
          </TD>
          <TD>
            <para>The Paradox user name. This is the name displayed to other users of Paradox files when a lock is encountered.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>PARADOXUSERNAME</legacyBold> keyword in a call to <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>