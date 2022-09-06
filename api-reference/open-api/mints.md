---
description: >-
  The Mints APIs provide users the entries to mint the NFTs by calling the
  method in the ERC721 or ERC1155 contract.
---

# Mints

## Mint Actions

The Mints APIs provide three methods to help users mint NFTs, including the custom minting, minting with a file and minting with metadata.

### Mint NFT

The `Mint NFT` provides users with the entry to call the ERC721 or ERC1155 contract to mint the NFT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the NFT</td><td>body</td><td>integer</td><td>false</td></tr><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>metadata_uri</td><td>The uri of the metadata</td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_type</td><td>The type of the contract</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "token_id": 123,
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "contract_address": "cfxtest:aca7psszv5pvak2hesk3e33m5yabkn3d5j2gzsmm5n",
    "contract_type": "erc721",
    "metadata_uri": "https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png"
}
```
{% endtab %}

{% tab title="Response" %}
| Name        | Meaning                                                       | Type    |
| ----------- | ------------------------------------------------------------- | ------- |
| amount      | The amount of the nft                                         | integer |
| app\_id     | The id of the app                                             | integer |
| chain\_id   | The id of the chain                                           | integer |
| chain\_type | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                         | integer |
| contract    | The address of the nft                                        | string  |
| error       | The error during executing tx                                 | string  |
| hash        | The hash of the transaction                                   | string  |
| id          | The id of the storage                                                                           | integer |
| mint\_to    | The owner of the nft                                   | string  |
| status      | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id   | The id of the token                                           | integer |
| token\_uri  | The uri of the token                                          | string  |
| tx\_id      | The id of the transaction                                     | integer |
| mint_type      | The type of the minting                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
        {
            "id": 8109,
            "created_at": "2022-08-24T04:56:09.841Z",
            "updated_at": "2022-08-24T04:56:52.986Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
            "contract_type": 0,
            "tx_id": 8121,
            "hash": "0x5e8eafa9cf8fc52f3fb0d0810a86b5ac97ef23c3ba057bfa8a9f889907e65209",
            "status": 1,
            "error": "",
            "mint_to": "cfxtest:aar9up0wsbgtw7f0g5tyc4hbwb2wa5wf7emmk94znd",
            "token_id": 0,
            "amount": 1,
            "token_uri": "https://dev.nftrainbow.xyz/assets/metadata/0/nft/0b7ba21ca161facbf392e8b275f2d62bbf78eb5302f13564415de85879b7cd7bjson",
            "mint_type": 0
        }
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.xyz/v1/mints/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
  --data '{
    "chain": "conflux_test",
    "token_id": "",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "contract_address": "cfxtest:acgat1yux2rk0xmk2s8ceferyprgm0u1hetj0w72yf",
    "metadata_uri": "http://dev.nftrainbow/assets/metadata/0/nft/2dfd6b3add9d5154cf4ccef7a040f4c5c3c965ec5845bd11ca297e8550ac63ee.json"
}'
```
{% endtab %}
{% endtabs %}

### Batch Mint NFTs
The `Batch Mint NFTs` API provides users with the entry to call the ERC721 or ERC1155 contract to mint several NFTs once. 
{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/customizable/batch" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>description</td><td>The description of the NFT</td><td>body</td><td>string</td><td>false</td></tr><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_type</td><td>The type of the contract, which includes <code>erc721</code> and <code>erc1155</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>contract_address</td><td>The address of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>mint_items</td><td>The mint tasks</td><td>body</td><td>The array of the MintItemDto</td><td>true</td></tr></tbody></table>

The MintItemDto construct is presented in the following.
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the NFT</td><td>body</td><td>string</td><td>false</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>amount</td><td>The amount of the NFTs</td><td>body</td><td>integer</td><td>false</td></tr><tr><td>metadata_uri</td><td>The uri of the metadata</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "name": "test-mia",
    "description": "test-mia",
    "contract_type":"erc721",
    "contract_address": "cfxtest:aceng286bm0xnu8s4wdf1xzdchgn0zxxapb1jj597t",
    "mint_items": [
        {
            "mint_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "metadata_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/10",
            "token_id":"10",
            "amount": 1
        },
        {
            "mint_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "metadata_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/11",
            "token_id":"11",
            "amount": 1
        },
        {
            "mint_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "metadata_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/12",
            "token_id":"12",
            "amount": 1
        }
    ]
}
```
{% endtab %}


{% tab title="Response" %}
| Name        | Meaning                                    | Type    |
| ----------- | ------------------------------------------ | ------- |
| id          | The id of the NFTs                          | integer |
| app\_id     | The id of the app                          | integer |
| chain\_type | The type of the chain.                     | integer |
| chain\_id   | The id of the chain                        | integer |
| contract    | The address of the contract                | string  |
| contract_type    | The type of the contract                | integer  |
| mint\_to    | The address of the owner                   | string  |
| token\_uri  | The uri of the token                       | string  |
| token\_id   | The id of the token                        | integer |
| amount      | The amount of the token                    | integer |
| status      | The status of the transaction              | integer |
| hash        | The hash of the transaction                | string  |
| tx\_id      | The id of the transaction                  | integer |
| error       | The error during executing the transaction | string  |
| items       | The items of the NFT intformations | []MintItem |

The MintItem construct is presented in the following:
| Name        | Meaning                                    | Type    |
| ----------- | ------------------------------------------ | ------- |
| id          | The id of the NFTs                          | integer |
| chain\_id   | The id of the chain                        | integer |
| mint\_to    | The address of the owner                   | string  |
| token\_uri  | The uri of the token                       | string  |
| amount      | The amount of the token                    | integer |
| MintBachTaskID       | The id of the mintBach task | integer|
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 1,
    "created_at": "2022-08-22T16:06:21.058+08:00",
    "updated_at": "2022-08-22T16:06:21.058+08:00",
    "deleted_at": null,
    "app_id": 4,
    "chain_type": 1,
    "chain_id": 1,
    "contract": "cfxtest:acbyjkpzzux69s2mpfxz3kw897nuxw01x20tpnbh0e",
    "contract_type": 1,
    "tx_id": 65,
    "hash": "",
    "status": 0,
    "error": "",
    "items": [
        {
            "id": 1,
            "created_at": "2022-08-22T16:06:21.06+08:00",
            "updated_at": "2022-08-22T16:06:21.06+08:00",
            "deleted_at": null,
            "mint_to": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "token_id": 10,
            "amount": 2,
            "token_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/10",
            "MintBatchTaskID": 1
        },
        {
            "id": 2,
            "created_at": "2022-08-22T16:06:21.06+08:00",
            "updated_at": "2022-08-22T16:06:21.06+08:00",
            "deleted_at": null,
            "mint_to": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "token_id": 11,
            "amount": 2,
            "token_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/11",
            "MintBatchTaskID": 1
        },
        {
            "id": 3,
            "created_at": "2022-08-22T16:06:21.06+08:00",
            "updated_at": "2022-08-22T16:06:21.06+08:00",
            "deleted_at": null,
            "mint_to": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "token_id": 12,
            "amount": 2,
            "token_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/12",
            "MintBatchTaskID": 1
        }
    ]
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.xyz/v1/mints/customizable/batch \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \ 
  --data '{
    "chain": "conflux_test",
    "name": "test-mia",
    "description": "test-mia",
    "contract_type":"erc721",
    "contract_address": "cfxtest:aceng286bm0xnu8s4wdf1xzdchgn0zxxapb1jj597t",
    "mint_items": [
        {
            "mint_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "metadata_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/10",
            "token_id":"10",
            "amount": 1
        },
        {
            "mint_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "metadata_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/11",
            "token_id":"11",
            "amount": 1
        },
        {
            "mint_to_address": "cfxtest:aam1eawbm9pzp0dnwv96tts5shnbdfv9nuwu7zgzz8",
            "metadata_uri": "https://live---metadata-5covpqijaa-uc.a.run.app/metadata/12",
            "token_id":"12",
            "amount": 1
        }
    ]
}'
```
{% endtab %}
{% endtabs %}

### Mint NFT with file

The `Mint NFT with file` API provides users with the entry to call the ERC721 or ERC1155 contract to mint the NFT with uploading files. The uploaded files can be images, video and so on.

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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>formData</td><td>string</td><td>true</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>description</td><td>The description of the contract</td><td>formData</td><td>string</td><td>true</td></tr><tr><td>file</td><td>The uploaded file</td><td>formData</td><td></td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name        | Meaning                                                       | Type    |
| ----------- | ------------------------------------------------------------- | ------- |
| amount      | The amount of the nft                                         | integer |
| app\_id     | The id of the app                                             | integer |
| chain\_id   | The id of the chain                                           | integer |
| chain\_type | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                         | integer |
| contract    | The address of the nft                                        | string  |
| error       | The error during executing tx                                 | string  |
| hash        | The hash of the transaction                                   | string  |
| id          | The id of the storage                                                                           | integer |
| mint\_to    | The owner of the nft                                   | string  |
| status      | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id   | The id of the token                                           | integer |
| token\_uri  | The uri of the token                                          | string  |
| tx\_id      | The id of the transaction                                     | integer |
| mint_type      | The type of the minting                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
        {
            "id": 8109,
            "created_at": "2022-08-24T04:56:09.841Z",
            "updated_at": "2022-08-24T04:56:52.986Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
            "contract_type": 0,
            "tx_id": 8121,
            "hash": "0x5e8eafa9cf8fc52f3fb0d0810a86b5ac97ef23c3ba057bfa8a9f889907e65209",
            "status": 1,
            "error": "",
            "mint_to": "cfxtest:aar9up0wsbgtw7f0g5tyc4hbwb2wa5wf7emmk94znd",
            "token_id": 0,
            "amount": 1,
            "token_uri": "https://dev.nftrainbow.xyz/assets/metadata/0/nft/0b7ba21ca161facbf392e8b275f2d62bbf78eb5302f13564415de85879b7cd7bjson",
            "mint_type": 0
        }
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.xyz/v1/mints/easy/files \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: multipart/form-data' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form file= \
  --form chain= 'conflux_test' \
  --form description= 'throll description' \ 
  --form mint_to_address= 'cfxtest:aatk708nbb7573bkwumsu00h0r1rtkcdz2chwhttzk' \
  --form name= 'throll'
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the nft</td><td>body</td><td>string</td><td>true</td></tr><tr><td>chain</td><td>The chain type. The types include <code>conflux</code> and <code>conflux_test</code></td><td>body</td><td>string</td><td>true</td></tr><tr><td>mint_to_address</td><td>The creater of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>description</td><td>The description of the contract</td><td>body</td><td>string</td><td>true</td></tr><tr><td>file_url</td><td>The url of the file</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "chain": "conflux_test",
    "name": "123",
    "description": "123",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "file_url": "http://dev.nftrainbow/assets/file/1/nft/67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111.jpeg"
}
```
{% endtab %}

{% tab title="Response" %}


| Name  | Meaning                          | Type        |
| ----- | -------------------------------- | ----------- |
| count | The number of the uploaded files | integer     |
| items | The files information            | \[]MintTask |

The **`MintTask Struct`** is listed as follow:

| Name        | Meaning                                                       | Type    |
| ----------- | ------------------------------------------------------------- | ------- |
| amount      | The amount of the nft                                         | integer |
| app\_id     | The id of the app                                             | integer |
| chain\_id   | The id of the chain                                           | integer |
| chain\_type | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                         | integer |
| contract    | The address of the nft                                        | string  |
| error       | The error during executing tx                                 | string  |
| hash        | The hash of the transaction                                   | string  |
| id          | The id of the storage                                                                           | integer |
| mint\_to    | The owner of the nft                                   | string  |
| status      | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id   | The id of the token                                           | integer |
| token\_uri  | The uri of the token                                          | string  |
| tx\_id      | The id of the transaction                                     | integer |
| mint_type      | The type of the minting                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
        {
            "id": 8109,
            "created_at": "2022-08-24T04:56:09.841Z",
            "updated_at": "2022-08-24T04:56:52.986Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
            "contract_type": 0,
            "tx_id": 8121,
            "hash": "0x5e8eafa9cf8fc52f3fb0d0810a86b5ac97ef23c3ba057bfa8a9f889907e65209",
            "status": 1,
            "error": "",
            "mint_to": "cfxtest:aar9up0wsbgtw7f0g5tyc4hbwb2wa5wf7emmk94znd",
            "token_id": 0,
            "amount": 1,
            "token_uri": "https://dev.nftrainbow.xyz/assets/metadata/0/nft/0b7ba21ca161facbf392e8b275f2d62bbf78eb5302f13564415de85879b7cd7bjson",
            "mint_type": 0
        }
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.xyz/v1/mints/easy/urls \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json' \
  --data '{
    "chain": "conflux_test",
    "name": "123",
    "description": "123",
    "mint_to_address": "cfxtest:aasr1hmezez1wepvh8ew8sk9p40khhhj1ymxwmpaf0",
    "file_url": "http://dev.nftrainbow/assets/file/1/nft/67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111.jpeg"
}'
```
{% endtab %}
{% endtabs %}

## Obtain Informations
### Obtain NFT list
The `Obtain NFT list` API provides users with the entry to query the NFTs information created on a spcific app.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/" method="get" %}
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
| count | The number of the minted NFTs | integer     |
| items | The nfts information                | \[]MintTask |

The **`MintTask Struct`** is listed as follow:
| Name        | Meaning                                                       | Type    |
| ----------- | ------------------------------------------------------------- | ------- |
| amount      | The amount of the nft                                         | integer |
| app\_id     | The id of the app                                             | integer |
| chain\_id   | The id of the chain                                           | integer |
| chain\_type | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                         | integer |
| contract    | The address of the nft                                        | string  |
| error       | The error during executing tx                                 | string  |
| hash        | The hash of the transaction                                   | string  |
| id          | The id of the storage                                                                           | integer |
| mint\_to    | The owner of the nft                                   | string  |
| status      | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id   | The id of the token                                           | integer |
| token\_uri  | The uri of the token                                          | string  |
| tx\_id      | The id of the transaction                                     | integer |
| mint_type      | The type of the minting                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
 {
        "count": 1,
        "items": [
            {
            "id": 8109,
            "created_at": "2022-08-24T04:56:09.841Z",
            "updated_at": "2022-08-24T04:56:52.986Z",
            "deleted_at": null,
            "app_id": 2,
            "chain_type": 1,
            "chain_id": 1,
            "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
            "contract_type": 0,
            "tx_id": 8121,
            "status": 1,
            "error": "",
            "mint_to": "cfxtest:aar9up0wsbgtw7f0g5tyc4hbwb2wa5wf7emmk94znd",
            "token_id": 0,
            "amount": 1,
            "token_uri": "https://dev.nftrainbow.xyz/assets/metadata/0/nft/0b7ba21ca161facbf392e8b275f2d62bbf78eb5302f13564415de85879b7cd7bjson",
            "mint_type": 0
            }
]
 
    }
```

{% endtab %}


{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.xyz/v1/mints/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Query detailed NFT
The `Query detailed NFT` API provides users with the entry to query the detailed NFT information created on a spcific app according to the NFT's id.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/{id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>id</td><td>NFT id</td><td>path</td><td>integer</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name        | Meaning                                                       | Type    |
| ----------- | ------------------------------------------------------------- | ------- |
| amount      | The amount of the nft                                         | integer |
| app\_id     | The id of the app                                             | integer |
| chain\_id   | The id of the chain                                           | integer |
| chain\_type | The type of the chain                                         | integer |
| contract\_type | The type of the contract                                         | integer |
| contract    | The address of the nft                                        | string  |
| error       | The error during executing tx                                 | string  |
| hash        | The hash of the transaction                                   | string  |
| id          | The id of the storage                                                                           | integer |
| mint\_to    | The owner of the nft                                    | string  |
| status      | The status of the transaction. 0-pending, 1-success, 2-failed | integer |
| token\_id   | The id of the token                                           | integer |
| token\_uri  | The uri of the token                                          | string  |
| tx\_id      | The id of the transaction                                     | integer |
| mint_type      | The type of the minting                                     | integer |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "id": 22,
    "created_at": "2022-08-16T15:14:04.737+08:00",
    "updated_at": "2022-08-16T15:14:40.78+08:00",
    "deleted_at": null,
    "app_id": 4,
    "chain_type": 1,
    "chain_id": 1,
    "contract": "cfxtest:acgraybn1g1upesed09g96vxev79sdhmxjmz7bxzyy",
    "contract_type": 0,
    "tx_id": 14,
    "hash": "0xb060076e19fc4c69fb5399faa2f8c63c0bb3179f54f069b164b84b7c312fef62",
    "status": 1,
    "error": "",
    "mint_to": "cfxtest:aajb342mw5kzad6pjjkdz0wxx0tr54nfwpbu6yaj49",
    "token_id": 14488,
    "amount": 1,
    "token_uri": "http://localhost:8080/assets/metadata/0/nft/2a4dc76844247c2ae927a1a67877e76b4f02f627a5b84667549fbad3d6f57250.json",
    "mint_type": 0
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.xyz/v1/mints/{id} \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
