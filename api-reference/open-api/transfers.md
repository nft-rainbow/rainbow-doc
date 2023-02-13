---
description: The Transfer APIs provide users the entries to tranfer the NFTs easily.
---

# Transfers

## Transfer Actions

The Transfer APIs provide two methods to help users transfer NFTs, including the tranfer or batch transfer NFTs.

### Transfer NFT

The `Transfer NFT` provides users with the entry to transfer the NFT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/transfers/customizable" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>contract_type</td><td>The type of the contract</td><td>body</td><td>string</td><td>false</td></tr><tr><td>token_id</td><td>The id of the NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>transfer_from_address</td><td>The sender of the sending NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>transfer_to_address</td><td>The receiver of the sending NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>amount</td><td>The amount of the sending NFT</td><td>body</td><td>integer</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "contract_address": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
    "contract_type":"erc1155",
    "transfer_from_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "transfer_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "token_id":"20",
    "amount":1
}
```
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| created\_at    | The time of creating the item in the database                 | string  |
| updated\_at    | The time of updating the item in the database                 | string  |
| deleted\_at    | The time of deleting the item in the database                 | string  |
| id             | The id of the item in the database                                         | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_type    | The type of the chain. 1-CFX, 2-ETH.                                        | integer |
| chain\_id      | The id of the chain. 1029-mainnet, 1-testnet                                           | integer |
| contract       | The address of the contract                                   | string  |
| contract\_type | The type of the contract. 1-ERC721, 2-ERC1155                                      | integer |
| token\_id      | The id of the token                                           | string  |
| transfer\_from | The sender of the sending NFT                                 | string  |
| transfer\_to   | The receiver of the sending NFT                               | string  |
| amount         | The amount of the sending NFT                                       | integer |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| hash           | The hash of the transaction                                   | string  |
| tx\_id         | The id of the transaction                                     | integer |
| error          | The error during executing the transaction                    | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 1,
    "created_at": "2022-08-24T07:33:59.985Z",
    "updated_at": "2022-08-24T07:33:59.985Z",
    "deleted_at": null,
    "app_id": 2,
    "chain_type": 1,
    "chain_id": 1,
    "contract": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
    "contract_type": 2,
    "tx_id": 8127,
    "hash": "",
    "status": 0,
    "error": "",
    "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "transfer_to": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "token_id": "20",
    "amount": 1
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/transfers/customizable \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
  --data-raw '{
    "chain": "conflux_test",
    "contract_address": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
    "contract_type":"erc1155",
    "transfer_from_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "transfer_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "token_id":"20",
    "amount":1
}'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The token\_id is the number like "123", which type is string
{% endhint %}

### Batch Transfer NFTs

The `Batch Transfer NFTs` API provides users with the entry to transfer several NFTs once.

{% swagger src="../../.gitbook/assets/swagger.json" path="/transfers/customizable/batch" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_type</td><td>The type of the contract, which includes <code>erc721</code> and <code>erc1155</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>items</td><td>The mint tasks</td><td>body</td><td>The array of the TransferItem</td><td>true</td></tr></tbody></table>

The TransferItem construct is presented in the following.

<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>transfer_from_address</td><td>The sender of the sending NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>transfer_to_address</td><td>The receiver of the sending NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>amount</td><td>The amount of the NFTs</td><td>body</td><td>integer</td><td>true</td></tr><tr><td>token_id</td><td>The id of the token</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "contract_address": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
    "contract_type": "erc1155",
    "items": [
        {
            "transfer_from_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to_address": "cfxtest:aanpu16mtgc7dke5xhuktyfyef8f00pz8a2z5mc14g",
            "token_id": "20",
            "amount": 2
        },
        {
            "transfer_from_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to_address": "cfxtest:aang4d91rejdbpgmgtmspdyefxkubj2bbywrwm9j3z",
            "token_id": "21",
            "amount": 1
        }
    ]
}
```
{% endtab %}

{% tab title="Response" %}
The response is the array of transferTask construct. The construct is showed in the following.

| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| created\_at    | The time of creating the item in the database                 | string  |
| updated\_at    | The time of updating the item in the database                 | string  |
| deleted\_at    | The time of deleting the item in the database                 | string  |
| id             | The id of the item in the database                            | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_type    | The type of the chain. 1-CFX, 2-ETH.                                        | integer |
| chain\_id      | The id of the chain. 1029-mainnet, 1-testnet                                           | integer |
| contract       | The address of the contract                                   | string  |
| contract\_type | The type of the contract. 1-ERC721, 2-ERC1155                                      | integer |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| hash           | The hash of the transaction                                   | string  |
| tx\_id         | The id of the transaction                                     | integer |
| error          | The error during executing the transaction                    | string  |
| transfer\_to   | The receiver of the sending NFT                               | string  |
| transfer\_from | The sender of the sending NFT                                 | string  |
| token\_id      | The id of the token                                           | integer |
| amount         | The amount of the sending NFT                                       | integer |
{% endtab %}

{% tab title="Response Example" %}
```
[
    {
        "id": 1,
        "created_at": "2022-08-24T07:47:48.558Z",
        "updated_at": "2022-08-24T07:47:48.558Z",
        "deleted_at": null,
        "app_id": 2,
        "chain_type": 1,
        "chain_id": 1,
        "contract": "cfxtest:acbf8taf6zzy99kncvu7d81vyavaz2ay5254ca3j7c",
        "contract_type": 1,
        "tx_id": 8474,
        "hash": "",
        "status": 0,
        "error": "",
        "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
        "transfer_to": "cfxtest:aanpu16mtgc7dke5xhuktyfyef8f00pz8a2z5mc14g",
        "token_id": "20",
        "amount": 2,
    },
    {
        "id": 2,
        "created_at": "2022-08-24T07:47:48.558Z",
        "updated_at": "2022-08-24T07:47:48.558Z",
        "deleted_at": null,
        "app_id": 2,
        "chain_type": 1,
        "chain_id": 1,
        "contract": "cfxtest:acbf8taf6zzy99kncvu7d81vyavaz2ay5254ca3j7c",
        "contract_type": 1,
        "tx_id": 8474,
        "hash": "",
        "status": 0,
        "error": "",
        "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
        "transfer_to": "cfxtest:aang4d91rejdbpgmgtmspdyefxkubj2bbywrwm9j3z",
        "token_id": "21",
        "amount": 1,
    }
]
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/transfers/customizable/batch \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
  --data-raw '{
    "chain": "conflux_test",
    "contract_address": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
    "contract_type": "erc1155",
    "items": [
        {
            "transfer_from_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to_address": "cfxtest:aanpu16mtgc7dke5xhuktyfyef8f00pz8a2z5mc14g",
            "token_id": "20",
            "amount": 2
        },
        {
            "transfer_from_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to_address": "cfxtest:aang4d91rejdbpgmgtmspdyefxkubj2bbywrwm9j3z",
            "token_id": "21",
            "amount": 1
        }
    ]
}'
```
{% endtab %}
{% endtabs %}

## Obtain Informations

### Obtain transferred NFT list

The `Obtain transferred NFT list` API provides users with the entry to query the transferred NFTs information.

{% swagger src="../../.gitbook/assets/swagger.json" path="/transfers/" method="get" %}
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
| Name  | Meaning                           | Type        |
| ----- | --------------------------------- | ----------- |
| count | The number of the tranferred NFTs | integer     |
| items | The nfts information              | \[]TransferTask |

The **`TransferTask Struct`** is listed as follow:

| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| created\_at    | The time of creating the item in the database                 | string  |
| updated\_at    | The time of updating the item in the database                 | string  |
| deleted\_at    | The time of deleting the item in the database                 | string  |
| id             | The id of the item in the database                                         | integer |
| amount         | The amount of the sending NFTs                                         | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_id      | The id of the chain. 1029-mainnet, 1-testnet                                           | integer |
| chain\_type    | The type of the chain. 1-CFX, 2-ETH                                         | integer |
| contract       | The address of the nft                                        | string  |
| contract\_type | The type of the contract. 1-ERC721, 2-ERC1155                                      | integer |
| error          | The error during executing tx                                 | string  |
| hash           | The hash of the transaction                                   | string  |
| transfer\_to   | The receiver of the sending NFT                               | string  |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id      | The id of the token                                           | string  |
| transfer\_from | The sender of the sending NFT                                 | string  |
| tx\_id         | The id of the transaction                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "count": 3,
    "items": [
        {
            "id": 3,
            "created_at": "2022-08-24T07:47:48.56Z",
            "updated_at": "2022-08-24T07:47:51.882Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
            "contract_type": 2,
            "tx_id": 8129,
            "hash": "",
            "status": 2,
            "error": "",
            "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to": "cfxtest:aang4d91rejdbpgmgtmspdyefxkubj2bbywrwm9j3z",
            "token_id": "21",
            "amount": 1
        },
        {
            "id": 2,
            "created_at": "2022-08-24T07:47:48.56Z",
            "updated_at": "2022-08-24T07:47:51.877Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
            "contract_type": 2,
            "tx_id": 8129,
            "hash": "",
            "status": 2,
            "error": "",
            "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to": "cfxtest:aanpu16mtgc7dke5xhuktyfyef8f00pz8a2z5mc14g",
            "token_id": "20",
            "amount": 2
        },
        {
            "id": 1,
            "created_at": "2022-08-24T07:33:59.985Z",
            "updated_at": "2022-08-24T07:34:21.757Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
            "contract_type": 2,
            "tx_id": 8127,
            "hash": "",
            "status": 2,
            "error": "",
            "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "transfer_to": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "token_id": "20",
            "amount": 1
        }
    ]
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/transfers/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Obtain Detialed NFT Transfer Information

The `Obtain Detialed NFT Transfer Information` API provides users with the entry to query the transferred NFT information according to its `id`.

{% swagger src="../../.gitbook/assets/swagger.json" path="/transfers/{id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>id</td><td>transfer id</td><td>path</td><td>integer</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| created\_at    | The time of creating the item in the database                 | string  |
| updated\_at    | The time of updating the item in the database                 | string  |
| deleted\_at    | The time of deleting the item in the database                 | string  |
| id             | The id of the item in the database                                         | integer |
| amount         | The amount of the sending NFTs                                         | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_id      | The id of the chain. 1029-mainnet, 1-testnet                                           | integer |
| chain\_type    | The type of the chain. 1-CFX, 2-ETH                                         | integer |
| contract       | The address of the nft                                        | string  |
| contract\_type | The type of the contract. 1-ERC721, 2-ERC1155                                      | integer |
| error          | The error during executing tx                                 | string  |
| hash           | The hash of the transaction                                   | string  |
| transfer\_to   | The receiver of the sending NFT                               | string  |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id      | The id of the token                                           | string  |
| transfer\_from | The sender of the sending NFT                                 | string  |
| tx\_id         | The id of the transaction                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 3,
    "created_at": "2022-08-24T07:47:48.56Z",
    "updated_at": "2022-08-24T07:47:51.882Z",
    "deleted_at": null,
    "app_id": 2,
    "chain_type": 1,
    "chain_id": 1,
    "contract": "cfxtest:accy6epch754uamc4x55mcv3pzgae8vfvaufj6v4uj",
    "contract_type": 2,
    "tx_id": 8129,
    "hash": "",
    "status": 2,
    "error": "",
    "transfer_from": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "transfer_to": "cfxtest:aang4d91rejdbpgmgtmspdyefxkubj2bbywrwm9j3z",
    "token_id": "21",
    "amount": 1
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/transfers/{id} \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
