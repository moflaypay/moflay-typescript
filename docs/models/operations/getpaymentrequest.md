# GetPaymentRequest

## Example Usage

```typescript
import { GetPaymentRequest } from "@moflay/sdk/models/operations";

let value: GetPaymentRequest = {
  id: "pay_ABC123DEF456GHI",
};
```

## Fields

| Field                                                                                                               | Type                                                                                                                | Required                                                                                                            | Description                                                                                                         | Example                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                | *string*                                                                                                            | :heavy_check_mark:                                                                                                  | Payment lookup identifier. Use a paymentId prefixed with 'pay_' or the related transactionId prefixed with 'trxn_'. | pay_ABC123DEF456GHI                                                                                                 |