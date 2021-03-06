---
description: >-
  The contract API provide users the entries to interact with the ERC721
  contracts, including deploying the contracts, setting the sponsors and other
  query functions.
---

# Contract

## Contract Actions

### Deploy Contract

The `Deploy contract` API helps users to deploy a ERC721 or a ERC1155 contract.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>symbol</td><td>The symbol of the NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>owner_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>type</td><td>The type of the contract, e.g., ERC721, ERC1155</td><td>body</td><td>string</td><td>true</td></tr><tr><td>base_uri</td><td>The uri of the NFT</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type, which can be <code>conflux</code> or <code>conflux_test</code> </td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
 {
    "chain": "conflux_test",
    "name": "NFT-name",
    "symbol": "ENFT",
    "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
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
| id             | The id of the contract                                         | integer |
| chain\_id      | The id of the chain                                            | string  |
| owner\_address | The uri of the nft                                             | string  |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed  | string  |
| tx\_id         | The id of the transaction                                      | integer |
| type           | The type of the contract. 1-ERC721, 2-ERC1155                  | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
        "id": 3,
        "created_at": "2022-07-27T11:00:57.519+08:00",
        "updated_at": "2022-07-27T11:00:57.519+08:00",
        "deleted_at": null,
        "app_id": 1,
        "chain_type": 1,
        "chain_id": 1,
        "address": "",
        "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
        "type": 1,
        "base_uri": "",
        "name": "NFT-name",
        "symbol": "ENFT",
        "hash": "",
        "tx_id": 3,
        "status": 0
    }
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.xyz/v1/contracts \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \
  --data '{
    "chain": "conflux_test",
    "name": "NFT-name",
    "symbol": "ENFT",
    "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
    "type": "erc721",
    "base_uri": ""
}'
```
{% endtab %}
{% endtabs %}

### Set Sponsor

{% hint style="info" %}
**Good to know:** Conflux provides users the sponsor function. Once a contract is sponsored by an account, the accounts in the contract white list can call this contracts for free.&#x20;
{% endhint %}

The `Set sponsor` API provides users to set a sponser for a specific contract according to the sponsor' address.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/:address/sponsor" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>address</td><td>The address of the contract</td><td>Path</td><td>string</td><td>true</td></tr></tbody></table>
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
  --url https://api.nftrainbow.xyz/v1/contracts/:address/sponsor \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Note:**  UP to now, only `conlux_test` network supports `Set sponsor` API.
{% endhint %}

## Query Informations

### Obtain Contract List

The `Obtain contarct list` API provides users the entry to get the inforamtion of the  contracts deployed in a specified app. The parameter `page` and `size` are optional parameters.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>page</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr><tr><td>limit</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning                              | Type        |
| ----- | ------------------------------------ | ----------- |
| count | The number of the deployed contracts | integer     |
| items | The files information                | \[]Contract |

The **`Contract Struct`** is listed as follow:

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
{
        "count": 2,
        "items": [
            {
                "id": 2,
                "created_at": "2022-07-27T10:55:13.12+08:00",
                "updated_at": "2022-07-27T10:55:13.12+08:00",
                "deleted_at": null,
                "app_id": 1,
                "chain_type": 1,
                "chain_id": 1,
                "address": "",
                "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
                "type": 1,
                "base_uri": "",
                "name": "NFT-name",
                "symbol": "ENFT",
                "hash": "",
                "tx_id": 2,
                "status": 0
            },
            {
                "id": 1,
                "created_at": "2022-07-27T10:47:58.362+08:00",
                "updated_at": "2022-07-27T10:48:14.891+08:00",
                "deleted_at": null,
                "app_id": 1,
                "chain_type": 1,
                "chain_id": 1,
                "address": "",
                "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
                "type": 1,
                "base_uri": "",
                "name": "NFT-name",
                "symbol": "ENFT",
                "hash": "",
                "tx_id": 1,
                "status": 2
            }
        ]
    }
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.xyz/v1/contracts \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Query Sponsor

The `Query sponsor` API provides users the entry to get the sponsors of a specific contract according to the contract's address. The parameter `chain` is optional, which can be used to choose the test or main network of conflux.

{% hint style="info" %}
**Good to know:** Conflux Network can be divided into the main network and the test network. The later is used to test the developed functions for developers.
{% endhint %}

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/:address/sponsor" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>address</td><td>The address of the sponsor </td><td>Path</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type, which can be <code>conflux</code> or <code>conflux_test</code> </td><td>query</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name                         | Meaning                                  | Type    |
| ---------------------------- | ---------------------------------------- | ------- |
| collateral\_sponsor          | The address of the collateral sponsor    | string  |
| collateral\_sponsor\_balance | The balance of the collateral sponsor    | integer |
| gas\_sponsor                 | The address of the gas sponsor           | string  |
| gas\_sponsor\_balance        | The balance of the gas sponsor           | integer |
| gas\_upper\_bound            | The upper bound of using gas             | integer |
| is\_all\_white\_listed       | wheter the sponsor in the all white list | bool    |
{% endtab %}

{% tab title="Response Example" %}
```
{
        "gas_sponsor": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
        "gas_sponsor_balance": 10000000000000000000,
        "collateral_sponsor": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
        "collateral_sponsor_balance": 100000000000000000000,
        "is_all_white_listed": true,
        "gas_upper_bound": 5000000000000000
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.xyz/v1/contracts/:address/sponsor \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
&#x20; **Good to know:**  For more detailed information, please refer to the following link.
{% endhint %}

{% embed url="https://developer.confluxnetwork.org/conflux-rust/internal_contract/internal_contract#sponsorwhitelistcontrol-contract" %}
SponsorWhitelistControl Contract
{% endembed %}
