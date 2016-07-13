---
title: Deferred Buffers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Deferred Buffers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>deferred buffer</legacyItalic> is one whose value is used at some time <legacyItalic>after</legacyItalic> it is specified in a function call. For example, <legacyBold>SQLBindParameter</legacyBold> is used to associate, or <legacyItalic>bind,</legacyItalic> a data buffer with a parameter in an SQL statement. The application specifies the number of the parameter and passes the address, byte length, and type of the buffer. The driver saves this information but does not examine the contents of the buffer. Later, when the application executes the statement, the driver retrieves the information and uses it to retrieve the parameter data and send it to the data source. Therefore, the input of data in the buffer is deferred. Because deferred buffers are specified in one function and used in another, it is an application programming error to free a deferred buffer while the driver still expects it to exist; for more information, see <legacyLink xlink:href="886bc9ed-39d4-43d2-82ff-aebc35b14d39">Allocating and Freeing Buffers</legacyLink>, later in this section.</para>
    <para>Both input and output buffers can be deferred. The following table summarizes the uses of deferred buffers. Note that deferred buffers bound to result set columns are specified with <legacyBold>SQLBindCol</legacyBold>, and deferred buffers bound to SQL statement parameters are specified with <legacyBold>SQLBindParameter</legacyBold>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Buffer use</para>
          </TD>
          <TD>
            <para>Type</para>
          </TD>
          <TD>
            <para>Specified with</para>
          </TD>
          <TD>
            <para>Used by</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Sending data for input parameters</para>
          </TD>
          <TD>
            <para>Deferred input</para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLBindParameter</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLExecute</legacyBold>               <legacyBold>SQLExecDirect</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Sending data to update or insert a row in a result set</para>
          </TD>
          <TD>
            <para>Deferred input</para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLBindCol</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLSetPos</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Returning data for output and input/output parameters</para>
          </TD>
          <TD>
            <para>Deferred output</para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLBindParameter</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLExecute</legacyBold>               <legacyBold>SQLExecDirect</legacyBold>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Returning result set data</para>
          </TD>
          <TD>
            <para>Deferred output</para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLBindCol</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>SQLFetch</legacyBold>               <legacyBold>SQLFetchScroll</legacyBold> <legacyBold>SQLSetPos</legacyBold></para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>