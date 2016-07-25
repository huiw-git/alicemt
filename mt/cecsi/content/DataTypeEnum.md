---
title: "DataTypeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
caps.latest.revision: 13
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
# DataTypeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the data type of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink>, or <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink>. The corresponding OLE DB type indicator is shown in parentheses in the description column of the following table. </para>
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
              <legacyBold>AdArray</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2000</para>
          </TD>
          <TD>
            <para>A flag value, always combined with another data type constant, that indicates an array of the other data type. Does not apply to ADOX.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adBigInt</legacyBold>  </para>
          </TD>
          <TD>
            <para>20</para>
          </TD>
          <TD>
            <para>Indicates an eight-byte signed integer (DBTYPE_I8).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adBinary</legacyBold>  </para>
          </TD>
          <TD>
            <para>128</para>
          </TD>
          <TD>
            <para>Indicates a binary value (DBTYPE_BYTES).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adBoolean</legacyBold>  </para>
          </TD>
          <TD>
            <para>11</para>
          </TD>
          <TD>
            <para>Indicates a <languageKeyword>Boolean</languageKeyword> value (DBTYPE_BOOL).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adBSTR</legacyBold>  </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>Indicates a null-terminated character string (Unicode) (DBTYPE_BSTR).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adChapter</legacyBold>  </para>
          </TD>
          <TD>
            <para>136</para>
          </TD>
          <TD>
            <para>Indicates a four-byte chapter value that identifies rows in a child rowset (DBTYPE_HCHAPTER).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adChar</legacyBold>  </para>
          </TD>
          <TD>
            <para>129</para>
          </TD>
          <TD>
            <para>Indicates a string value (DBTYPE_STR).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCurrency</legacyBold>  </para>
          </TD>
          <TD>
            <para>6</para>
          </TD>
          <TD>
            <para>Indicates a currency value (DBTYPE_CY). Currency is a fixed-point number with four digits to the right of the decimal point. It is stored in an eight-byte signed integer scaled by 10,000.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDate</legacyBold>  </para>
          </TD>
          <TD>
            <para>7</para>
          </TD>
          <TD>
            <para>Indicates a date value (DBTYPE_DATE). A date is stored as a double, the whole part of which is the number of days since December 30, 1899, and the fractional part of which is the fraction of a day.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDBDate</legacyBold>  </para>
          </TD>
          <TD>
            <para>133</para>
          </TD>
          <TD>
            <para>Indicates a date value (yyyymmdd) (DBTYPE_DBDATE).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDBTime</legacyBold>  </para>
          </TD>
          <TD>
            <para>134</para>
          </TD>
          <TD>
            <para>Indicates a time value (hhmmss) (DBTYPE_DBTIME).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDBTimeStamp</legacyBold>  </para>
          </TD>
          <TD>
            <para>135</para>
          </TD>
          <TD>
            <para>Indicates a date/time stamp (yyyymmddhhmmss plus a fraction in billionths) (DBTYPE_DBTIMESTAMP).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDecimal</legacyBold>  </para>
          </TD>
          <TD>
            <para>14</para>
          </TD>
          <TD>
            <para>Indicates an exact numeric value with a fixed precision and scale (DBTYPE_DECIMAL).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDouble</legacyBold>  </para>
          </TD>
          <TD>
            <para>5</para>
          </TD>
          <TD>
            <para>Indicates a double-precision floating-point value (DBTYPE_R8).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adEmpty</legacyBold>  </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Specifies no value (DBTYPE_EMPTY).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adError</legacyBold>  </para>
          </TD>
          <TD>
            <para>10</para>
          </TD>
          <TD>
            <para>Indicates a 32-bit error code (DBTYPE_ERROR).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFileTime</legacyBold>  </para>
          </TD>
          <TD>
            <para>64</para>
          </TD>
          <TD>
            <para>Indicates a 64-bit value representing the number of 100-nanosecond intervals since January 1, 1601 (DBTYPE_FILETIME).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adGUID</legacyBold>  </para>
          </TD>
          <TD>
            <para>72</para>
          </TD>
          <TD>
            <para>Indicates a globally unique identifier (GUID) (DBTYPE_GUID).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adIDispatch</legacyBold>  </para>
          </TD>
          <TD>
            <para>9</para>
          </TD>
          <TD>
            <para>Indicates a pointer to an <legacyBold>IDispatch</legacyBold> interface on a COM object (DBTYPE_IDISPATCH).</para>
            <para>
              <embeddedLabel>Note</embeddedLabel>   This data type is currently not supported by ADO. Usage may cause unpredictable results.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adInteger</legacyBold>  </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates a four-byte signed integer (DBTYPE_I4).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adIUnknown</legacyBold>  </para>
          </TD>
          <TD>
            <para>13</para>
          </TD>
          <TD>
            <para>Indicates a pointer to an <legacyBold>IUnknown</legacyBold> interface on a COM object (DBTYPE_IUNKNOWN).</para>
            <para>
              <embeddedLabel>Note</embeddedLabel>
              <legacyBold>   </legacyBold>This data type is currently not supported by ADO. Usage may cause unpredictable results.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLongVarBinary</legacyBold>  </para>
          </TD>
          <TD>
            <para>205</para>
          </TD>
          <TD>
            <para>Indicates a long binary value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLongVarChar</legacyBold>  </para>
          </TD>
          <TD>
            <para>201</para>
          </TD>
          <TD>
            <para>Indicates a long string value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adLongVarWChar</legacyBold>  </para>
          </TD>
          <TD>
            <para>203</para>
          </TD>
          <TD>
            <para>Indicates a long null-terminated Unicode string value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adNumeric</legacyBold>  </para>
          </TD>
          <TD>
            <para>131</para>
          </TD>
          <TD>
            <para>Indicates an exact numeric value with a fixed precision and scale (DBTYPE_NUMERIC).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPropVariant</legacyBold>  </para>
          </TD>
          <TD>
            <para>138</para>
          </TD>
          <TD>
            <para>Indicates an Automation PROPVARIANT (DBTYPE_PROP_VARIANT).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSingle</legacyBold>  </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates a single-precision floating-point value (DBTYPE_R4).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSmallInt</legacyBold>  </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates a two-byte signed integer (DBTYPE_I2).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adTinyInt</legacyBold>  </para>
          </TD>
          <TD>
            <para>16</para>
          </TD>
          <TD>
            <para>Indicates a one-byte signed integer (DBTYPE_I1).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUnsignedBigInt</legacyBold>  </para>
          </TD>
          <TD>
            <para>21</para>
          </TD>
          <TD>
            <para>Indicates an eight-byte unsigned integer (DBTYPE_UI8).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUnsignedInt</legacyBold>  </para>
          </TD>
          <TD>
            <para>19</para>
          </TD>
          <TD>
            <para>Indicates a four-byte unsigned integer (DBTYPE_UI4).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUnsignedSmallInt</legacyBold>  </para>
          </TD>
          <TD>
            <para>18</para>
          </TD>
          <TD>
            <para>Indicates a two-byte unsigned integer (DBTYPE_UI2).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUnsignedTinyInt</legacyBold> </para>
          </TD>
          <TD>
            <para>17</para>
          </TD>
          <TD>
            <para>Indicates a one-byte unsigned integer (DBTYPE_UI1).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUserDefined</legacyBold>  </para>
          </TD>
          <TD>
            <para>132</para>
          </TD>
          <TD>
            <para>Indicates a user-defined variable (DBTYPE_UDT).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adVarBinary</legacyBold>  </para>
          </TD>
          <TD>
            <para>204</para>
          </TD>
          <TD>
            <para>Indicates a binary value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adVarChar</legacyBold>  </para>
          </TD>
          <TD>
            <para>200</para>
          </TD>
          <TD>
            <para>Indicates a string value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adVariant</legacyBold>  </para>
          </TD>
          <TD>
            <para>12</para>
          </TD>
          <TD>
            <para>Indicates an Automation <languageKeyword>Variant</languageKeyword> (DBTYPE_VARIANT).</para>
            <para>
              <embeddedLabel>Note</embeddedLabel>
              <legacyBold>   </legacyBold>This data type is currently not supported by ADO. Usage may cause unpredictable results.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adVarNumeric</legacyBold>  </para>
          </TD>
          <TD>
            <para>139</para>
          </TD>
          <TD>
            <para>Indicates a numeric value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adVarWChar</legacyBold>  </para>
          </TD>
          <TD>
            <para>202</para>
          </TD>
          <TD>
            <para>Indicates a null-terminated Unicode character string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adWChar</legacyBold>  </para>
          </TD>
          <TD>
            <para>130</para>
          </TD>
          <TD>
            <para>Indicates a null-terminated Unicode character string (DBTYPE_WSTR).</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.DataType.ARRAY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.BIGINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.BINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.BOOLEAN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.BSTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.CHAPTER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.CHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.CURRENCY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.DATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.DBDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.DBTIME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.DBTIMESTAMP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.DECIMAL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.DOUBLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.EMPTY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.ERROR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.FILETIME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.GUID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.IDISPATCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.INTEGER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.IUNKNOWN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.LONGVARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.LONGVARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.LONGVARWCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.NUMERIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.PROPVARIANT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.SINGLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.SMALLINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.TINYINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.UNSIGNEDBIGINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.UNSIGNEDINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.UNSIGNEDSMALLINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.UNSIGNEDTINYINT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.USERDEFINED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.VARBINARY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.VARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.VARIANT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.VARNUMERIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.VARWCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.DataType.WCHAR</para>
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
                <link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset Method (RDS)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>