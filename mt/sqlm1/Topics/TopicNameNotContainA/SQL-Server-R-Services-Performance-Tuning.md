---
title: SQL Server R Services Performance Tuning
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf6f3b7d-f9f9-4e45-b0d1-07850b53e0c5
---
# SQL Server R Services Performance Tuning
[!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)] provides a platform for developing intelligent applications that uncover new insights. A data scientist can use the power of R language to train and create models using data stored inside [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)]. Once the model is ready for production, a data scientist can work with database administrators and SQL engineers to deploy their solution in production. The information in this section provides high level guidance on tuning performance both when creating and training models, and when deploying models to production.

The information in this document assumes that you are familiar with [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)] concepts and terminology. For general information on R Services, see [SQL Server R Services](../../Topics\TopicNameNotContainA/SQL-Server-R-Services.md).

> [!NOTE]
> While much of the information in this section is general guidance on configuring [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)], some information is specific to RevoScaleR analytic functions.

## In This Section

* [SQL Server Configuration](SQL%20Server%20Configuration%20\(R%20Services\).md): This document provides guidance for configuring the hardware that [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] is installed on. It is most useful to __Database Administrators__.

* [R and Data Optimization](R%20and%20Data%20Optimization%20\(R%20Services\).md): This document provides guidance on using R scripts with R Services. It is most useful to __Data Scientists__.

* [Performance Case Study](Performance%20Case%20Study%20\(R%20Services\).md): This document provides test data and R scripts that can be used to test the impact of guidance provided in the previous documents.

## References

The following are links to information used in the development of this document.

* [How to determine the appropriate page file size for 64-bit versions of Windows](https://support.microsoft.com/kb/2860880)

* [Data Compression](../../Topics\TopicNameNotContainA/Data-Compression.md)

* [Enable Compression on a Table or Index](../../Topics\TopicNameContainA/Enable-Compression-on-a-Table-or-Index.md)

* [Disable Compression on a Table or Index](../../Topics\TopicNameContainA/Disable-Compression-on-a-Table-or-Index.md)

* [DISKSPD storage load generator/performance test tool](https://github.com/microsoft/diskspd)

* [FSUtil utility reference](https://technet.microsoft.com/library/cc753059.aspx)

* [Reorganize and Rebuild Indexes](../../Topics\TopicNameNotContainA/Reorganize-and-Rebuild-Indexes.md)

* [R Services](../../Topics\TopicNameNotContainA/R-Services.md)

* [Performance Tuning Options for rxDForest and rxDTree](https://support.microsoft.com/kb/3104235)

* [Monitor and Tune for Performance](../../Topics\TopicNameNotContainA/Monitor-and-Tune-for-Performance.md)

* [RevoScaleR Users Guide](https://packages.revolutionanalytics.com/doc/7.0.0/win/RevoScaleR_Users_Guide.pdf)

* [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)