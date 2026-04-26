# TransactionListResponse

List of all transactions

## Example Usage

```typescript
import { TransactionListResponse } from "@moflay/sdk/models";

let value: TransactionListResponse = {
  data: [
    {
      id: "trxn_ABC123DEF456GHI",
      customerId: "cus_MNO345PQR678STU",
      object: "transaction",
      environment: "sandbox",
      currency: "KES",
      amount: 1000,
      description: "Payment for Order #12345 - Premium Subscription",
      phoneNumber: "254712345678",
      status: "completed",
      type: "payment",
      receiptNumber: "QMF7MBB5ED",
      processedAt: "2024-12-19T10:30:00.000Z",
      paidAt: "2024-12-19T10:32:00.000Z",
      failedAt: null,
      unknownAt: null,
      failureReason: null,
      metadata: {},
      createdAt: "2024-12-19T10:25:00.000Z",
      source: "api",
    },
  ],
  meta: {
    cursor: "eyJpZCI6InRyeG5fQUJDMTIzREVGNDU2R0hJIn0=",
    hasPreviousPage: false,
    hasNextPage: true,
  },
};
```

## Fields

| Field                                                                          | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `data`                                                                         | [models.Transaction](../models/transaction.md)[]                               | :heavy_check_mark:                                                             | N/A                                                                            |
| `meta`                                                                         | [models.TransactionListResponseMeta](../models/transactionlistresponsemeta.md) | :heavy_check_mark:                                                             | N/A                                                                            |