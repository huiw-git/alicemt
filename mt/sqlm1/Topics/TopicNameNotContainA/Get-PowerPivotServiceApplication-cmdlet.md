---
title: Get-PowerPivotServiceApplication cmdlet
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
---
# Get-PowerPivotServiceApplication cmdlet
  Returns one or more [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] service applications.  
  
 **Applies To:** SharePoint 2010 and SharePoint 2013.  
  
## Syntax  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## Description  
 The Get\-PowerPivotServiceApplication cmdlet returns the service application specified by the Identity parameter. If no parameter is specified, the cmdlet returns all [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] service applications in the farm. Each application is identified by its display name, application type, and GUID. To view additional properties of a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] service application, add the format\-list option to the cmdlet.  
  
## Parameters  
  
### \-Identity \<SPGeminiServiceApplicationPipeBind\>  
 Specifies the service application to get. The value must be a valid GUID that uniquely identifies the object in the farm.  
  
|||  
|-|-|  
|Required?|false|  
|Position?|0|  
|Default value||  
|Accept pipeline input?|true|  
|Accept wildcard characters?|false|  
  
### \<CommonParameters\>  
 This cmdlet supports the common parameters: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable,OutBuffer and OutVariable. For more information, see [About\_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Inputs and Outputs  
 The input type is the type of the objects that you can pipe to the cmdlet. The return type is the type of the objects that the cmdlet returns.  
  
|||  
|-|-|  
|Inputs|None.|  
|Outputs|None.|  
  
## Example 1  
  
```  
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 This example returns one or more service applications in the farm.  
  
## Example 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 This example returns all of the properties of a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] service application.  
  
## Example 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 This example returns a single service application, showing the display name, application type, and GUID of the application. If the display name is long, it will be truncated. Use the format\-list option to view the full name.  
  
  