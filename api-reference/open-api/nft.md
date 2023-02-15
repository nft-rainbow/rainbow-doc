---
description: The nft API provide users the entries to interact with the NFTs.
---

# NFT

## Update NFT

### Update NFT token uri

The `Update NFT token uri` API provides users to update the nft token uri according to the contract address and the token\_id.

{% swagger src="../../.gitbook/assets/swagger.json" path="/nft/{address}/{token_id}/tokenUri" method="put" %}
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
| Name          | Meaning                               | Type    |
| ------------- | ------------------------------------- | ------- |
| hash          | The hash of the transaction           | string  |
| state\_code   | The code of the transaction state     | integer |
| state\_msg    | The msg of the state                  | string  |
| is\_finalized | Whether the transaction is finalized  | boolean |
| is\_success   | Whether the transaction is successful | boolean |
| error\_msg    | The msg of the error during executing | string  |
{% endtab %}
{% endtabs %}

## Query NFT

### Query specific NFT of specific account

The `Query specific NFT of specific account` API provides users to get the nft information according to the contract address and the token\_id.

{% swagger src="../../.gitbook/assets/swagger.json" path="/nft/{address}/{token_id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>token_id</td><td>The id of the nft</td><td>Path</td><td>string</td><td>true</td></tr><tr><td>address</td><td>The address of the contract</td><td>Path</td><td>string</td><td>true</td></tr></tbody></table>
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
    "token_id": "17"
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
The token\_id is the number like "123", which type is string
{% endhint %}
