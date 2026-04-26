# ExpressRequest

## Example Usage

```typescript
import { ExpressRequest } from "@moflay/sdk/models/operations";

let value: ExpressRequest = {
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
    amount: 276581,
    description: "foolishly ah stupendous shell and as tomb unbearably oh",
    accountReference: "ORDER123",
    metadata: {
      "user_preference": "dark_mode",
      "last_login": 1640995200,
      "is_premium": true,
      "account_balance": 1250.75,
      "notifications_enabled": false,
    },
  },
};
```

## Fields

| Field                                                                                                                       | Type                                                                                                                        | Required                                                                                                                    | Description                                                                                                                 | Example                                                                                                                     |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                                            | *string*                                                                                                                    | :heavy_minus_sign:                                                                                                          | Optional idempotency key used to safely retry the same Express payment request without creating duplicate payment attempts. | express_order_12345                                                                                                         |
| `requestBody`                                                                                                               | [operations.ExpressRequestBody](../../models/operations/expressrequestbody.md)                                              | :heavy_check_mark:                                                                                                          | N/A                                                                                                                         |                                                                                                                             |