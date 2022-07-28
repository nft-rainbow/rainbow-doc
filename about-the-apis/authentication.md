# Authentication

All the open APIs use a single authentication scheme: a Bearer JWT passed in the HTTP request header.

To obtain the access to [open APIs](../api-reference/open-api/), users have to do the following:

1. Use `app_id` and `app_secret` to call [login](../api-reference/open-api/login.md#login) to get the Bearer JWT.
2. Add the `Authorization: YOUR-BEARER-JWT-HERE` in the request header to call the corresponding API.

{% hint style="info" %}
**Note:** `app_id` and `app_secret` are obtained from Rainbow Console.
{% endhint %}

The Bearer JWT is valid for one hour to call [open APIs](../api-reference/open-api/). Once the token is expired for one hour, users have to call [Refersh JWT](../api-reference/open-api/login.md#refresh\_token) to obtain a new JWT.

{% hint style="info" %}
Note: Bearer JWT is valid for five hours to call [Refersh JWT](../api-reference/open-api/login.md#refresh\_token). Once the token is expired for five hours, users have to call [login](../api-reference/open-api/login.md#login) again.
{% endhint %}

To debug various error codes related to authentication, please see[ Error codes.](error-codes.md)
