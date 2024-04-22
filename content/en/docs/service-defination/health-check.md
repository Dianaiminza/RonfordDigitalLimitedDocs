---
title: Health Check
description: ''
position: 1
category: Service Definition
---
Probe the merchant service to confirm if it is live and ready to process requests.

## Endpoint

```bash
curl -X GET {base-url}/health/alive
```

## Request

Payload - None

## Response

Sample Response

```json

{
    "statusCode": 100,
    "message": "Success",
    "succeeded": true,
    "data": {
        "status": "Healthy/Degraded",
        "expectedDownTime": true,
        "downTimeAdvice": "Expected System Downtime",
        "downTimeReason": "Scheduled Maintenance",
        "downTimeFrom": "2023-07-05T00:00:00.000Z",
        "downTimeMinutes": 60
    }
}


```
