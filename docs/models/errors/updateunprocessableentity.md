# UpdateUnprocessableEntity

The validation error(s) or invalid access error


## Supported Types

### `errors.ValidationError`

```typescript
const value: errors.ValidationError = {
  error: {
    status: 422,
    code: "validation_error",
    message: "We found an error with one or more fields in the request.",
    validation: [
      {
        field: "email",
        message: "Invalid email format",
      },
      {
        field: "age",
        message: "Expected number, received string",
      },
    ],
  },
};
```

### `errors.InvalidAccessError`

```typescript
const value: errors.InvalidAccessError = {
  error: {
    status: 422,
  },
  code: "invalid_access",
  message:
    "The API key does not have the necessary permissions to access this resource.",
};
```

