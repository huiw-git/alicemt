---
title: HOST_NAME Values
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
---
# HOST_NAME Values
  Merge publications with parameterized filters use the SUSER\_SNAME\(\) function and\/or the HOST\_NAME\(\) function to filter data. The function is specified in the New Publication Wizard or the **Publication Properties** dialog box.  
  
 By default, the HOST\_NAME\(\) function returns the name of the computer connecting to the Publisher. When using parameterized filters, it is common to override this value by supplying a value on this page of the wizard. The HOST\_NAME\(\) function then returns the value you specify rather than the name of the computer. For more information, see the "Overriding the HOST\_NAME\(\) Value" section of [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
> [!NOTE]  
>  If you override HOST\_NAME\(\), all calls to the HOST\_NAME\(\) function will return the value you specify. Ensure that other applications are not depending on HOST\_NAME\(\) returning the computer name.  
  
## Options  
 **Subscription properties**  
 Enter a value for each Subscriber in the **HOST\_NAME Value** column or accept the default, which is the name of the Subscriber computer.  
  
## See Also  
 [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)   
 [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md)   
 [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md)   
 [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](../Topic/HOST_NAME%20\(Transact-SQL\).md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  