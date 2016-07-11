---
title: How to Enable an Email Notification Channel
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb68582d-fe83-4d79-9017-55673f7f65b9
---
# How to Enable an Email Notification Channel
To configure alert notifications for [!INCLUDE[om12long](../../om/manage/includes/om12long_md.md)], your first task is to enable a notification channel. This topic describes how to configure a channel that will send alert notifications to subscribers by using email.  
  
Before you begin, gather the following information:  
  
-   SMTP server information  
  
    -   Fully qualified domain name \(FQDN\).  
  
    -   Port number for the SMTP server.  
  
    -   Authentication method for the SMTP server. You have two choices: anonymous or Windows Integrated.  
  
-   Return email address. This address is used for all email notifications on this channel and will receive any replies to notifications.  
  
-   Email subject and body text that you want subscribers to receive. For more information, see [How to Customize Message Content for Notifications](../../om/manage/How-to-Customize-Message-Content-for-Notifications.md).  
  
### To enable an email notification channel  
  
1.  Log on to the computer with a user account that is a member of the Operations Manager Administrators role.  
  
2.  In the Operations console, click **Administration**.  
  
3.  In the navigation pane, under **Notifications**, right\-click **Channels**. Click **New channel** and then click **E\-mail \(SMTP\)**.  
  
4.  Type a name for the channel, such as **SMTP channel** and optionally provide a description. Click **Next**.  
  
5.  In the **SMTP servers** area, click **Add**.  
  
6.  In the **Add SMTP Server** dialog box, type the fully qualified domain name \(FQDN\) of a Simple Mail Transfer Protocol \(SMTP\) server, type the port number, select the authentication method used by the SMTP server, and then click **OK**.  
  
    > [!NOTE]  
    > You can add one or more additional servers to act as backup servers. If the primary SMTP server is unavailable, notifications are sent through the secondary server.  
  
7.  Type the **Return Address** that should appear on email notifications, and then in the **Retry interval** list, select the number of minutes to wait before trying to resend a notification to the primary SMTP server. Click **Next**.  
  
    > [!NOTE]  
    > If you have only one SMTP server and it’s unavailable, the Retry interval has no effect. The Retry interval is used when you have a secondary server and mail sending to the primary server fails. When this happens, Operations Manager switches to the secondary server and checks the Retry interval time. If the Retry interval time has passed, Operations Manager tries to use the primary server.  
  
8.  In the **Default e\-mail notification format** area, specify the **E\-mail subject** and **E\-mail message** text or leave the default selections, select the **Importance** level that you want the emails sent with, and then specify the **Encoding** type. You can click the right arrow next to the **E\-mail subject** and **E\-mail message** boxes for a full list of available variables. For more information, see [How to Customize Message Content for Notifications](../../om/manage/How-to-Customize-Message-Content-for-Notifications.md).  
  
9. Click **Finish**, and then click **Close**.  
  
Next task: [How to Create and Configure the Notification Action Account](../../om/manage/How-to-Create-and-Configure-the-Notification-Action-Account.md)  
  
## See Also  
[How to Enable an Instant Message Notification Channel](../../om/manage/How-to-Enable-an-Instant-Message-Notification-Channel.md)  
[How to Enable a Text Message &#40;SMS&#41; Notification Channel](../../om/manage/How-to-Enable-a-Text-Message--SMS--Notification-Channel.md)  
[How to Enable a Command Notification Channel](../../om/manage/How-to-Enable-a-Command-Notification-Channel.md)  
[How to Create Notification Subscribers](../../om/manage/How-to-Create-Notification-Subscribers.md)  
[How to Create Notification Subscriptions](../../om/manage/How-to-Create-Notification-Subscriptions.md)  
[Subscribing to Alert Notifications](../../om/manage/Subscribing-to-Alert-Notifications.md)  
[How to Create and Configure the Notification Action Account](../../om/manage/How-to-Create-and-Configure-the-Notification-Action-Account.md)  
[How to Customize Message Content for Notifications](../../om/manage/How-to-Customize-Message-Content-for-Notifications.md)  
[How to Subscribe to Notifications from an Alert](../../om/manage/How-to-Subscribe-to-Notifications-from-an-Alert.md)  
[How to Create Subscriptions Using Classes and Groups](../../om/manage/How-to-Create-Subscriptions-Using-Classes-and-Groups.md)  
[How to Specify Which Alerts Generate Notifications &#40;Conditions&#41;](../../om/manage/How-to-Specify-Which-Alerts-Generate-Notifications--Conditions-.md)  
[Sending Notifications for Specific Computers and Specific Alerts to Specific Teams](../../om/manage/Sending-Notifications-for-Specific-Computers-and-Specific-Alerts-to-Specific-Teams.md)  
  
