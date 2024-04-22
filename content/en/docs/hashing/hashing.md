---
title: Hashing
description: ''
position: 7
category: Hashing
---

This is a security measure implemented in the API to ensure data integrity. This applies to select endpoints with a **hash** segment as reflected on the specs. The data to be hashed is below each request.

## Pre-Requisites

- Client secret issued by the merchant

Consider providing a sample hashing endpoint on the API to test similarity in output from our function and the implementation in your API.

## Endpoint

```bash
curl -X  {base-url}/api/v1/test/generate-test-hash

```

The process of hashing is as follows:

1. Convert the request payload to a json string. For serializer settings use the below:

- Strategy -> Camel Case
- Formatting -> None
- DateHandling -> Date with offset

2. Append your secret key to the json string as shown below.

```bash
{jsonString}{channelSecretKey}
```

3. Use SHA256 to compute the hash using the secret key to get the hashed string.
4. Compare hash to the hash shared in the request
