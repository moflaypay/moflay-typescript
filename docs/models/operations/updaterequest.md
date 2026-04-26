# UpdateRequest

## Example Usage

```typescript
import { UpdateRequest } from "@moflay/sdk/models/operations";

let value: UpdateRequest = {
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
};
```

## Fields

| Field                                                     | Type                                                      | Required                                                  | Description                                               | Example                                                   |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `id`                                                      | *string*                                                  | :heavy_check_mark:                                        | Unique identifier for the customer, prefixed with 'cus_'. | cus_GqfKXLmg61LURZhB                                      |
| `customerRequest`                                         | [models.CustomerRequest](../../models/customerrequest.md) | :heavy_check_mark:                                        | N/A                                                       |                                                           |