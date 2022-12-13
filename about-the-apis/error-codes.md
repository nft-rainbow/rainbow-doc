# Error codes

Most errors in Rainbow-API include an error code and a brief explanation.

The possible errors containing the `error codes`, `status code` and how to fix them are listed in the following. &#x20;

### Auth Errors

| ERROR CODE | ERROR MESSAGE                     | EXPLANATION                                                                                          |
| ---------- | --------------------------------- | ---------------------------------------------------------------------------------------------------- |
| 40100      | `Unauthorized`                    | The account does not have the access to kyc file. Please validate your information.                  |
| 40101      | `Unauthorized, invalid JWT token` | The JWT token is invalied. Please use the correct JWT                                                |
| 40102      | `Authorization header is empty`   | The Authorization header is empty. Please add it.                                                    |
| 40103      | `Authorization token is invalid`  | Your authorization token is invalid. Please use the correct JWT.                                     |
| 40104      | `Token is expired`                | Your JWT is expired. Please call refresh JWT to get a new JWT.                                       |
| 40105      | `KYC required`                    | Your personal information has not been validated. Please validate your information.                  |
| 40106      | `No permission to access`         | Your account does not have the permission to access the kyc files. Please validate your information. |
| 40107      | `Auth header is empty`            | Your auth header is empty. Please add the JWT.                                                       |
| 40108      | `Missing exp field`               | The expired time is missing. Please add it.                                                          |
| 40109      | `Exp must be float64 format`      | The expired time should be float64.                                                                  |
| 40110      | `Jwt payload content uncorrect`   | The payload content uncorrect. Please correct it.                                                    |

{% hint style="info" %}
**Note:** The character `*` means the error message is not stationary. It depends on the detailed error. Please refer the detailed error message.
{% endhint %}

### Validation Errors

| ERROR CODE | ERROR MESSAGE                                                                 | EXPLANATION                                                                                           |
| ---------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| 40000      | `Invalid request`                                                             | Your request is invalid. Please check the parameters.                                                 |
| 40001      | `Invalid app id`                                                              | Your `appid` _is not valid. Please use the correct `app_id`._                                         |
| 40002      | `Invalid address`                                                             | The input address is incorrect. Please check the address.                                             |
| 40003      | `Chain is not supported`                                                      | The chain type is not supported. The chain type includes `conflux` and `conflux_test`.                |
| 40004      | `Contract type is not supported`                                              | The contract type does not be supported. The supported contract type includes `ERC721` and `ERC1155`. |
| 40005      | `Invalid url`                                                                 | The url path is not true. Please check the url again.                                                 |
| 40006      | `Invalid mint amount, mint amount could not be 0`                             | The mint amount is invalied. Please set the mint amount again.                                        |
| 40007      | `Invalid mint amount, mint amount could not more than 1 for erc 721 contract` | The mint amount is invalied. Please set the mint amount again.                                        |
| 40008      | `Invalid token ID`                                                            | The token id is invalied. Please check the token id again.                                            |
| 40009      | `Contract type and contract address not match`                                | The contract type and contract address do not match. Please check the contract type again.            |
| 40010      | `Invalid page or limit`                                                       | The page or limit are invalid. The parameters should be integer.                                      |

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
| 50002      | \*                         | The data does not been found in the database.                       |

### Business Errors

| ERROR CODE | ERROR MESSAGE                                   | EXPLANATION                                                                                             |
| ---------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 60000      | `Business error`                                | The transactions have not been processed. Please wait.                                                  |
| 60001      | `Mint limit exceeded`                           | The number of minted NFTs exceed the limits. Please reduce the number of the minted NFTs.               |
| 60002      | `Deploy limit exceeded`                         | The number of deployed contracts exceed the limits. Please reduce the number of the deployed contracts. |
| 60003      | `Uploade file limit exceeded`                   | The number of uploaded files exceed the limits. Please reduce the number of the uploaded files          |
| 60004      | `Contract has no sponsor`                       | Your contract has no sponsor. Please set the sponsor first.                                             |
| 60005      | `Contract sponsor balance not enough`           | The sponsor balance is not enough. Please connect to the sponsor.                                       |
| 60006      | `Contract has no sponsor for application admin` | The contract has not sponsors.                                                                          |
| 60007      | `Only admin can reset admin`                    | Only the app admin can reset the contract admin.                                                        |
| 60008      | `Contract is not belong to this application`    | Contract does not belong to the application.                                                            |
| 60009      | `Contract not exist`                            | The contract does not exist. Please use the correct one.                                                |
