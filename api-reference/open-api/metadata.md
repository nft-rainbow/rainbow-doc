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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>file</td><td>uploaded file</td><td>multipart/form-data</td><td></td><td>true</td></tr></tbody></table>
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
  "file_name": "http://localhost:8080/assets/file/1/nft/67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111.jpeg",
  "file_size": 11295,
  "file_type": "jpeg",
  "file_url": "67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.xyz/v1/metadata/files \
  --header 'Authorization: 'Bearer {JWT}' \
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>name</td><td>The name of the metadata</td><td>body</td><td>string</td><td>true</td></tr><tr><td>file</td><td>The file url of the metadata</td><td>body</td><td>string</td><td>true</td></tr><tr><td>external_link</td><td>The externanl link of the metadata</td><td>body</td><td>string</td><td>false</td></tr><tr><td>description</td><td>The description of the metadata</td><td>body</td><td>string</td><td>true</td></tr><tr><td>attributes</td><td>The attributes of the metadata</td><td>array</td><td>attribute</td><td>false</td></tr><tr><td>nft_address</td><td>The address of the NFT</td><td>body</td><td>string</td><td>false</td></tr></tbody></table>

The struct of the attributes is listed as bellow.

<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>attribute_name</td><td>The name of the attribute</td><td>body</td><td>string</td><td>false</td></tr><tr><td>display_type</td><td>The display type of the attribute</td><td>body</td><td>string</td><td>false</td></tr><tr><td>trait_type</td><td>The trait type of the attribute</td><td>body</td><td>string</td><td>false</td></tr><tr><td>value</td><td>The value of the attribute</td><td>body</td><td>string</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Parameter Example" %}
```
{
  "attributes": [
    {
      "attribute_name": "mouse",
      "display_type": "test hey hey",
      "trait_type": "big",
      "value": "big"
    }
  ],
  "description": "this is a test metadata",
  "external_link": "https://www.google.com/search",
  "file": "https://www.google.com/search",
  "name": "test"
}
```
{% endtab %}

{% tab title="Responses" %}
| Name          | Meaning                 | Type   |
| ------------- | ----------------------- | ------ |
| metadata\_uri | The uri of the metadata | string |
{% endtab %}

{% tab title="Response Example" %}
```
{
  "metadata_uri": "http://localhost:8080/assets/metadata/1/nft/46708cf66a806743cfc27b110a41a2ea2e1b7a47fbcfb2efc9cac8fd3bf29cd1.json"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST
--url https://api.nftrainbow.xyz/v1/metadata/ \
--header 'Authorization: 'Bearer {JWT}' \
--header 'Content-Type: application/json' \
--data '{
  "attributes": [
    {
      "attribute_name": "mouse",
      "display_type": "test hey hey",
      "trait_type": "big",
      "value": "big"
    }
  ],
  "description": "this is a test metadata",
  "external_link": "https://www.google.com/search",
  "file": "https://www.google.com/search",
  "name": "test"
}'
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>metadata_id</td><td>The id of the metadata</td><td>Path</td><td>Integer</td><td>true</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name           | Meaning                           | Data Type      |
| -------------- | --------------------------------- | -------------- |
| attributes     | The attribute of the metadata     | \[]attributes  |
| description    | The description of the metadata   | string         |
| external\_link | The external link of the metadata | string         |
| file           | The file url of the metadata      | string         |
| name           | The name of the metadata          | string         |

The **attributes struct** is listed as follow:

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
      "attribute_name": "mouse",
      "display_type": "test hey hey",
      "trait_type": "big",
      "value": "big"
    }
  ],
  "description": "this is a test metadata",
  "external_link": "https://www.google.com/search",
  "file": "https://www.google.com/search",
  "name": "test"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://localhost:8080/v1/metadata/:metadata_id \
  --header 'Authorization: 'Bearer {JWT}' \
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
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>nft_address</td><td>The address of the contract</td><td>query</td><td>string</td><td>false</td></tr><tr><td>page</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr><tr><td>limit</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning                          | Type                    |
| ----- | -------------------------------- | ----------------------- |
| count | The number of the uploaded files | integer                 |
| items | The files information            | \[]QueryMetadataRsponse |

The **`QueryMetadataResponse struct`** is listed as follow:

| Name           | Meaning                           | Data Type      |
| -------------- | --------------------------------- | -------------- |
| attributes     | The attribute of the              | \[]attributes  |
| description    | The description of the metadata   | string         |
| external\_link | The external link of the metadata | string         |
| file           | The file url of the metadata      | string         |
| name           | The name of the metadata          | string         |

The **`attributes struct`** is listed as follow:

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
        "count": 1,
        "items": [
            {
                "metadata": {
                    "name": "test",
                    "description": "this is a test metadata",
                    "external_link": "https://www.google.com/search",
                    "file": "https://www.google.com/search",
                    "attributes": [
                        {
                            "attribute_name": "eyes",
                            "trait_type": "test trait",
                            "display_type": "",
                            "value": "big"
                        },
                        {
                            "attribute_name": "mouse",
                            "trait_type": "test hey hey",
                            "display_type": "",
                            "value": "big"
                        }
                    ]
                },
                "uri": "http://localhost:8080/assets/metadata/1/nft/46708cf66a806743cfc27b110a41a2ea2e1b7a47fbcfb2efc9cac8fd3bf29cd1.json"
            }
        ]
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.xyz/v1/metadata/ \
  --header 'Authorization: 'Bearer {JWT}' \
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

{% tab title="Parameters" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>page</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr><tr><td>limit</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
| Name  | Meaning                          | Type           |
| ----- | -------------------------------- | -------------- |
| count | The number of the uploaded files | integer        |
| items | The files information            | \[]ExposedFile |

The **`ExposedFile`** struct is lised as follow:

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
        "count": 1,
        "items": [
            {
                "file_url": "http://localhost:8080/assets/file/1/nft/67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111.jpeg",
                "file_size": 11295,
                "file_type": "jpeg",
                "file_name": "67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111"
            }
        ]
]
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.xyz/v1/metadata/files \
  --header 'Authorization: 'Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}
