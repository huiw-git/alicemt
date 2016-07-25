---
title: "ErrorValueEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea
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
# ErrorValueEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the type of ADO run-time error.</para>
    <para>Three forms of the error number are listed:  </para>
    <list class="bullet">
      <listItem>
        <para>Positive decimal—The low two bytes of the full number in decimal format. This number is displayed in the default Visual Basic error message dialog box. For example, Run-time error '3707'.</para>
      </listItem>
      <listItem>
        <para>Negative decimal—The decimal translation of the full error number.</para>
      </listItem>
      <listItem>
        <para>Hexadecimal—The hexadecimal representation of the full error number. The Windows facility code is in the fourth digit. The facility code for ADO error numbers is <legacyItalic>A</legacyItalic>. For example: 0x800<legacyBold><legacyItalic>A</legacyItalic></legacyBold>0E7B.</para>
      </listItem>
    </list>
    <alert class="note">
      <para>OLE DB errors may be passed to your ADO application. Typically, these can be identified by a Windows facility code of <legacyItalic>4</legacyItalic>. For example, 0x800<legacyBold><legacyItalic>4</legacyItalic></legacyBold>.</para>
    </alert>
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
              <legacyBold>adErrBoundToCommand</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3707 -2146824581 0x800A0E7B</para>
          </TD>
          <TD>
            <para>Cannot change the <legacyBold>ActiveConnection</legacyBold> property of a <legacyBold>Recordset</legacyBold> object that has a <legacyBold>Command</legacyBold> object as its source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrCannotComplete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3732 -2146824556 0x800A0E94</para>
          </TD>
          <TD>
            <para>Server cannot complete the operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrCantChangeConnection</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3748 -2146824540 0x800A0EA4</para>
          </TD>
          <TD>
            <para>Connection was denied. New connection you requested has different characteristics than the one already being used.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrCantChangeProvider</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3220 -2146825068 0X800A0C94</para>
          </TD>
          <TD>
            <para>Supplied provider differs from the one already being used.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrCantConvertvalue</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3724 -2146824564 0x800A0E8C</para>
          </TD>
          <TD>
            <para>Data value cannot be converted for reasons other than sign mismatch or data overflow. For example, conversion would have truncated data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrCantCreate</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3725 -2146824563 0x800A0E8D</para>
          </TD>
          <TD>
            <para>Data value cannot be set or retrieved because the field data type was unknown, or the provider had insufficient resources to perform the operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrCatalogNotSet</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3747 -2146824541 0x800A0EA3</para>
          </TD>
          <TD>
            <para>Operation requires a valid <legacyBold>ParentCatalog</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrColumnNotOnThisRow</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3726 -2146824562 0x800A0E8E</para>
          </TD>
          <TD>
            <para>Record does not contain this field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrDataConversion</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3421 -2146824867 0x800A0D5D</para>
          </TD>
          <TD>
            <para>Application uses a value of the wrong type for the current operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrDataOverflow</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3721 -2146824567 0x800A0E89</para>
          </TD>
          <TD>
            <para>Data value is too large to be represented by the field data type.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrDelResOutOfScope</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3738 -2146824550 0x800A0E9A</para>
          </TD>
          <TD>
            <para>URL of the object to be deleted is outside the scope of the current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrDenyNotSupported</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3750 -2146824538 0x800A0EA6</para>
          </TD>
          <TD>
            <para>Provider does not support sharing restrictions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrDenyTypeNotSupported</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3751 -2146824537 0x800A0EA7</para>
          </TD>
          <TD>
            <para>Provider does not support the requested kind of sharing restriction.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrFeatureNotAvailable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3251 -2146825037 0x800A0CB3</para>
          </TD>
          <TD>
            <para>Object or provider is not able to perform requested operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrFieldsUpdateFailed</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3749 -2146824539 0x800A0EA5</para>
          </TD>
          <TD>
            <para>Fields update failed. For more information, examine the <legacyBold>Status </legacyBold>property of individual field objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrIllegalOperation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3219 -2146825069 0x800A0C93</para>
          </TD>
          <TD>
            <para>Operation is not allowed in this context.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrIntegrityViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3719 -2146824569 0x800A0E87</para>
          </TD>
          <TD>
            <para>Data value conflicts with the integrity constraints of the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrInTransaction</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3246 -2146825042 0x800A0CAE</para>
          </TD>
          <TD>
            <para>
              <legacyBold>Connection</legacyBold> object cannot be explicitly closed while in a transaction.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrInvalidArgument</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3001 -2146825287 0x800A0BB9</para>
          </TD>
          <TD>
            <para>Arguments are of the wrong type, are out of acceptable range, or are in conflict with one another.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrInvalidConnection</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3709 -2146824579 0x800A0E7D</para>
          </TD>
          <TD>
            <para>The connection cannot be used to perform this operation. It is either closed or invalid in this context.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrInvalidParamInfo</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3708 -2146824580 0x800A0E7C</para>
          </TD>
          <TD>
            <para>
              <legacyBold>Parameter</legacyBold> object is incorrectly defined. Inconsistent or incomplete information was provided.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrInvalidTransaction</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3714 -2146824574 0x800A0E82</para>
          </TD>
          <TD>
            <para>Coordinating transaction is invalid or has not started.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrInvalidURL</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3729 -2146824559 0x800A0E91</para>
          </TD>
          <TD>
            <para>URL contains invalid characters. Make sure that the URL is typed correctly.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrItemNotFound</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3265 -2146825023 0x800A0CC1</para>
          </TD>
          <TD>
            <para>Item cannot be found in the collection that corresponds to the requested name or ordinal.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrNoCurrentRecord</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3021 -2146825267 0x800A0BCD</para>
          </TD>
          <TD>
            <para>Either <legacyBold>BOF</legacyBold> or <legacyBold>EOF</legacyBold> is True, or the current record has been deleted. Requested operation requires a current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrNotExecuting</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3715 -2146824573 0x800A0E83</para>
          </TD>
          <TD>
            <para>Operation cannot be performed while not executing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrNotReentrant</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3710 -2146824578 0x800A0E7E</para>
          </TD>
          <TD>
            <para>Operation cannot be performed while processing event. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrObjectClosed</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3704 -2146824584 0x800A0E78</para>
          </TD>
          <TD>
            <para>Operation is not allowed when the object is closed. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrObjectInCollection</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3367 -2146824921 0x800A0D27</para>
          </TD>
          <TD>
            <para>Object is already in collection. Cannot append.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrObjectNotSet</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3420 -2146824868 0x800A0D5C</para>
          </TD>
          <TD>
            <para>Object is no longer valid.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrObjectOpen</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3705 -2146824583 0x800A0E79</para>
          </TD>
          <TD>
            <para>Operation is not allowed when the object is open. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrOpeningFile</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3002 -2146825286 0x800A0BBA</para>
          </TD>
          <TD>
            <para>File could not be opened.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrOperationCancelled</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3712 -2146824576 0x800A0E80</para>
          </TD>
          <TD>
            <para>Operation has been canceled by the user.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrOutOfSpace</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3734 -2146824554 0x800A0E96</para>
          </TD>
          <TD>
            <para>Operation cannot be performed. Provider cannot obtain enough storage space.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrPermissionDenied</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3720 -2146824568 0x800A0E88</para>
          </TD>
          <TD>
            <para>Insufficient permission prevents writing to the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrProviderFailed</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3000 -2146825288 0x800A0BB8</para>
          </TD>
          <TD>
            <para>Provider did not perform the requested operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrProviderNotFound</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3706 -2146824582 0x800A0E7A</para>
          </TD>
          <TD>
            <para>Provider cannot be found. It may not be correctly installed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrReadFile</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3003 -2146825285 0x800A0BBB</para>
          </TD>
          <TD>
            <para>File could not be read.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrResourceExists</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3731 -2146824557 0x800A0E93</para>
          </TD>
          <TD>
            <para>Copy operation cannot be performed. Object named by destination URL already exists. Specify <legacyBold>adCopyOverwrite</legacyBold> to replace the object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrResourceLocked</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3730 -2146824558 0x800A0E92</para>
          </TD>
          <TD>
            <para>Object represented by the specified URL is locked by one or more other processes. Wait until the process has finished and try the operation again.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrResourceOutOfScope</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3735 -2146824553 0x800A0E97</para>
          </TD>
          <TD>
            <para>Source or destination URL is outside the scope of the current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrSchemaViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3722 -2146824566 0x800A0E8A</para>
          </TD>
          <TD>
            <para>Data value conflicts with the data type or constraints of the field.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrSignMismatch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3723 -2146824565 0x800A0E8B</para>
          </TD>
          <TD>
            <para>Conversion failed because the data value was signed and the field data type used by the provider was unsigned.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrStillConnecting</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3713 -2146824575 0x800A0E81</para>
          </TD>
          <TD>
            <para>Operation cannot be performed while connecting asynchronously.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrStillExecuting</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3711 -2146824577 0x800A0E7F</para>
          </TD>
          <TD>
            <para>Operation cannot be performed while executing asynchronously.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrTreePermissionDenied</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3728 -2146824560 0x800A0E90</para>
          </TD>
          <TD>
            <para>Permissions are insufficient to access tree or subtree. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrUnavailable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3736 -2146824552 0x800A0E98</para>
          </TD>
          <TD>
            <para>Operation did not complete and the status is unavailable. The field may be unavailable or the operation was not attempted.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrUnsafeOperation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3716 -2146824572 0x800A0E84</para>
          </TD>
          <TD>
            <para>Safety settings on this computer prevent accessing a data source on another domain.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrURLDoesNotExist</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3727 -2146824561 0x800A0E8F</para>
          </TD>
          <TD>
            <para>Either the source URL or the parent of the destination URL does not exist.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrURLNamedRowDoesNotExist</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3737 -2146824551 0x800A0E99</para>
          </TD>
          <TD>
            <para>Record named by this URL does not exist. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrVolumeNotFound</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3733 -2146824555 0x800A0E95</para>
          </TD>
          <TD>
            <para>Provider cannot locate the storage device indicated by the URL. Make sure that the URL is typed correctly.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adErrWriteFile</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3004 -2146825284 0x800A0BBC</para>
          </TD>
          <TD>
            <para>Write to file failed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adWrnSecurityDialog</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3717 -2146824571 0x800A0E85</para>
          </TD>
          <TD>
            <para>For internal use only. Do not use.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adWrnSecurityDialogHeader</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3718 -2146824570 0x800A0E86</para>
          </TD>
          <TD>
            <para>For internal use only. Do not use.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <para>Only the following subsets of ADO/WFC equivalents are defined.</para>
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
              <para>AdoEnums.ErrorValue.BOUNDTOCOMMAND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.DATACONVERSION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.FEATURENOTAVAILABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.ILLEGALOPERATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.INTRANSACTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.INVALIDARGUMENT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.INVALIDCONNECTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.INVALIDPARAMINFO</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.ITEMNOTFOUND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.NOCURRENTRECORD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.NOTEXECUTING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.NOTREENTRANT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.OBJECTCLOSED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.OBJECTINCOLLECTION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.OBJECTNOTSET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.OBJECTOPEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.OPERATIONCANCELLED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.PROVIDERNOTFOUND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.STILLCONNECTING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.STILLEXECUTING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ErrorValue.UNSAFEOPERATION</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number Property</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3aee61c7-a9b7-4596-b78e-5828a00d0281">ADO Error Codes</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>