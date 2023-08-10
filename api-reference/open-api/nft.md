---
description: The nft API provide users the entries to interact with the NFTs.
---

# NFT

## Update NFT

### Update NFT token uri

The `Update NFT token uri` API provides users to update the nft token uri according to the contract address and the token\_id.

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/nft/{address}/{token_id}/tokenUri" method="put" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the nft</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>address</td><td>The address of the contract</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>token_uri</td><td>The updated token uri</td><td>body</td><td>string</td><td>false</td></tr><tr><td>contract_type</td><td>The type of the contract, which includes erc721 and erc1155</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The type of the chain, which includes conflux and conflux_test</td><td>body</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name            | Meaning                                                                                                                                                                                                    | Type    |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| created\_at     | The time of creating the item in the database                                                                                                                                                              | string  |
| updated\_at     | The time of updating the item in the database                                                                                                                                                              | string  |
| deleted\_at     | The time of deleting the item in the database                                                                                                                                                              | string  |
| id              | The id of the item in the database                                                                                                                                                                         | integer |
| TaskType        | The type of the item in the transaction. 1-deploy, 2-mint, 3-batch mint, 4-transfer, 5-batch transfer, 6-burn, 7-batch burn, 8-update admin, 9-sponsor balance, 10-sponsor privilege, 11-update token\_uri | integer |
| ChainType       | The type of the chain, 1-cfx, 2-eth                                                                                                                                                                        | integer |
| ChainId         | The type of the chain, 1-testnet, 1029-mainnet                                                                                                                                                             | integer |
| From            | The sender of the transaction                                                                                                                                                                              | string  |
| To              | The receiver of the transaction                                                                                                                                                                            | string  |
| Nonce           | The nonce of the transaction                                                                                                                                                                               | string  |
| Value           | The value of the transaction                                                                                                                                                                               | string  |
| Data            | The data of the transaction                                                                                                                                                                                | string  |
| Hash            | The hash of the transaction                                                                                                                                                                                | string  |
| State           | The state of the transaction                                                                                                                                                                               | integer |
| epoch\_number   | The epoch number of the transaction                                                                                                                                                                        | integer |
| error           | The error of the transaction                                                                                                                                                                               | string  |
| GasPrice        | The gas price of the transaction                                                                                                                                                                           | string  |
| Gas             | The used gas of the transaction                                                                                                                                                                            | string  |
| StorageLimit    | The storage limit of the transaction                                                                                                                                                                       | string  |
| EpochHeight     | The epoch height of the transaction                                                                                                                                                                        | string  |
| pending\_reason | The pending reason of the transaction                                                                                                                                                                      | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 181295,
    "created_at": "2023-02-15T10:19:00.166+08:00",
    "updated_at": "2023-02-15T10:19:00.166+08:00",
    "deleted_at": null,
    "TaskType": 11,
    "ChainType": 1,
    "ChainId": 1,
    "From": "cfxtest:aanygt6awrrj1rv9jtctu763t3j6f9hh4p1xc4bkdd",
    "To": "cfxtest:acdggzx0r58uykdz19t42fyab92xmdk4g6vazyywns",
    "Nonce": 0,
    "Value": "0",
    "Data": "0x18e97fd100000000000000000000000000000000000000000000000000000000000000060000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000d7777772e62616964752e636f6d00000000000000000000000000000000000000",
    "Hash": "",
    "State": 0,
    "epoch_number": 0,
    "error": "",
    "GasPrice": "0",
    "Gas": "0",
    "StorageLimit": "0",
    "EpochHeight": "0",
    "pending_reason": ""
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request PUT \
  --url https://api.nftrainbow.cn/v1/nft/{address}/{token_id} \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
  --data-raw '
  {
    "token_uri": "www.baidu.com",
    "contract_type": "erc1155",
    "chain": "conflux_test"
}'
```
{% endtab %}
{% endtabs %}

## Query NFT

### Query specific NFT of specific account

The `Query specific NFT of specific account` API provides users to get the nft information according to the contract address and the token\_id.

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/nft/{address}/{token_id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the nft</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>address</td><td>The address of the contract</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>type</td><td>The contract type: erc721, erc1155. Default is erc721</td><td>Query</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name              | Meaning                     | Type   |
| ----------------- | --------------------------- | ------ |
| owner             | The owner of the NFT        | string |
| contract\_address | The address of the contract | string |
| token\_id         | The id of the token         | string |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "owner": "cfxtest:aakkfzezns4h8ymx1cgmcnd4x3aev6e2he38nnu8sv",
    "contract_address": "cfxtest:acd8eue6shtzvnc7mts66hh88nvw2gtnaez6c4s1a5",
    "token_id": "17",
    "token_uri": "https://nftrainbow.cn/assets/1.json"
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/nft/{address}/{token_id} \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The token\_id is a number like "123", which type is string. If the type parameter pass erc1155, the response's owner field will be empty.
{% endhint %}

### Query NFT Hold count
