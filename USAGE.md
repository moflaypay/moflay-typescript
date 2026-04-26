<!-- Start SDK Example Usage [usage] -->
```typescript
import { Moflay } from "@moflay/sdk";

const moflay = new Moflay({
  token: "MOFLAY_API_KEY",
});

async function run() {
  const result = await moflay.express.pay({
    idempotencyKey: "express_order_12345",
    requestBody: {
      phoneNumber: "254712345678",
      customerMetadata: {
        "user_preference": "dark_mode",
        "last_login": 1640995200,
        "is_premium": true,
        "account_balance": 1250.75,
        "notifications_enabled": false,
      },
      amount: 526895,
      description: "busily judgementally silently upset usher daddy in edible",
      accountReference: "ORDER123",
      metadata: {
        "user_preference": "dark_mode",
        "last_login": 1640995200,
        "is_premium": true,
        "account_balance": 1250.75,
        "notifications_enabled": false,
      },
    },
  });

  console.log(result);
}

run();

```
<!-- End SDK Example Usage [usage] -->