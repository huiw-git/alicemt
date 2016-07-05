---
title: ConfigDSN Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - ConfigDSN
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 01ced74e-c575-4a25-83f5-bd7d918123f8
translation.priority.ht: 
  - en-gb
---
# ConfigDSN Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>ConfigDSN</legacyBold> adds, modifies, or deletes data sources from the system information. It may prompt the user for connection information. It can be in the driver DLL or a separate setup DLL.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>ConfigDSN</legacyBold>(
     HWND     <parameterReference>hwndParent</parameterReference>,
     WORD     <parameterReference>fRequest</parameterReference>,
     LPCSTR   <parameterReference>lpszDriver</parameterReference>,
     LPCSTR   <parameterReference>lpszAttributes</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hwndParent</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parent window handle. The function will not display any dialog boxes if the handle is null.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fRequest</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of request. The <legacyItalic>fRequest</legacyItalic> argument must contain one of the following values:</para>
          <para>ODBC_ADD_DSN: Add a new data source.</para>
          <para>ODBC_CONFIG_DSN: Configure (modify) an existing data source.</para>
          <para>ODBC_REMOVE_DSN: Remove an existing data source. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Driver description (usually the name of the associated DBMS) presented to users instead of the physical driver name.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszAttributes</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A doubly null-terminated list of attributes in the form of keyword-value pairs. For more information, see "Comments."</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>The function returns TRUE if it is successful, FALSE if it fails.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>ConfigDSN</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value is posted to the installer error buffer by a call to <legacyBold>SQLPostInstallerError</legacyBold> and can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>*pfErrorCode</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_HWND</para>
            </TD>
            <TD>
              <para>Invalid window handle</para>
            </TD>
            <TD>
              <para>The <legacyItalic>hwndParent</legacyItalic> argument was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_KEYWORD_VALUE</para>
            </TD>
            <TD>
              <para>Invalid keyword-value pairs</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszAttributes</legacyItalic> argument contained a syntax error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_NAME</para>
            </TD>
            <TD>
              <para>Invalid driver or translator name</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument was invalid. It could not be found in the registry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_REQUEST_TYPE</para>
            </TD>
            <TD>
              <para>Invalid type of request</para>
            </TD>
            <TD>
              <para>The <legacyItalic>fRequest</legacyItalic> argument was not one of the following:</para>
              <para>ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Request</legacyItalic> failed</para>
            </TD>
            <TD>
              <para>Could not perform the operation requested by the <legacyItalic>fRequest</legacyItalic> argument.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_DRIVER_SPECIFIC</para>
            </TD>
            <TD>
              <para>Driver- or translator-specific error</para>
            </TD>
            <TD>
              <para>A driver-specific error for which there is no defined ODBC installer error. The <legacyItalic>SzError</legacyItalic> argument in a call to the <legacyBold>SQLPostInstallerError</legacyBold> function should contain the driver-specific error message.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>ConfigDSN</legacyBold> receives connection information from the installer DLL as a list of attributes in the form of keyword-value pairs. Each pair is terminated with a null byte, and the entire list is terminated with a null byte. (That is, two null bytes mark the end of the list.) Spaces are not allowed around the equal sign in the keyword-value pair. <legacyBold>ConfigDSN</legacyBold> can accept keywords that are not valid keywords for <legacyBold>SQLBrowseConnect</legacyBold> and <legacyBold>SQLDriverConnect</legacyBold>. <legacyBold>ConfigDSN</legacyBold> does not necessarily support all keywords that are valid keywords for <legacyBold>SQLBrowseConnect</legacyBold> and <legacyBold>SQLDriverConnect</legacyBold>. (<legacyBold>ConfigDSN</legacyBold> does not accept the <legacyBold>DRIVER</legacyBold> keyword.) The keywords used by the <legacyBold>ConfigDSN</legacyBold> function must support all the options required to re-create the data source using the AUTO setup feature of the installer. When the uses of the <legacyBold>ConfigDSN</legacyBold> values and the connection string values are the same, the same keywords should be used. </para>
      <para>As in <legacyBold>SQLBrowseConnect</legacyBold> and <legacyBold>SQLDriverConnect</legacyBold>, the keywords and their values should not contain the <legacyBold>[]{}(),;?*=!@</legacyBold> characters, and the value of the <legacyBold>DSN</legacyBold> keyword cannot consist only of blanks. Because of the registry grammar, keywords and data source names cannot contain the backslash (\) character.</para>
      <para>
        <legacyBold>ConfigDSN</legacyBold> should call <legacyBold>SQLValidDSN</legacyBold> to check the length of the data source name and to verify that no invalid characters are included in the name. If the data source name is longer than SQL_MAX_DSN_LENGTH or includes invalid characters, <legacyBold>SQLValidDSN</legacyBold> returns an error and <legacyBold>ConfigDSN</legacyBold> returns an error. The length of the data source name is also checked by <legacyBold>SQLWriteDSNToIni</legacyBold>.</para>
      <para>For example, to configure a data source that requires a user ID, password, and database name, a setup application might pass the following keyword-value pairs:</para>
      <code>DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0</code>
      <para>For more information about these keywords, see <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> and each driver's documentation.</para>
      <para>To display a dialog box, <legacyItalic>hwndParent</legacyItalic> must not be null.</para>
    </content>
  </section>
  <section>
    <title>Adding a Data Source</title>
    <content>
      <para>If a data source name is passed to <legacyBold>ConfigDSN</legacyBold> in <legacyItalic>lpszAttributes</legacyItalic>, <legacyBold>ConfigDSN</legacyBold> checks that the name is valid. If the data source name matches an existing data source name and <legacyItalic>hwndParent</legacyItalic> is null, <legacyBold>ConfigDSN</legacyBold> overwrites the existing name. If it matches an existing name and <legacyItalic>hwndParent</legacyItalic> is not null, <legacyBold>ConfigDSN</legacyBold> prompts the user to overwrite the existing name.</para>
      <para>If <legacyItalic>lpszAttributes</legacyItalic> contains enough information to connect to a data source, <legacyBold>ConfigDSN</legacyBold> can add the data source or display a dialog box with which the user can change the connection information. If <legacyItalic>lpszAttributes</legacyItalic> does not contain enough information to connect to a data source, <legacyBold>ConfigDSN</legacyBold> must determine the necessary information; if <legacyItalic>hwndParent</legacyItalic> is not null, it displays a dialog box to retrieve the information from the user.</para>
      <para>If <legacyBold>ConfigDSN</legacyBold> displays a dialog box, it must display any connection information passed to it in <legacyItalic>lpszAttributes</legacyItalic>. In particular, if a data source name was passed to it, <legacyBold>ConfigDSN</legacyBold> displays that name but does not allow the user to change it. <legacyBold>ConfigDSN</legacyBold> can supply default values for connection information not passed to it in <legacyItalic>lpszAttributes</legacyItalic>.</para>
      <para>If <legacyBold>ConfigDSN</legacyBold> cannot get complete connection information for a data source, it returns FALSE.</para>
      <para>If <legacyBold>ConfigDSN</legacyBold> can get complete connection information for a data source, it calls <legacyBold>SQLWriteDSNToIni</legacyBold> in the installer DLL to add the new data source specification to the Odbc.ini file (or registry). <legacyBold>SQLWriteDSNToIni</legacyBold> adds the data source name to the [ODBC Data Sources] section, creates the data source specification section, and adds the <legacyBold>DRIVER</legacyBold> keyword with the driver description as its value. <legacyBold>ConfigDSN</legacyBold> calls <legacyBold>SQLWritePrivateProfileString</legacyBold> in the installer DLL to add any additional keywords and values used by the driver.</para>
    </content>
  </section>
  <section>
    <title>Modifying a Data Source</title>
    <content>
      <para>To modify a data source, a data source name must be passed to <legacyBold>ConfigDSN</legacyBold> in <legacyItalic>lpszAttributes</legacyItalic>. <legacyBold>ConfigDSN</legacyBold> checks that the data source name is in the Odbc.ini file (or registry).</para>
      <para>If <legacyItalic>hwndParent</legacyItalic> is null, <legacyBold>ConfigDSN</legacyBold> uses the information in <legacyItalic>lpszAttributes</legacyItalic> to modify the information in the Odbc.ini file (or registry). If <legacyItalic>hwndParent</legacyItalic> is not null, <legacyBold>ConfigDSN</legacyBold> displays a dialog box using the information in <legacyItalic>lpszAttributes</legacyItalic>; for information not in <legacyItalic>lpszAttributes</legacyItalic>, it uses information from the system information. The user can modify the information before <legacyBold>ConfigDSN</legacyBold> stores it in the system information.</para>
      <para>If the data source name was changed, <legacyBold>ConfigDSN</legacyBold> first calls <legacyBold>SQLRemoveDSNFromIni</legacyBold> in the installer DLL to remove the existing data source specification from the Odbc.ini file (or registry). It then follows the steps in the preceding section to add the new data source specification. If the data source name was not changed, <legacyBold>ConfigDSN</legacyBold> calls <legacyBold>SQLWritePrivateProfileString</legacyBold> in the installer DLL to make any other changes. <legacyBold>ConfigDSN</legacyBold> may not delete or change the value of the <legacyBold>Driver</legacyBold> keyword.</para>
    </content>
  </section>
  <section>
    <title>Deleting a Data Source</title>
    <content>
      <para>To delete a data source, a data source name must be passed to <legacyBold>ConfigDSN</legacyBold> in <legacyItalic>lpszAttributes</legacyItalic>. <legacyBold>ConfigDSN</legacyBold> checks that the data source name is in the Odbc.ini file (or registry). It then calls <legacyBold>SQLRemoveDSNFromIni</legacyBold> in the installer DLL to remove the data source.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For information about</para>
            </TD>
            <TD>
              <para>See</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Adding, modifying, or removing a data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Getting a value from the Odbc.ini file or the registry</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="b72ca065-4d67-48df-baac-e18379a8320a">SQLGetPrivateProfileString</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing the default data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="db803266-57df-4864-a41b-901247549c1f">SQLRemoveDefaultDataSource</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing a data source name from Odbc.ini (or registry)</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bb2e8273-7b61-4113-bfc8-f7ccc607c811">SQLRemoveDSNFromIni</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Adding a data source name to Odbc.ini (or registry)</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="dc7018b2-18d4-4657-96d0-086479a47474">SQLWriteDSNToIni</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Writing a value to the Odbc.ini file or the registry</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="526f36a4-92ed-4874-9725-82d27c0b86f9">SQLWritePrivateProfileString</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>