---
description: >-
  The files APIs provide users to make preparations for creating NFTs including
  uploading files and the corresponding query functions.
---

# Files

### Upload File

`Upload file` API helps users to upload a file to get the corresponding url for creating NFT metadata.  The file can be a video, a image and so on.

{% swagger src="../../.gitbook/assets/swagger.json" path="/files" method="post" %}
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
  --url https://api.nftrainbow.xyz/v1/files \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: multipart/form-data' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form file=
```
{% endtab %}
{% endtabs %}

### Obtain File List

`Obtain file list` API helps users to obtain the list including the inforamion of the files uploaded in the specified app. The information of each file contains `file_url`, `file_size`, `file_type` and `file_name`.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/files" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
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
  --url https://api.nftrainbow.xyz/v1/files \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}



###
