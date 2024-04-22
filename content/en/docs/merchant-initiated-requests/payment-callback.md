---
title: Payment Callback
description: ''
position: 5
category: Merchant Initiated Requests
---

Partner to send status of the transaction on the callback url to confirm if the transaction failed or succeeded if the final status when posting was indicated to be unknown. The callback url is sent on every payment notification.

## Endpoint

```bash
curl -X POST {base-url}/api/v1/payments/payment-callback

```

## Request

Sample Request

```json

{
    "data": {
        "requestId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "transactionId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "bankRef": "FT-32464564563",
        "finalStatus": "RDTS000",
        "message": "Payment processed successfully"
        "extraData": [
            {
                "key": "ExternalId",
                "value": "2354635364",
                "type": "number"
            }
        ]
    },
    "hash": "NotificationHash"
}


```

```bash
Hash string: {requestId}{transactionId}{bankRef}{clientSecret}
```

## Response

Sample Response

```json

{
    "statusCode": 200,
    "message": "Success",
    "succeeded": true,
    "data": "Callback request received"
}



```
