---
description: >-
  The contract API provide users the entries to interact with the ERC721
  contracts, including deploying the contracts, setting the sponsors and other
  query functions.
---

# Contract

## Contract actions

### Deploy Contract

The `Deploy contract` API helps users to deploy a ERC721 contract.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}
| Name | Meaning | Type |
| ---- | ------- | ---- |
|      |         |      |
|      |         |      |
|      |         |      |
{% endtab %}

{% tab title="Parameter Example" %}

{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Response Example" %}
```
{
  "address": "string",
  "app_id": 0,
  "base_uri": "string",
  "chain_id": 0,
  "chain_type": 0,
  "created_at": "string",
  "deleted_at": {
    "time": "string",
    "valid": true
  },
  "hash": "string",
  "id": 0,
  "name": "string",
  "owner_address": "string",
  "status": 0,
  "symbol": "string",
  "tx_id": 0,
  "type": 0,
  "updated_at": "string"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://localhost:8080/v1/contracts \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Set the sponsor for a contract

{% hint style="success" %}
**Good to know:** Conflux provides users the sponsor function. Once a contract is sponsored by an account, the accounts in the contract white list can call this contracts for free.&#x20;
{% endhint %}

The `Set the sponsor for a contract` API provides users to set sponsers for a specific contract.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/:address/sponsor" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

## Query informations

### Get the contract list

The `Get the contarct list` API provides users the entry to get the deployed contracts.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Get the sponsor of a contract

The `Get the sponsor of a contract` API provides users the entry to get the sponsors of a specific contract.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/:address/sponsor" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}
