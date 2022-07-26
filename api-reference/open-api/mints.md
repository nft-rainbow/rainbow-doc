---
description: >-
  The Mints APIs provide users the entries to mint the NFTs by calling the
  method in the ERC721 contract.
---

# Mints

## Mint Actions

The Mints APIs provides three methods to help users mint NFTs, including the custom minting, minting with a file and minting with  a metada.

### Mint NFT

The `Mint NFT` provides users with the entry to call the ERC721 contract to mint the NFT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Optional</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type</td><td>body</td><td>string</td><td>false</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>false</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>integer</td><td>false</td></tr><tr><td>metadata_uri</td><td>The uri of the metadata</td><td>body</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "name": "123",
    "description": "123",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "contract_address": "cfxtest:acgat1yux2rk0xmk2s8ceferyprgm0u1hetj0w72yf",
    "metadata_uri": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png"
}
```
{% endtab %}

{% tab title="Response" %}
| Name              | Meaning                    | Type   |
| ----------------- | -------------------------- | ------ |
| chain             | The type of the chain      | string |
| description       | The description of the nft | string |
| mint\_to\_address | The creator of the address | string |
| name              | The name of the nft        | string |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "chain": "string",
    "description": "string",
    "mint_to_address": "string",
    "name": "string"
  }
]
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://localhost/v1/mints \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Mint NFT with file

The `Mint NFT with file` provides users with the entry to call the ERC721 contract to mint the NFT with uploading files. The uploaded files can be images, video and so on.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/easy/files" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">optional</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type</td><td>body</td><td>string</td><td>false</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>false</td></tr><tr><td>description</td><td>The description of the contract</td><td>body</td><td>string</td><td>false</td></tr><tr><td>file</td><td>The uploaded file</td><td>body</td><td></td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name              | Meaning                    | Type   |
| ----------------- | -------------------------- | ------ |
| chain             | The type of the chain      | string |
| description       | The description of the nft | string |
| mint\_to\_address | The creator of the address | string |
| name              | The name of the nft        | string |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "chain": "string",
    "description": "string",
    "mint_to_address": "string",
    "name": "string"
  }
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://localhost:8080/v1/mints/files \
  --header 'Authorization: ' \
  --header 'Content-Type: multipart/form-data' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form chain= \
  --form description= \
  --form mint_to_address= \
  --form name=
```
{% endtab %}
{% endtabs %}

### Mint NFT with metadata

The `Mint NFT with metadata` provides users with the entry to call the ERC721 or ERC1155 contract to mint the NFT with creating metadata by providing a file url.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/easy/urls" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Optional</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type</td><td>body</td><td>string</td><td>false</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>false</td></tr><tr><td>description</td><td>The description of the contract</td><td>body</td><td>string</td><td>false</td></tr><tr><td>file_url</td><td>The url of the file</td><td>body</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "name": "123",
    "description": "123",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "file_url": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png"
}
```
{% endtab %}

{% tab title="Response" %}
| Name              | Meaning                    | Type   |
| ----------------- | -------------------------- | ------ |
| chain             | The type of the chain      | string |
| description       | The description of the nft | string |
| mint\_to\_address | The creator of the address | string |
| name              | The name of the nft        | string |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "chain": "string",
    "description": "string",
    "mint_to_address": "string",
    "name": "string"
  }
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://localhost:8080/mints/urls \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

## Obtain Informations

The `Obtain NFT list` API provide users with the entry to query the NFTs information created on a spcific app.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Optional</th></tr></thead><tbody><tr><td>page</td><td>Page Request</td><td>query</td><td>integer</td><td>true</td></tr><tr><td>limit</td><td>Page Request</td><td>query</td><td>integer</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name        | Meaning                                                       | Type    |
| ----------- | ------------------------------------------------------------- | ------- |
| amount      | The amount of the nft                                         | integer |
| app\_id     | The id of the app                                             | integer |
| chain\_id   | The id of the chain                                           | integer |
| chain\_type | The type of the chain                                         | integer |
| contract    | The address of the nft                                        | string  |
| error       | The error during executing tx                                 | string  |
| hash        | The hash of the transaction                                   | string  |
| id          |                                                               | integer |
| mint\_to    | The creater of the contract                                   | string  |
| status      | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id   | The id of the token                                           | integer |
| token\_uri  | The uri of the token                                          | string  |
| tx\_id      | The id of the transaction                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "amount": 0,
    "app_id": 0,
    "chain_id": 0,
    "chain_type": 0,
    "contract": "string",
    "created_at": "string",
    "deleted_at": {
      "time": "string",
      "valid": true
    },
    "error": "string",
    "hash": "string",
    "id": 0,
    "mint_to": "string",
    "status": 0,
    "token_id": 0,
    "token_uri": "string",
    "tx_id": 0,
    "updated_at": "string"
  }
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/mints \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
