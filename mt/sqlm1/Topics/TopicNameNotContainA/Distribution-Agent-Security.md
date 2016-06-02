---
title: Distribution Agent Security
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
---
# Distribution Agent Security
  The **Distribution Agent Security** dialog box allows you to specify the Windows account under which the Distribution Agent runs. The Distribution Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions. The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account is also referred to as the *process account*, because the agent process runs under this account. Additional options available in the dialog box depend on how you access it:  
  
-   If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Distribution Agent makes connections to the Subscriber \(for push subscriptions\) or the Distributor \(for pull subscriptions\). The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account you specify.  
  
-   If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Distribution Agent makes connections by clicking the properties button \(**...**\) in the **Subscriber Connection** or **Distributor Connection** row of that dialog box. For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md) and how to: [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md).  
  
 All accounts must be valid, with the correct password specified for each account. Accounts and passwords are not validated until an agent runs.  
  
## Options  
 **Process Account**  
 Enter a Windows account under which the Distribution Agent runs:  
  
-   For push subscriptions, the account must:  
  
    -   At minimum be a member of the **db\_owner** fixed database role in the distribution database.  
  
    -   Be a member of the publication access list \(PAL\).  
  
    -   Have read permissions on the snapshot share.  
  
    -   Have read permissions on the install directory of the OLE DB provider for the Subscriber if the subscription is for a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscriber.  
  
-   For pull subscriptions, the account must at minimum be a member of the **db\_owner** fixed database role in the subscription database.  
  
 Additional permissions are required if the process account is impersonated when connections are made. See the **Connect to the Distributor** and **Connect to the Subscriber** sections below.  
  
 **Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)], because the Distribution Agent does not run on instances of [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)].  
  
 **Password** and **Confirm Password**  
 Enter the password for the Windows account.  
  
 **Connect to the Distributor**  
 For push subscriptions, connections to the Distributor are always made by impersonating the account specified in the **Process account** text box.  
  
 For pull subscriptions, select whether the Distribution Agent should make connections to the Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account. If you select to use a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account, enter a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login and password.  
  
> [!NOTE]  
>  It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account.  
  
 The Windows account or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account used for the connection must:  
  
-   Be a member of the PAL.  
  
-   Have read permissions on the snapshot share.  
  
 **Connect to the Subscriber**  
 For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.  
  
 For push subscriptions, the options are different for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers and non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers:  
  
-   For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers: select whether the Distribution Agent should make connections to the Subscriber by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account. If you select to use a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account, enter a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login and password.  
  
    > [!NOTE]  
    >  It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account.  
  
     The Windows account or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db\_owner** fixed database role in the subscription database.  
  
-   For non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers, specify the database login at the Subscriber that should be used when the Distribution Agent connects to the Subscriber. The login should have sufficient permissions to create objects in the subscription database. For more information about configuring non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers, see [Create a Subscription for a Non-SQL Server Subscriber](../../Topics\TopicNameContainA/Create-a-Subscription-for-a-Non-SQL-Server-Subscriber.md).  
  
 **Additional connection options**  
 Non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers only. Specify any connection options for the Subscriber in the form of a connection string \(Oracle does not require additional options\). Each option should be separated by a semi\-colon. The following is an example of an IBM DB2 connection string \(line breaks are for readability\):  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 Most of the options in the string are specific to the DB2 server you are configuring, but the **Process Binary as Character** option should always be set to **False**. A value is required for the **Initial Catalog** option to identify the subscription database. For more information, see [IBM DB2 Subscribers](../../Topics\TopicNameNotContainA/IBM-DB2-Subscribers.md).  
  
## See Also  
 [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md)   
 [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md)   
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  