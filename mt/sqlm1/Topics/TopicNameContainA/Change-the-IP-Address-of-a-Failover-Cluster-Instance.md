---
title: Change the IP Address of a Failover Cluster Instance
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
---
# Change the IP Address of a Failover Cluster Instance
  This topic describes how to change the IP address resource in an Always On Failover Cluster Instance \(FCI\) by using the Failover Cluster Manager snap\-in. The Failover Cluster Manager snap\-in is the cluster management application for the Windows Server Failover Clustering \(WSFC\) service.  
  
-   **Before you begin:**  [Security](#Security)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
 Before you begin, review the following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online topic: [Before Installing Failover Clustering](../../Topics\TopicNameNotContainA/Before-Installing-Failover-Clustering.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 To maintain or update an FCI, you must be a local administrator with permission to logon as a service on all nodes of the FCI.  
  
##  <a name="WSFC"></a> Using the Failover Cluster Manager Snap\-in  
 **To change the IP address resource for an FCI**  
  
1.  Open the Failover Cluster Manager snap\-in.  
  
2.  Expand the **Services and applications** node, in the left pane and click on the FCI.  
  
3.  On the right pane, under the **Server Name** category, right\-click the SQL Server Instance, and select **Properties** option to open the **Properties** dialog box.  
  
4.  On the **General** tab, change the IP address resource.  
  
5.  Click **OK** to close the dialog box.  
  
6.  In the right\-hand pane, right\-click the SQL IP Address1\(failover cluster instance name\) and select **Take Offline**. You will see the SQL IP Address1\(failover cluster instance name\), SQL Network Name\(failover cluster instance name\), and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] status change from Online to Offline Pending, and then to Offline.  
  
7.  In the right\-hand pane, right\-click [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and then select **Bring Online**. You will see the SQL IP Address1\(failover cluster instance name\), SQL Network Name\(failover cluster instance name\), and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] status change from Offline to Online Pending, and then to Online.  
  
8.  Close the Failover Cluster Manager snap\-in.  
  
  