---
description: >-
  Rainbow-APIs is based on JWT. In order to use the open APIs, login APIs
  provide us entries to get the JWT.
---

# Login

## Login actions

Login actions provide users the entries to call the open APIs including [metadata.md](metadata.md "mention"), [mints.md](mints.md "mention"), [contract.md](contract.md "mention"), [files.md](files.md "mention").

### App Login

`APP login` API helps users to get the JWT according to `app_id` and `app_secret`. JWT can be used to access other open APIs.

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/login" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameters" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>app_id</td><td>The id of the app</td><td>body</td><td>string</td><td>true</td></tr><tr><td>app_secret</td><td>The secret of the app</td><td>body</td><td>string</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
    "app_id": "qUUcdueA",
    "app_secret": "zGCaP8kAFEmwanqo"
}
```
{% endtab %}

{% tab title="Response" %}
The returned result can be used to access other OPEN-APIs

| Name   | Meaning          | Type   |
| ------ | ---------------- | ------ |
| token  | JWT token        | String |
| expire | The expired time | String |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "expire": "2022-08-31T15:54:04.2046805+08:00",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjE5MzI0NDQsImlkIjozLCJvcmlnX2lhdCI6MTY1OTM0MDQ0NH0.BLkzyiQzxlljYLj5Gjjqjnd4fFm1GdoEduaVrVlU_Tw"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/login \
  --header 'Content-Type: application/json' \
  --data-raw `{
    "app_id": "qUUcdueA",
    "app_secret": "zGCaP8kAFEmwanqo"
}`
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Note:** Each JWT is valid to call open APIs for one hour. Once the JWT is expired, users have to call [Refresh JWT](login.md#refresh\_token) to get the new JWT.
{% endhint %}

### Refresh JWT

`Refresh JWT` API helps users to get a new JWT of the specified app.

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/refresh_token" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Response" %}
| Name   | Meaning          | Type   |
| ------ | ---------------- | ------ |
| token  | JWT token        | String |
| expire | The expired time | String |
{% endtab %}

{% tab title="Response Example" %}
```
{
    "expire": "2022-08-31T15:54:04.2046805+08:00",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NjE5MzI0NDQsImlkIjozLCJvcmlnX2lhdCI6MTY1OTM0MDQ0NH0.BLkzyiQzxlljYLj5Gjjqjnd4fFm1GdoEduaVrVlU_Tw"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/refresh_token \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Note: Each JWT is valid to call [Refresh JWT](login.md#refresh\_token) for five hours. Once the JWT is expired, users have to call [App Login](login.md#login) to get JWT agian.
{% endhint %}
