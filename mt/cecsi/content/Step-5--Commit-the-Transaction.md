---
title: "Step 5: Commit the Transaction"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Step 5: Commit the Transaction
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The next step is to commit the transaction, as shown in the following illustration.</para>
    <mediaLink>
      <image xlink:href="bddb349a-256e-4d02-b325-8dc1ccd6a6db" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>The fifth step is to call <legacyBold>SQLEndTran</legacyBold> to commit or roll back the transaction. The application performs this step only if it set the transaction commit mode to manual-commit; if the transaction commit mode is auto-commit, which is the default, the transaction is automatically committed when the statement is executed. For more information, see <legacyLink xlink:href="b4ca861a-c164-4e87-8672-d5de15e3823c">Transactions</legacyLink>.</para>
      <para>To execute a statement in a new transaction, the application returns to step 3. To disconnect from the data source, the application proceeds to step 6.</para>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>