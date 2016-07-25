---
title: "ADO Events Model Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29530153-b963-4a7c-8665-2335f1d604a8
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
# ADO Events Model Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Visual C++ section of <legacyLink xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</legacyLink> gives a general description of how to instantiate the ADO event model. The following is a specific example of instantiating the event model within the environment created by the <legacyBold>#import</legacyBold> directive.</para>
    <para>The general description uses <legacyBold>adoint.h</legacyBold> as a reference for method signatures. However, a few details in the general description change slightly as a result of using the <legacyBold>#import</legacyBold> directive:  </para>
    <list class="bullet">
      <listItem>
        <para>The <legacyBold>#import</legacyBold> directive resolves <legacyBold>typedef</legacyBold>'s, method signature data types, and modifiers to their fundamental forms.</para>
      </listItem>
      <listItem>
        <para>The pure virtual methods that must be overwritten are all prefixed by "<legacyBold>raw_</legacyBold>".</para>
      </listItem>
    </list>
    <para>Some of the code simply reflects coding style.  </para>
    <list class="bullet">
      <listItem>
        <para>The pointer to <legacyBold>IUnknown</legacyBold> used by the <legacyBold>Advise</legacyBold> method is obtained explicitly with a call to <legacyBold>QueryInterface</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>You don't need to explicitly code a destructor in the class definitions.</para>
      </listItem>
      <listItem>
        <para>You may want to code more robust implementations of QueryInterface, AddRef, and Release.</para>
      </listItem>
      <listItem>
        <para>The <legacyBold>__uuidof()</legacyBold> directive is used extensively to obtain interface IDs.</para>
      </listItem>
    </list>
    <para>Finally, the example contains some working code.  </para>
    <list class="bullet">
      <listItem>
        <para>The example is written as a console application.</para>
      </listItem>
      <listItem>
        <para>You should insert your own code under the comment, "<codeInline>// Do some work</codeInline>".</para>
      </listItem>
      <listItem>
        <para>All the event handlers default to doing nothing, and canceling further notifications. You should insert the appropriate code for your application, and allow notifications if required.</para>
      </listItem>
    </list>
    <code>// ADO_Events_Model_Example.cpp
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// The Connection events
class CConnEvent : public ConnectionEventsVt {
private:
   ULONG m_cRef;

public:
   CConnEvent() { m_cRef = 0; };
   ~CConnEvent() {};

   STDMETHODIMP QueryInterface(REFIID riid, void ** ppv);
   STDMETHODIMP_(ULONG) AddRef();
   STDMETHODIMP_(ULONG) Release();

   STDMETHODIMP raw_InfoMessage( struct Error *pError, 
                                 EventStatusEnum *adStatus, 
                                 struct _Connection *pConnection);

   STDMETHODIMP raw_BeginTransComplete( LONG TransactionLevel,
                                        struct Error *pError,
                                        EventStatusEnum *adStatus,
                                        struct _Connection *pConnection);

   STDMETHODIMP raw_CommitTransComplete( struct Error *pError, 
                                         EventStatusEnum *adStatus,
                                         struct _Connection *pConnection);

   STDMETHODIMP raw_RollbackTransComplete( struct Error *pError, 
                                           EventStatusEnum *adStatus,
                                           struct _Connection *pConnection);

   STDMETHODIMP raw_WillExecute( BSTR *Source,
                                 CursorTypeEnum *CursorType,
                                 LockTypeEnum *LockType,
                                 long *Options,
                                 EventStatusEnum *adStatus,
                                 struct _Command *pCommand,
                                 struct _Recordset *pRecordset,
                                 struct _Connection *pConnection);

   STDMETHODIMP raw_ExecuteComplete( LONG RecordsAffected,
                                     struct Error *pError,
                                     EventStatusEnum *adStatus,
                                     struct _Command *pCommand,
                                     struct _Recordset *pRecordset,
                                     struct _Connection *pConnection);

   STDMETHODIMP raw_WillConnect( BSTR *ConnectionString,
                                 BSTR *UserID,
                                 BSTR *Password,
                                 long *Options,
                                 EventStatusEnum *adStatus,
                                 struct _Connection *pConnection);

   STDMETHODIMP raw_ConnectComplete( struct Error *pError,
                                     EventStatusEnum *adStatus,
                                     struct _Connection *pConnection);

   STDMETHODIMP raw_Disconnect( EventStatusEnum *adStatus, struct _Connection *pConnection);
};

// The Recordset events
class CRstEvent : public RecordsetEventsVt {
private:
   ULONG m_cRef;   

public:
   CRstEvent() { m_cRef = 0; };
   ~CRstEvent() {};

   STDMETHODIMP QueryInterface(REFIID riid, void ** ppv);
   STDMETHODIMP_(ULONG) AddRef();
   STDMETHODIMP_(ULONG) Release();

   STDMETHODIMP raw_WillChangeField( LONG cFields,      
                                     VARIANT Fields,
                                     EventStatusEnum *adStatus,
                                     struct _Recordset *pRecordset);

   STDMETHODIMP raw_FieldChangeComplete( LONG cFields,
                                         VARIANT Fields,
                                         struct Error *pError,
                                         EventStatusEnum *adStatus,
                                         struct _Recordset *pRecordset);

   STDMETHODIMP raw_WillChangeRecord( EventReasonEnum adReason,
                                      LONG cRecords,
                                      EventStatusEnum *adStatus,
                                      struct _Recordset *pRecordset);

   STDMETHODIMP raw_RecordChangeComplete( EventReasonEnum adReason,
                                          LONG cRecords,
                                          struct Error *pError,
                                          EventStatusEnum *adStatus,
                                          struct _Recordset *pRecordset);

   STDMETHODIMP raw_WillChangeRecordset( EventReasonEnum adReason,
                                         EventStatusEnum *adStatus,
                                         struct _Recordset *pRecordset);

   STDMETHODIMP raw_RecordsetChangeComplete( EventReasonEnum adReason,
                                             struct Error *pError,
                                             EventStatusEnum *adStatus,
                                             struct _Recordset *pRecordset);

   STDMETHODIMP raw_WillMove( EventReasonEnum adReason,
                              EventStatusEnum *adStatus,
                              struct _Recordset *pRecordset);

   STDMETHODIMP raw_MoveComplete( EventReasonEnum adReason,
                                  struct Error *pError,
                                  EventStatusEnum *adStatus,
                                  struct _Recordset *pRecordset);

   STDMETHODIMP raw_EndOfRecordset( VARIANT_BOOL *fMoreData,
                                    EventStatusEnum *adStatus,
                                    struct _Recordset *pRecordset);

   STDMETHODIMP raw_FetchProgress( long Progress,
                                   long MaxProgress,
                                   EventStatusEnum *adStatus,
                                   struct _Recordset *pRecordset);

   STDMETHODIMP raw_FetchComplete( struct Error *pError, 
                                   EventStatusEnum *adStatus,
                                   struct _Recordset *pRecordset);
};

// Implement each connection method
STDMETHODIMP CConnEvent::raw_InfoMessage( struct Error *pError, 
                                         EventStatusEnum *adStatus,
                                         struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_BeginTransComplete( LONG TransactionLevel,
                                                 struct Error *pError,
                                                 EventStatusEnum *adStatus,
                                                 struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_CommitTransComplete( struct Error *pError,
                                                  EventStatusEnum *adStatus,
                                                  struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_RollbackTransComplete( struct Error *pError,
                                                    EventStatusEnum *adStatus,
                                                    struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_WillExecute( BSTR *Source,
                                          CursorTypeEnum *CursorType,
                                          LockTypeEnum *LockType,
                                          long *Options,
                                          EventStatusEnum *adStatus,
                                          struct _Command *pCommand,
                                          struct _Recordset *pRecordset,
                                          struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_ExecuteComplete( LONG RecordsAffected,
                                              struct Error *pError,
                                              EventStatusEnum *adStatus,
                                              struct _Command *pCommand,
                                              struct _Recordset *pRecordset,
                                              struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_WillConnect( BSTR *ConnectionString,
                                          BSTR *UserID,
                                          BSTR *Password,
                                          long *Options,
                                          EventStatusEnum *adStatus,
                                          struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_ConnectComplete( struct Error *pError,
                                              EventStatusEnum *adStatus,
                                              struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CConnEvent::raw_Disconnect( EventStatusEnum *adStatus, struct _Connection *pConnection) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

// Implement each recordset method
STDMETHODIMP CRstEvent::raw_WillChangeField( LONG cFields,
                                             VARIANT Fields,
                                             EventStatusEnum *adStatus,
                                             struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_FieldChangeComplete( LONG cFields,
                                                 VARIANT Fields,
                                                 struct Error *pError,
                                                 EventStatusEnum *adStatus,
                                                 struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_WillChangeRecord( EventReasonEnum adReason,
                                              LONG cRecords,
                                              EventStatusEnum *adStatus,
                                              struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_RecordChangeComplete( EventReasonEnum adReason,
                                                  LONG cRecords,
                                                  struct Error *pError,
                                                  EventStatusEnum *adStatus,
                                                  struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_WillChangeRecordset( EventReasonEnum adReason,
                                                 EventStatusEnum *adStatus,
                                                 struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_RecordsetChangeComplete( EventReasonEnum adReason,
                                                     struct Error *pError,
                                                     EventStatusEnum *adStatus,
                                                     struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_WillMove( EventReasonEnum adReason, 
                                      EventStatusEnum *adStatus,
                                      struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_MoveComplete( EventReasonEnum adReason,
                                          struct Error *pError,
                                          EventStatusEnum *adStatus,
                                          struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_EndOfRecordset( VARIANT_BOOL *fMoreData,
                                            EventStatusEnum *adStatus,
                                            struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_FetchProgress( long Progress,
                                           long MaxProgress,
                                           EventStatusEnum *adStatus,
                                           struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::raw_FetchComplete( struct Error *pError,
                                           EventStatusEnum *adStatus,
                                           struct _Recordset *pRecordset) {
   *adStatus = adStatusUnwantedEvent;
   return S_OK;
};

STDMETHODIMP CRstEvent::QueryInterface(REFIID riid, void ** ppv) {
   *ppv = NULL;
   if (riid == __uuidof(IUnknown) || riid == __uuidof(RecordsetEventsVt)) 
      *ppv = this;

   if (*ppv == NULL)
      return ResultFromScode(E_NOINTERFACE);

   AddRef();
   return NOERROR;
}

STDMETHODIMP_(ULONG) CRstEvent::AddRef() { 
   return ++m_cRef; 
};

STDMETHODIMP_(ULONG) CRstEvent::Release() { 
   if (0 != --m_cRef) 
      return m_cRef;
   delete this;
   return 0;
}

STDMETHODIMP CConnEvent::QueryInterface(REFIID riid, void ** ppv) {
   *ppv = NULL;
   if (riid == __uuidof(IUnknown) || riid == __uuidof(ConnectionEventsVt)) 
      *ppv = this;

   if (*ppv == NULL)
      return ResultFromScode(E_NOINTERFACE);

   AddRef();
   return NOERROR;
}

STDMETHODIMP_(ULONG) CConnEvent::AddRef() { 
   return ++m_cRef; 
};

STDMETHODIMP_(ULONG) CConnEvent::Release() { 
   if (0 != --m_cRef) 
      return m_cRef;
   delete this;
   return 0;
}

int main() {
   HRESULT hr;
   DWORD dwConnEvt;
   DWORD dwRstEvt;
   IConnectionPointContainer *pCPC = NULL;
   IConnectionPoint *pCP = NULL;
   IUnknown *pUnk = NULL;
   CRstEvent *pRstEvent = NULL;
   CConnEvent *pConnEvent= NULL;
   int rc = 0;
   _RecordsetPtr pRst; 
   _ConnectionPtr pConn;

   ::CoInitialize(NULL);

   hr = pConn.CreateInstance(__uuidof(Connection));

   if (FAILED(hr)) 
      return rc;

   hr = pRst.CreateInstance(__uuidof(Recordset));

   if (FAILED(hr)) 
      return rc;

   // Start using the Connection events
   hr = pConn-&gt;QueryInterface(__uuidof(IConnectionPointContainer), (void **)&amp;pCPC);

   if (FAILED(hr)) 
      return rc;
   
   hr = pCPC-&gt;FindConnectionPoint(__uuidof(ConnectionEvents), &amp;pCP);
   pCPC-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   pConnEvent = new CConnEvent();
   hr = pConnEvent-&gt;QueryInterface(__uuidof(IUnknown), (void **) &amp;pUnk);

   if (FAILED(hr)) 
      return rc;
   
   hr = pCP-&gt;Advise(pUnk, &amp;dwConnEvt);
   pCP-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   // Start using the Recordset events
   hr = pRst-&gt;QueryInterface(__uuidof(IConnectionPointContainer), (void **)&amp;pCPC);

   if (FAILED(hr)) 
      return rc;

   hr = pCPC-&gt;FindConnectionPoint(__uuidof(RecordsetEvents), &amp;pCP);
   pCPC-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   pRstEvent = new CRstEvent();
   hr = pRstEvent-&gt;QueryInterface(__uuidof(IUnknown), (void **) &amp;pUnk);

   if (FAILED(hr)) 
      return rc;

   hr = pCP-&gt;Advise(pUnk, &amp;dwRstEvt);
   pCP-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   // Do some work
   pConn-&gt;Open("dsn=DataPubs;", "", "", adConnectUnspecified);
   pRst-&gt;Open("SELECT * FROM authors", (IDispatch *) pConn, adOpenStatic, adLockReadOnly, adCmdText);

   pRst-&gt;MoveFirst();
   while (pRst-&gt;EndOfFile == FALSE) {
      wprintf(L"Name = '%s'\n", (wchar_t*) ((_bstr_t) pRst-&gt;Fields-&gt;GetItem("au_lname")-&gt;Value));
      pRst-&gt;MoveNext();
   }

   pRst-&gt;Close();
   pConn-&gt;Close();

   // Stop using the Connection events
   hr = pConn-&gt;QueryInterface(__uuidof(IConnectionPointContainer), (void **) &amp;pCPC);

   if (FAILED(hr)) 
      return rc;

   hr = pCPC-&gt;FindConnectionPoint(__uuidof(ConnectionEvents), &amp;pCP);
   pCPC-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   hr = pCP-&gt;Unadvise( dwConnEvt );
   pCP-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   // Stop using the Recordset events
   hr = pRst-&gt;QueryInterface(__uuidof(IConnectionPointContainer), (void **) &amp;pCPC);

   if (FAILED(hr)) 
      return rc;

   hr = pCPC-&gt;FindConnectionPoint(__uuidof(RecordsetEvents), &amp;pCP);
   pCPC-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   hr = pCP-&gt;Unadvise( dwRstEvt );
   pCP-&gt;Release();

   if (FAILED(hr)) 
      return rc;

   CoUninitialize();
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>