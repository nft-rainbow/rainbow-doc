---
description: >-
  The contract API provide users the entries to interact with the ERC721
  contracts, including deploying the contracts, setting the sponsors and so on.
---

# Contract

## Contract Actions

### Deploy Contract

The `Deploy contract` API helps users to deploy a ERC721 or a ERC1155 contract.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>symbol</td><td>The symbol of the NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>owner_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>type</td><td>The type of the contract, e.g., erc721, erc1155</td><td>body</td><td>string</td><td>true</td></tr><tr><td>base_uri</td><td>The uri of the NFT</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type, which can be <code>conflux</code> or <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>royalties_bps</td><td><p>The price</p><p>of the royalties. When a transferring happens, the projector or creator of the NFT can obtain from the transaction.</p></td><td>body</td><td>integer</td><td>true</td></tr><tr><td>royalties_address</td><td>The address of the beneficiary. When a  transaferring happens, this address can obtain from the transaction.</td><td>body</td><td>string</td><td>false</td></tr><tr><td>tokens_burnable</td><td>Whether the function of burning tokens by the token owner is supported</td><td>body</td><td>bool</td><td>false</td></tr><tr><td>tokens_transferable_by_admin</td><td>Whether the function of  transferring tokens by the contract admin is supported</td><td>body</td><td>bool</td><td>false</td></tr><tr><td>tokens_transferable_by_user</td><td>Whether the function of transferring tokens by contract user is supported</td><td>body</td><td>bool</td><td>false</td></tr><tr><td>transfer_cooldown_time</td><td>The cooldown time of transfering tokens.  Once a transfer transaction is confirmed, the cooldown time must pass before the transfer transaction can be proposed again.</td><td>body</td><td>integer</td><td>true</td></tr><tr><td>is_sponsor_for_all_user</td><td>Whether all users are <a href="../../docs/shu-tu-contract-sponsor.md">sponsored </a>in the contract.  Once the function is opened, all users can call the contract free. </td><td>body</td><td>bool</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
 {
    "chain": "conflux_test",
    "name": "NFT-name",
    "symbol": "ENFT",
    "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
    "type": "erc721",
    "base_uri": "",
    "royalties_bps": 0,
    "royalties_address": "",
    "tokens_burnable": false,
    "tokens_transferable_by_admin": false,
    "tokens_transferable_by_user": false,
    "transfer_cooldown_time": 0,
    "is_sponsor_for_all_user": true
}
```
{% endtab %}

{% tab title="Response" %}
| Name                            | Meaning                                                                                                                                                                | Type    |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| name                            | The name of the NFT                                                                                                                                                    | string  |
| symbol                          | The symbol of the NFT                                                                                                                                                  | string  |
| owner\_address                  | The creater of the contract                                                                                                                                            | string  |
| type                            | The type of the contract, e.g., erc721, erc1155                                                                                                                        | string  |
| base\_uri                       | The uri of the NFT                                                                                                                                                     | string  |
| chain                           | The chain type, which can be `conflux` or `conflux_test`                                                                                                               | string  |
| royalties\_bps                  | <p>The price</p><p>of the royalties. When a transferring happens, the projector or creator of the NFT can obtain from the transaction.</p>                             | integer |
| royalties\_address              | The address of the beneficiary. When a  transaferring happens, this address can obtain from the transaction.                                                           | string  |
| tokens\_burnable                | Whether the function of burning tokens by the token owner is supported                                                                                                 | bool    |
| tokens\_transferable\_by\_admin | Whether the function of  transferring tokens by the contract admin is supported                                                                                        | bool    |
| tokens\_transferable\_by\_user  | Whether the function of transferring tokens by contract user is supported                                                                                              | bool    |
| transfer\_cooldown\_time        | The cooldown time of transfering tokens.  Once a transfer transaction is confirmed, the cooldown time must pass before the transfer transaction can be proposed again. | integer |
| is\_sponsor\_for\_all\_user     | Whether all users are [sponsored ](../../docs/shu-tu-contract-sponsor.md)in the contract.  Once the function is opened, all users can call the contract free.          | bool    |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 20,
    "created_at": "2022-08-22T15:49:42.46+08:00",
    "updated_at": "2022-08-22T15:49:42.46+08:00",
    "deleted_at": null,
    "app_id": 4,
    "chain_type": 1,
    "chain_id": 1,
    "address": "",
    "owner_address": "cfxtest:aajb342mw5kzad6pjjkdz0wxx0tr54nfwpbu6yaj49",
    "type": 1,
    "base_uri": "",
    "name": "NFT-name",
    "symbol": "ENFT",
    "royalties_bps": 0,
    "royalties_address": "cfxtest:aajb342mw5kzad6pjjkdz0wxx0tr54nfwpbu6yaj49",
    "tokens_burnable": false,
    "tokens_transferable_by_admin": false,
    "tokens_transferable_by_user": false,
    "transfer_cooldown_time": 0,
    "hash": "",
    "tx_id": 64,
    "status": 0
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/contracts/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \
  --data ' {
    "chain": "conflux_test",
    "name": "NFT-name",
    "symbol": "ENFT",
    "owner_address": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
    "type": "erc721",
    "base_uri": "",
    "royalties_bps": 0,
    "royalties_address": "",
    "tokens_burnable": false,
    "tokens_transferable_by_admin": false,
    "tokens_transferable_by_user": false,
    "transfer_cooldown_time": 0
}'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
When the api is called successfully, we need to use the `id` in response to call [Query contract detail api](contract.md#query-detail-contract) to get the contract address. It is several seconds that the contract address can be obtained from [Query contract detail api](contract.md#query-detail-contract).
{% endhint %}

### Update contract admin

The `Update contract admin` API provides users the entry to update the admin of the specific contract.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/admin" method="put" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>address</td><td>The address of the contract</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>admin_address</td><td>The address of the admin</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name   | Meaning                   | Type    |
| ------ | ------------------------- | ------- |
| tx\_id | The id of the transaction | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "tx_id": 421312
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request PUT \
  --url https://api.nftrainbow.cn/v1/contracts/{address}/admin \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Set Sponsor

{% hint style="info" %}
**Good to know:** Conflux provides users the sponsor function. Once a contract is sponsored by an account, the accounts in the contract white list can call this contracts for free.
{% endhint %}

The `Set sponsor` API provides users to set a sponser for a specific contract according to the sponsor' address.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/sponsor" method="post" %}
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
| Name                       | Meaning                                                                                   | Type    |
| -------------------------- | ----------------------------------------------------------------------------------------- | ------- |
| sponsor\_gas\_tx\_id       | The id of the sponsor gas setting transaction. `gas` is used for contract running.        | integer |
| sponsor\_collateral\_tx\_i | The id of the sponsor storage setting transaction. `collateral` is presented for storage. | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "sponsor_gas_tx_id": 8475,
    "sponsor_collateral_tx_id": 8476
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/contracts/{address}/sponsor \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Note:** UP to now, only `conlux_test` network supports `Set sponsor` API.
{% endhint %}

### Add Contract Sponsor Users

The `Add Contract Sponsor Users` API provides users to add the address in the whitelist.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/sponsor/whitelist" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>users</td><td>The addresses being added into the <a href="../../docs/shu-tu-contract-sponsor.md">whitelist</a></td><td>body</td><td>[]string</td><td>true</td></tr><tr><td>address</td><td>The address of the contract</td><td>Path</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name   | Meaning                   | Type    |
| ------ | ------------------------- | ------- |
| tx\_id | The id of the transaction | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "tx_id": 421312
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/contracts/{address}/sponsor/whitelist/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \
  --data `["cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8"]`
```
{% endtab %}
{% endtabs %}

### Remove Contract Sponsor Users

The `Remove Contract Sponsor Users` API provides users to remove the address from the whitelist.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/sponsor/whitelist" method="delete" %}
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
| Name   | Meaning                   | Type    |
| ------ | ------------------------- | ------- |
| tx\_id | The id of the transaction | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "tx_id": 421312
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request DELETE \
  --url https://api.nftrainbow.cn/v1/contracts/{address}/sponsor/whitelist/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \
  --data `["cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8"]`
  
```
{% endtab %}
{% endtabs %}

## Query Informations

### Obtain Contract List

The `Obtain contarct list` API provides users the entry to get the inforamtion of the contracts deployed in a specified app. The parameter `page` and `size` are optional parameters.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th><th>Default</th></tr></thead><tbody><tr><td>page</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td><td>1</td></tr><tr><td>limit</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td><td>10</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning                              | Type        |
| ----- | ------------------------------------ | ----------- |
| count | The number of the deployed contracts | integer     |
| items | The contract information             | \[]Contract |

The **`Contract Struct`** is listed as follow:

| Name                            | Meaning                                                                                                                                                                | Type    |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| name                            | The name of the NFT                                                                                                                                                    | string  |
| symbol                          | The symbol of the NFT                                                                                                                                                  | string  |
| owner\_address                  | The creater of the contract                                                                                                                                            | string  |
| type                            | The type of the contract, e.g., erc721, erc1155                                                                                                                        | string  |
| base\_uri                       | The uri of the NFT                                                                                                                                                     | string  |
| chain                           | The chain type, which can be `conflux` or `conflux_test`                                                                                                               | string  |
| royalties\_bps                  | <p>The price</p><p>of the royalties. When a transferring happens, the projector or creator of the NFT can obtain from the transaction.</p>                             | integer |
| royalties\_address              | The address of the beneficiary. When a  transaferring happens, this address can obtain from the transaction.                                                           | string  |
| tokens\_burnable                | Whether the function of burning tokens by the token owner is supported                                                                                                 | bool    |
| tokens\_transferable\_by\_admin | Whether the function of  transferring tokens by the contract admin is supported                                                                                        | bool    |
| tokens\_transferable\_by\_user  | Whether the function of transferring tokens by contract user is supported                                                                                              | bool    |
| transfer\_cooldown\_time        | The cooldown time of transfering tokens.  Once a transfer transaction is confirmed, the cooldown time must pass before the transfer transaction can be proposed again. | integer |
| is\_sponsor\_for\_all\_user     | Whether all users are [sponsored ](../../docs/shu-tu-contract-sponsor.md)in the contract.  Once the function is opened, all users can call the contract free.          | bool    |
{% endtab %}

{% tab title="Response Example" %}
```
{
        "count": 1,
        "items": [
            {
                "id": 1,
                "created_at": "2022-08-19T10:48:13.049+08:00",
                "updated_at": "2022-08-19T10:49:15.853+08:00",
                "deleted_at": null,
                "app_id": 4,
                "chain_type": 1,
                "chain_id": 1,
                "address": "cfxtest:acdzrjc92rds9tuta8rdkx3mn10yzf0jny1z3s0s8e",
                "owner_address": "cfxtest:aajb342mw5kzad6pjjkdz0wxx0tr54nfwpbu6yaj49",
                "type": 1,
                "base_uri": "",
                "name": "ttt",
                "symbol": "test",
                "royalties_bps": 0,
                "royalties_address": "",
                "tokens_burnable": false,
               "tokens_transferable_by_admin": false,
                "tokens_transferable_by_user": false,
                "transfer_cooldown_time": 0,
                "hash": "0xcbcedb27eb941a9a4fb6008d343055d98d9fe1ccdba65268680f46af6bf3fa0a",
                "tx_id": 49,
                "status": 1
            }
        ]
    }
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/contracts/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Query detail contract

The `Query detail contract` API provides users the entry to get the detail contract information of a specific contract according to the contract's id. The parameter `chain` is optional, which can be used to choose the test or main network of conflux.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/detail/{id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>id</td><td>The id of the contract</td><td>Path</td><td>integer</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name                            | Meaning                                                                                                                                                                | Type    |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| name                            | The name of the NFT                                                                                                                                                    | string  |
| symbol                          | The symbol of the NFT                                                                                                                                                  | string  |
| owner\_address                  | The creater of the contract                                                                                                                                            | string  |
| type                            | The type of the contract, e.g., erc721, erc1155                                                                                                                        | string  |
| base\_uri                       | The uri of the NFT                                                                                                                                                     | string  |
| chain                           | The chain type, which can be `conflux` or `conflux_test`                                                                                                               | string  |
| royalties\_bps                  | <p>The price</p><p>of the royalties. When a transferring happens, the projector or creator of the NFT can obtain from the transaction.</p>                             | integer |
| royalties\_address              | The address of the beneficiary. When a  transaferring happens, this address can obtain from the transaction.                                                           | string  |
| tokens\_burnable                | Whether the function of burning tokens by the token owner is supported                                                                                                 | bool    |
| tokens\_transferable\_by\_admin | Whether the function of  transferring tokens by the contract admin is supported                                                                                        | bool    |
| tokens\_transferable\_by\_user  | Whether the function of transferring tokens by contract user is supported                                                                                              | bool    |
| transfer\_cooldown\_time        | The cooldown time of transfering tokens.  Once a transfer transaction is confirmed, the cooldown time must pass before the transfer transaction can be proposed again. | integer |
| is\_sponsor\_for\_all\_user     | Whether all users are [sponsored ](../../docs/shu-tu-contract-sponsor.md)in the contract.  Once the function is opened, all users can call the contract free.          | bool    |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 10,
    "created_at": "2022-08-19T10:48:13.049+08:00",
    "updated_at": "2022-08-19T10:49:15.853+08:00",
    "deleted_at": null,
    "app_id": 4,
    "chain_type": 1,
    "chain_id": 1,
    "address": "cfxtest:acdzrjc92rds9tuta8rdkx3mn10yzf0jny1z3s0s8e",
    "owner_address": "cfxtest:aajb342mw5kzad6pjjkdz0wxx0tr54nfwpbu6yaj49",
    "type": 1,
    "base_uri": "",
    "name": "ttt",
    "symbol": "test",
    "royalties_bps": 0,
    "royalties_address": "",
    "tokens_burnable": false,
    "tokens_transferable_by_admin": false,
    "tokens_transferable_by_user": false,
    "transfer_cooldown_time": 0,
    "hash": "0xcbcedb27eb941a9a4fb6008d343055d98d9fe1ccdba65268680f46af6bf3fa0a",
    "tx_id": 49,
    "status": 1
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/contracts/detail/{id} \
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

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/sponsor" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>address</td><td>The address of the sponsor</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type, which can be <code>conflux</code> or <code>conflux_test</code></td><td>query</td><td>string</td><td>true</td></tr></tbody></table>
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
  --url https://api.nftrainbow.cn/v1/contracts/{address}/sponsor \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know:** For more detailed information, please refer to the following link.
{% endhint %}

{% embed url="https://developer.confluxnetwork.org/conflux-rust/internal_contract/internal_contract#sponsorwhitelistcontrol-contract" %}
SponsorWhitelistControl Contract
{% endembed %}

### Query contract admin

The `Query contract admin` API provides users the entry to get the admin of the specific contract.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/admin" method="get" %}
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

{% tab title="Response Example" %}
```
{
  "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/contracts/{address}/admin \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Query Contract Whitelist

The `Query Contract Whitelist` API provides users to get the whitelist of the specific contract. Only the addresses in the whitelist can call the contract free.

{% swagger src="../../.gitbook/assets/swagger.json" path="/contracts/{address}/sponsor/whitelist" method="get" %}
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
Return the slices of the addresses in the whiltelist.
```
{% endtab %}

{% tab title="Response Example" %}
```
["cfxtest:acexyjf36ddwcct171wr1k5srd289zp9te70p67zc1"]
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/contracts/{address}/sponsor/whitelist/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
