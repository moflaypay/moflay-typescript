# @moflay/sdk

Developer-friendly & type-safe Typescript SDK specifically catered to leverage *@moflay/sdk* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=@moflay/sdk&utm_campaign=typescript"><img src="https://www.speakeasy.com/assets/badges/built-by-speakeasy.svg" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<!-- Start Summary [summary] -->
## Summary

Moflay API: The fastest way to add M-Pesa payments.

For more information about the API: [Moflay Documentation](https://moflay.com/docs)
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [@moflay/sdk](#moflaysdk)
  * [SDK Installation](#sdk-installation)
  * [Requirements](#requirements)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Standalone functions](#standalone-functions)
  * [Pagination](#pagination)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

The SDK can be installed with either [npm](https://www.npmjs.com/), [pnpm](https://pnpm.io/), [bun](https://bun.sh/) or [yarn](https://classic.yarnpkg.com/en/) package managers.

### NPM

```bash
npm add @moflay/sdk
```

### PNPM

```bash
pnpm add @moflay/sdk
```

### Bun

```bash
bun add @moflay/sdk
```

### Yarn

```bash
yarn add @moflay/sdk
```

> [!NOTE]
> This package is published with CommonJS and ES Modules (ESM) support.
<!-- End SDK Installation [installation] -->

<!-- Start Requirements [requirements] -->
## Requirements

For supported JavaScript runtimes, please consult [RUNTIMES.md](RUNTIMES.md).
<!-- End Requirements [requirements] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name    | Type | Scheme      | Environment Variable |
| ------- | ---- | ----------- | -------------------- |
| `token` | http | HTTP Bearer | `MOFLAY_TOKEN`       |

To authenticate with the API the `token` parameter must be set when initializing the SDK client instance. For example:
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Customers](docs/sdks/customers/README.md)

* [list](docs/sdks/customers/README.md#list) - List all customers
* [create](docs/sdks/customers/README.md#create) - Create a customer
* [getOne](docs/sdks/customers/README.md#getone) - Get a customer
* [delete](docs/sdks/customers/README.md#delete) - Delete a customer
* [update](docs/sdks/customers/README.md#update) - Update a customer

### [Express](docs/sdks/express/README.md)

* [pay](docs/sdks/express/README.md#pay) - Initiate express payment

### [Payments](docs/sdks/payments/README.md)

* [getOne](docs/sdks/payments/README.md#getone) - Get payment

### [Transactions](docs/sdks/transactions/README.md)

* [list](docs/sdks/transactions/README.md#list) - List transactions
* [getOne](docs/sdks/transactions/README.md#getone) - Get transaction

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Standalone functions [standalone-funcs] -->
## Standalone functions

All the methods listed above are available as standalone functions. These
functions are ideal for use in applications running in the browser, serverless
runtimes or other environments where application bundle size is a primary
concern. When using a bundler to build your application, all unused
functionality will be either excluded from the final bundle or tree-shaken away.

To read more about standalone functions, check [FUNCTIONS.md](./FUNCTIONS.md).

<details>

<summary>Available standalone functions</summary>

- [`customersCreate`](docs/sdks/customers/README.md#create) - Create a customer
- [`customersDelete`](docs/sdks/customers/README.md#delete) - Delete a customer
- [`customersGetOne`](docs/sdks/customers/README.md#getone) - Get a customer
- [`customersList`](docs/sdks/customers/README.md#list) - List all customers
- [`customersUpdate`](docs/sdks/customers/README.md#update) - Update a customer
- [`expressPay`](docs/sdks/express/README.md#pay) - Initiate express payment
- [`paymentsGetOne`](docs/sdks/payments/README.md#getone) - Get payment
- [`transactionsGetOne`](docs/sdks/transactions/README.md#getone) - Get transaction
- [`transactionsList`](docs/sdks/transactions/README.md#list) - List transactions

</details>
<!-- End Standalone functions [standalone-funcs] -->

<!-- Start Pagination [pagination] -->
## Pagination

Some of the endpoints in this SDK support pagination. To use pagination, you
make your SDK calls as usual, but the returned response object will also be an
async iterable that can be consumed using the [`for await...of`][for-await-of]
syntax.

[for-await-of]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of

Here's an example of one such pagination call:

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
<!-- End Pagination [pagination] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries.  If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API.  However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a retryConfig object to the call:
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
  }, {
    retries: {
      strategy: "backoff",
      backoff: {
        initialInterval: 1,
        maxInterval: 50,
        exponent: 1.1,
        maxElapsedTime: 100,
      },
      retryConnectionErrors: false,
    },
  });

  for await (const page of result) {
    console.log(page);
  }
}

run();

```

If you'd like to override the default retry strategy for all operations that support retries, you can provide a retryConfig at SDK initialization:
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  retryConfig: {
    strategy: "backoff",
    backoff: {
      initialInterval: 1,
      maxInterval: 50,
      exponent: 1.1,
      maxElapsedTime: 100,
    },
    retryConnectionErrors: false,
  },
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
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`MoflayError`](./src/models/errors/moflayerror.ts) is the base class for all HTTP error responses. It has the following properties:

| Property            | Type       | Description                                                                             |
| ------------------- | ---------- | --------------------------------------------------------------------------------------- |
| `error.message`     | `string`   | Error message                                                                           |
| `error.statusCode`  | `number`   | HTTP response status code eg `404`                                                      |
| `error.headers`     | `Headers`  | HTTP response headers                                                                   |
| `error.body`        | `string`   | HTTP body. Can be empty string if no body is returned.                                  |
| `error.rawResponse` | `Response` | Raw HTTP response                                                                       |
| `error.data$`       |            | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```typescript
import { Moflay } from "@moflay/sdk";
import * as errors from "@moflay/sdk/models/errors";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  try {
    const result = await moflay.customers.list({
      q: "John Doe",
      cursor: "eyJpZCI6IjEyMyJ9",
      start: new Date("2024-12-01T00:00:00.000Z"),
      end: new Date("2024-12-31T23:59:59.999Z"),
    });

    for await (const page of result) {
      console.log(page);
    }
  } catch (error) {
    // The base class for HTTP error responses
    if (error instanceof errors.MoflayError) {
      console.log(error.message);
      console.log(error.statusCode);
      console.log(error.body);
      console.log(error.headers);

      // Depending on the method different errors may be thrown
      if (error instanceof errors.MissingApiKeyError) {
        console.log(error.data$.error); // models.MissingApiKeyErrorError
      }
    }
  }
}

run();

```

### Error Classes
**Primary errors:**
* [`MoflayError`](./src/models/errors/moflayerror.ts): The base class for HTTP error responses.
  * [`MissingApiKeyError`](./src/models/errors/missingapikeyerror.ts): Missing API Key Error. Status code `401`.
  * [`InvalidApiKeyError`](./src/models/errors/invalidapikeyerror.ts): Invalid API Key Error. Status code `403`.
  * [`MethodNotAllowedError`](./src/models/errors/methodnotallowederror.ts): Method Not Allowed Error. Status code `405`.
  * [`ValidationError`](./src/models/errors/validationerror.ts): The validation error(s) or invalid access error. Status code `422`.
  * [`InvalidAccessError`](./src/models/errors/invalidaccesserror.ts): The validation error(s) or invalid access error. Status code `422`.
  * [`RateLimitExceededError`](./src/models/errors/ratelimitexceedederror.ts): Rate Limit Exceeded Error. Status code `429`.
  * [`InternalServerError`](./src/models/errors/internalservererror.ts): Internal Server Error. Status code `500`.

<details><summary>Less common errors (8)</summary>

<br />

**Network errors:**
* [`ConnectionError`](./src/models/errors/httpclienterrors.ts): HTTP client was unable to make a request to a server.
* [`RequestTimeoutError`](./src/models/errors/httpclienterrors.ts): HTTP request timed out due to an AbortSignal signal.
* [`RequestAbortedError`](./src/models/errors/httpclienterrors.ts): HTTP request was aborted by the client.
* [`InvalidRequestError`](./src/models/errors/httpclienterrors.ts): Any input used to create a request is invalid.
* [`UnexpectedClientError`](./src/models/errors/httpclienterrors.ts): Unrecognised or unexpected error.


**Inherit from [`MoflayError`](./src/models/errors/moflayerror.ts)**:
* [`NotFoundError`](./src/models/errors/notfounderror.ts): Customer Not Found. Status code `404`. Applicable to 5 of 9 methods.*
* [`DuplicateError`](./src/models/errors/duplicateerror.ts): Duplicate Error. Status code `409`. Applicable to 2 of 9 methods.*
* [`ResponseValidationError`](./src/models/errors/responsevalidationerror.ts): Type mismatch between the data returned from the server and the structure expected by the SDK. See `error.rawValue` for the raw value and `error.pretty()` for a nicely formatted multi-line string.

</details>

\* Check [the method documentation](#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally by passing a URL to the `serverURL: string` optional parameter when initializing the SDK client instance. For example:
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  serverURL: "https://api.moflay.com",
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
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The TypeScript SDK makes API calls using an `HTTPClient` that wraps the native
[Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API). This
client is a thin wrapper around `fetch` and provides the ability to attach hooks
around the request lifecycle that can be used to modify the request or handle
errors and response.

The `HTTPClient` constructor takes an optional `fetcher` argument that can be
used to integrate a third-party HTTP client or when writing tests to mock out
the HTTP client and feed in fixtures.

The following example shows how to:
- route requests through a proxy server using [undici](https://www.npmjs.com/package/undici)'s ProxyAgent
- use the `"beforeRequest"` hook to add a custom header and a timeout to requests
- use the `"requestError"` hook to log errors

```typescript
import { Moflay } from "@moflay/sdk";
import { ProxyAgent } from "undici";
import { HTTPClient } from "@moflay/sdk/lib/http";

const dispatcher = new ProxyAgent("http://proxy.example.com:8080");

const httpClient = new HTTPClient({
  // 'fetcher' takes a function that has the same signature as native 'fetch'.
  fetcher: (input, init) =>
    // 'dispatcher' is specific to undici and not part of the standard Fetch API.
    fetch(input, { ...init, dispatcher } as RequestInit),
});

httpClient.addHook("beforeRequest", (request) => {
  const nextRequest = new Request(request, {
    signal: request.signal || AbortSignal.timeout(5000)
  });

  nextRequest.headers.set("x-custom-header", "custom value");

  return nextRequest;
});

httpClient.addHook("requestError", (error, request) => {
  console.group("Request Error");
  console.log("Reason:", `${error}`);
  console.log("Endpoint:", `${request.method} ${request.url}`);
  console.groupEnd();
});

const sdk = new Moflay({ httpClient: httpClient });
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass a logger that matches `console`'s interface as an SDK option.

> [!WARNING]
> Beware that debug logging will reveal secrets, like API tokens in headers, in log messages printed to a console or files. It's recommended to use this feature only during local development and not in production.

```typescript
import { Moflay } from "@moflay/sdk";

const sdk = new Moflay({ debugLogger: console });
```

You can also enable a default debug logger by setting an environment variable `MOFLAY_DEBUG` to true.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=@moflay/sdk&utm_campaign=typescript)
