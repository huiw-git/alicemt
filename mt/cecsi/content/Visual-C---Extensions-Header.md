---
title: "Visual C++ Extensions Header"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e492d307-24cb-489c-a5b0-99cdc09b07da
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
# Visual C++ Extensions Header
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following header, <legacyBold>icrsint.h</legacyBold>, details the interface that allow clients to retrieve fields from a <legacyBold>Recordset</legacyBold> into variables defined in a class derived from <legacyBold>CADORecordBinding</legacyBold>. You must specify an ADO binding macro for each field you intend to access.</para>
    <code>#ifndef _ICRSINT_H_
#define _ICRSINT_H_

#include &lt;olectl.h&gt;
#include &lt;stddef.h&gt;

// forwards
class CADORecordBinding;

#define classoffset(base, derived) ((DWORD)(static_cast&lt;base*&gt;((derived*)8))-8)

enum ADOFieldStatusEnum
{   
   adFldOK = 0,
   adFldBadAccessor = 1,
   adFldCantConvertValue = 2,
   adFldNull = 3,
   adFldTruncated = 4,
   adFldSignMismatch = 5,
   adFldDataOverFlow = 6,
   adFldCantCreate = 7,
   adFldUnavailable = 8,
   adFldPermissionDenied = 9,
   adFldIntegrityViolation = 10,
   adFldSchemaViolation = 11,
   adFldBadStatus = 12,
   adFldDefault = 13
};

typedef struct stADO_BINDING_ENTRY
{
   ULONG      ulOrdinal;
   WORD       wDataType;
   BYTE       bPrecision;
   BYTE       bScale;
   ULONG      ulSize;
   ULONG      ulBufferOffset;
   ULONG      ulStatusOffset;
   ULONG      ulLengthOffset;
   ULONG      ulADORecordBindingOffSet;
   BOOL       fModify;
} ADO_BINDING_ENTRY;

#define BEGIN_ADO_BINDING(cls) public: \
   typedef cls ADORowClass; \
   const ADO_BINDING_ENTRY* STDMETHODCALLTYPE GetADOBindingEntries() { \
   static const ADO_BINDING_ENTRY rgADOBindingEntries[] = { 

//
// Fixed length non-numeric data
//
#define ADO_FIXED_LENGTH_ENTRY(Ordinal, DataType, Buffer, Status, Modify)\
   {Ordinal, \
   DataType, \
   0, \
   0, \
   0, \
   offsetof(ADORowClass, Buffer), \
   offsetof(ADORowClass, Status), \
   0, \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

#define ADO_FIXED_LENGTH_ENTRY2(Ordinal, DataType, Buffer, Modify)\
   {Ordinal, \
   DataType, \
   0, \
   0, \
   0, \
   offsetof(ADORowClass, Buffer), \
   0, \
   0, \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

//
// Numeric data
// 
#define ADO_NUMERIC_ENTRY(Ordinal, DataType, Buffer, Precision, Scale, Status, Modify)\
   {Ordinal, \
   DataType, \
   Precision, \
   Scale, \
   0, \
   offsetof(ADORowClass, Buffer), \
   offsetof(ADORowClass, Status), \
   0, \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

#define ADO_NUMERIC_ENTRY2(Ordinal, DataType, Buffer, Precision, Scale, Modify)\
   {Ordinal, \
   DataType, \
   Precision, \
   Scale, \
   0, \
   offsetof(ADORowClass, Buffer), \
   0, \
   0, \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

//
// Variable length data
//
#define ADO_VARIABLE_LENGTH_ENTRY(Ordinal, DataType, Buffer, Size, Status, Length, Modify)\
   {Ordinal, \
   DataType, \
   0, \
   0, \
   Size, \
   offsetof(ADORowClass, Buffer), \
   offsetof(ADORowClass, Status), \
   offsetof(ADORowClass, Length), \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

#define ADO_VARIABLE_LENGTH_ENTRY2(Ordinal, DataType, Buffer, Size, Status, Modify)\
   {Ordinal, \
   DataType, \
   0, \
   0, \
   Size, \
   offsetof(ADORowClass, Buffer), \
   offsetof(ADORowClass, Status), \
   0, \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

#define ADO_VARIABLE_LENGTH_ENTRY3(Ordinal, DataType, Buffer, Size, Length, Modify)\
   {Ordinal, \
   DataType, \
   0, \
   0, \
   Size, \
   offsetof(ADORowClass, Buffer), \
   0, \
   offsetof(ADORowClass, Length), \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

#define ADO_VARIABLE_LENGTH_ENTRY4(Ordinal, DataType, Buffer, Size, Modify)\
   {Ordinal, \
   DataType, \
   0, \
   0, \
   Size, \
   offsetof(ADORowClass, Buffer), \
   0, \
   0, \
   classoffset(CADORecordBinding, ADORowClass), \
   Modify},

#define END_ADO_BINDING()   {0, adEmpty, 0, 0, 0, 0, 0, 0, 0, FALSE}};\
   return rgADOBindingEntries;}

//
// Interface that the client 'record' class needs to support. The ADO Binding entries
// provide the implementation for this interface.
//
class CADORecordBinding
{
public:
   STDMETHOD_(const ADO_BINDING_ENTRY*, GetADOBindingEntries) (VOID) PURE;
};

//
// Interface that allows a client to fetch a record of data into class data members.
//
struct __declspec(uuid("00000544-0000-0010-8000-00aa006d2ea4")) IADORecordBinding;
DECLARE_INTERFACE_(IADORecordBinding, IUnknown)
{
public:
   STDMETHOD(BindToRecordset) (CADORecordBinding *pAdoRecordBinding) PURE;
   STDMETHOD(AddNew) (CADORecordBinding *pAdoRecordBinding) PURE;
   STDMETHOD(Update) (CADORecordBinding *pAdoRecordBinding) PURE;
};

#endif // !_ICRSINT_H_</code>
  </introduction>
  <relatedTopics>
<link xlink:href="9739c278-582c-402b-a158-7f68a1b2c293">ADO with Visual C++ Extensions Example</link>
<link xlink:href="ff759185-df41-4507-8d12-0921894ffbd9">Using Visual C++ Extensions for ADO</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>