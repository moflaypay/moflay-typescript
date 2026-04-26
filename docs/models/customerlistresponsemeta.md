# CustomerListResponseMeta

## Example Usage

```typescript
import { CustomerListResponseMeta } from "@moflay/sdk/models";

let value: CustomerListResponseMeta = {
  cursor: "eyJpZCI6IjEyMyJ9",
  hasPreviousPage: false,
  hasNextPage: true,
};
```

## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              | Example                                                                  |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `cursor`                                                                 | *string*                                                                 | :heavy_check_mark:                                                       | Cursor for pagination, representing the last item from the previous page | eyJpZCI6IjEyMyJ9                                                         |
| `hasPreviousPage`                                                        | *boolean*                                                                | :heavy_check_mark:                                                       | N/A                                                                      | false                                                                    |
| `hasNextPage`                                                            | *boolean*                                                                | :heavy_check_mark:                                                       | N/A                                                                      | true                                                                     |