---
title: Reversal
description: ''
position: 6
category: Merchant Initiated Requests
---

This service will allow the partner to initiate transaction reversals. Reversal happens in two legs.

1. Book a reversal ticket
2. Send the reversal request

## Book a reversal ticket

Partner sends the reversal details, the bank will validate the request immediately and confirm if the reversal is possible or not. If possible, the bank will issue a ticket. With the ticket, the partner can reverse the transaction and send the reversal request for the same to be effected at the bank.

### Endpoint

```bash
curl -X POST {base-url}/api/v1/payments/book-reverse-ticket


```

### Request

Sample Request

```json

{
    "data": {
        "requestId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "transactionId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "bankRef": "FT-32464564563"
    },
    "hash": "NotificationHash"
}


```

```bash
Hash string: {requestId}{transactionId}{bankRef}{clientSecret}

```

### Response

Sample Response

```json

{
    "statusCode": 200,
    "message": "Success",
    "succeeded": true,
    "data": {
        "ticket": "18ceeca5-437d-41ac-b6eb-0d133156939b"
    }
}


```

## Send the reversal request

After the partner gets a valid reversal ticket and reverses the transaction, the next step is to post the reversal request to also be completed at the bank.

### Endpoint

```bash
curl -X POST {base-url}/api/v1/payments/reverse

```

### Request

Sample Request

```json

{
    "data": {
        "requestId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "transactionId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "bankRef": "FT-32464564563"
        "ticket": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    },
    "hash": "NotificationHash"
}



```

```bash
Hash string: {requestId}{transactionId}{bankRef}{ticket}{clientSecret}


```

### Response

Sample Response

```json

{
    "statusCode": 200,
    "message": "Success",
    "succeeded": true,
    "data": "Reversal request accepted"
}



```
