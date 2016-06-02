---
title: Specify the Default Snapshot Location (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
---
# Specify the Default Snapshot Location (SQL Server Management Studio)
  Specify the default snapshot location on the **Snapshot Folder** page of the Configure Distribution Wizard. For more information about using this wizard, see [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md). If you create a publication on a server that is not configured as a Distributor, specify a default snapshot location on the **Snapshot Folder** page of the New Publication Wizard. For more information about using this wizard, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
 Modify the default snapshot location on the **Publishers** page of the **Distributor Properties \- \<Distributor\>** dialog box. For more information, see [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md). Set the snapshot folder for each publication in the **Publication Properties \- \<Publication\>** dialog box. For more information, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
### To modify the default snapshot location  
  
1.  On the **Publishers** page of the **Distributor Properties \- \<Distributor\>** dialog box, click the properties button \(**…**\) for the Publisher for which you want to change the default snapshot location.  
  
2.  In the **Publisher Properties \- \<Publisher\>** dialog box, enter a value for the **Default Snapshot Folder** property.  
  
    > [!NOTE]  
    >  The Snapshot Agent must have write permissions for the directory you specify, and the Distribution Agent or Merge Agent must have read permissions. If pull subscriptions are used, you must specify a shared directory as a universal naming convention \(UNC\) path, such as \\\\computername\\snapshot. For more information, see [Secure the Snapshot Folder](../../Topics\TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
3.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Alternate Snapshot Folder Locations](../../Topics\TopicNameNotContainA/Alternate-Snapshot-Folder-Locations.md)   
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)  
  
  