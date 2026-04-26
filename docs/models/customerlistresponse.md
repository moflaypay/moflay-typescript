# CustomerListResponse

List of all customers

## Example Usage

```typescript
import { CustomerListResponse } from "@moflay/sdk/models";

let value: CustomerListResponse = {
  data: [
    {
      id: "cus_GqfKXLmg61LURZhB",
      object: "customer",
      environment: "sandbox",
      name: "John Doe",
      phoneNumber: "254712345678",
      description: "VIP customer with recurring payments",
      countryCode: "KE",
      isActive: true,
      isVerified: true,
      lastActiveAt: "2024-12-19T16:45:00.000Z",
      firstTransactionAt: "2024-12-15T09:15:00.000Z",
      source: "api",
      metadata: {},
      createdAt: "2024-12-10T08:30:00.000Z",
      updatedAt: "2024-12-19T14:22:00.000Z",
    },
  ],
  meta: {
    cursor: "eyJpZCI6ImN1c19HcWZLWExtZzYxTFVSWmhCIn0=",
    hasPreviousPage: false,
    hasNextPage: true,
  },
};
```

## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `data`                                                                   | [models.Customer](../models/customer.md)[]                               | :heavy_check_mark:                                                       | N/A                                                                      |
| `meta`                                                                   | [models.CustomerListResponseMeta](../models/customerlistresponsemeta.md) | :heavy_check_mark:                                                       | N/A                                                                      |