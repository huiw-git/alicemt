---
title: "ADO Event Instantiation: Visual C++"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 385ad90a-37d0-497c-94aa-935d21fed78f
caps.latest.revision: 11
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
# ADO Event Instantiation: Visual C++
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This is a schematic description of how to instantiate ADO events in Microsoft® Visual C++®. See <legacyLink xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">ADO Events Model Example (VC++)</legacyLink> for a complete description.</para>
    <para>Create classes derived from the <legacyBold>ConnectionEventsVt</legacyBold> and <legacyBold>RecordsetEventsVt</legacyBold> interfaces found in the file adoint.h.</para>
    <code>// BeginEventExampleVC01
class CConnEvent : public ConnectionEventsVt
{
    public:
    STDMETHODIMP InfoMessage( 
            ADOError *pError,
            EventStatusEnum *adStatus,
            _ADOConnection *pConnection);
...
}

class CRstEvent : public RecordsetEventsVt 
{
    public:
        STDMETHODIMP WillChangeField( 
                LONG cFields,
                VARIANT Fields,
                EventStatusEnum *adStatus,
                _ADORecordset *pRecordset);
...
}
// EndEventExampleVC01</code>
    <para>Implement each of the event-handler methods in both classes. It is sufficient that each method merely return an HRESULT of S_OK. However, when you make it known that your event handlers are available, they will be called continuously by default. Instead, you might want to request no further notification after the first time by setting <legacyBold>adStatus</legacyBold> to <legacyBold>adStatusUnwantedEvent</legacyBold>.</para>
    <code>// BeginEventExampleVC02
STDMETHODIMP CConnEvent::ConnectComplete(
            ADOError *pError,
            EventStatusEnum *adStatus,
            _ADOConnection *pConnection) 
        {
        *adStatus = adStatusUnwantedEvent;
        return S_OK;
        }

// EndEventExampleVC02</code>
    <para>The event classes inherit from <legacyBold>IUnknown</legacyBold>, so you must also implement the <legacyBold>QueryInterface</legacyBold>, <legacyBold>AddRef</legacyBold>, and <legacyBold>Release</legacyBold> methods. Also implement class constructors and destructors. Choose the Visual C++ tools with which you are most comfortable to simplify this part of the task.</para>
    <para>Make it known that your event handlers are available by issuing <legacyBold>QueryInterface</legacyBold> on the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> objects for the <legacyBold>IConnectionPointContainer</legacyBold> and <legacyBold>IConnectionPoint</legacyBold> interfaces. Then issue <legacyBold>IConnectionPoint::Advise</legacyBold> for each class.</para>
    <para>For example, assume you are using a Boolean function that returns <legacyBold>True</legacyBold> if it successfully informs a <legacyBold>Recordset</legacyBold> object that you have event handlers available.</para>
    <code>// BeginEventExampleVC03
HRESULT    hr;
DWORD      dwEvtClass;
IConnectionPointContainer    *pCPC = NULL;
IConnectionPoint             *pCP = NULL;
CRstEvent                    *pRStEvent = NULL;
...
_RecordsetPtr                pRs;
pRs.CreateInstance(__uuidof(Recordset));
pRStEvent = new CRstEvent;
if (pRStEvent == NULL) return FALSE;
...
hr = pRs-&gt;QueryInterface(IID_IConnectionPointContainer, (LPVOID *)&amp;pCPC);
if (FAILED(hr)) return FALSE;
hr = pCPC-&gt;FindConnectionPoint(RecordsetEvents, &amp;pCP);
pCPC-&gt;Release();    // Always Release now, even before checking.
if (FAILED(hr)) return FALSE;
hr = pCP-&gt;Advise(pRstEvent, &amp;dwEvtClass);   //Turn on event support.
pCP-&gt;Release();
if (FAILED(hr)) return FALSE;
...
return TRUE;
...
// EndEventExampleVC03</code>
    <para>At this point, events for the <legacyBold>RecordsetEvent</legacyBold> family are enabled and your methods will be called as <legacyBold>Recordset</legacyBold> events occur.</para>
    <para>Later, when you want to make your event handlers unavailable, get the connection point again and issue the <legacyBold>IConnectionPoint::Unadvise</legacyBold> method.</para>
    <code>// BeginEventExampleVC04
...
hr = pCP-&gt;Unadvise(dwEvtClass);    //Turn off event support.
pCP-&gt;Release();
if (FAILED(hr)) return FALSE;
...
// EndEventExampleVC04</code>
    <para>You must release interfaces and destroy class objects as appropriate.</para>
    <para>The following code shows a complete example of a <legacyBold>Recordset</legacyBold> Event sink class.</para>
    <code>// BeginEventExampleVC05.cpp
// compile with: /LD
#include &lt;adoint.h&gt;

class CADORecordsetEvents : public RecordsetEventsVt {

public:
   ULONG m_ulRefCount;
   CADORecordsetEvents():m_ulRefCount(1){}

   STDMETHOD(QueryInterface)(REFIID iid, LPVOID * ppvObject) {
      if (IsEqualIID(__uuidof(IUnknown), iid) || IsEqualIID(__uuidof(RecordsetEventsVt), iid)) {
         *ppvObject = this;
         return S_OK;
      }
      else 
         return E_NOINTERFACE;
   }

   STDMETHOD_(ULONG, AddRef)() {
      return m_ulRefCount++;
   }

   STDMETHOD_(ULONG, Release)() {
      if (--m_ulRefCount == 0) {
         delete this;
         return 0;
      }
      else 
         return m_ulRefCount;
   }


   STDMETHOD(WillChangeField)( LONG cFields, 
                               VARIANT Fields, 
                               EventStatusEnum *adStatus,
                               _ADORecordset *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(FieldChangeComplete)( LONG cFields,
                                   VARIANT Fields,
                                   ADOError *pError,
                                   EventStatusEnum *adStatus,
                                   _ADORecordset *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(WillChangeRecord)( EventReasonEnum adReason,
                                LONG cRecords,
                                EventStatusEnum *adStatus,
                                _ADORecordset *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(RecordChangeComplete)( EventReasonEnum adReason,
                                    LONG cRecords,
                                    ADOError  *pError,
                                    EventStatusEnum  *adStatus,
                                    _ADORecordset  *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(WillChangeRecordset)( EventReasonEnum adReason,
                                   EventStatusEnum *adStatus,
                                   _ADORecordset  *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(RecordsetChangeComplete)( EventReasonEnum adReason,
                                       ADOError *pError,
                                       EventStatusEnum  *adStatus,
                                       _ADORecordset  *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(WillMove)( EventReasonEnum adReason,
                        EventStatusEnum  *adStatus,
                        _ADORecordset  *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(MoveComplete)( EventReasonEnum adReason,
                            ADOError *pError,
                            EventStatusEnum *adStatus,
                            _ADORecordset  *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(EndOfRecordset)( VARIANT_BOOL *fMoreData,
                              EventStatusEnum *adStatus,
                              _ADORecordset *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(FetchProgress)( long Progress,
                             long MaxProgress,
                             EventStatusEnum *adStatus,
                             _ADORecordset *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }

   STDMETHOD(FetchComplete)( ADOError *pError,
                             EventStatusEnum *adStatus,
                             _ADORecordset *pRecordset) {
      *adStatus = adStatusUnwantedEvent; 
      return S_OK;
   }
};</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>