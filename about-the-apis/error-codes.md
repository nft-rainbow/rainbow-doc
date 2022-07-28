# Error codes

Most errors in Rainbow-API include an error code and a brief explanation.

The possible errors containing the `error codes`, `status code` and how to fix them are listed in the following. &#x20;

### Auth Errors

| STATUS CODE | ERROR CODE                           | EXPLANATION                                                             |
| ----------- | ------------------------------------ | ----------------------------------------------------------------------- |
| 401         | AUTHORIZATION\_TOKEN\_MISSING\_ERROR | Your auth header is empty. Please add the Bearer JWT.                   |
| 401         | AUTHORIZATION\_TOKEN\_INVALID\_ERROR | Your authorization token is invalid. Please use the correct Bearer JWT. |
| 401         | AUTHORIZATION\_TOKEN\_EXPIRED\_ERROR | Your JWT is expired. Please call refresh JWT to get a new JWT.          |

### Request Validation Errors

| STATUS CODE | ERROR CODE                     | EXPLANATION                                                                                           |
| ----------- | ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 400         | INVALID\_REQUEST\_ERROR        | Your request is invalid. Please check the parameters.                                                 |
| 422         | INVALID\_ADDRESS\_ERROR        | The input address is incorrect. Please check the address.                                             |
| 422         | INVALID\_CHAIN\_ERROR          | The chain type is not supported. The chain type includes `conflux` and `conflux_test`.                |
| 422         | INVALID\_CONTRACT\_TYPE\_ERROR | The contract type does not be supported. The supported contract type includes `ERC721` and `ERC1155`. |
| 422         | INVALID\_URL\_ERROR            | The url path is not true. Please check the url again.                                                 |
| 422         | REQUEST\_TOO\_LARGE\_ERROR     | The request is too large. Please minify the request.                                                  |
| 405         | METHOD\_NOT\_ALLOWED\_ERROR    | The method does not be allowed in the contract.                                                       |

### Requst Limit Errors

| STATUS CODE | ERROR CODE                   | EXPLANATION                                                                               |
| ----------- | ---------------------------- | ----------------------------------------------------------------------------------------- |
| 429         | TOO\_MANY\_REQUESTS\_ERROR   | Too many requests are sent in the meantime. Please reduce the number of requests.         |
| 429         | MINT\_LIMIT\_EXCEEDED\_ERROR | The number of minted NFTs exceed the limits. Please reduce the number of the minted NFTs. |

### Server Errors

| STATUS CODE | ERROR CODE              | EXPLANATION                             |
| ----------- | ----------------------- | --------------------------------------- |
| 500         | INTERNAL\_SERVER\_ERROR | There are error in the internal server. |
