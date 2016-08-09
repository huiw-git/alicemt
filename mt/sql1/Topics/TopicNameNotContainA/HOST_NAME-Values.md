---
title: "HOST_NAME Values"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 21
manager: jhubbard
---
# HOST_NAME Values
Merge publications with parameterized filters use the SUSER_SNAME() function and/or the HOST_NAME() function to filter data. The function is specified in the New Publication Wizard or the **Publication Properties** dialog box.  
  
 By default, the HOST_NAME() function returns the name of the computer connecting to the Publisher. When using parameterized filters, it is common to override this value by supplying a value on this page of the wizard. The HOST_NAME() function then returns the value you specify rather than the name of the computer. For more information, see the "Overriding the HOST_NAME() Value" section of [Parameterized Row Filters](../../Topics/TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
> [!NOTE]  
>  If you override HOST_NAME(), all calls to the HOST_NAME() function will return the value you specify. Ensure that other applications are not depending on HOST_NAME() returning the computer name.  
  
## Options  
 **Subscription properties**  
 Enter a value for each Subscriber in the **HOST_NAME Value** column or accept the default, which is the name of the Subscriber computer.  
  
## See Also  
 [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md)   
 [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md)   
 [View and Modify Pull Subscription Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md)   
 [View and Modify Push Subscription Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md)   
 [HOST_NAME (Transact-SQL)](assetId:///4b8b0705-c083-4b07-b954-c83ee73b2ebb)   
 [Subscribe to Publications](../../Topics/TopicNameNotContainA/Subscribe-to-Publications.md)