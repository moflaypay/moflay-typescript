# MethodNotAllowedErrorError

## Example Usage

```typescript
import { MethodNotAllowedErrorError } from "@moflay/sdk/models";

let value: MethodNotAllowedErrorError = {
  status: 405,
  code: "method_not_allowed",
  message: "Method is not allowed for the requested path.",
};
```

## Fields

| Field                                         | Type                                          | Required                                      | Description                                   | Example                                       |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| `status`                                      | *number*                                      | :heavy_check_mark:                            | HTTP status code of the error                 | 405                                           |
| `code`                                        | *string*                                      | :heavy_check_mark:                            | Machine-readable error name                   | method_not_allowed                            |
| `message`                                     | *string*                                      | :heavy_check_mark:                            | Human-readable error message                  | Method is not allowed for the requested path. |