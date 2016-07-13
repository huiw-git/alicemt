---
title: SQLServerParameterMetaData Members
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9ebb203-2013-4feb-94f5-494b7f098f9a
manager:jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# SQLServerParameterMetaData Members
  The following tables list the members that are exposed by the [SQLServerParameterMetaData](../content/SQLServerParameterMetaData-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
 None.  
  
## Inherited Fields  
  
|Name|Description|  
|----------|-----------------|  
|java.sql.ParameterMetaData|parameterModeIn, parameterModeInOut, parameterModeOut, parameterModeUnknown, parameterNoNulls, parameterNullable, parameterNullableUnknown|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[getParameterClassName](../content/getParameterClassName-Method--SQLServerParameterMetaData-.md)|Retrieves the fully\-qualified name of the Java class whose instances should be passed to the [setObject](../content/setObject-Method--SQLServerPreparedStatement-.md) method of the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class.|  
|[getParameterCount](../content/getParameterCount-Method--SQLServerParameterMetaData-.md)|Retrieves the number of parameters in the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) object for which this [SQLServerParameterMetaData](../content/SQLServerParameterMetaData-Class.md) object contains information.|  
|[getParameterMode](../content/getParameterMode-Method--SQLServerParameterMetaData-.md)|Retrieves the mode of the designated parameter.|  
|[getParameterType](../content/getParameterType-Method--SQLServerParameterMetaData-.md)|Retrieves the SQL type of the designated parameter.|  
|[getParameterTypeName](../content/getParameterTypeName-Method--SQLServerParameterMetaData-.md)|Retrieves the database\-specific type name of the designated parameter.|  
|[getPrecision](../content/getPrecision-Method--SQLServerParameterMetaData-.md)|Retrieves the number of decimal digits for the designated parameter.|  
|[getScale](../content/getScale-Method--SQLServerParameterMetaData-.md)|Retrieves the number of digits to the right of the decimal point for the designated parameter.|  
|[isNullable](../content/isNullable-Method--SQLServerParameterMetaData-.md)|Retrieves whether null values are allowed in the designated parameter.|  
|[isSigned](../content/isSigned-Method--SQLServerParameterMetaData-.md)|Retrieves whether values for the designated parameter can be signed numbers.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerParameterMetaData Class](../content/SQLServerParameterMetaData-Class.md)  
  
  