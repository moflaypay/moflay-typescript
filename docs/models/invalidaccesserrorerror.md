# InvalidAccessErrorError

## Example Usage

```typescript
import { InvalidAccessErrorError } from "@moflay/sdk/models";

let value: InvalidAccessErrorError = {
  status: 422,
};
```

## Fields

| Field                         | Type                          | Required                      | Description                   | Example                       |
| ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- |
| `status`                      | *number*                      | :heavy_check_mark:            | HTTP status code of the error | 422                           |