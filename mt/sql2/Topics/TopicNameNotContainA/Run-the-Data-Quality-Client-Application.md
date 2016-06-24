---
title: Run the Data Quality Client Application
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
---
# Run the Data Quality Client Application
  Run [!INCLUDE[ssDQSClient](../../Topics/TopicNameContainA/includes/ssDQSClient_md.md)], and log on to a [!INCLUDE[ssDQSServer](../../Topics/TopicNameContainA/includes/ssDQSServer_md.md)].  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 You must have completed the [!INCLUDE[ssDQSServer](../../Topics/TopicNameContainA/includes/ssDQSServer_md.md)] installation by running the DQSInstaller.exe file. For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](../../Topics/TopicNameNotContainA/Run-DQSInstaller.exe-to-Complete-Data-Quality-Server-Installation.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have one of the three DQS roles (dqs_adminstrator, dqs_kb_editor, or dqs_kb_operator) granted on the DQS_MAIN database to be able to log on to [!INCLUDE[ssDQSServer](../../Topics/TopicNameContainA/includes/ssDQSServer_md.md)].  
  
##  <a name="Run"></a> Run Data Quality Client  
 To run [!INCLUDE[ssDQSClient](../../Topics/TopicNameContainA/includes/ssDQSClient_md.md)] on the computer where you have installed it:  
  
1.  Click **Start**, point to **All Programs**, click **[!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)]**, click **Data Quality Services**, and then click **Data Quality Client**.  
  
2.  In the **Connect to Server** dialog box:  
  
    1.  Specify the server that you want to connect the [!INCLUDE[ssDQSClient](../../Topics/TopicNameContainA/includes/ssDQSClient_md.md)] application to. Select **(LOCAL)** to connect to [!INCLUDE[ssDQSServer](../../Topics/TopicNameContainA/includes/ssDQSServer_md.md)] on the local computer. You can also click the down arrow and select **<Browse network for more servers\>** to connect to a different server (or to connect to the local server by name). The **Browse for Servers** dialog box will be displayed. You can select a server in the **Local Servers** tab or in the **Network Servers** tab.  
  
    2.  To encrypt data transfer between [!INCLUDE[ssDQSServer](../../Topics/TopicNameContainA/includes/ssDQSServer_md.md)] and [!INCLUDE[ssDQSClient](../../Topics/TopicNameContainA/includes/ssDQSClient_md.md)], click **Options**, and then select the **Encrypt Connection** check box.  
  
3.  Click **Connect**.  
  
 The [!INCLUDE[ssDQSClient](../../Topics/TopicNameContainA/includes/ssDQSClient_md.md)] home screen appears. For more information, see [Data Quality Client Home Screen](../../Topics/TopicNameNotContainA/Data-Quality-Client-Home-Screen.md).  
  
  