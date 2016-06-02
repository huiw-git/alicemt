---
title: LANGUAGE and FORMAT_STRING on FORMATED_VALUE
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7534ff5f-954e-47d4-a2ed-4b5b8ccb30e6
---
# LANGUAGE and FORMAT_STRING on FORMATED_VALUE
  The FORMATTED\_VALUE property is built on the interactions of the VALUE, FORMAT\_STRING and LANGUAGE properties of the cell. This topic explains how these properties interact to build the FORMATTED\_VALUE property.  
  
## VALUE, FORMAT\_STRING, LANGUAGE properties  
 The following table explains what these properties are, to help prepare us to use them in combination.  
  
 VALUE  
 The unformatted value of the cell.  
  
 FORMAT\_STRING  
 The formatting template to be applied to the value of the cell to generate FORMATTED\_VALUE property  
  
 LANGUAGE  
 The locale specification to be applied alongside FORMAT\_STRING to generate a localized version of FORMATTED\_VALUE  
  
## FORMATTED\_VALUE constructed  
 The FORMATTED\_VALUE property is constructed by using the value from the VALUE property and applying the format template specified in the FORMAT\_STRING property to that value. In addition, whenever the formatting value is a **named formatting literal** the LANGUAGE property specification modifies the output of FORMAT\_STRING to follow the language usage for the named formatting. Named formatting literals are all defined in a way that can be localized. For example, `"General Date"` is a specification that can be localized, as opposed to the following template `"YYYY-MM-DD hh:nn:ss",` which states that the date is to be presented as defined by the template regardless of the language specification.  
  
 If there is a conflict between the FORMAT\_STRING template and the LANGUAGE specification, the FORMAT\_STRING template overrides the LANGUAGE specification. For example, if FORMAT\_STRING\="$ \#0" and LANGUAGE\=1034 \(Spain\), and VALUE\=123.456 then FORMATTED\_VALUE\="$ 123" instead of FORMATTED\_VALUE\="€ 123", the expected format is in Euros, because the value of the format template overrides the language specified.  
  
### Examples  
 The following examples show the output obtained when LANGUAGE is used in conjunction with FORMAT\_STRING.  
  
 The first example explains formatting numerical values; the second example explains formatting date and time values.  
  
 For each example the Multidimensional Expressions \(MDX\) code is given.  
  
 `with`  
  
 `member measures.A as 5040, FORMAT_STRING="Currency"`  
  
 `member measures.B as measures.A, LANGUAGE=1034`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="$#,##0.00"`  
  
 `member measures.D as measures.A, FORMAT_STRING="Scientific"`  
  
 `member measures.E as measures.A, LANGUAGE=1034 , FORMAT_STRING="Scientific"`  
  
 `member measures.F as 0.5040, FORMAT_STRING="Percent"`  
  
 `member measures.G as measures.F, LANGUAGE=1034`  
  
 `member measures.H as 0, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.I as 59, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.J as 0, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `member measures.K as -312, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F, measures.G, measures.H, measures.I, measures.J, measures.K} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] over a server and client with locale 1033 are as follows:  
  
|Member|FORMATTED\_VALUE|Explanation|  
|------------|----------------------|-----------------|  
|A|$5,040.00|FORMAT\_STRING is set to `Currency` and LANGUAGE is `1033`, inherited from system locale value|  
|B|€5.040,00|FORMAT\_STRING is set to `Currency` \(inherited from A\) and LANGUAGE is explicitly set to `1034` \(Spain\) hence the Euro sign, the different decimal separator and the different thousand separator.|  
|C|$5.040,00|FORMAT\_STRING is set to `$#,##0.00` an override to Currency, from A, and LANGUAGE is explicitly set to `1034` \(Spain\). Because the FORMAT\_STRING property explicitly set the currency symbol to $, the FORMATTED\_VALUE is presented with the $ sign. However, because `.` \(dot\) and `,` \(comma\) are placeholders for decimal separator and thousand separator respectively, the language specification affects them generating an output that is localized for decimal and thousand separators.|  
|D|5.04E\+03|FORMAT\_STRING is set to `Scientific` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` \(dot\) is the decimal separator.|  
|E|5,04E\+03|FORMAT\_STRING is set to `Scientific` and LANGUAGE is set explicitly to `1034,` hence `,` \(comma\) is the decimal separator.|  
|F|50.40%|FORMAT\_STRING is set to `Percent` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` \(dot\) is the decimal separator.<br /><br /> Note that VALUE was changed from 5040 to 0.5040|  
|G|50,40%|FORMAT\_STRING is set to `Percent`, inherited from F, and LANGUAGE is set explicitly to `1034` hence `,` \(comma\) is the decimal separator.<br /><br /> Note that VALUE was inherited from F value.|  
|H|No|FORMAT\_STRING is set to `YES/NO`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; because there is no difference between English NO and Spanish NO the user sees no difference in the FORMATTED\_VALUE.|  
|I|SI|FORMAT\_STRING is set to `YES/NO`, VALUE is set to 59 and LANGUAGE is set explicitly to `1034`; as defined for YES\/NO formatting, any value different from zero \(0\) is a YES and because language is set to Spanish then the FORMATTED\_VALUE is SI.|  
|J|Desactivado|FORMAT\_STRING is set to `ON/OFF`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; as defined for ON\/OFF formatting, any value equal to zero \(0\) is an OFF and because language is set to Spanish then the FORMATTED\_VALUE is Desactivado.|  
|K|Activado|FORMAT\_STRING is set to `ON/OFF`, VALUE is set to \-312 and LANGUAGE is set explicitly to `1034`; as defined for ON\/OFF formatting, any value different from zero \(0\) is an ON and because language is set to Spanish then the FORMATTED\_VALUE is Activado.|  
  
 `with`  
  
 `member measures.A as 'CDate("1959-03-12 06:30")'`  
  
 `member measures.B as measures.A, FORMAT_STRING="Long Date"`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="General Date"`  
  
 `member measures.D as measures.A, LANGUAGE=1034, FORMAT_STRING="Long Date"`  
  
 `member measures.E as measures.A, LANGUAGE=1041 , FORMAT_STRING="General Date"`  
  
 `member measures.F as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Date"`  
  
 `member measures.G as measures.A, FORMAT_STRING="Long Time"`  
  
 `member measures.H as measures.A, FORMAT_STRING="Short Time"`  
  
 `member measures.I as measures.A, LANGUAGE=1034 , FORMAT_STRING="Long Time"`  
  
 `member measures.J as measures.A, LANGUAGE=1034 , FORMAT_STRING="Short Time"`  
  
 `member measures.K as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Time"`  
  
 `member measures.L as measures.A, LANGUAGE=1041 , FORMAT_STRING="Short Time"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F`  
  
 `, measures.G, measures.H, measures.I, measures.J, measures.K, measures.L} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] over a server and client with locale 1033 are as follows:  
  
|Member|FORMATTED\_VALUE|Explanation|  
|------------|----------------------|-----------------|  
|A|3\/12\/1959 6:30:00 AM|FORMAT\_STRING is set implicitly to `General Date` by the CDate\(\) expression and LANGUAGE is `1033` \(English\), inherited from system locale value|  
|B|Thursday, March 12, 1959|FORMAT\_STRING is set explicitly to `Long Date` and LANGUAGE is `1033` \(English\), inherited from system locale value|  
|C|12\/03\/1959 6:30:00|FORMAT\_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1034` \(Spanish\).<br /><br /> Note that month and day are switched when compared to U.S. formatting style|  
|D|jueves, 12 de marzo de 1959|FORMAT\_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1034` \(Spanish\).<br /><br /> Note that month and day of the week are worded in Spanish|  
|E|1959\/03\/12 6:30:00|FORMAT\_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1041` \(Japanese\).<br /><br /> Note that the date is now formatted Year\/Month\/Day Hour:Minutes:Seconds|  
|F|1959年3月12日|FORMAT\_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1041` \(Japanese\).|  
|G|6:30:00 AM|FORMAT\_STRING is set explicitly to `Long Time` and LANGUAGE is `1033` \(English\), inherited from system locale value.|  
|H|06:30|FORMAT\_STRING is set explicitly to `Short Time` and LANGUAGE is `1033` \(English\), inherited from system locale value.|  
|I|6:30:00|FORMAT\_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1034` \(Spanish\).|  
|J|06:30|FORMAT\_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1034` \(Spanish\).|  
|K|6:30:00|FORMAT\_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1041` \(Japanese\).|  
|L|06:30|FORMAT\_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1041` \(Japanese\).|  
  
## See Also  
 [FORMAT_STRING Contents &#40;MDX&#41;](../Topic/FORMAT_STRING%20Contents%20\(MDX\).md)   
 [Using Cell Properties &#40;MDX&#41;](../Topic/Using%20Cell%20Properties%20\(MDX\).md)   
 [Creating and Using Property Values &#40;MDX&#41;](../Topic/Creating%20and%20Using%20Property%20Values%20\(MDX\).md)   
 [MDX Query Fundamentals &#40;Analysis Services&#41;](../Topic/MDX%20Query%20Fundamentals%20\(Analysis%20Services\).md)  
  
  