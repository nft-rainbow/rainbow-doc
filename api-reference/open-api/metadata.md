---
description: >-
  The metadata APIs provide users to make preparations for creating NFTs,
  including uploading files and creating nft metadata.
---

# Metadata

## Create metadata actions

### Upload File

The APIs provide users to upload files to get the urls for creating nft metadata.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/files" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameters" %}
| Name          | Meaning       | Param Type          | Type   |
| ------------- | ------------- | ------------------- | ------ |
| Authorization | Bear JWT      | Header              | string |
| file          | uploaded file | multipart/form-data |        |
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

### Create nft metadata

After obtaining the file urls, users can create the nft metadata by calling the [#v1-metadata](metadata.md#v1-metadata "mention").&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameters" %}
| Name           | Meaning                            | Param Type | Data Type       |
| -------------- | ---------------------------------- | ---------- | --------------- |
| Authorization  | Bear JWT                           | Header     | Header / string |
| name           | The name of the metadata           | body       | string          |
| file           | The file url of the metadata       | body       | string          |
| external\_link | The externanl link of the metadata | body       | string          |
| description    | The description of the metadata    | body       | string          |
| attributes     | The attributes of the metadata     | array      | attribute       |

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
curl --request POST\
\--url https://stoplight.io/mocks/xqyang/test/2579772/v1/metadata/\
\--header 'Authorization: '\
\--header 'Content-Type: application/json'
{% endtab %}
{% endtabs %}

## Get the related metadata information&#x20;

### Query Metadata

After metadata is created, users can call this api to query the detailed information of the specific metadata. This api returns the `name`, `description`, `external link`, `file` and `attributes` of the quired metada.

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/:metadata_id" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
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

### Query Metadata List

Users can call the api to get the metadata list. The results are the array of the result of [#v1-metadata-metadata\_id](metadata.md#v1-metadata-metadata\_id "mention").sers can call the api to get the metadata list. The results are the array of the result of [#v1-metadata-metadata\_id](metadata.md#v1-metadata-metadata\_id "mention").

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameters" %}
| Name          | Meaning                     | Param Type | Type           |
| ------------- | --------------------------- | ---------- | -------------- |
| nft\_address  | The address of the contract | query      | string(option) |
| Authorization | Bear JWT                    | Header     | string         |
|               |                             |            |                |
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

### File

After files are uploaded, users can call this api to query the files information including the `file_url`, `file_size`, `file_type` and `file_name.`

{% swagger src="../../.gitbook/assets/swagger.json" path="/metadata/files" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Parameter" %}
| Name          | Meanning | Param Type | Data Type |
| ------------- | -------- | ---------- | --------- |
| Authorization | Bear JWT | Header     | string    |
|               |          |            |           |
|               |          |            |           |
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
