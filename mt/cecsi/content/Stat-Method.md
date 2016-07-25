---
title: "Stat Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
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
# Stat Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves information about a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
Long <parameterReference>stream</parameterReference>.Stat(StatStg, StatFlag)</legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>A <languageKeyword>Long</languageKeyword> value indicating the status of the operation.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>StatStg</legacyItalic> </definedTerm>
        <definition>
          <para>A STATSTG structure that will be filled in with information about the stream. The implementation of the <unmanagedCodeEntityReference>Stat</unmanagedCodeEntityReference> method used by the ADO Stream object does not fill in all of the fields of the structure.</para>
        </definition>
        <definedTerm> <legacyItalic>StatFlag</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies that this method does not return some of the members in the STATSTG structure, thus saving a memory allocation operation. Values are taken from the STATFLAG enumeration. The STATFLAG enumeration has two values</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Constant</para>
                </TD>
                <TD>
                  <para>Value</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>STATFLAG_DEFAULT</para>
                </TD>
                <TD>
                  <para>0</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>STATFLAG_NONAME</para>
                </TD>
                <TD>
                  <para>1</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The version of the Stat method implemented for the ADO Stream object fills in the following fields of the STATSTG structure:  </para>
      <definitionTable>
        <definedTerm> <legacyItalic>pwcsName</legacyItalic> </definedTerm>
        <definition>
          <para>A string containing the name of the stream, if one is available and the StatFlag value STATFLAG_NONAME was not specified.</para>
        </definition>
        <definedTerm> <legacyItalic>cbSize</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies the size in bytes of the stream or byte array.</para>
        </definition>
        <definedTerm> <legacyItalic>mtime</legacyItalic> </definedTerm>
        <definition>
          <para>Indicates the last modification time for this storage, stream, or byte array.</para>
        </definition>
        <definedTerm> <legacyItalic>ctime</legacyItalic> </definedTerm>
        <definition>
          <para>Indicates the creation time for this storage, stream, or byte array.</para>
        </definition>
        <definedTerm> <legacyItalic>atime</legacyItalic> </definedTerm>
        <definition>
          <para>Indicates the last access time for this storage, stream or byte array.</para>
        </definition>
      </definitionTable>
      <para>If STATFLAG_NONAME is specified in the StatFlag parameter, the name of the stream is not returned.</para>
      <para>If STATFLAG_NONAME was not specified in the StatFlag parameter, and there is no name available for the current stream, this value will be E_NOTIMPL.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>