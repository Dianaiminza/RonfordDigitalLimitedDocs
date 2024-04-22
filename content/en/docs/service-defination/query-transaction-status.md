---
title: Query Transaction Status
description: ''
position: 4
category: Service Definition
---

This service allows the bank to query transaction status if a callback with final transaction status is not received on the callback url after some time.

## Endpoint

```bash
curl -X POST {base-url}/api/v1/payments/check-status
```

## Request

Sample Request

```json
{
    "data": {
        "bankRef": "FT-32464564563",
        "extraData": [
            {
                "key": "TransactionId",
                "value": "2354635364",
                "type": "string"
            }
        ]
    },
    "hash": "NotificationHash"
}

```

```bash
Hash string: {bankRef}{clientSecret}

```

## Response

Sample Response

```json
{
    "transactionId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "bankRef": "FT-32464564563",
    "finalStatus": "RDTS000",
    "message": "Payment processed successfully",
    "extraData": [
        {
            "key": "ExternalId",
            "value": "2354635364",
            "type": "number"
        }
    ]
}
```
