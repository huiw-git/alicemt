---
title: Create and Manage Subscriptions for Native Mode Report Servers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
---
# Create and Manage Subscriptions for Native Mode Report Servers
  A standard subscription is one that is created by individual users who want to have a report delivered through e\-mail or to a shared folder. This topic provides information about standard subscriptions that are created and managed by individual users. Data\-driven subscriptions have different requirements and steps, and are discussed in a separate topic. For more information, see [Create, Modify, and Delete Data-Driven Subscriptions](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Delete-Data-Driven-Subscriptions.md)  
  
 **In this topic:**  
  
-   [General requirements for subscriptions](#bkmk_create_subscription)  
  
-   [To Create a File Share Subscription](#bkmk_create_fileshare_subscription)  
  
-   [To Create an E-mail Subscription](#bkmk_create_email_subscription)  
  
-   [To modify a subscription](#bkmk_modify_subscription)  
  
-   [To Delete a Subscription](#bkmk_delete_subscription)  
  
##  <a name="bkmk_create_subscription"></a> General requirements for subscriptions  
 The content in this topic explains how to create subscriptions on a native mode report server using [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Report Manager. After you define a subscription, you can access it in Report Manager through the My Subscriptions page or the **Subscriptions** tab of a specific report.  
  
 [Create and Manage Subscriptions for SharePoint Mode Report Servers](../../Topics\TopicNameNotContainA/Create-and-Manage-Subscriptions-for-SharePoint-Mode-Report-Servers.md) explains how to use the application pages in a SharePoint site to subscribe to reports on a SharePoint mode report server.  
  
-   To use e\-mail delivery, the report server must be configured for an SMTP server or gateway connection before you create the subscription.  
  
-   To use file share delivery, you must have target folder already defined. For more information, see [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83).  
  
 Before you can subscribe to a report, the report data source must be configured to use stored credentials or no credentials. For more information, see [Store Credentials in a Reporting Services Data Source](../../Topics\TopicNameContainA/Store-Credentials-in-a-Reporting-Services-Data-Source.md). If it does not, the **New Subscription** button is not available.  
  
 This topic does not explain how to create a data\-driven subscription. For instructions on how to create a data\-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../Topic/Create%20a%20Data-Driven%20Subscription%20\(SSRS%20Tutorial\).md) or the online help for the Create a Data\-driven Subscription page in Report Manager.  
  
###  <a name="bkmk_create_fileshare_subscription"></a> To Create a File Share Subscription  
  
1.  Start [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  Navigate to the report you want to subscribe to. Click the report menu and click **Subscribe**.  
  
     ![report menu](../../Images\Image\ImageNotContaina/ssrs_report_menu_report_manager.png "ssrs_report_menu_report_manager")  
  
3.  **Description**: Type a description for the report, maximum 512 characters.  
  
4.  **Owner**: The owner field defaults to the current user and cannot be edited when you create the subscription. However, after the subscription is saved, you can change the subscription properties including the owner and description.  
  
5.  **Delivered by**: Select **Windows File Share**.  
  
6.  **File Name**: Type a file name for the report.  
  
7.  **Add a file extension when the file is created**: This option adds a three\-character file extension to the file name. The file extension is determined by the report output format you select.  
  
8.  **Path**: Type a Universal Naming Convention \(UNC\) path to an existing folder where you want to deliver the reports \(for example, \\\\\<servername\>\\\<myreports\>\). Include double backslash characters at the beginning of the path. Do not specify a trailing backslash.  
  
     ![file share subscription](../../Images\Image\ImageNotContaina/ssrs_file_share_subscription.png "ssrs_file_share_subscription")  
  
9. **Render Format**: Select a report output format for file delivery. Choose a format that corresponds to the desktop application that will be used to open the report. Avoid formats that do not render a report in a single stream or that introduce interactivity that cannot be supported in a static file \(for example, HTML 4.0\).  
  
10. **Credentials**: Select to use either the File share account or a specific Windows user credentials. The **Use file share account** is disabled if your report administrator has not configured a file share account. For more information, see [Subscription Settings and a File Share Account &#40;Configuration Manager&#41;](../Topic/Subscription%20Settings%20and%20a%20File%20Share%20Account%20\(Configuration%20Manager\).md). In the **User name** and **Password** text boxes, specify the credentials required to access the file share, using the format *\<domain\>*\\*\<user name\>* for the user name.  
  
11. **Overwrite options**:  
  
    -   **Do not overwrite the file if a previous version exists**, the delivery will not occur if an existing file is detected.  
  
    -   **Increment file names as newer versions are added**, the report server appends a number to the file name to distinguish it from existing files of the same name.  
  
12. **Schedule**: Specify when you want the report delivered:  
  
    -   To schedule a delivery time, click **When the scheduled report run is complete** and click the **Select Schedule** button. A schedule page opens.  
  
    -   To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.  
  
    -   To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**. If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.  
  
        > [!NOTE]  
        >  This option is available only for snapshots that are already associated with an update schedule.  
  
13. For parameterized reports, specify parameters to use for the report for this subscription. The parameters can be different from those used to run the report on demand or in other scheduled operations.  
  
 The report is delivered as a static file. If the report includes interactive features \(for example, links to additional rows and columns\), those features are not available.  
  
###  <a name="bkmk_create_email_subscription"></a> To Create an E\-mail Subscription  
  
1.  Start [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  Navigate to the report you want to subscribe to. Click the report menu and click **Subscribe**.  
  
     ![report menu](../../Images\Image\ImageNotContaina/ssrs_report_menu_report_manager.png "ssrs_report_menu_report_manager")  
  
3.  **Description**: Type a description for the report, maximum 512 characters.  
  
4.  **Owner**: The owner field defaults to the current user and cannot be edited when you create the subscription. However, after the subscription is saved, you can change the subscription properties including the owner and description.  
  
5.  **Delivered by**: Select **E\-Mail**. If **E\-Mail** is not available, your report server has not been configured for e\-mail subscriptions. See [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83)  
  
6.  **To**: The recipient name in the To: field is self\-addressed using your domain user account. Verify the format is \[user name\]@\[domain.com\]Report server configuration settings determine whether the **To** field is self\-addressed with your user account. For more information about changing the configuration settings e\-mail addresses, see [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83).  
  
    > [!NOTE]  
    >  Depending on your permissions, you might be able to type the e\-mail address you want the report delivered to. To specify multiple e\-mail addresses, separate them with a semicolon \(;\). You can also type additional e\-mail addresses in the **Cc**, **Bcc**, and **Reply\-To** text boxes. This requires that you have permission to manage all subscriptions.  
  
7.  **Subject**: Defaults to “@ReportName was executed at @ExecutionTime”. You can edit the subject but note that the @ReportName and @ExecutionTime are the only global variables supported in the **Subject** field.  
  
8.  Select the delivery options as follows:  
  
    -   **Include Report**: Select this option to embed or attach a copy of the report. The format of the report is determined by the rendering format you select. Do not choose this option if you think the report size will exceed the limit defined for your e\-mail system.  
  
    -   **Include Link**: Select this option to include a URL link to the report in the body of the e\-mail message.  
  
    > [!NOTE]  
    >  If you clear both of these options, only the notification text in the Subject line is sent.  
  
9. Choose a rendering format from the **Render Format** list box. This option is available if you select **Include Report** to embed or attach a copy of the report.  
  
    -   To embed the report in the body of the e\-mail message, select **Web archive**.  
  
    -   To send the report as an attachment, choose any of the other rendering formats.  
  
10. Select a priority from the **Priority** list box. In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Exchange, this setting sets a flag for the importance level of the e\-mail message.  
  
11. Specify when you want the report delivered:  
  
    -   To schedule a delivery time, click **When the scheduled report run is complete** and click **Select Schedule**. A schedule page opens for you.  
  
    -   To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.  
  
    -   To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**. If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.  
  
    > [!NOTE]  
    >  This option is available only for snapshots that are already associated with an update schedule.  
  
12. For parameterized reports, specify parameters to use for the report for this subscription. The parameters that you specify can be different from those used to run the report on demand or in other scheduled operations.  
  
##  <a name="bkmk_modify_subscription"></a> To modify a subscription  
 You can modify a subscription at any time. If you modify a subscription while it is being processed, the updated settings are used if they are saved to the report server before the delivery extension receives the subscription data. Otherwise, the existing settings are used.  
  
 A user who creates a subscription owns that subscription. Each user can modify or delete the subscriptions that he or she owns. You can change the owner of the report from the subscription properties page or you can change the ownership programmatically. For more information, see the following:  
  
-   [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../Topics\TopicNameContainA/Use-PowerShell-to-Change-and-List-Reporting-Services-Subscription-Owners-and-Run-a-Subscription.md)  
  
-   [ChangeSubscriptionOwner](assetId:///M:ReportService2010.ReportingService2010.ChangeSubscriptionOwner(System.String,System.String))  
  
 To locate a subscription, use the **My Subscriptions** page or view the subscription definitions that are associated with a report. You cannot search for subscriptions directly, nor can you search for a subscription based on owner name, trigger information, status information, and so forth.  
  
 Subscriptions can also be modified or deleted by report server administrators.  
  
> [!NOTE]  
>  A report server administrator cannot manage from one place all the individual subscriptions that are in use on a given report server. However, report server administrators can access each individual subscription to modify or delete it.  
  
##  <a name="bkmk_delete_subscription"></a> To Delete a Subscription  
 To delete a subscription”  
  
1.  Start [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  In Report Manager, click **My Subscriptions** on the toolbar and navigate to the subscription you want to modify or delete.  
  
3.  Open the report menu and click **Delete**  
  
     ![report menu](../../Images\Image\ImageNotContaina/ssrs_report_menu_report_manager.png "ssrs_report_menu_report_manager")  
  
 To cancel a subscription that is currently processing on the report server, see [Manage a Running Process](../../Topics\TopicNameContainA/Manage-a-Running-Process.md).  
  
 If you want to end a subscription and you cannot locate the subscription, make a note of the report you are receiving and search for it by name. Once you access the report, you can remove yourself from the subscription. If you cannot locate the subscription, the subscription may be a data\-driven subscription. For more information, see your report server administrator.  
  
 A subscription is deleted automatically if the underlying report is deleted. If you delete a subscription while it is being processed, the subscription stops if the delete operation occurs before the delivery extension receives subscription data. Otherwise, the subscription continues to be processed.  
  
## See Also  
 [Create and Manage Subscriptions for SharePoint Mode Report Servers](../../Topics\TopicNameNotContainA/Create-and-Manage-Subscriptions-for-SharePoint-Mode-Report-Servers.md)   
 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../Topics\TopicNameContainA/Use-PowerShell-to-Change-and-List-Reporting-Services-Subscription-Owners-and-Run-a-Subscription.md)   
 [Data-Driven Subscriptions](../../Topics\TopicNameNotContainA/Data-Driven-Subscriptions.md)   
 [Subscriptions and Delivery &#40;Reporting Services&#41;](../Topic/Subscriptions%20and%20Delivery%20\(Reporting%20Services\).md)   
 [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Use My Subscriptions &#40;Native Mode Report Server&#41;](../Topic/Use%20My%20Subscriptions%20\(Native%20Mode%20Report%20Server\).md)  
  
  