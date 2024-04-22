---
title: Payment Notification
description: ''
position: 3
category: Service Definition
---

The endpoint receives instant payment notifications. Processing should be idempotent - Each unique bank reference should only be processed once regardless of the number of requests posted on the endpoint.

## Endpoint

```bash
curl -X POST {base-url}/api/v1/payments/notification
```

## Request

Sample Request

```json

{
    "data": {
        "transactionId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "accountIdentifier": "ACC-2532453",
        "bankRef": "FT-32464564563",
        "valueDate": "2023-06-29T07:48:58.857Z",
        "creditAccount": "121212121212",
        "creditCurrency": "UGX",
        "creditAmount": 75000.00,
        "paymentMode": "AIRTEL/MTN/INTERNAL TRANSFER/CASH DEPOSIT/CARD ETC",
        "narration": "NCBA - MuzuriPayment Payment",
        "payerName": "John Doe",
        "payerEmail": "johndoe@email.com",
        "payerPhone": "256700000000",
        "callbackUrl": "https://callback.sample.ncba/api/v1/muzuripay-payment-callback",
        "extraData": [
            {
                "key": "CustomerType",
                "value": "PREPAID",
                "type": "string"
            }
        ]
    },
    "hash": "NotificationHash"
}

```

```bash
Hash string: {transactionId}{accountIdentifier}{bankRef}{clientSecret}
```

## Response

Sample Response

```json

{
    "statusCode": 200,
    "message": "Success",
    "succeeded": true,
    "data": {
        "transactionId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "merchantRef": "REF-903745GD",
        "finalStatus": "RDTU000/RDTS000/RDTF000",
        "extraData": [
            {
                "key": "CustomerType",
                "value": "PREPAID",
                "type": "string"
            },
            {
                "key": "ExternalId",
                "value": "2354635364",
                "type": "number"
            }
        ]
    }
}

```
