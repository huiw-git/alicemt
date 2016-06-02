---
title: Manage (Open, Unlock, Rename, and Delete) a Data Quality Project
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
---
# Manage (Open, Unlock, Rename, and Delete) a Data Quality Project
  This topic describes how to manage a data quality project by using [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] such as open, unlock, rename, and delete a data quality project.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="LimitationsRestrictions"></a> Limitations and Restrictions  
  
-   You cannot open a locked project that is created by another user.  
  
-   You cannot unlock, rename, or delete a data quality project that is created by another user.  
  
-   You cannot delete a locked data quality project. You must first unlock it to delete.  
  
-   You can only unlock a data quality project that is created by you.  
  
###  <a name="Prerequisites"></a> Prerequisites  
 You must have at least one data quality project to manage.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have the dqs\_kb\_editor or dqs\_kb\_operator role on the DQS\_MAIN database to manage a data quality project.  
  
##  <a name="Open"></a> Open a Data Quality Project  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **Open data quality project**. The **Open project** screen appears.  
  
     Alternately, you can directly open a data quality project listed under **Recent data quality project** area by clicking it.  
  
3.  In the **Open project** screen, click to select the data quality project that you want to open, and click **Next**.  
  
4.  The data quality project opens at the same state of the activity where it was last closed. A data quality project has the following states:  
  
    -   For the **Cleansing** activity, a data quality project can have the following states: **Cleansing \- Map**, **Cleansing \- Cleanse**, **Cleansing – Manage and View Results**, and **Cleansing – Export**.  
  
    -   For the **Matching** activity, a data quality project can have the following states: **Matching \- Map**, **Matching \- Matching**, **Matching – Survivorship**, and **Matching – Export**.  
  
##  <a name="Unlock"></a> Unlock a Data Quality Project  
 When you create a data quality project, it is in a locked state to prevent usage or modification by other users. You must unlock the data quality project after you have completed your work if you want other users to work on your data quality project. A lock symbol is displayed for projects that are locked.  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **Open data quality project**. The **Open project** screen appears.  
  
3.  In the **Open project** screen, right\-click a locked data quality project that is created by you, and then click **Unlock** in the shortcut menu. A green check mark is displayed for the project indicating that it is unlocked.  
  
##  <a name="Rename"></a> Rename a Data Quality Project  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **Open data quality project**. The **Open project** screen appears.  
  
3.  In the **Open project** screen, right\-click a data quality project that is created by you, and then click **Rename** in the shortcut menu.  
  
4.  The data quality project name becomes editable in the **Name** column. Type a new name, and then press Enter.  
  
##  <a name="Delete"></a> Delete a Data Quality Project  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, click **Open data quality project**. The **Open project** screen appears.  
  
3.  In the **Open project** screen, right\-click an unlocked data quality project that is created by you, and then click **Delete** in the shortcut menu.  
  
4.  A confirmation message appears. Click **Yes**.  
  
  