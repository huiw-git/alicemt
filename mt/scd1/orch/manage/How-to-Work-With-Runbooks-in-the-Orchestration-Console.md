---
title: How to Work With Runbooks in the Orchestration Console
ms.custom: na
ms.prod: system-center-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - orchestrator
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c844a02-9fb0-4c32-834c-22b90459c476
manager:cfreeman
---
# How to Work With Runbooks in the Orchestration Console
Use the following steps to run a runbook, to view the status of the jobs and instances of a runbook, and to stop a job in the Orchestration console.  
  
### To run a runbook in the Orchestration console  
  
1.  Click **Runbooks** to open the **Runbooks** workspace.  
  
2.  If the runbook is located in a folder, select the folder in the **Runbooks** pane.  
  
3.  Click the **Runbooks** tab in the results pane.  
  
4.  Select the runbook, and then in the **Actions** pane, click **Start Runbook**.  
  
5.  If the runbook requires parameters, they are listed in the **Runbook Parameters** pane. Click the **Value** column for each runbook and type a value for the runbook to use.  
  
6.  If you want to run the runbook on a server other than its default, click a server in the **Available Runbook Server\(s\)** pane, and then click the right arrow to add the server to the **Selected Runbook Server\(s\)** pane.  
  
    > [!NOTE]  
    > If you add multiple servers to the **Selected Runbook Server\(s\)** pane, the runbook runs only on the first server if it is available. The other servers are backup servers where the runbook runs only if the primary server is not available.  
  
7.  Click **Start**.  
  
### To view the status of a runbook in the Orchestration console  
  
1.  Click **Runbooks** to open the **Runbooks** workspace.  
  
2.  If the runbook is located in a folder, select the folder in the **Runbooks** pane.  
  
3.  Select the **Runbooks** tab in the results pane.  
  
4.  Select the runbook.  
  
5.  To view all jobs that the runbook created, in the **Actions** pane, select **View Jobs**.  
  
6.  To view all instances that the runbook created, in the **Actions** pane, select **View Instances**.  
  
### To stop a runbook in the Orchestration console  
  
1.  Click **Runbooks** to open the **Runbooks** workspace.  
  
2.  If the runbook is located in a folder, select the folder in the **Runbooks** pane.  
  
3.  Click the **Runbooks** tab in the results pane.  
  
4.  Select the runbook, and then in the **Actions** pane, click **Stop Runbook**.  
  
5.  Click **OK** to the message to confirm that you want to stop the jobs.  
  
6.  If the runbook was started successfully, you receive a confirmation message that the job was stopped. If the runbook has no running jobs, you receive a message that no job was running.  
  
## See Also  
[Overview of Orchestration Console](../../orch/manage/Overview-of-Orchestration-Console.md)  
[Orchestration Console Browser Requirements](../../orch/manage/Orchestration-Console-Browser-Requirements.md)  
[Orchestration Console Browser Requirements](../../orch/manage/Orchestration-Console-Browser-Requirements.md)  
  
