# Error codes

Most errors in Rainbow-API include an error code and a brief explanation.

The possible errors containing the `error codes`, `status code` and how to fix them are listed in the following. &#x20;

### Auth Errors

| ERROR CODE | ERROR MESSAGE                    | EXPLANATION                                                                         |
| ---------- | -------------------------------- | ----------------------------------------------------------------------------------- |
| 40101      | \*                               | Auth failed. Please check the input parameters.                                     |
| 40102      | `auth header is empty`           | Your auth header is empty. Please add the JWT.                                      |
| 40103      | `Authorization token is invalid` | Your authorization token is invalid. Please use the correct JWT.                    |
| 40104      | `Token is expired`               | Your JWT is expired. Please call refresh JWT to get a new JWT.                      |
| 40105      | `KYC required`                   | Your personal information has not been validated. Please validate your information. |

{% hint style="info" %}
**Note:** The character `*` means the error message is not stationary. It depends on the detailed error. Please refer the detailed error message.
{% endhint %}

### Validation Errors

| ERROR CODE | ERROR MESSAGE                    | EXPLANATION                                                                                           |
| ---------- | -------------------------------- | ----------------------------------------------------------------------------------------------------- |
| 40000      | `Invalid request`                | Your request is invalid. Please check the parameters.                                                 |
| 40001      | `Invalid app id`                 | Your `appid` _is not valid. Please use the correct `app_id`._                                         |
| 40002      | `Invalid address`                | The input address is incorrect. Please check the address.                                             |
| 40003      | `Chain is not supported`         | The chain type is not supported. The chain type includes `conflux` and `conflux_test`.                |
| 40004      | `Contract type is not supported` | The contract type does not be supported. The supported contract type includes `ERC721` and `ERC1155`. |
| 40005      | `Invalid url`                    | The url path is not true. Please check the url again.                                                 |

### Conflict Errors

| ERROR CODE | ERROR MESSAGE            | EXPLANATION                                                               |
| ---------- | ------------------------ | ------------------------------------------------------------------------- |
| 40900      | `Conflict`               |                                                                           |
| 40901      | `company already exists` | The company has been validated by other accounts. Please use another one. |

### Ratelimit Errors

| ERROR CODE | ERROR MESSAGE       | EXPLANATION                                                                       |
| ---------- | ------------------- | --------------------------------------------------------------------------------- |
| 42900      | `Too many requests` | Too many requests are sent in the meantime. Please reduce the number of requests. |

### Internal Server Errors

| ERROR CODE | ERROR MESSAGE              | EXPLANATION                                                         |
| ---------- | -------------------------- | ------------------------------------------------------------------- |
| 50000      | `Internal Server error`    | <p>There are errors in the </p><p>internal server.</p>              |
| 50001      | `database operation error` | The databse operation is not correct. Please check your operation.  |

### Business Errors

| ERROR CODE | ERROR MESSAGE             | EXPLANATION                                                                               |
| ---------- | ------------------------- | ----------------------------------------------------------------------------------------- |
| 60000      | `Mint limit exceeded`     | Your contract has no sponsor. Please set the sponsor first.                               |
| 60001      | `Contract has no sponsor` | The number of minted NFTs exceed the limits. Please reduce the number of the minted NFTs. |
