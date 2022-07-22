---
description: >-
  The metadata APIs provide users to make preparations for creating NFTs,
  including uploading files and creating nft metadata.
---

# Metadata

## Create metadata actions

The APIs provide users to upload files to get the urls for creating nft metadata.&#x20;

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/metadata/files" method="post" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

After obtaining the file urls, users can create the nft metadata by calling the [#v1-metadata](metadata.md#v1-metadata "mention").&#x20;

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/metadata/" method="post" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

## Get the related metadata information&#x20;

### Metadata

After metadata is created, users can call this api to query the detailed information of the specific metadata. This api returns the `name`, `description`, `external link`, `file` and `attributes` of the quired metada.

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/metadata/:metadata_id" method="get" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

Users can call the api to get the metadata list. The results are the array of the result of [#v1-metadata-metadata\_id](metadata.md#v1-metadata-metadata\_id "mention").sers can call the api to get the metadata list. The results are the array of the result of [#v1-metadata-metadata\_id](metadata.md#v1-metadata-metadata\_id "mention").

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/metadata/" method="get" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

### File

After files are uploaded, users can call this api to query the files information including the `file_url`, `file_size`, `file_type` and `file_name.`

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/metadata/files" method="get" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}
