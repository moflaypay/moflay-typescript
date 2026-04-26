# Express
(*express*)

## Overview

Create M-Pesa Express payments. Use the returned paymentId with the Payments API to read status.

### Available Operations

* [pay](#pay) - Initiate express payment

## pay

Initiate an M-Pesa Express (STK Push) payment.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="express" method="post" path="/v1/express" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.express.pay({
    idempotencyKey: "express_order_12345",
    requestBody: {
      phoneNumber: "254712345678",
      customerMetadata: {
        "user_preference": "dark_mode",
        "last_login": 1640995200,
        "is_premium": true,
        "account_balance": 1250.75,
        "notifications_enabled": false,
      },
      amount: 526895,
      description: "busily judgementally silently upset usher daddy in edible",
      accountReference: "ORDER123",
      metadata: {
        "user_preference": "dark_mode",
        "last_login": 1640995200,
        "is_premium": true,
        "account_balance": 1250.75,
        "notifications_enabled": false,
      },
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { MoflayCore } from "@moflay/sdk/core.js";
import { expressPay } from "@moflay/sdk/funcs/expressPay.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await expressPay(moflay, {
    idempotencyKey: "express_order_12345",
    requestBody: {
      phoneNumber: "254712345678",
      customerMetadata: {
        "user_preference": "dark_mode",
        "last_login": 1640995200,
        "is_premium": true,
        "account_balance": 1250.75,
        "notifications_enabled": false,
      },
      amount: 526895,
      description: "busily judgementally silently upset usher daddy in edible",
      accountReference: "ORDER123",
      metadata: {
        "user_preference": "dark_mode",
        "last_login": 1640995200,
        "is_premium": true,
        "account_balance": 1250.75,
        "notifications_enabled": false,
      },
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("expressPay failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ExpressRequest](../../models/operations/expressrequest.md)                                                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.DarajaExpressResponse](../../models/darajaexpressresponse.md)\>**

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