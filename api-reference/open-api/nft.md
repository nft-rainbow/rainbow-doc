---
description: >-
  The nft API provide users the entries to interact with the NFTs.
---

# NFT

## Query NFT

### Query specific NFT of specific account
The `Query specific NFT of specific account` API provides users to get the nft information according to the contract address and the token_id.

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
| Name           | Meaning                                    | Type    |
| -------------- | ------------------------------------------ | ------- |
| owner             | The owner of the NFT                                   | string                     |
| contract_address        | The address of the contract                        | string |
| token_id    | The id of the token                     | string |

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
  --url https://api.nftrainbow.xyz/v1/nft/{address}/{token_id} \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}