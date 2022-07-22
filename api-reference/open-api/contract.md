---
description: >-
  The contract API provide users the entries to interact with the ERC721
  contracts, including deploying the contracts, setting the sponsors and other
  query functions.
---

# Contract

## Contract actions

The `Deploy contract` API helps users to deploy a ERC721 contract.

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/contracts" method="post" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

Conflux provides users the sponsor function. Once a contract is sponsored by an account, the accounts in the contract white list can call this contracts for free.&#x20;

The `Set the sponsor for a contract` API provides users to set sponsers for a specific contract.

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/contracts/:address/sponsor" method="post" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

## Query informations

The `Get the contarct list` API provides users the entry to get the deployed contracts.

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/contracts" method="get" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}

The `Get the sponsor of a contract` API provides users the entry to get the sponsors of a specific contract.&#x20;

{% swagger src="../../.gitbook/assets/swagger.yaml" path="/v1/contracts/:address/sponsor" method="get" %}
[swagger.yaml](../../.gitbook/assets/swagger.yaml)
{% endswagger %}
