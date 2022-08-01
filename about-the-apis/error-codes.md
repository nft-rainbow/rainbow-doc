# Error codes

Most errors in Rainbow-API include an error code and a brief explanation.

The possible errors containing the `error codes`, `status code` and how to fix them are listed in the following. &#x20;

### Auth Errors

| STATUS CODE | ERROR CODE                         | EXPLANATION                                                         |
| ----------- | ---------------------------------- | ------------------------------------------------------------------- |
| 40101       | ERR\_AUTHORIZATION\_JWT            | Auth failed. Please check the input parameaters.                    |
| 40102       | ERR\_AUTHORIZATION\_TOKEN\_MISSING | Your auth header is empty. Please add the JWT.                      |
| 40103       | ERR\_AUTHORIZATION\_TOKEN\_INVALID | Your authorization token is invalid. Please use the correct JWT.    |
| 40104       | ERR\_AUTHORIZATION\_TOKEN\_EXPIRED | Your JWT is expired. Please call refresh JWT to get a new JWT.      |
| 40105       | ERR\_AUTHORIZATION\_NOT\_KYC       | Your info has not been validated. Please validate your information. |

### Validation Errors

| STATUS CODE | ERROR CODE                    | EXPLANATION                                                                                           |
| ----------- | ----------------------------- | ----------------------------------------------------------------------------------------------------- |
| 40000       | ERR\_INVALID\_REQUEST\_OTHERS | Your request is invalid. Please check the parameters.                                                 |
| 40001       | ERR\_INVALID\_APP\_ID         | Your `appid` _is not valid. Please use the correct `app_id`._                                         |
| 40002       | ERR\_INVALID\_ADDRESS         | The input address is incorrect. Please check the address.                                             |
| 40003       | ERR\_INVALID\_CHAIN           | The chain type is not supported. The chain type includes `conflux` and `conflux_test`.                |
| 40004       | ERR\_INVALID\_CONTRACT\_TYPE  | The contract type does not be supported. The supported contract type includes `ERC721` and `ERC1155`. |
| 40005       | ERR\_INVALID\_URL             | The url path is not true. Please check the url again.                                                 |

### Conflict Errors

| STATUS CODE | ERROR CODE                     | EXPLANATION                                                               |
| ----------- | ------------------------------ | ------------------------------------------------------------------------- |
| 40900       | ERR\_CONFLICT\_OTHERS          |                                                                           |
| 40901       | ERR\_CONFLICT\_COMPANY\_EXISTS | The company has been validated by other accounts. Please use another one. |

### Ratelimit Errors

| STATUS CODE | ERROR CODE                      | EXPLANATION                                                                       |
| ----------- | ------------------------------- | --------------------------------------------------------------------------------- |
| 42900       | ERR\_TOO\_MANY\_REQUEST\_OTHERS | Too many requests are sent in the meantime. Please reduce the number of requests. |

### Internal Server Errors

| STATUS CODE | ERROR CODE                    | EXPLANATION                                                         |
| ----------- | ----------------------------- | ------------------------------------------------------------------- |
| 50000       | ERR\_INTERNAL\_SERVER\_OTHERS | <p>There are errors in the </p><p>internal server.</p>              |
| 50001       | ERR\_INTERNAL\_SERVER\_DB     | The databse operation is not correct. Please check your operation.  |

### Business Errors

| STATUS CODE | ERROR CODE                 | EXPLANATION                                                                               |
| ----------- | -------------------------- | ----------------------------------------------------------------------------------------- |
| 60000       | ERR\_NO\_SPONSOR           | Your contract has no sponsor. Please set the sponsor first.                               |
| 60001       | ERR\_MINT\_LIMIT\_EXCEEDED | The number of minted NFTs exceed the limits. Please reduce the number of the minted NFTs. |
