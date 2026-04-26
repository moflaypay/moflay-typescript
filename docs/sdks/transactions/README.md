# Transactions

## Overview

Everything about transactions in the organization

### Available Operations

* [list](#list) - List transactions
* [getOne](#getone) - Get transaction

## list

List all transactions in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="listTransactions" method="get" path="/v1/transactions" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.transactions.list({
    q: "Premium Subscription",
    cursor: "eyJpZCI6IjEyMyJ9",
    customerId: "cus_MNO345PQR678STU",
    statuses: [
      "pending",
      "completed",
    ],
    amountRange: [
      10000,
      50000,
    ],
    amount: [
      "150.75",
      "299.99",
      "1000.00",
    ],
    start: new Date("2024-12-01T00:00:00.000Z"),
    end: new Date("2024-12-31T23:59:59.999Z"),
  });

  for await (const page of result) {
    console.log(page);
  }
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { MoflayCore } from "@moflay/sdk/core.js";
import { transactionsList } from "@moflay/sdk/funcs/transactionsList.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await transactionsList(moflay, {
    q: "Premium Subscription",
    cursor: "eyJpZCI6IjEyMyJ9",
    customerId: "cus_MNO345PQR678STU",
    statuses: [
      "pending",
      "completed",
    ],
    amountRange: [
      10000,
      50000,
    ],
    amount: [
      "150.75",
      "299.99",
      "1000.00",
    ],
    start: new Date("2024-12-01T00:00:00.000Z"),
    end: new Date("2024-12-31T23:59:59.999Z"),
  });
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("transactionsList failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListTransactionsRequest](../../models/operations/listtransactionsrequest.md)                                                                                       | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.ListTransactionsResponse](../../models/operations/listtransactionsresponse.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.MissingApiKeyError     | 401                           | application/json              |
| errors.InvalidApiKeyError     | 403                           | application/json              |
| errors.MethodNotAllowedError  | 405                           | application/json              |
| errors.ValidationError        | 422                           | application/json              |
| errors.InvalidAccessError     | 422                           | application/json              |
| errors.RateLimitExceededError | 429                           | application/json              |
| errors.InternalServerError    | 500                           | application/json              |
| errors.MoflayDefaultError     | 4XX, 5XX                      | \*/\*                         |

## getOne

Get a transaction in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getTransaction" method="get" path="/v1/transactions/{id}" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.transactions.getOne({
    id: "trxn_ABC123DEF456GHI",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { MoflayCore } from "@moflay/sdk/core.js";
import { transactionsGetOne } from "@moflay/sdk/funcs/transactionsGetOne.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await transactionsGetOne(moflay, {
    id: "trxn_ABC123DEF456GHI",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("transactionsGetOne failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetTransactionRequest](../../models/operations/gettransactionrequest.md)                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Transaction](../../models/transaction.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.MissingApiKeyError     | 401                           | application/json              |
| errors.InvalidApiKeyError     | 403                           | application/json              |
| errors.NotFoundError          | 404                           | application/json              |
| errors.MethodNotAllowedError  | 405                           | application/json              |
| errors.ValidationError        | 422                           | application/json              |
| errors.InvalidAccessError     | 422                           | application/json              |
| errors.RateLimitExceededError | 429                           | application/json              |
| errors.InternalServerError    | 500                           | application/json              |
| errors.MoflayDefaultError     | 4XX, 5XX                      | \*/\*                         |