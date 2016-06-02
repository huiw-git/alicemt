---
title: Import Policies Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
---
# Import Policies Dialog Box
  Use this dialog box to import one or more policies \(and their referenced condition\) that are saved as XML files, into the current [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] instance.  
  
## Options  
 **Files to import**  
 To import a policy from an XML file, type the path and name of the file or use the Browse \(**...**\) button.  
  
 **Replace duplicates with items imported**  
 Select to overwrite any existing policy or condition of the same name if it already exists on this [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance. A condition with a dependent policy cannot be overwritten unless the dependent policy is also being overwritten. If this option is not selected, an existing condition that is using the same condition expression will not cause an error.  
  
 **Policy state**  
 Select the state that you want for the imported policy:  
  
-   **Preserve policy state on import**  
  
-   **Enable all policies on import**  
  
-   **Disable all policies on import**  
  
## See Also  
 [Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md)   
 [Import a Policy-Based Management Policy](../../Topics\TopicNameContainA/Import-a-Policy-Based-Management-Policy.md)   
 [Export a Policy-Based Management Policy](../../Topics\TopicNameContainA/Export-a-Policy-Based-Management-Policy.md)  
  
  