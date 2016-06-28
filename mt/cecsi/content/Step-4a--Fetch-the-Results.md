---
title: Step 4a: Fetch the Results
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
translation.priority.ht: 
  - en-gb
---
# Step 4a: Fetch the Results
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The next step is to fetch the results, as shown in the following illustration.</para>
    <mediaLink>
      <image xlink:href="74bf6ebe-8bba-4887-a0dc-d7cf88fab34e" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>If the statement executed in "Step 3: Build and Execute an SQL Statement" was a <legacyBold>SELECT</legacyBold> statement or a catalog function, the application first calls <legacyBold>SQLNumResultCols</legacyBold> to determine the number of columns in the result set. This step is not necessary if the application already knows the number of result set columns, such as when the SQL statement is hard-coded in a vertical or custom application.</para>
      <para>Next, the application retrieves the name, data type, precision, and scale of each result set column with <legacyBold>SQLDescribeCol</legacyBold>. Again, this is not necessary for applications such as vertical and custom applications that already know this information. The application passes this information to <legacyBold>SQLBindCol</legacyBold>, which binds an application variable to a column in the result set.</para>
      <para>The application now calls <legacyBold>SQLFetch</legacyBold> to retrieve the first row of data and place the data from that row in the variables bound with <legacyBold>SQLBindCol</legacyBold>. If there is any long data in the row, it then calls <legacyBold>SQLGetData</legacyBold> to retrieve that data. The application continues to call <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLGetData</legacyBold> to retrieve additional data. After it has finished fetching data, it calls <legacyBold>SQLCloseCursor</legacyBold> to close the cursor.</para>
      <para>For a complete description of retrieving results, see <legacyLink xlink:href="052870e3-3f3f-4f07-91da-b649348225f4">Retrieving Results (Basic)</legacyLink> and <legacyLink xlink:href="bc00c379-71a7-407a-975c-898243f39bb6">Retrieving Results (Advanced)</legacyLink>.</para>
      <para>The application now returns to "Step 3: Build and Execute an SQL Statement" to execute another statement in the same transaction; or proceeds to "Step 5: Commit the Transaction" to commit or roll back the transaction.</para>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>