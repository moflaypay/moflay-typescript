# InternalServerErrorError

## Example Usage

```typescript
import { InternalServerErrorError } from "@moflay/sdk/models";

let value: InternalServerErrorError = {
  status: 500,
  code: "internal_server_error",
  message: "An unexpected error occurred.",
};
```

## Fields

| Field                         | Type                          | Required                      | Description                   | Example                       |
| ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- |
| `status`                      | *number*                      | :heavy_check_mark:            | HTTP status code of the error | 500                           |
| `code`                        | *string*                      | :heavy_check_mark:            | Machine-readable error name   | internal_server_error         |
| `message`                     | *string*                      | :heavy_check_mark:            | Human-readable error message  | An unexpected error occurred. |