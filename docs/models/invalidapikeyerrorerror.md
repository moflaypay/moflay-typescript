# InvalidApiKeyErrorError

## Example Usage

```typescript
import { InvalidApiKeyErrorError } from "@moflay/sdk/models";

let value: InvalidApiKeyErrorError = {
  status: 403,
  code: "invalid_api_key",
  message: "API key is invalid.",
};
```

## Fields

| Field                         | Type                          | Required                      | Description                   | Example                       |
| ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- |
| `status`                      | *number*                      | :heavy_check_mark:            | HTTP status code of the error | 403                           |
| `code`                        | *string*                      | :heavy_check_mark:            | Machine-readable error name   | invalid_api_key               |
| `message`                     | *string*                      | :heavy_check_mark:            | Human-readable error message  | API key is invalid.           |