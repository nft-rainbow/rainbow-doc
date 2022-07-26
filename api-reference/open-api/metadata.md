---
description: >-
  The metadata APIs provide users to make preparations for creating NFTs,
  including uploading files and creating NFT metadata.
---

# Metadata

## Create Actions

### Upload File

`Upload file` API helps users to upload a file to get the corresponding url for creating NFT metadata.  The file can be a video, a image and so on.

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/files" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameters" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>file</td><td>uploaded file</td><td>multipart/form-data</td><td></td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Responses" %}
| Name       | Meaning                      | Type    |
| ---------- | ---------------------------- | ------- |
| file\_name | The name of the uploaed file | string  |
| file\_size | The size of the uploaed file | integer |
| file\_type | The type of the uploaed file | string  |
| file\_url  | The url of the uploaed file  | string  |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "file_name": "string",
  "file_size": 0,
  "file_type": "string",
  "file_url": "string"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://localhost:8080/v1/metadata/files \
  --header 'Authorization: ' \
  --header 'Content-Type: multipart/form-data' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form file=
```
{% endtab %}
{% endtabs %}

### Create NFT Metadata

`Create NFT metadata` API helps users to create their own metadata after calling [Upload File](metadata.md#metadata-files) to get the corresponding file url.  To call  `Create NFT metadata` , users have to provide the metadata information including `name`, `file`, `external_link` and so on.

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameters" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the metadata</td><td>body</td><td>string</td><td>false</td></tr><tr><td>file</td><td>The file url of the metadata</td><td>body</td><td>string</td><td>false</td></tr><tr><td>external_link</td><td>The externanl link of the metadata</td><td>body</td><td>string</td><td>false</td></tr><tr><td>description</td><td>The description of the metadata</td><td>body</td><td>string</td><td>false</td></tr><tr><td>attributes</td><td>The attributes of the metadata</td><td>array</td><td>attribute</td><td>false</td></tr></tbody></table>

The struct of the attributes is listed as bellow.

| Name            | Meaning                           | Param Type | Type   |
| --------------- | --------------------------------- | ---------- | ------ |
| attribute\_name | The name of the attribute         | body       | string |
| display\_type   | The display type of the attribute | body       | string |
| trait\_type     | The trait type of the attribute   | body       | string |
| value           | The value of the attribute        | body       | string |
{% endtab %}

{% tab title="Parameter Example" %}
```
{
  "attributes": [
    {
      "attribute_name": "string",
      "display_type": "string",
      "trait_type": "string",
      "value": "string"
    }
  ],
  "description": "string",
  "external_link": "string",
  "file": "string",
  "name": "string"
}
```
{% endtab %}

{% tab title="Responses" %}
| Name          | Meaning                 | Type   |
| ------------- | ----------------------- | ------ |
| metadata\_uri | The uri of the metadata | string |
|               |                         |        |
|               |                         |        |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "metadata_uri": "string"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
/curl --request POST
--url https://localhost:8080/v1/metadata/
--header 'Authorization: '
--header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

## Get Informations&#x20;

### Query Metadata

`Query metadata` API helps users to query the detailed information of the specified metadata according to `metadata_id`. This api returns the `name`, `description`, `external link`, `file` and `attributes` of the queried metada.

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/:metadata_id" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameters" %}
| Name          | Meaning                | Param Type | Data Type |
| ------------- | ---------------------- | ---------- | --------- |
| metadata\_id  | The id of the metadata | Path       | Integer   |
| Authorization | Bear JWT               | Header     | string    |
|               |                        |            |           |
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                           | Param Type     | Data Type   |
| -------------- | --------------------------------- | -------------- | ----------- |
| attributes     | The attribute of the              | array\[object] | attributes  |
| description    | The description of the metadata   | body           | string      |
| external\_link | The external link of the metadata | body           | string      |
| file           | The file url of the metadata      | body           | string      |
| name           | The name of the metadata          | body           | string      |

The struct of the attributes is listed as bellow.

| Name            | Meaning                          | Type   |
| --------------- | -------------------------------- | ------ |
| attribute\_name | The name of the attribute        | string |
| display\_type   | The display type of the attribut | string |
| trait\_type     | The trait type of the attribute  | string |
| value           | The value of the attribute       | string |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "attributes": [
    {
      "attribute_name": "string",
      "display_type": "string",
      "trait_type": "string",
      "value": "string"
    }
  ],
  "description": "string",
  "external_link": "string",
  "file": "string",
  "name": "string"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/metadata/:metadata_id \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Obtain Metadata List

`Query metadata list` API helps users to obain the metadata list including the information of the metadata created in the specified app. The `nft_address` is optional. This API returns the array of the result from calling [Query matadata](metadata.md#metadata-metadata\_id).

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameters" %}
| Name         | Meaning                     | Param Type | Type           |
| ------------ | --------------------------- | ---------- | -------------- |
| nft\_address | The address of the contract | query      | string(option) |
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                           | Param Type     | Data Type   |
| -------------- | --------------------------------- | -------------- | ----------- |
| attributes     | The attribute of the              | array\[object] | attributes  |
| description    | The description of the metadata   | body           | string      |
| external\_link | The external link of the metadata | body           | string      |
| file           | The file url of the metadata      | body           | string      |
| name           | The name of the metadata          | body           | string      |

The struct of the attributes is listed as bellow.

| Name            | Meaning                          | Type   |
| --------------- | -------------------------------- | ------ |
| attribute\_name | The name of the attribute        | string |
| display\_type   | The display type of the attribut | string |
| trait\_type     | The trait type of the attribute  | string |
| value           | The value of the attribute       | string |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "metadata": {
      "attributes": [
        {
          "attribute_name": "string",
          "display_type": "string",
          "trait_type": "string",
          "value": "string"
        }
      ],
      "description": "string",
      "external_link": "string",
      "file": "string",
      "name": "string"
    },
    "uri": "string"
  }
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/metadata/ \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

### Obtain File List

`Obtain file list` API helps users to obtain the list including the inforamion of the files uploaded in the specified app. The information of each file contains `file_url`, `file_size`, `file_type` and `file_name`.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/files" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Response" %}
| Name       | Meaning                      | Type    |
| ---------- | ---------------------------- | ------- |
| file\_name | The name of the uploaed file | string  |
| file\_size | The size of the uploaed file | integer |
| file\_type | The type of the uploaed file | string  |
| file\_url  | The url of the uploaed file  | string  |
{% endtab %}

{% tab title="Response Example" %}
```
[
  {
    "file_name": "string",
    "file_size": "string",
    "file_type": "string",
    "file_url": "string"
  }
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/metadata/files \
  --header 'Authorization: ' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
