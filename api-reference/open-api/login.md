---
description: >-
  Rainbow-APIs is based on JWT. In order to use the open APIs, login inferfaces
  provide us entries to get the JWT.
---

# Login

## Login actions

Login actions provide users the entries to call the open APIs including [metadata.md](metadata.md "mention"), [mints.md](mints.md "mention"), [contract.md](contract.md "mention"). Firstly, users have to call the `App Login` inferface to get the JWT.

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/login" method="post" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

{% hint style="info" %}
**Good to know:** The JWT is valid for one hour. If the token is expired, users have to call the [#v1-refresh\_token](login.md#v1-refresh\_token "mention") to get the new token.
{% endhint %}

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/refresh_token" method="post" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}
