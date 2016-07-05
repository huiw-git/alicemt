---
title: Replace Template Parameters
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Replace Template Parameters
Templates contain parameters that can be replaced by implementation\-specific values each time the template is used. After opening a template in a code editor, you can replace the parameters with values relevant to your implementation.  
  
## Before You Begin  
The **Specify Values for Template Parameters** dialog is a grid with three columns. The **Parameter** and **Type** columns are read\-only and cannot be changed. Review the contents of the **Value** column, and change any of the defaults to values appropriate for your implementation.  
  
To use this dialog box, you must have parameters in your script enclosed in angle brackets (`< >`) in the format `<`*parameter\_name*`,` *data\_type*`,` *default\_value*`>`.  
  
## Replace Template Parameters  
After opening the template in a code editor window:  
  
1.  On the **Query** menu, click **Specify Values for Template Parameters**.  
  
2.  In the **Specify Values for Template Parameters** dialog box, the **Values** column contains a suggested value for each parameter. Accept the value or replace it with a new value.  
  
3.  Click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the query editor.  
  
## See Also  
[Template Explorer](../content/Template-Explorer.md)  
[Open a Template](../content/Open-a-Template.md)  
  
