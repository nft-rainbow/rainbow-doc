---
description: >-
  The Mints APIs provide users the entries to mint the NFTs by calling the
  method in the ERC721 contract.
---

# Mints

## Mint NFTs

The Mints APIs provides three methods to help users mint NFTs, including the custom minting, minting with a file and minting with  a metada.

### Mint a NFT

The `Mint a nft` provides users with the entry to call the ERC721 contract to mint the NFT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}
| Name              | Meaning                     | Param Type | Type    |
| ----------------- | --------------------------- | ---------- | ------- |
| name              | The name of the nft         | body       | string  |
| chain             | The chain type              | body       | string  |
| mint\_to\_address | The creater of the contract | body       | string  |
| contract\_address | The address of the contract | body       | integer |
| metadata\_uri     | The uri of the metadata     | body       | string  |
| Authorization     | Bear JWT                    | Header     | string  |
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

### Mint a NFT with a file

The `Mint a nft by uploading a file` provides users with the entry to call the ERC721 contract to mint the NFT with uploading files.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/files" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}

{% endtab %}

{% tab title="Parameter Example" %}

{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Response Example" %}

{% endtab %}

{% tab title="Request Sample" %}

{% endtab %}
{% endtabs %}

### Mint a NFT with metadata

The `Mint a nft by creating a metadata` provides users with the entry to call the ERC721 contract to mint the NFT with creating metadata.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/urls" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}

{% endtab %}

{% tab title="Parameter Example" %}

{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Response Example" %}

{% endtab %}

{% tab title="Request Sample" %}

{% endtab %}
{% endtabs %}

## Query NFTs

The `Get a nft list of a specific app` API provide users with the entry to query the NFTs information created on a spcific app.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}

{% endtab %}

{% tab title="Parameter Example" %}

{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Response Example" %}

{% endtab %}

{% tab title="Request Sample" %}

{% endtab %}
{% endtabs %}
