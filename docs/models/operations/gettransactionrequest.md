# GetTransactionRequest

## Example Usage

```typescript
import { GetTransactionRequest } from "@moflay/sdk/models/operations";

let value: GetTransactionRequest = {
  id: "trxn_ABC123DEF456GHI",
};
```

## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `id`                                                         | *string*                                                     | :heavy_check_mark:                                           | Unique identifier for the transaction, prefixed with 'trxn_' | trxn_ABC123DEF456GHI                                         |