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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the nft</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type</td><td>body</td><td>string</td><td>true</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>metadata_uri</td><td>The uri of the metadata</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "token_id": "",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "contract_address": "cfxtest:acgat1yux2rk0xmk2s8ceferyprgm0u1hetj0w72yf",
    "metadata_uri": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png"
}
```
{% endtab %}

{% tab title="Response" %}
| Name        | Meaning                                    | Type    |
| ----------- | ------------------------------------------ | ------- |
| app\_id     | The id of the app                          | integer |
| chain\_type | The type of the chain.                     | integer |
| chain\_id   | The id of the chain                        | integer |
| contract    | The address of the contract                | string  |
| mint\_to    | The address of the owner                   | string  |
| token\_uri  | The uri of the token                       | string  |
| token\_id   | The id of the token                        | integer |
| amount      | The amount of the token                    | integer |
| status      | The status of the transaction              | integer |
| hash        | The hash of the transaction                | string  |
| tx\_id      | The id of the transaction                  | integer |
| error       | The error during executing the transaction | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
        "id": 1,
        "created_at": "2022-07-27T11:14:09.686+08:00",
        "updated_at": "2022-07-27T11:14:09.686+08:00",
        "deleted_at": null,
        "app_id": 1,
        "chain_type": 1,
        "chain_id": 1,
        "contract": "cfxtest:acf8m2gzrv8pnfsjbne2d28m4h2ycj569uupgys473",
        "mint_to": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
        "token_uri": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png",
        "token_id": 7958647809,
        "amount": 1,
        "status": 0,
        "hash": "",
        "tx_id": 5,
        "error": ""
    }
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>description</td><td>The description of the contract</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>file</td><td>The uploaded file</td><td>formData</td><td></td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name        | Meaning                                    | Type    |
| ----------- | ------------------------------------------ | ------- |
| app\_id     | The id of the app                          | integer |
| chain\_type | The type of the chain.                     | integer |
| chain\_id   | The id of the chain                        | integer |
| contract    | The address of the contract                | string  |
| mint\_to    | The address of the owner                   | string  |
| token\_uri  | The uri of the token                       | string  |
| token\_id   | The id of the token                        | integer |
| amount      | The amount of the token                    | integer |
| status      | The status of the transaction              | integer |
| hash        | The hash of the transaction                | string  |
| tx\_id      | The id of the transaction                  | integer |
| error       | The error during executing the transaction | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
        "id": 4,
        "created_at": "2022-07-27T11:27:36.636+08:00",
        "updated_at": "2022-07-27T11:27:36.636+08:00",
        "deleted_at": null,
        "app_id": 1,
        "chain_type": 1,
        "chain_id": 1,
        "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
        "mint_to": "cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk",
        "token_uri": "http://localhost:8080/assets/metadata/0/nft/2dfd6b3add9d5154cf4ccef7a040f4c5c3c965ec5845bd11ca297e8550ac63ee.json",
        "token_id": 0,
        "amount": 1,
        "status": 0,
        "hash": "",
        "tx_id": 8,
        "error": ""
    }
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>body</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type</td><td>body</td><td>string</td><td>true</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>description</td><td>The description of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>file_url</td><td>The url of the file</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
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


| Name  | Meaning                          | Type        |
| ----- | -------------------------------- | ----------- |
| count | The number of the uploaded files | integer     |
| items | The files information            | \[]MintTask |

The **`MintTask Struct`** is listed as follow:

| Name        | Meaning                                    | Type    |
| ----------- | ------------------------------------------ | ------- |
| app\_id     | The id of the app                          | integer |
| chain\_type | The type of the chain.                     | integer |
| chain\_id   | The id of the chain                        | integer |
| contract    | The address of the contract                | string  |
| mint\_to    | The address of the owner                   | string  |
| token\_uri  | The uri of the token                       | string  |
| token\_id   | The id of the token                        | integer |
| amount      | The amount of the token                    | integer |
| status      | The status of the transaction              | integer |
| hash        | The hash of the transaction                | string  |
| tx\_id      | The id of the transaction                  | integer |
| error       | The error during executing the transaction | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
        "id": 5,
        "created_at": "2022-07-27T11:28:22.34+08:00",
        "updated_at": "2022-07-27T11:28:22.34+08:00",
        "deleted_at": null,
        "app_id": 1,
        "chain_type": 1,
        "chain_id": 1,
        "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
        "mint_to": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
        "token_uri": "http://localhost:8080/assets/metadata/0/nft/35dd0e140460bcb3197ace4364c41f7f5c51b71582c421121e7bea9bcf4391a1.json",
        "token_id": 0,
        "amount": 1,
        "status": 0,
        "hash": "",
        "tx_id": 9,
        "error": ""
    }
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>page</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr><tr><td>limit</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr></tbody></table>
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
{
        "count": 1,
        "items": [
            {
                "id": 1,
                "created_at": "2022-07-27T11:14:09.686+08:00",
                "updated_at": "2022-07-27T11:14:14.921+08:00",
                "deleted_at": null,
                "app_id": 1,
                "chain_type": 1,
                "chain_id": 1,
                "contract": "cfxtest:acf8m2gzrv8pnfsjbne2d28m4h2ycj569uupgys473",
                "mint_to": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
                "token_uri": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png",
                "token_id": 7958647809,
                "amount": 1,
                "status": 2,
                "hash": "",
                "tx_id": 5,
                "error": "failed to get default account: address list is empty"
            }
        ]
    }
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
