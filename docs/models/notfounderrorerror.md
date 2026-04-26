# NotFoundErrorError

## Example Usage

```typescript
import { NotFoundErrorError } from "@moflay/sdk/models";

let value: NotFoundErrorError = {
  status: 404,
  code: "not_found",
  message: "The requested endpoint does not exist.",
};
```

## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `status`                               | *number*                               | :heavy_check_mark:                     | HTTP status code of the error          | 404                                    |
| `code`                                 | *string*                               | :heavy_check_mark:                     | Machine-readable error name            | not_found                              |
| `message`                              | *string*                               | :heavy_check_mark:                     | Human-readable error message           | The requested endpoint does not exist. |