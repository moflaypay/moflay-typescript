# Payments

## Overview

Track payment lifecycle and status for paymentIds returned by Express payment creation.

### Available Operations

* [getOne](#getone) - Get payment

## getOne

Get the current status of an Express payment attempt using either the paymentId or related transactionId returned by POST /v1/express.

**Permissions**: `transactions.read`

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getPayment" method="get" path="/v1/payments/{id}" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.payments.getOne({
    id: "pay_ABC123DEF456GHI",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { MoflayCore } from "@moflay/sdk/core.js";
import { paymentsGetOne } from "@moflay/sdk/funcs/paymentsGetOne.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await paymentsGetOne(moflay, {
    id: "pay_ABC123DEF456GHI",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("paymentsGetOne failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetPaymentRequest](../../models/operations/getpaymentrequest.md)                                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.PaymentStatus](../../models/paymentstatus.md)\>**

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