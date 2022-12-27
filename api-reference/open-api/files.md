---
description: >-
  The files APIs provide users to make preparations for creating NFTs including
  uploading files and the corresponding query functions.
---

# Files

### Upload File

`Upload file` API helps users to upload a file to get the corresponding url for creating NFT metadata. The file can be a video, a figure and so on.

{% swagger src="../../.gitbook/assets/swagger.json" path="/files/" method="post" %}
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
  "file_url": "http://dev.nftrainbow/assets/file/1/nft/67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111.jpeg",
  "file_size": 11295,
  "file_type": "jpeg",
  "file_name": "67c96aee8ee1293594a4b4ded15c60ea7853e49c0a2eb41a4805a01a70bc3111"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/files/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: multipart/form-data' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form file=
```
{% endtab %}
{% endtabs %}

### Upload File to OSS

OSS is a storage service provided by Alibaba. Users can choose to upload the files to OSS storage. `Upload file to OSS` API helps users to achieve the target. The file can be a video, a figure and so on.

{% swagger src="../../.gitbook/assets/swagger.json" path="/files/oss" method="post" %}
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
    "file_url": "https://nft-rainbow.oss-cn-hangzhou.aliyuncs.com/file/4/nft/377d21aaeddfff1f4f1fa73498df70a462945bb06f5a984358202cec0682c4d2.jpeg",
    "file_size": 11295,
    "file_type": "jpeg",
    "file_name": "377d21aaeddfff1f4f1fa73498df70a462945bb06f5a984358202cec0682c4d2"
}
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request POST \
  --url https://api.nftrainbow.cn/v1/files/oss \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: multipart/form-data' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form file=
```
{% endtab %}
{% endtabs %}

### Obtain File List

`Obtain file list` API helps users to obtain the list including the inforamion of the files uploaded in the specified app. The information of each file contains `file_url`, `file_size`, `file_type` and `file_name`.

{% swagger src="../../.gitbook/assets/swagger.json" path="/files/" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% tabs %}
{% tab title="Auth" %}
| Name          | Meaning      | Param Type | Data Type |
| ------------- | ------------ | ---------- | --------- |
| Authorization | Bearer Token | Header     | string    |
{% endtab %}

{% tab title="Parameter" %}
<table><thead><tr><th>Name</th><th>Meaning</th><th>Param Type</th><th>Data Type</th><th data-type="checkbox">Required</th><th>Default</th></tr></thead><tbody><tr><td>page</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td><td>1</td></tr><tr><td>limit</td><td>Page Query</td><td>query</td><td>integer</td><td>false</td><td>10</td></tr></tbody></table>
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
        "count": 3,
        "items": [
            {
                "file_url": "http://dev.nftrainbow/assets/file/2/nft/fa6f733c258e3a0f364aeb18198c9e2bae2e2c91bee4d38a1c88fb9cc8a71a1b.jpeg",
                "file_size": 11295,
                "file_type": "jpeg",
                "file_name": "fa6f733c258e3a0f364aeb18198c9e2bae2e2c91bee4d38a1c88fb9cc8a71a1b"
            },
            {
                "file_url": "http://dev.nftrainbow/assets/file/2/nft/06edf22f414234ea59c949104a054ca4af27cd71e87170d99401b50d15651cdc.jpeg",
                "file_size": 11295,
                "file_type": "jpeg",
                "file_name": "06edf22f414234ea59c949104a054ca4af27cd71e87170d99401b50d15651cdc"
            },
            {
                "file_url": "http://dev.nftrainbow/assets/file/2/nft/bf822838b7b3a7dadc96bd6f38defcbb21376852284ded6302aac69a71e58027.jpeg",
                "file_size": 11295,
                "file_type": "jpeg",
                "file_name": "bf822838b7b3a7dadc96bd6f38defcbb21376852284ded6302aac69a71e58027"
            }
        ]
    }
```
{% endtab %}

{% tab title="Request Sample" %}
```
curl --request GET \
  --url https://api.nftrainbow.cn/v1/files/ \
  --header 'Authorization: Bearer {JWT}' \
  --header 'Content-Type: application/json'
```
{% endtab %}
{% endtabs %}

###
