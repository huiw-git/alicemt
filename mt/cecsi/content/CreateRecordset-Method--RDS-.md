---
title: "CreateRecordset Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
caps.latest.revision: 15
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
# CreateRecordset Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates an empty, disconnected <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>object</parameterReference>.<legacyBold>CreateRecordset(</legacyBold><parameterReference>ColumnInfos</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Object</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> or <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>ColumnsInfos</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Variant</legacyBold> array of attributes that defines each column in the <legacyBold>Recordset</legacyBold> created. Each column definition contains an array of four required attributes and one optional attribute.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Attribute</para>
                </TD>
                <TD>
                  <para>Description</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Name</para>
                </TD>
                <TD>
                  <para>Name of the column header.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Type</para>
                </TD>
                <TD>
                  <para>Integer of the data type.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Size</para>
                </TD>
                <TD>
                  <para>Integer of the width in characters, regardless of data type.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Nullability</para>
                </TD>
                <TD>
                  <para>Boolean value.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Scale (Optional)</para>
                </TD>
                <TD>
                  <para>This optional attribute defines the scale for numeric fields. If this value is not specified, numeric values will be truncated to a scale of three. Precision is not affected, but the number of digits following the decimal point will be truncated to three.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>The set of column arrays is then grouped into an array, which defines the <legacyBold>Recordset</legacyBold>. </para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The server-side business object can populate the resulting <legacyBold>Recordset</legacyBold> with data from a non-OLE DB data provider, such as an operating system file containing stock quotes.</para>
      <para>The following table lists the <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> values supported by the <legacyBold>CreateRecordset</legacyBold> method. The number listed is the reference number used to define fields.</para>
      <para>Each of the data types is either fixed length or variable length. Fixed-length types should be defined with a size of –1, because the size is predetermined and a size definition is still required. Variable-length data types allow a size from 1 to 32767.</para>
      <para>For some of the variable data types, the type can be coerced to the type noted in the Substitution column. You will not see the substitutions until after the <legacyBold>Recordset</legacyBold> is created and filled. Then you can check for the actual data type, if necessary.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Length</para>
            </TD>
            <TD>
              <para>Constant</para>
            </TD>
            <TD>
              <para>Number</para>
            </TD>
            <TD>
              <para>Substitution</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adTinyInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>16</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adSmallInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adInteger</legacyBold>
              </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adBigInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>20</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adUnsignedTinyInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>17</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adUnsignedSmallInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>18</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adUnsignedInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>19</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adUnsignedBigInt</legacyBold>
              </para>
            </TD>
            <TD>
              <para>21</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adSingle</legacyBold>
              </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adDouble</legacyBold>
              </para>
            </TD>
            <TD>
              <para>5</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adCurrency</legacyBold>
              </para>
            </TD>
            <TD>
              <para>6</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adDecimal</legacyBold>
              </para>
            </TD>
            <TD>
              <para>14</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adNumeric</legacyBold>
              </para>
            </TD>
            <TD>
              <para>131</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adBoolean</legacyBold>
              </para>
            </TD>
            <TD>
              <para>11</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adError</legacyBold>
              </para>
            </TD>
            <TD>
              <para>10</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adGuid</legacyBold>
              </para>
            </TD>
            <TD>
              <para>72</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adDate</legacyBold>
              </para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adDBDate</legacyBold>
              </para>
            </TD>
            <TD>
              <para>133</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adDBTime</legacyBold>
              </para>
            </TD>
            <TD>
              <para>134</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixed</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adDBTimestamp</legacyBold>
              </para>
            </TD>
            <TD>
              <para>135</para>
            </TD>
            <TD>
              <para>7</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adBSTR</legacyBold>
              </para>
            </TD>
            <TD>
              <para>8</para>
            </TD>
            <TD>
              <para>130</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adChar</legacyBold>
              </para>
            </TD>
            <TD>
              <para>129</para>
            </TD>
            <TD>
              <para>200</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adVarChar</legacyBold>
              </para>
            </TD>
            <TD>
              <para>200</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adLongVarChar</legacyBold>
              </para>
            </TD>
            <TD>
              <para>201</para>
            </TD>
            <TD>
              <para>200</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adWChar</legacyBold>
              </para>
            </TD>
            <TD>
              <para>130</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adVarWChar</legacyBold>
              </para>
            </TD>
            <TD>
              <para>202</para>
            </TD>
            <TD>
              <para>130</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adLongVarWChar</legacyBold>
              </para>
            </TD>
            <TD>
              <para>203</para>
            </TD>
            <TD>
              <para>130</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adBinary</legacyBold>
              </para>
            </TD>
            <TD>
              <para>128</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adVarBinary</legacyBold>
              </para>
            </TD>
            <TD>
              <para>204</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Variable</para>
            </TD>
            <TD>
              <para>
                <legacyBold>adLongVarBinary</legacyBold>
              </para>
            </TD>
            <TD>
              <para>205</para>
            </TD>
            <TD>
              <para>204</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2de8fd02-0f49-4d47-8bd3-397726d1c644">Visual Basic Example</link>
<link xlink:href="cce0d8b5-e87b-4f7b-a8a0-37d5025a1f5d">VBScript Example</link>
<link xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>