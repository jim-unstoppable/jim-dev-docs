---
title: Domain Name Availability Guide | Unstoppable Domains Developer Portal
description: This guide shows how to check the availability of a domain name before purchase with your Partner account.
---

# Domain Name Availability Guide

The Partner API offers an endpoint that lets you check the availability of a domain name before purchase to avoid making minting calls to non-available domains. Partners can use this endpoint to implement a domain name search field in their application to shows users which domain names are available and the prices to purchase them.

<figure>

![Domain search field example](/images/domain-search-field.png)

<figcaption>Domain search field example</figcaption>
</figure>

## Step 1: Retrieve Your Reseller ID and Secret API Token

<embed src="/snippets/_reseller-id-location.md" />

## Step 2: Prepare Authorization Headers

<embed src="/snippets/_auth-headers-preparation.md" />

## Step 3: Use the Domain Name Availability Endpoint

Send a `GET` request with the authorization headers you have prepared and the domain name you want to check to the [Domain Name Availability](https://docs.unstoppabledomains.com/openapi/reference/#operation/GetDomain) endpoint. Here is the URL for our API environments:

Sandbox Environment:

```bash
https://api.ud-sandbox.com/api/v2/resellers/{PARTNER_RESELLERID}/domains/{DOMAIN_TO_CHECK}
```

Production Environment:

```bash
https://unstoppabledomains.com/api/v2/resellers/{PARTNER_RESELLERID}/domains/{DOMAIN_TO_CHECK}
```

:::info
The `PARTNER_RESELLERID` path parameter is the same one you retrieved from your partner account earlier.
:::

## Example

Here is an example request to check the availability of the `buyadomain.dao` domain before purchase:

```bash Request
curl --location --request GET 'https://api.ud-sandbox.com/api/v2/resellers/{PARTNER_RESELLERID}/domains/buyadomain.dao' \
--header 'Authorization: Bearer {SECRET_API_TOKEN}'
```

```json Response
{
    "domain": {
        "id": 167892438,
        "name": "buyadomain.dao",
        "ownerAddress": null,
        "resolver": null,
        "resolution": {},
        "blockchain": "MATIC",
        "projectedBlockchain": "MATIC",
        "registryAddress": "0xa9a6a3626993d487d2dbda3173cf58ca1a9d9e9f",
        "networkId": 137,
        "freeToClaim": true,
        "node": "0xbaee34a867ed94387a307bf426ae01af9f4254f8c1dc2c633c577278df0d6454"
    },
    "availability": {
        "registered": false,
        "protected": false,
        "price": 20,
        "availableForFree": false,
        "test": false
    }
}
```

From the `availability` field in the API response, we can see the domain hasn't been registered and costs `$20` to purchase.

:::success Congratulations!
You have successfully checked the availability of a domain name with the Partner API.
:::

<embed src="/snippets/_discord.md" />
