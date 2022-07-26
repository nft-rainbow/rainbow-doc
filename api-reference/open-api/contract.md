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
| Name           | Meaning                                         | Param Type | Type    |
| -------------- | ----------------------------------------------- | ---------- | ------- |
| name           | The name of the nft                             | body       | string  |
| symbol         | The symbol of the nft                           | body       | string  |
| owner\_address | The creater of the contract                     | body       | string  |
| type           | The type of the contract, e.g., ERC721, ERC1155 | body       | integer |
| base\_uri      | The uri of the nft                              | body       | string  |
| Authorization  | Bear JWT                                        | Header     | string  |
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "name": "NFT-name",
    "symbol": "ENFT",
    "owner_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "type": "erc721",
    "base_uri": ""
}
```
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                                                        | Type    |
| -------------- | -------------------------------------------------------------- | ------- |
| address        | The address of the contract                                    | string  |
| hash           | The hash of the transaction                                    | string  |
| id             |                                                                | integer |
| chain\_id      | The id of the chain                                            | string  |
| owner\_address | The uri of the nft                                             | string  |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed  | string  |
| tx\_id         | The id of the transaction                                      | integer |
| type           | The type of the contract. 1-ERC721, 2-ERC1155                  | integer |
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

{% tabs %}
{% tab title="Parameter" %}


| Name          | Meaning                     | Param Type | Data Type |
| ------------- | --------------------------- | ---------- | --------- |
| address       | The address of the sponsor  | formData   | string    |
| address       | The address of the contract | Path       | string    |
| Authorization | Bear JWT                    | Header     | string    |
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "address": "cfxtest:acdemzrsy4sfdcz1811bn5s565ecvrtz729caz3r5d"
}
```
{% endtab %}

{% tab title="Response" %}
```
"success"
```
{% endtab %}

{% tab title="Response Example" %}
```
"success"
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://localhost:8080/v1/contracts/:address/sponsor \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

## Query informations

### Get the contract list

The `Get the contarct list` API provides users the entry to get the deployed contracts.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| page          | Page Request | query      | integer   |
| limit         | Page Request | query      | integer   |
| Authorization | Bear JWT     | Header     | string    |
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| address        | Page Request                                                  | string  |
| app\_id        | Page Request                                                  | string  |
| base\_uri      | The uri of the nft                                            | string  |
| chain\_id      | The id of the chain                                           | integer |
| chain\_type    | The type of the chain                                         | integer |
| hash           | The hash of the transaction                                   | string  |
| id             | The id of the contract                                        | integer |
| name           | The name of the nft                                           | string  |
| owner\_address | The creator of the contract                                   | string  |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| symbol         | The symbol of the nft                                         | string  |
| tx\_id         | The id of the transaction                                     | integer |
| type           | The type of the contract. 1-ERC721, 2-ERC1155                 | integer |
| Authorization  | Bear JWT                                                      | string  |
{% endtab %}

{% tab title="Response Example" %}
```
[
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
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/contracts \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Get the sponsor of a contract

The `Get the sponsor of a contract` API provides users the entry to get the sponsors of a specific contract.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/:address/sponsor" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}
| Name          | Meaning                     | Param Type | Data Type |
| ------------- | --------------------------- | ---------- | --------- |
| Authorization | Bear JWT                    | Header     | string    |
| address       | The address of the sponsor  | Path       | string    |
| chain         | The type of the chain       | query      | string    |
{% endtab %}

{% tab title="Response" %}
| Name                         | Meaning                                  | Type |
| ---------------------------- | ---------------------------------------- | ---- |
| collateral\_sponsor          | The address of the collateral sponsor    |      |
| collateral\_sponsor\_balance | The balance of the collateral sponsor    |      |
| gas\_sponsor                 | The address of the gas sponsor           |      |
| gas\_sponsor\_balance        | The balance of the gas sponsor           |      |
| gas\_upper\_bound            | The upper bound of using gas             |      |
| is\_all\_white\_listed       | wheter the sponsor in the all white list |      |
|                              |                                          |      |
|                              |                                          |      |
|                              |                                          |      |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "collateral_sponsor": {},
    "collateral_sponsor_balance": {},
    "gas_sponsor": {},
    "gas_sponsor_balance": {},
    "gas_upper_bound": {},
    "is_all_white_listed": true
  }
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/contracts/:address/sponsor \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know:**  For more detailed information, please refer to the developer documentation:

&#x20;[https://developer.confluxnetwork.org/conflux-rust/internal\_contract/internal\_contract#sponsorwhitelistcontrol-contract:\~:text=Copy-,SponsorWhitelistControl%20contract,-%23](https://developer.confluxnetwork.org/conflux-rust/internal\_contract/internal\_contract#sponsorwhitelistcontrol-contract)
{% endhint %}
