# MissingApiKeyErrorError

## Example Usage

```typescript
import { MissingApiKeyErrorError } from "@moflay/sdk/models";

let value: MissingApiKeyErrorError = {
  status: 401,
  code: "missing_api_key",
  message: "Missing API key in the authorization header.",
};
```

## Fields

| Field                                        | Type                                         | Required                                     | Description                                  | Example                                      |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `status`                                     | *number*                                     | :heavy_check_mark:                           | HTTP status code of the error                | 401                                          |
| `code`                                       | *string*                                     | :heavy_check_mark:                           | Machine-readable error name                  | missing_api_key                              |
| `message`                                    | *string*                                     | :heavy_check_mark:                           | Human-readable error message                 | Missing API key in the authorization header. |