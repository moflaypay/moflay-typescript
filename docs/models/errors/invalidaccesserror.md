# InvalidAccessError

## Example Usage

```typescript
import { InvalidAccessError } from "@moflay/sdk/models/errors";

// No examples available for this model
```

## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  | Example                                                                      |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `error`                                                                      | [models.InvalidAccessErrorError](../../models/invalidaccesserrorerror.md)    | :heavy_check_mark:                                                           | N/A                                                                          |                                                                              |
| `code`                                                                       | *string*                                                                     | :heavy_check_mark:                                                           | Machine-readable error name                                                  | invalid_access                                                               |
| `message`                                                                    | *string*                                                                     | :heavy_check_mark:                                                           | Human-readable error message                                                 | The API key does not have the necessary permissions to access this resource. |