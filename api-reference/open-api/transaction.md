---
description: >-
  The transaction API provide users the entries to interact with the transactions.
---

# Transaction


## Query Transaction

### Query Transaction Information
The `Query Transaction Information` API provides users to get the transaction information according to id.

{% swagger src="../../.gitbook/assets/swagger.json" path="/tx/{id}" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>id</td><td>The id of the transaction</td><td>Path</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                                    | Type    |
| -------------- | ------------------------------------------ | ------- |
| hash             | The hash of the transaction                                   | string                     | string |
| state_code        | The code of the transaction state                          | integer |
| state_msg    | The msg of the state                     | string |
| is_finalized      | Whether the transaction is finalized                        | boolean ||
| is_success       | Whether the transaction is successful                 | boolean  |
| error_msg | The msg of the error during executing                 | string |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "hash": "0xd7b1403ff021df36b98bece9eacdb3cab7cc10c5ff76dfb0f885bc08b362658f",
    "state_code": 3,
    "state_msg": "Excuted and success",
    "is_finalized": true,
    "is_success": true,
    "error_msg": ""
}
```
{% endtab %}

{% tab title="Requst Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/tx/{id} \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
