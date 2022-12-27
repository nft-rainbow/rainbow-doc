---
description: The burns API provide users the entries to burn the NFTs.
---

# Burns

## Burn NFTs

### Burn NFT by Admin

The `Burn NFT by Admin` API helps users to burn the corresponding NFT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/burns" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the NFT</td><td>body</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_type</td><td>The type of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>amount</td><td>The amount of the burned NFTs</td><td>body</td><td>integer</td><td>false</td></tr><tr><td>user</td><td>The address of the user</td><td>body</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "contract_address": "cfxtest:acg1rr3cxaykwymwrajgat0vbk44wvzsrj0ftk7wb1",
    "contract_type":"erc721",
    "user": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "token_id":"23",
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
| amount         | The amount of the nft                                         | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_id      | The id of the chain                                           | integer |
| chain\_type    | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                      | integer |
| contract       | The address of the nft                                        | string  |
| error          | The error during executing tx                                 | string  |
| hash           | The hash of the transaction                                   | string  |
| id             | The id of the storage                                         | integer |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id      | The id of the token                                           | string  |
| user           | The address of the user                                       | string  |
| tx\_id         | The id of the transaction                                     | integer |
| mint\_type     | The type of the minting                                       | integer |
| error          | The error during executing the transaction                    | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 106,
    "created_at": "2022-10-11T17:18:29.494+08:00",
    "updated_at": "2022-10-11T17:18:29.494+08:00",
    "deleted_at": null,
    "app_id": 18,
    "chain_type": 1,
    "chain_id": 1,
    "contract": "cfxtest:acdyu08shg7mu816y0xkty81hev50g7gtu2effygtk",
    "contract_type": 1,
    "tx_id": 767,
    "hash": "",
    "status": 0,
    "error": "",
    "user": "cfxtest:aarep2p1rcadt0j1x0gkybggfkk97uxwty45grxxt7",
    "token_id": "23",
    "amount": 1
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/burns/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
  --data '{
    "chain{
    "chain": "conflux_test",
    "contract_address": "cfxtest:acg1rr3cxaykwymwrajgat0vbk44wvzsrj0ftk7wb1",
    "contract_type":"erc721",
    "user": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
    "token_id":"23",
    "amount":1
}'
```
{% endtab %}
{% endtabs %}

## Query Operations

### Query specific Burning NFT information

The `Query specific Burning NFT information` API helps users to query burning record according to `id`.

{% swagger src="../../.gitbook/assets/swagger.json" path="/burns/{id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>id</td><td>The id of the record</td><td>path</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| created\_at    | The time of creating the item in the database                 | string  |
| updated\_at    | The time of updating the item in the database                 | string  |
| deleted\_at    | The time of deleting the item in the database                 | string  |
| amount         | The amount of the nft                                         | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_id      | The id of the chain                                           | integer |
| chain\_type    | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                      | integer |
| contract       | The address of the nft                                        | string  |
| error          | The error during executing tx                                 | string  |
| hash           | The hash of the transaction                                   | string  |
| id             | The id of the storage                                         | integer |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id      | The id of the token                                           | string  |
| user           | The address of the user                                       | string  |
| tx\_id         | The id of the transaction                                     | integer |
| mint\_type     | The type of the minting                                       | integer |
| error          | The error during executing the transaction                    | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 106,
    "created_at": "2022-10-11T17:18:29.494+08:00",
    "updated_at": "2022-10-11T17:18:44.02+08:00",
    "deleted_at": null,
    "app_id": 18,
    "chain_type": 1,
    "chain_id": 1,
    "contract": "cfxtest:acdyu08shg7mu816y0xkty81hev50g7gtu2effygtk",
    "contract_type": 1,
    "tx_id": 767,
    "hash": "0xc7bc8b1e33c30cd0e522d973b8ab63880549125ec12389701e7e54a6d6836bb0",
    "status": 1,
    "error": "",
    "user": "cfxtest:aarep2p1rcadt0j1x0gkybggfkk97uxwty45grxxt7",
    "token_id": "4646046442",
    "amount": 1
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request get \
  --url https://api.nftrainbow.cn/v1/burns/105 \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
```
{% endtab %}
{% endtabs %}

### Query Burning List

The `Query Burning List` API helps users to query burning list.

{% swagger src="../../.gitbook/assets/swagger.json" path="/burns" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>page</td><td>The page request</td><td>query</td><td>string</td><td>false</td></tr><tr><td>limit</td><td>The page request</td><td>query</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning                  | Type        |
| ----- | ------------------------ | ----------- |
| count | The count of the records | string      |
| Items | The array of items       | \[]BurnTask |

The BurnTask struct is showed in the following.

| Name           | Meaning                                                       | Type    |
| -------------- | ------------------------------------------------------------- | ------- |
| created\_at    | The time of creating the item in the database                 | string  |
| updated\_at    | The time of updating the item in the database                 | string  |
| deleted\_at    | The time of deleting the item in the database                 | string  |
| amount         | The amount of the nft                                         | integer |
| app\_id        | The id of the app                                             | integer |
| chain\_id      | The id of the chain                                           | integer |
| chain\_type    | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                      | integer |
| contract       | The address of the nft                                        | string  |
| error          | The error during executing tx                                 | string  |
| hash           | The hash of the transaction                                   | string  |
| id             | The id of the storage                                         | integer |
| status         | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id      | The id of the token                                           | string  |
| user           | The address of the user                                       | string  |
| tx\_id         | The id of the transaction                                     | integer |
| mint\_type     | The type of the minting                                       | integer |
| error          | The error during executing the transaction                    | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "count": 1,
    "items": [
        {
            "id": 1,
            "created_at": "2022-10-10T23:07:17.747+08:00",
            "updated_at": "2022-10-10T23:07:36.485+08:00",
            "deleted_at": null,
            "app_id": 19,
            "chain_type": 1,
            "chain_id": 1029,
            "contract": "cfx:acd1pmsj9crnr79rmmd9ne5pb5dbk51p4ydf6msz5e",
            "contract_type": 2,
            "tx_id": 657,
            "hash": "0x26acea5c8f60aeb8964e6505e33b66cbb017185b93d7ea1fb9d4d80139a307a8",
            "status": 1,
            "error": "",
            "user": "cfx:aat5w71vgxyumvm2bzsxshed027rwjst6e8mt3sam0",
            "token_id": "9262474764",
            "amount": 1
        }
    ]
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/burns/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
```
{% endtab %}
{% endtabs %}
