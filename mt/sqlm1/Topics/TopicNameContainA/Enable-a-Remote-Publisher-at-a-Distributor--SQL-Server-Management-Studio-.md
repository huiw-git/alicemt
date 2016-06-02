---
title: Enable a Remote Publisher at a Distributor (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
---
# Enable a Remote Publisher at a Distributor (SQL Server Management Studio)
  Enable a Publisher to use a remote Distributor on the **Publishers** page. This page is available in the Configure Distribution Wizard and the **Distributor Properties \- \<Distributor\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md) and [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md).  
  
### To enable a Publisher in the Configure Distribution Wizard  
  
1.  On the **Publishers** page of the Configure Distribution Wizard, click **Add**.  
  
2.  Click **Add SQL Server Publisher**. For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](../../Topics\TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md).  
  
3.  In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.  
  
4.  On the **Distributor Password** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor\_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.  
  
5.  To view and modify settings for a Publisher, click the properties button \(**…**\).  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
### To enable a Publisher in the Distributor Properties dialog box  
  
1.  On the **Publishers** page of the **Distributor Properties \- \<Distributor\>** dialog box, click **Add**.  
  
2.  Click **Add SQL Server Publisher**. For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](../../Topics\TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md).  
  
3.  In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.  
  
4.  On the **Publishers** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor\_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.  
  
5.  To view and modify settings for a Publisher, click the properties button \(**…**\).  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md)  
  
  