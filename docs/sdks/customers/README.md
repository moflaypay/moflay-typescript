# Customers

## Overview

Create and manage customers in the organization

### Available Operations

* [list](#list) - List all customers
* [create](#create) - Create a customer
* [getOne](#getone) - Get a customer
* [delete](#delete) - Delete a customer
* [update](#update) - Update a customer

## list

Get a list of all customers in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="listCustomers" method="get" path="/v1/customers" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.customers.list({
    q: "John Doe",
    cursor: "eyJpZCI6IjEyMyJ9",
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
import { customersList } from "@moflay/sdk/funcs/customersList.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await customersList(moflay, {
    q: "John Doe",
    cursor: "eyJpZCI6IjEyMyJ9",
    start: new Date("2024-12-01T00:00:00.000Z"),
    end: new Date("2024-12-31T23:59:59.999Z"),
  });
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("customersList failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListCustomersRequest](../../models/operations/listcustomersrequest.md)                                                                                             | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.ListCustomersResponse](../../models/operations/listcustomersresponse.md)\>**

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

## create

Create a customer in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="create" method="post" path="/v1/customers" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.customers.create({
    phoneNumber: "254712345678",
    metadata: {
      "user_preference": "dark_mode",
      "last_login": 1640995200,
      "is_premium": true,
      "account_balance": 1250.75,
      "notifications_enabled": false,
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
import { customersCreate } from "@moflay/sdk/funcs/customersCreate.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await customersCreate(moflay, {
    phoneNumber: "254712345678",
    metadata: {
      "user_preference": "dark_mode",
      "last_login": 1640995200,
      "is_premium": true,
      "account_balance": 1250.75,
      "notifications_enabled": false,
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customersCreate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [models.CustomerRequest](../../models/customerrequest.md)                                                                                                                      | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Customer](../../models/customer.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.MissingApiKeyError     | 401                           | application/json              |
| errors.InvalidApiKeyError     | 403                           | application/json              |
| errors.MethodNotAllowedError  | 405                           | application/json              |
| errors.DuplicateError         | 409                           | application/json              |
| errors.ValidationError        | 422                           | application/json              |
| errors.InvalidAccessError     | 422                           | application/json              |
| errors.RateLimitExceededError | 429                           | application/json              |
| errors.InternalServerError    | 500                           | application/json              |
| errors.MoflayDefaultError     | 4XX, 5XX                      | \*/\*                         |

## getOne

Get a customer by their ID in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getCustomer" method="get" path="/v1/customers/{id}" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.customers.getOne({
    id: "cus_GqfKXLmg61LURZhB",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { MoflayCore } from "@moflay/sdk/core.js";
import { customersGetOne } from "@moflay/sdk/funcs/customersGetOne.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await customersGetOne(moflay, {
    id: "cus_GqfKXLmg61LURZhB",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customersGetOne failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetCustomerRequest](../../models/operations/getcustomerrequest.md)                                                                                                 | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Customer](../../models/customer.md)\>**

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

## delete

Delete a customer by their ID in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="delete" method="delete" path="/v1/customers/{id}" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.customers.delete({
    id: "cus_GqfKXLmg61LURZhB",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { MoflayCore } from "@moflay/sdk/core.js";
import { customersDelete } from "@moflay/sdk/funcs/customersDelete.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await customersDelete(moflay, {
    id: "cus_GqfKXLmg61LURZhB",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("customersDelete failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.DeleteRequest](../../models/operations/deleterequest.md)                                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.CustomerDeleteResponse](../../models/customerdeleteresponse.md)\>**

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

## update

Update a customer in the organization

### Example Usage

<!-- UsageSnippet language="typescript" operationID="update" method="patch" path="/v1/customers/{id}" -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.customers.update({
    id: "cus_GqfKXLmg61LURZhB",
    customerRequest: {
      phoneNumber: "254712345678",
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
import { customersUpdate } from "@moflay/sdk/funcs/customersUpdate.js";

// Use `MoflayCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const moflay = new MoflayCore({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const res = await customersUpdate(moflay, {
    id: "cus_GqfKXLmg61LURZhB",
    customerRequest: {
      phoneNumber: "254712345678",
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
    console.log("customersUpdate failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UpdateRequest](../../models/operations/updaterequest.md)                                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Customer](../../models/customer.md)\>**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| errors.MissingApiKeyError     | 401                           | application/json              |
| errors.InvalidApiKeyError     | 403                           | application/json              |
| errors.NotFoundError          | 404                           | application/json              |
| errors.MethodNotAllowedError  | 405                           | application/json              |
| errors.DuplicateError         | 409                           | application/json              |
| errors.ValidationError        | 422                           | application/json              |
| errors.InvalidAccessError     | 422                           | application/json              |
| errors.RateLimitExceededError | 429                           | application/json              |
| errors.InternalServerError    | 500                           | application/json              |
| errors.MoflayDefaultError     | 4XX, 5XX                      | \*/\*                         |