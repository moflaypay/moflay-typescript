# DuplicateErrorError

## Example Usage

```typescript
import { DuplicateErrorError } from "@moflay/sdk/models";

let value: DuplicateErrorError = {
  status: 409,
  code: "duplicate_error",
  message: "A record with this information already exists.",
};
```

## Fields

| Field                                          | Type                                           | Required                                       | Description                                    | Example                                        |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `status`                                       | *number*                                       | :heavy_check_mark:                             | HTTP status code of the error                  | 409                                            |
| `code`                                         | *string*                                       | :heavy_check_mark:                             | Machine-readable error name                    | duplicate_error                                |
| `message`                                      | *string*                                       | :heavy_check_mark:                             | Human-readable error message                   | A record with this information already exists. |