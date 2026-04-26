# RateLimitExceededErrorError

## Example Usage

```typescript
import { RateLimitExceededErrorError } from "@moflay/sdk/models";

let value: RateLimitExceededErrorError = {
  status: 429,
  code: "rate_limit_exceeded",
  message: "You have exceeded your request limit. Please try again later.",
};
```

## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   | Example                                                       |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `status`                                                      | *number*                                                      | :heavy_check_mark:                                            | HTTP status code of the error                                 | 429                                                           |
| `code`                                                        | *string*                                                      | :heavy_check_mark:                                            | Machine-readable error name                                   | rate_limit_exceeded                                           |
| `message`                                                     | *string*                                                      | :heavy_check_mark:                                            | Human-readable error message                                  | You have exceeded your request limit. Please try again later. |