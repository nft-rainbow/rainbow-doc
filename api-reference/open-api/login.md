---
description: >-
  Rainbow-APIs is based on JWT. In order to use the open APIs, login inferfaces
  provide us entries to get the JWT.
---

# Login

## Login actions

Login actions provide users the entries to call the open APIs including [metadata.md](metadata.md "mention"), [mints.md](mints.md "mention"), [contract.md](contract.md "mention").&#x20;

### App Login

Firstly, users have to call the `App Login` inferface to get the JWT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/login" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameters" %}
| Name          | Meaning    | Type   |
| ------------- | ---------- | ------ |
| Authorization | Bear Token | string |
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

curl --request POST \
  --url https://localhost:8080/v1/login \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Refresh Open API Token

{% swagger src="../../.gitbook/assets/swagger.json" path="/refresh_token" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameters" %}
| Name          | Meaning    | Type   |
| ------------- | ---------- | ------ |
| Authorization | Bear Token | string |
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning   | Type   |
| ----- | --------- | ------ |
| Toekn | JWT token | String |
|       |           |        |
|       |           |        |
{% endtab %}

{% tab title="Response Example" %}
```
string
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://stoplight.io/mocks/xqyang/test/2579772/v1/refresh_token \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
