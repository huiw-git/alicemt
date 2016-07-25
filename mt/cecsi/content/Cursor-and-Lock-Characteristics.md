---
title: "Cursor and Lock Characteristics"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
caps.latest.revision: 8
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
# Cursor and Lock Characteristics
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>While the characteristics of a cursor depend upon capabilities of the provider, the following advantages and disadvantages generally apply to the various types of cursors and locks.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Cursor or lock type</para>
            </TD>
            <TD>
              <para>Advantages</para>
            </TD>
            <TD>
              <para>Disadvantages</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyBold>adOpenForwardOnly</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Low resource requirements</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Cannot scroll backward</para>
                </listItem>
                <listItem>
                  <para>No data concurrency</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adOpenStatic</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Scrollable</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>No data concurrency</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adOpenKeyset</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Some data concurrency</para>
                </listItem>
                <listItem>
                  <para>Scrollable</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Higher resource requirements</para>
                </listItem>
                <listItem>
                  <para>Not available in disconnected scenario</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adOpenDynamic</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>High data concurrency</para>
                </listItem>
                <listItem>
                  <para>Scrollable</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Highest resource requirements</para>
                </listItem>
                <listItem>
                  <para>Not available in disconnected scenario</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adLockReadOnly</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Low resource requirements</para>
                </listItem>
                <listItem>
                  <para>Highly scalable</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Data not updatable through cursor</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adLockBatchOptimistic</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Batch updates </para>
                </listItem>
                <listItem>
                  <para>Allows disconnected scenarios</para>
                </listItem>
                <listItem>
                  <para>Other users able to access data</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Data can be changed by multiple users at once</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adLockPessimistic</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Data cannot be changed by other users while locked</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Prevents other users from accessing data while locked</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>adLockOptimistic</legacyBold>
            </para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Other users able to access data</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Data can be changed by multiple users at once</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>