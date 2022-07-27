---
description: >-
  Rainbow-APIs is based on JWT. In order to use the open APIs, login APIs
  provide us entries to get the JWT.
---

# Login

## Login actions

Login actions provide users the entries to call the open APIs including [metadata.md](metadata.md "mention"), [mints.md](mints.md "mention"), [contract.md](contract.md "mention").&#x20;

### App Login

`APP login` API helps users to get the JWT according to `app_id` and `app_secret`. JWT can be used to access other open APIs.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/login" method="post" %}
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

| Name  | Meaning   | Type   |
| ----- | --------- | ------ |
| Token | JWT token | String |
{% endtab %}

{% tab title="Response Example" %}
```
string
```


{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://localhost:8080/v1/login \
  --header 'Content-Type: application/json' \
  --data `{
    "app_id": "qUUcdueA",
    "app_secret": "zGCaP8kAFEmwanqo"
}`
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Note:** Each JWT is valid to call open APIs for one hour. Once the JWT is expired, users have to call [Refresh JWT](login.md#refresh\_token) to get the new JWT.&#x20;
{% endhint %}

### Refresh JWT

`Refresh JWT` API helps users to get a new JWT of the specified app.

{% swagger src="../../.gitbook/assets/swagger.json" path="/refresh_token" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning   | Type   |
| ----- | --------- | ------ |
| Token | JWT token | String |
{% endtab %}

{% tab title="Response Example" %}
```
string
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/refresh_token \
  --header 'Authorization: 'Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Note: Each JWT is valid to call [Refresh JWT](login.md#refresh\_token) for five hours. Once the JWT is expired, users have to call [App Login](login.md#login) to get JWT agian.
{% endhint %}
