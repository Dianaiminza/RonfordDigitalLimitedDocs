---
sidebar_position: 1
---

# Documentation Intro

This document is a description of the integration process to the MuzuriPay API. The service enables bank and non-bank customers to make payments to merchant accounts at NCBA through multiple payment options. This scope covers the services to be used in the integration and describes payloads for different services in the API. The merchant API should support all the bank initiated requests in the section below.

## List of APIs to be used

### Bank Initiated Requests

1. Health check
2. Account/Reference validation
3. Payment notification
4. Check transaction status

### Merchant initiated Requests

1. Payment processing result callback
2. Reversal

## Message Exchange

The API is a json web service with requests sent over HTTPS. Standard HTTP methods are supported and responses use standard HTTP status codes.

## Security Measures

- HTTPs only - Merchant to provide a HTTPS URL
- All endpoints are protected with an API key
- Payment notification and reversal endpoints require a hash
- IP whitelisting - Merchant service to whitelist bank IPs
- Periodic client id and secret rotation

## Credentials to be shared by merchant

1. Service base url
2. API Key / Client Id
3. Secret Key / Client Secret

## Credentials to be shared by the bank

Source IPs to be whitelisted
Callback url - On every payment notification

## Global Headers

x-api-key **Required** **Yes**

## Message Structure

### Requests

Requests are made to the API using standard HTTP methods and JSON payloads. Some endpoints require a Hash to be provided. The hash should be validated and the request failed if there is a mismatch. Find a section on hash generation and use at the end of this document.

### Responses

All responses have 4 parts: A  **StatusCode**, **Message**, **Succeeded**, and **Data**. The data segment changes depending on the service and the processing result of the request. If model validation fails for instance, the validation errors are added as a list on the data segment. If a request is successful, the respective response data for the service is included as data.

### Generic Sample

```json

{
    "statusCode": 100,
    "message": "SUCCESS",
    "succeeded": true,
    "data": {}
}


```
