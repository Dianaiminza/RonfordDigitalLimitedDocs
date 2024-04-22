---
title: Account Validation
description: ''
position: 2
category: Service Definition
---

Validate payment is being made against the correct reference. The response can also include additional information like the date when payment is due, the amount to be paid and more.

## Endpoint

```bash
curl -X POST {base-url}/api/v1/payments/validate-ref
```

## Request

Sample Request

```json

{
  "accountIdentifier": "ACC-2532453",
  "extraData": [
      {
          "key": "CustomerType",
          "value": "PREPAID",
          "type": "string"
      }
  ]
}


```

## Response

Sample Response

```json

{
    "statusCode": 200,
    "message": "Success",
    "succeeded": true,
    "data": {
        "accountIdentifier": "ACC-2532453",
        "accountName": "John Doe",
        "billCurrencyCode": "UGX",
        "balance": 75000.00,
        "minPaymentAmount": 5000.00,
        "maxPaymentAmount": 5000000.00,
        "dueDate": "2023-08-01",
        "extraData": {
            "customerType": "PREPAID",
            "merchantName": "BRITAM/UAT/UDB/JUBILEE/ROKE etc",
            "billNumber": "123456"
        }
    }
}


```
