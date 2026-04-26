# ListCustomersSortBy

The field to sort results by. Defaults to `'createdAt'`. Supported fields include any sortable customer property.

## Example Usage

```typescript
import { ListCustomersSortBy } from "@moflay/sdk/models/operations";

let value: ListCustomersSortBy = "createdAt";
```

## Values

```typescript
"createdAt" | "name" | "lastActiveAt" | "countryCode" | "phoneNumber" | "firstTransactionAt" | "isActive" | "isVerified"
```