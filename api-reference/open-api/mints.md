---
description: >-
  The Mints APIs provide users the entries to mint the NFTs by calling the
  method in the ERC721 contract.
---

# Mints

## Mint NFTs

The Mints APIs provides three methods to help users mint NFTs, including the custom minting, minting with a file and minting with  a metada.

The `Mint a nft` provides users with the entry to call the ERC721 contract to mint the NFT.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

The `Mint a nft by uploading a file` provides users with the entry to call the ERC721 contract to mint the NFT with uploading files.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/files" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

The `Mint a nft by creating a metadata` provides users with the entry to call the ERC721 contract to mint the NFT with creating metadata.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints/urls" method="post" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

## Query NFTs

The `Get a nft list of a specific app` API provide users with the entry to query the NFTs information created on a spcific app.

{% swagger src="../../.gitbook/assets/swagger.json" path="/mints" method="get" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}
